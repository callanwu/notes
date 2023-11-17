# Position

## PostLN

* 在Transformer的原始结构中，采用了PostLN结构，即在残差链接之后layerNorm。
* 在LLM中训练过程中发现，PostLN的输出层附近的梯度过大会造成训练的不稳定性。

## PreLN

* PreLN将layerNorm放置在残差链接的过程中。
* 相比PostLN，使用PreLN的深层transforme的训练更稳定，但是性能有一定损伤。
