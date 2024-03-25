# Activation function

## Gaussian Error Linear Units(GeLU)

$$GeLU\approx0.5x(1+\tanh(\sqrt(\frac{2}{\pi(x+0.044715x^{3}}))))$$

```
@torch.jit.script
def gelu_impl(x):
    """ OpenAI's gelu implementation."""
    return 0.5 * x * (1.0 + torch.tanh(0.7978845608028654 * x *
                                       (1.0 + 0.044715 * x * x)))
​
def gelu(x):
    return gelu_impl(x)
```

