# LLaMA

Pre-training Data

* Textual and code data.
* Cover 20 languages, which use either the Latin or Cyrillic. Chinese are not covered.
* Use the byte-pair encoding (BPE) algorithm to tokenize the data. The vocabulary size is 32000.
* LLaMA-33B and 65B were trained on 1.4T tokens. The smaller models were trained on 1.0T tokens.

Architecture

* Pre-normalization using RMSNorm
* SwiGLU activation function
* Rotary Embeddings

Implementation

* FlashAttention
