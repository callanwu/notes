# Prompt Tuning

In contrast to _hard_ prompt tuning, _soft_ prompt tuning concatenates the embeddings of the input tokens with a trainable tensor that can be optimized via backpropagation to improve the modeling performance on a target task.&#x20;

不需要加入 MLP 进行调整。

Prompt Tuning采用类标签初始化模型的效果更好。在peft框架中，设置prompt\_tuning\_init，在prompt-tuning\_init\_tetx中输出类标签，即本来的prompt，例如 predict if sentiment of this review is positive, negative or neutral.

params\_num = virtual\_tokens\_num  \* $$d_{model}$$

Paper:

[https://arxiv.org/pdf/2104.08691.pdf](https://arxiv.org/pdf/2104.08691.pdf)
