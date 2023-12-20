# Prompt Tuning

增加soft-prompt，与输入的embedding进行拼接。

不需要加入 MLP 进行调整。

Prompt Tuning采用类标签初始化模型的效果更好。在peft框架中，设置prompt\_tuning\_init，在prompt-tuning\_init\_tetx中输出类标签，即本来的prompt，例如 predict if sentiment of this review is positive, negative or neutral.

params\_num = virtual\_tokens\_num  \* $$d_{model}$$

