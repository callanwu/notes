# Position

## PostLN

* 在Transformer的原始结构中，采用了PostLN结构，即在残差链接之后layerNorm。
* 在LLM中训练过程中发现，PostLN的输出层附近的梯度过大会造成训练的不稳定性。

## PreLN

* To improve the training stability, we normalize the input of each transformer sub-layer instead of normalizing the output. \[LLaMA2 paper]
