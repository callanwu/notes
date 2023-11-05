# Assisted Decoding

1. Use greedy decoding to generate a certain number of candidate tokens with the assistant model, producing `candidates`. The number of produced candidate tokens is initialized to `5` the first time assisted generation is called.
2. Using our model, do a forward pass with `candidates`, obtaining `logits`.
3. Use the token selection method (`.argmax()` for greedy search or `.multinomial()` for sampling) to get the `next_tokens` from `logits`.
4. Compare `next_tokens` to `candidates` and get the number of matching tokens. Remember that this comparison has to be done with left-to-right causality: after the first mismatch, all candidates are invalidated.
5. Use the number of matches to slice things up and discard variables related to unconfirmed candidate tokens. In essence, in `next_tokens`, keep the matching tokens plus the first divergent token (which our model generates from a valid candidate subsequence).
6. Adjust the number of candidate tokens to be produced in the next iteration — our original heuristic increases it by `2` if ALL tokens match and decreases it by `1` otherwise.

* 小模型需要与大模型的tokenizer一致。
* 主要利用了矩阵的并行性，输入candidates，能拿到所有的logits。

Code：[https://github.com/huggingface/transformers/blob/4b796978656e461177a83d58ec3c2b06152c63db/src/transformers/generation/utils.py#L4186](https://github.com/huggingface/transformers/blob/4b796978656e461177a83d58ec3c2b06152c63db/src/transformers/generation/utils.py#L4186)
