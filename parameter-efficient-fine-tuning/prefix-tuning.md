# Prefix Tuning

Prefix tuning keeps language model parameters frozen, but optimizes a small continuous task-specific vector which pretends to $$h_i$$($$h_i$$ is composed of a key-value pair).

Use a two-layer MLP to encode the prefix.

Prefix tuning outperforms fine-tuning in low-data regimes.

Preserving LM parameters indeed has a positive impact on extrapolation.

Performance changes non-monotonically in trainable parameters.

Chain of increasing expressive power: discrete prompting < embedding-only ablation < prefix-tuning.

Prefix-tuning outperforms infix-tuning.&#x20;

params\_num = virtual\_tokens\_num \* 2 \* L \* $$d_{model}$$ ($$W_k$$ and $$W_v$$)

Code：[https://github.com/huggingface/peft/blob/02f0a4ca5992bf516b9807c5870811ef8ad199fa/src/peft/tuners/prefix\_tuning/model.py#L21](https://github.com/huggingface/peft/blob/02f0a4ca5992bf516b9807c5870811ef8ad199fa/src/peft/tuners/prefix\_tuning/model.py#L21)
