# Prefix Tuning

Prefix-Tuning 在模型输入前添加一个连续的且任务特定的向量序列（continuous task-specific vectors），称之为前缀（prefix）。前缀被视为一系列“虚拟 tokens”，但是它由不对应于真实 tokens 的自由参数组成。与更新所有 PLM 参数的全量微调不同，Prefix-Tuning 固定 PLM 的所有参数，只更新优化特定任务的 prefix。因此，在生产部署时，只需要存储一个大型 PLM 的副本和一个学习到的特定任务的 prefix，每个下游任务只产生非常小的额外的计算和存储开销。

在Prefix层前面加了MLP结构，训练完成后，只保留Prefix的参数。每层都加入prefix。

Prefix-tuning也是要略优于Infix-tuning的。

将可训练的的张量添加到所有transformer层，与K/V拼接。

params_num = virtual_tokens_num * 2 * layer_num * embedding_size ($ W_k$ and $W_v$)