
## Table of contents

- [Abstract](#Abstract)
- [Pretraining Language Models](#pretraining)
- [Reward Model](#reward-model)
- [Fine-tuning with RL](#fine-tuning)
- [Copyright and license](#copyright-and-license)


## Abstract

RKHF (Reinforcement learning from human feedback) is a challenging concpet because it involves a multiple-model
training process and diffrent stages of deployemnt. 
    The process goes through three steps:
        1/ Pretraining a language model (LM);
        2/ Gathering data and training a reward model;
        3/ Fine-tuning the LM with reinforcement learning;

## Pretraining Language Model

This Concpet uses a language model that has already been pretrained for example OpenAI used a smaller version of GPT-3 for its model [InstructGPT](https://openai.com/blog/instruction-following/), DeepMind used their 280 billion parameter model [Gopher](https://www.deepmind.com/blog/language-modelling-at-scale-gopher-ethical-considerations-and-retrieval/).

the model can also be fine-tuned on additinal text or conditions, but its not a required technique to understand RLHF. With language model (LM) we need to generate data to be able to train a reward model, which is how human preferences are integrated into the system.

![Langauge Model Training](languageModel_training.png)

## Reward Model

Generating a reward model is where this RLHF concpet begins, the goal is to get a model to that takes a squence of text, and returns a scalar reward which should numerically represents the human preference. The system could be either end-to-end language model or a modular system outputting a reward (basically the model ranks the outputs, and the ranking is converted to rewards). The output beging a scalar reward is critical for exsting RL algorithm being integrated seamlssly later in the RLHF process. These LMs could be either trained from scratch or fimne-tuned models, however, the LMs trained from scrtach could be more sample efficient than a fine-tuned models.

There are multiple methods for ranking the text. One method that has been sucessful is to have users compare generated text from two language models conditioned on the same promot.

At this level the RLHF system, has initial language model that can be used to generate text and a prefrence model that takes in any assigns it a score of how well humans preceive it. Next, we use reinforcement learning (RL) to optimize the original language model with respect to the reward model.

![Reward Model](reward_model.png)

## Fine-tuning


## Copyright and license

This work is inspiried by the following blog post [Illustrating Reinforcement Learning from Human Feedback](https://huggingface.co/blog/rlhf).


