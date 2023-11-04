# BLOOM

BLOOM系列模型是由BigScience团队训练的大语言模型。训练数据包含了英语、中文、法语、西班牙语、葡萄牙语等共46种语言，另外还包含13种编程语言。

* embedding layer norm
* 使用了pre layer Norm
* 激活函数：采用了GeLU激活函数
* 采用了相对位置编码ALiBi
* 使用Byte Pair Encoding(BPE)算法进行训练得到tokenizer，词表大小为250880
