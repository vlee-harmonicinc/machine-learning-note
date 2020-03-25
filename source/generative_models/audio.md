# Audio
## WaveNet 
[WaveNet: A Generative Model for Raw Audio (2016)](https://arxiv.org/abs/1609.03499) by DeepMind  
[WaveNet: A generative model for raw audio | DeepMind](https://deepmind.com/blog/article/wavenet-generative-model-raw-audio)
> * We show that WaveNets can generate raw speech signals with subjective naturalness never before reported in the field of text-to-speech (TTS), as assessed by human raters.
> * In order to deal with long-range temporal dependencies needed for raw audio generation, we develop new architectures based on **dilated causal convolutions**, which exhibit very large receptive fields.
> * We show that when **conditioned on a speaker identity**, a single model can be used to **generate different voices**.
> * The same architecture shows strong results when tested on a small speech recognition dataset, and is promising when used to generate other audio modalities such as music

P.S.
> We observed that adding speakers resulted in better validation set performance compared to training solely on a single speaker. This suggests that WaveNet’s internal representation was shared among multiple speakers