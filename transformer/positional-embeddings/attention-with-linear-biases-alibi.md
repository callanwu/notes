# Attention with Linear Biases (ALiBi)

* 不给词向量加入位置嵌入向量，而是用一个和query, key之间的距离成比例的一个“惩罚项”来偏置query-key的注意力得分。给注意力加上线性偏置的方法。

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

When using ALiBi, we do not add position embeddings at any point in the network. The only modification we apply is after the query-key dot product, where we add a static, non-learned bias:

$$softmax(q_{i}K^{\top} + m · [−(i − 1), ..., −2, −1, 0])$$

,where scalar $$m$$ is a head-specific slope fixed before training.

Code:

[https://nn.labml.ai/transformers/alibi/index.html](https://nn.labml.ai/transformers/alibi/index.html)
