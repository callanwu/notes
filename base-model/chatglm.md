# ChatGLM1

ChatGLM1是清华大学提出的支持中英双语问答的对话语言模型。ChatGLM-6B采用了prefix decoder-only的transformer模型框架，在输入上采用双向的注意力机制，在输出上采用单向注意力机制。

* embedding层梯度缩减
* 采用了基于Deep Norm的post layer norm
* 采用了GeGLU激活函数
* 采用了旋转位置编码RoPE
* ChatGLM-6B的训练任务是自回归文本填空。相比于采用causal decoder-only结构的大语言模型，采用prefix decoder-only结构的ChatGLM-6B存在一个劣势：训练效率低。
* 词表大小为130528
