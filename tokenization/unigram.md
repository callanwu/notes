# Unigram

Unigram Language Model(ULM)同样使用语言模型来挑选子词。不同之处在于，BPE和WordPiece算法的词表大小都是从小到大变化，属于增量法。而Unigram Language Model则是[减量法](https://www.zhihu.com/search?q=%E5%87%8F%E9%87%8F%E6%B3%95\&search\_source=Entity\&hybrid\_search\_source=Entity\&hybrid\_search\_extra=%7B%22sourceType%22%3A%22article%22%2C%22sourceId%22%3A%22191648421%22%7D),即先初始化一个大词表，根据评估准则不断丢弃词表，直到满足限定条件。ULM算法考虑了句子的不同分词可能，因而能够输出带概率的多个子词分段。

* 初始时，建立一个足够大的词表。一般，可用语料中的所有字符加上常见的子字符串初始化词表，也可以通过BPE算法初始化。
* 针对当前词表，用[EM算法](https://www.zhihu.com/search?q=EM%E7%AE%97%E6%B3%95\&search\_source=Entity\&hybrid\_search\_source=Entity\&hybrid\_search\_extra=%7B%22sourceType%22%3A%22article%22%2C%22sourceId%22%3A%22191648421%22%7D)求解每个子词在语料上的概率。
* 对于每个子词，计算当该子词被从词表中移除时，总的[loss](https://www.zhihu.com/search?q=loss\&search\_source=Entity\&hybrid\_search\_source=Entity\&hybrid\_search\_extra=%7B%22sourceType%22%3A%22article%22%2C%22sourceId%22%3A%22191648421%22%7D)降低了多少，记为该子词的loss。
* 将子词按照loss大小进行排序，丢弃一定比例loss最小的子词(比如20%)，保留下来的子词生成新的词表。这里需要注意的是，[单字符](https://www.zhihu.com/search?q=%E5%8D%95%E5%AD%97%E7%AC%A6\&search\_source=Entity\&hybrid\_search\_source=Entity\&hybrid\_search\_extra=%7B%22sourceType%22%3A%22article%22%2C%22sourceId%22%3A%22191648421%22%7D)不能被丢弃，这是为了避免OOV情况。
* 重复步骤2到4，直到词表大小减少到设定范围。
