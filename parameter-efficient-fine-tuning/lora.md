# LoRA

预训练的语言模型具有较低的内在维度。

$$f(x) = x * e^{2 pi i \xi x}$$

对于预训练的权重矩阵\$$ W\_0\in \mathbb{R}^{d\times k} \$$，通过低秩分解 $W\_0+\Delta W=W\_0+BA$, where $B\in \mathbb{R}^{d\times r}, A\in \mathbb{R}^{r\times k}$ 表示,后者来约束其更新，秩 $r \ll \min(d,k)$ 。

在训练期间， $W\_0$ 被冻结并且不接收梯度更新，而$A$和$B$包含可训练参数。注意，$W\_0$ 和 $\Delta W=BA$ 都与相同的输入相乘，并且它们各自的输出矢量在坐标方向上相加。对于 $h = W\_0x$,，修改的前向传递产生： $h = W\_0 x + \Delta W x = W\_0 x + BA x$

对 $A$ 使用随机高斯初始化，对 $B$ 使用零初始化，因此$\Delta W=BA$在训练开始时为零。

LoRA 原文中大多数实验是对$ W\_q$ 和 $W\_v$ 进行低秩分解。

params\_num = r \* embedding\_size \* 4 ($ W\_q$ and $W\_v$ , r-> embedding\_size and embedding\_size -> r)

During training, $W\_0$ is frozen and does not receive gradient updates, while $A$ and $B$ contain trainable parameters. Note both $W\_0$ and $\Delta W=BA$ are multiplied with the same input, and their respective output vectors are summed coordinate-wise. For $h = W\_0x$, our modified forward pass yields: $ h = W\_0 x + \Delta W x = W\_0 x + BA x $

We use a random Gaussian initialization for $A$ and zero for $B$, so $\Delta W=BA$ is zero at the beginning of training.
