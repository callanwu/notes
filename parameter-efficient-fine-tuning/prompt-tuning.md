# Prompt Tuning

增加soft-prompt，与输入的embedding进行拼接。

不需要加入 MLP 进行调整。

Prompt Tuning采用类标签初始化模型的效果更好。

params_num = virtual_tokens_num * embedding_size