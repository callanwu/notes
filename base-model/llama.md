# LLaMA

LLaMA是Meta提出的大语言模型。训练数据是以英语为主的拉丁语系，另外还包含了来自GitHub的代码数据。训练数据以英文为主，不包含中韩日文，所有训练数据都是开源的，分词之后大约有1400B的tokens。

* 使用了pre-layer Norm
* 激活函数使用了SwiGLU
* 采用了旋转位置编码RoPE
* 使用了Sentence Piece作为tokenizer，词表大小只有32000，即把token切得很碎，需要多个token才能表示一个汉字

