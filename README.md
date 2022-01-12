# advances-in-speech-synthesis

AVD(automated video dubbing), TTS with lip sync constraints.

[Neural Dubber](https://arxiv.org/abs/2110.08243) :
- given input text and corresponding video segment of a talking face, model should synthesize lips aligned audio spectrogram.
- image based speaker embedding (ISE). Given **pictures of a speaker (image domain)** model should learn speaker embedding, which encodes: **timber, F0 of a corresponding speaker (audio domain)**
- example of **multi-modal TTS**. inputs: (text, video) outputs: (audio)
- text-video learnable aligner module, with monotonicity constraint.
- experiments on a single-speaker taken from [lip2wav](https://github.com/Rudrabha/Lip2Wav) and multi-speaker [LRS2](https://www.robots.ox.ac.uk/~vgg/data/lip_reading/lrs2.html) datasets.
