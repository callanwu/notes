# LLaMA-Adapter

与[Prefix Tuning](./prefix-tuning.md)思路相似。

但是每个transformer层都有各自不同的可学习参数。
解决的问题是：随机初始化的张量可能会损坏预训练的语义所学的知识，导致微调不稳定和性能损失。

- 引入了零初始化的注意力机制和门控机制
- 只修改深层的L个transformer层

params_num = L * virtual_tokens_num * embedding_size + L (adaption_prompt + adaption_gate)