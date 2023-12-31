# Multi-Query Attention(MQA)

传统的多头注意力实质上是将输入分成多个头部，并为每个头部独立计算注意力。在MHA中，$$Q$$、$$K$$ 和 $$V$$ 都根据每个head进行不同的转换。这在头部数量较多时可能会计算密集。多查询注意力简化了这个过程，尤其是在$$K$$和$$V$$的部分。与为每个head提供多个、单独的$$K$$ 和 $$V$$ 映射不同，MQA为所有head应用单一的$$K$$和$$V$$转换。只有$$Q$$值才有多个head。

