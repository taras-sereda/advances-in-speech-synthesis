# advances-in-speech-synthesis

Self-supervised learning:
[VATT: Transformers for Multimodal Self-Supervised Learning from Raw Video, Audio and Text](https://arxiv.org/abs/2104.11178)


[UNSUPERVISED PRETRAINING TRANSFERS WELL ACROSS LANGUAGES](https://arxiv.org/pdf/2002.02848.pdf):
- a CPC based approach with slight modifications, where LSTM is used instead of GRU.
- stabilization of training, by replacing batch normalization with channel-wise normalization layer.
- linear classificator is replaced with 1 layer transformer. The intuitions is that it's hard to represent outputs as independent linearly separable units. Since phonemes themselves are just discrete abstractions of a continues singnal.


AVD(automated video dubbing), TTS with lip sync constraints.

[Neural Dubber](https://arxiv.org/abs/2110.08243):
- given input text and corresponding video segment of a talking face, model should synthesize lips aligned audio spectrogram.
- image based speaker embedding (ISE). Given **pictures of a speaker (image domain)** model should learn speaker embedding, which encodes: **timber, F0 of a corresponding speaker (audio domain)**
- example of **multi-modal TTS**. inputs: (text, video) outputs: (audio)
- text-video learnable aligner module, with monotonicity constraint.
- experiments on a single-speaker taken from [lip2wav](https://github.com/Rudrabha/Lip2Wav) and multi-speaker [LRS2](https://www.robots.ox.ac.uk/~vgg/data/lip_reading/lrs2.html) datasets.

Vocoders (spectrogram to waveform):

[Parallel WaveGAN](https://arxiv.org/abs/1910.11480):

unofficial implementation: https://github.com/kan-bayashi/ParallelWaveGAN

official samples: https://r9y9.github.io/demos/projects/icassp2020/

- distilation free, parallel, wavenet like (no casual convolutions) vocoder.
- optimized by joint minimization of adversarial loss and multi-resolution STFT to capture time-frequencty distribution of realistic speech.
- multi-resolution loss itself consists of **spectral convergence** loss (emphesizes high energy components of spectrum) and **l1_log_stft** loss (emphesizes low energy components). Resolutions: [10, 25, 50] ms
- trained with RAdam, disrciminator starts to train at 100_000 interation.
- batch size of 8 elements, each of 1 sec duration.
- Japanese corpus of a single speaker, sampled at 24 kHz
- **on real data** vocoder trained with adversarial loss (parallelWaveGAN) perfoms worse then distilation based vocoder (ClariNet) (adding GAN loss doesn't help to improve its quality).
- **on synth data(from TTS)** parallelWaveGAN achieves better performance then ClariNet, interesting thta ClariNet with adversarial loss is more robust to data from TTS then same model but trained without adversarial loss.
- they use TTS, which accepts suqence of phonemes and accents (for Japanese) [Yasuda, Wang](https://arxiv.org/abs/1810.11960v1)
