# [Leveraging Pre-trained Checkpoints for Sequence Generation Tasks](https://arxiv.org/pdf/1907.12461.pdf)

`#pretraining` `#seq2seq`

## What

What is the best way to leverage publicly available pre-trained checkpoints
from BERT and GPT-2 for warm-starting seq2seq models?

## How

Initialize encoder and decoder (independently) with a pretrained BERT, GPT-2, or
with random weights. You get a number of models like BERT2RND, RND2BERT,
RND2RND, BERT2GPT and so on.

Train and evaluate those models on the following tasks: sentence fusion,
split and rephrase, machine translation, abstractive summarization.

There are two other models they tried:

- Bert2Bert with the parameters between encoder and decoder shared.
- A decoder-only GPT model where the they treat input as a conditioning prefix
  of a language model.

Overall, they run over 300 experiments, spending thousands of TPU hours.

## Key findings

* Initializing *encoder* with BERT helps.

* Most task (but not machine translation) benefit from shared encoder and
  decoder.

* Bert2Gpt did not work well. This undermines HuggingFace's motivational
  example from their [encoders-decoders post](https://medium.com/huggingface/encoder-decoders-in-transformers-a-hybrid-pre-trained-architecture-for-seq2seq-af4d7bf14bb8):

    > They allow you to combine, for instance, the NLU superpowers of BERT with
    > the generation superpowers of GPT-2.