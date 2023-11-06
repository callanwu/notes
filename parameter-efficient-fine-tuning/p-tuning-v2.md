# P-tuning v2

类似于Prefix Tuning，P-Tuning v2是针对Prefix Tuning的改进。

* 不同的文本生成任务可能有不同的最佳提示长度。针对简单任务：如情感分析，较短的Prompt（\~20）即可取得不错的效果。 针对复杂任务：如阅读理解，需要更长的Prompt（\~100）。
* 采用随机初始化的分类头\[CLS]应用于tokens之上，以增强通用性，可以适配到序列标注任务。

Prefix Tuning 与 P-Tuning v2 最主要的差别就是是否使用MLP进行重新参数化编码。在peft框架中，只需要更改prefix\_projection，默认值为false，表示使用P-Tuning v2， 如果为true，则表示使用 Prefix Tuning。

## Embedding v.s. MLP reparameterization.

In both prefix-tuning and Ptuning, authors discover the reparameterization to be useful in improving training speed, robustness and performance. However, we conduct experiments to show that the reparameterization effect is inconsistent across different NLU tasks and datasets.

Code：[https://github.com/huggingface/peft/blob/02f0a4ca5992bf516b9807c5870811ef8ad199fa/src/peft/tuners/prefix\_tuning/model.py#L21](https://github.com/huggingface/peft/blob/02f0a4ca5992bf516b9807c5870811ef8ad199fa/src/peft/tuners/prefix\_tuning/model.py#L21)
