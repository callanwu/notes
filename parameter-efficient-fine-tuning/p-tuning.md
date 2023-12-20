# P-Tuning

P-Tuning是针对Prompt Tuning的改进。 考虑到预训练模型本身的embedding就比较离散了，同时prompt本身也是互相关联的，所以用一个LSTM+MLP去编码这些virtual token以后，再输入到模型。

在peft框架中，LSTM是可选的。

## Why LSTM encoder？

There will be additional experiment results on the comparison of direct embedding and LSTM encoder. A general conclusion is that for small pre-trained models, direct embedding converges slower but has a similar performance to LSTM, while in large models direct embedding shows a poorer performance.

Paper:

[https://arxiv.org/pdf/2104.08691.pdf](https://arxiv.org/pdf/2104.08691.pdf)

Model Code：

[https://github.com/huggingface/peft/blob/v0.6.0/src/peft/tuners/p\_tuning/model.py](https://github.com/huggingface/peft/blob/v0.6.0/src/peft/tuners/p\_tuning/model.py)
