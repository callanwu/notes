# P-tuning-v2

类似于Prefix Tuning，P-Tuning v2是针对Prefix Tuning的改进。

- 不同的文本生成任务可能有不同的最佳提示长度。针对简单任务：如情感分析，较短的Prompt（~20）即可取得不错的效果。
针对复杂任务：如阅读理解，需要更长的Prompt（~100）。
- 采用随机初始化的分类头[CLS]应用于tokens之上，以增强通用性，可以适配到序列标注任务。
