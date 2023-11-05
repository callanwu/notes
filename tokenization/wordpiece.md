# WordPiece

1. 计算初始词表：通过训练语料获得或者最初的英文中26个字母加上各种符号以及常见中文字符，这些作为初始词表。
2. 计算合并分数：对训练语料拆分的多个子词单元通过合拼规则计算合并分数。
3. 合并分数最高的子词对：选择分数最高的子词对，将它们合并成一个新的子词单元，并更新词表。
4. 重复合并步骤：不断重复步骤 2 和步骤 3，直到达到预定的词表大小、合并次数，或者直到不再有有意义的合并（即，进一步合并不会显著提高词表的效益）。
5. 分词：使用最终得到的词汇表对文本进行分词。

Code:

[https://github.com/Glanvery/LLM-Travel/blob/main/tokenization.ipynb](https://github.com/Glanvery/LLM-Travel/blob/main/tokenization.ipynb)
