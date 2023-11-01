# P-Tuning

P-Tuning是针对Prompt Tuning的改进。
考虑到预训练模型本身的embedding就比较离散了，同时prompt本身也是互相关联的，所以用一个LSTM+MLP去编码这些virtual token以后，再输入到模型。

## P-Tuning Forward Pass During Training
* Task name and input text are passed to the model.
* Task specific embeddings are predicted by the LSTM prompt encoder based on the task name.
The input text is tokenized, and discrete token embeddings are retrieved.
* Virtual token embeddings are inserted among discrete token embeddings according to a user defined template and passed together into the rest of the pretrained model.