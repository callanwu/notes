# Rotary Positional Embeddings(RoPE)

* RoPE通过绝对位置编码的方式实现相对位置编码，综合了绝对位置编码和相对位置编码的优点。
* 主要就是对attention中的q, k向量注入了绝对位置信息，然后用更新的q,k向量做attention中的内积就会引入相对位置信息了。即相当于对相关性添加了位置相关性的校正。

Rotary encoding transforms pairs of features by rotating in the 2D plane.

For position $$m$$,

$$\begin{pmatrix}     x^{(i)}_m \cos m \theta_i - x^{(i + \frac{d}{2})}_m \sin m \theta_i \\     x^{(i + \frac{d}{2})}_m \cos m\theta_i + x^{(i)}_m \sin m \theta_i \\     \end{pmatrix}$$

$$\theta_i = 10000^{-\frac{2(i-1)}{d}}, i \in [1, 2, ..., \frac{d}{2}]$$

Models used this methods: ChatGLM, LLaMA, PaLM

Code：[https://github.com/labmlai/annotated\_deep\_learning\_paper\_implementations/blob/master/labml\_nn/transformers/rope/\_\_init\_\_.py](https://github.com/labmlai/annotated\_deep\_learning\_paper\_implementations/blob/master/labml\_nn/transformers/rope/\_\_init\_\_.py)

[https://github.com/huggingface/transformers/issues/25199](https://github.com/huggingface/transformers/issues/25199)

[https://github.com/facebookresearch/llama/blob/main/llama/model.py#L280](https://github.com/facebookresearch/llama/blob/main/llama/model.py#L280)&#x20;
