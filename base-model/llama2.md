# LLaMA2

Pre-training Data

* A new mix of publicly available online data, 2T tokens of data
* Use the byte-pair encoding (BPE) algorithm to tokenize the data. The vocabulary size is 32000.

Architecture

* Pre-normalization using RMSNorm
* SwiGLU activation function
* Rotary Embeddings
* Bigger models(34B and 70B) use Grouped-Query Attention (GQA,  8 KV projections) for improved inference scalability.
* Increase the dimension of the feed-forward layers(1.3)
* Context Length is 4k

Original Attention Layer Parameters ($$W_q$$、$$W_k$$、$$W_v$$+$$W_o$$)：3\*head\_num\*attention\_dim\*embedding\_dim (head\_num\*attention\_dim =embedding\_dim)+embedding\_dim\*embedding\_dim

Group-Query Attention(GQA) Attention Layer Parameters($$W_q$$、$$W_k$$、$$W_v$$+$$W_o$$)：

head\_num\*attention\_dim\*embedding\_dim+1/8\*2\*head\_num\*attention\_dim\*embedding\_dim+embedding\_dim\*embedding\_dim

Code：[https://github.com/facebookresearch/llama/blob/main/llama/model.py#L291C1-L293](https://github.com/facebookresearch/llama/blob/main/llama/model.py#L291C1-L293)

Implementation

* FlashAttention
