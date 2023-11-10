# Fixed Positional Encoding

The positional encoding encodes the position along the sequence into a vector of size `d_model` .

$$PE_{p,2i} = sin(\frac{p}{10000^{\frac{2i}{d_{model}}}})$$

$$PE_{p,2i+1} = cos(\frac{p}{10000^{\frac{2i}{d_{model}}}})$$

Where $$1\leq2i,2i+1\leq d_{model}​$$ are the feature indexes in the encoding, and $$p$$ is the position.

Models used this methods: Vanilla Transformer

Code：

[https://nn.labml.ai/transformers/positional\_encoding.html](https://nn.labml.ai/transformers/positional\_encoding.html)
