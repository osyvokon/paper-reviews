## [ELECTRA: Pre-training Text Encoders as Discriminators Rather Than Generators](https://openreview.net/pdf?id=r1xMH1BtvB)

### What

A new pre-training method that is more sample and compute efficient than masked language modelling (MLM) tasks like BERT, GPT and XLNet.

### How

1. Instead of masking, replace some tokens with plausible alternatives sampled from a small generator network.
2. Train a discriminative model that predicts which of the tokens were replaced.
3. After training, throw away the generator (1) and just use the discriminator (2).

![image-20200228121413711](_img/image-20200228121413711.png)


### Results

* ELECTRA requires much less compute to achieve scores of larger models like GPT and BERT:
  ![image-20200228121440192](_img/image-20200228121440192.png)
* The method works well for small models and with small amounts of compute. It also works at scale: it performs comparably to RoBERTa and XLNet while using less than 1/4 of their compute and outperforms them when using the same amount of compute.

