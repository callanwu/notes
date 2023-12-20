# LoRA

Pre-trained lau=nguage models have a low "**instrisic dimension**".

During training, $$W_0$$ is frozen and does not receive gradient updates, while $$A$$ and $$B$$contain trainable parameters. Note both $$W_0$$and $$\Delta W=BA$$are multiplied with the same input, and their respective output vectors are summed coordinate-wise. For $$h = W_0x$$, our modified forward pass yields:&#x20;

$$
h = W_0 x + \Delta W x = W_0 x + BA x
$$

We use a random Gaussian initialization for $$A$$ and zero for $$B$$, so $$\Delta W=BA$$ is zero at the beginning of training.

In principle, we can apply LoRA to any subset of weight matrices in a a neural network to reduce the number of trainable parameters.

**Scaling factor** $$\alpha$$**.** Once the low-rank update to the weight matrix is derived, we scale it by $$\alpha$$alpha factor $$\alpha$$ prior to adding it to the model’s pretrained weights. The value of $$\alpha$$ can be changed to balance the importance of the pretrained model and new task-specific adaptation. When optimizing with Adam, tuning $$\alpha$$ is roughly the same as tuning the learning rate if we scale the initialization appropriately.

**Comparison to adapter layers.** At first glance, the approach used by LoRA might seem similar to adapter layers. However, there are two notable differences:

1. There is no non-linearity between the two linear projections.
2. The rank decomposition matrix is injected into an existing layer of the model, instead of being sequentially added as an extra layer.

It is more preferable to adapt more weight matrices than adapting a single type of weights with a larger rank.

Some tips:

* Performing multiple epochs of training over the finetuning dataset is oftentimes not beneficial (i.e., degrades performance).
* Applying LoRA across all weight matrices in the transformer is better than just applying LoRA to the query and value matrices.
* Setting $$\alpha$$ to 2X the value of $$r$$ yields competitive results. Larger values of $$r$$ call for larger values of α, and `r` is a hyperparameter that must be tuned.

params\_num = L \* 2 \*  $$d_{model}$$ \* embedding\_size \* 2  ($$W_q$$ and $$W_v$$)

Paper:

[https://arxiv.org/pdf/2106.09685.pdf](https://arxiv.org/pdf/2106.09685.pdf)

Model Code：

[https://github.com/huggingface/peft/tree/main/src/peft/tuners/lora](https://github.com/huggingface/peft/tree/main/src/peft/tuners/lora)
