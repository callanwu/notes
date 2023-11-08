# LLaMA2

* 采用了旋转位置编码RoPE
* 激活函数采用SwiGLU
* 残差连接与层归一化前置，归一化方法采用RMSNorm

34B和70B:

* 将Attention子层的MHA改成GQA，Group\_num=8 整体参数量会有减少

原本Attention子层参数量：3\*head\_num\*attention\_dim\*embedding\_dim (head\_num\*attention\_dim = embedding\_dim)+embedding\_dim\*embedding\_dim($$W_q$$、$$W_k$$、$$W_v$$+$$W_o$$)

Group-Query Attention(GQA)子层参数量：

head\_num\*attention\_dim\*embedding\_dim+1/8\*2\*head\_num\*attention\_dim\*embedding\_dim+embedding\_dim\*embedding\_dim($$W_q$$、$$W_k$$、$$W_v$$+$$W_o$$)

Code：[https://github.com/facebookresearch/llama/blob/main/llama/model.py#L291C1-L293](https://github.com/facebookresearch/llama/blob/main/llama/model.py#L291C1-L293)

* 扩充了FFN子层的维度：增强泛化能力，整体参数量有增加
