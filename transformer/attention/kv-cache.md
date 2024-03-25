# KV Cache

* $$Att_k$$只与$$Q_k$$有关，之前已经计算的Attention完全不需要重新计算。
* 推理第 $$x_k$$个字符的时候只需要输入字符$$x_{k-1}$$即可。
* 每轮推理只需读取Cache，同时将当前轮计算出的新的Key、Value追加写入至Cache，本质就是Concat操作。

Code：[https://github.com/huggingface/transformers/blob/main/src/transformers/models/gpt2/modeling\_gpt2.py#L318C1-L331C97](https://github.com/huggingface/transformers/blob/main/src/transformers/models/gpt2/modeling\_gpt2.py#L318C1-L331C97)
