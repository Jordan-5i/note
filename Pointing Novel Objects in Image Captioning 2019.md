这篇和X-Linear Attention Networks for Image Captioning的作者一样，京东AI实验室

# Abstract

在训练image caption模型的时候，模型只认识in-domain的物体，对out-domain的物体几乎不了解，因此解决的思路是扩展vocabulary，和在生成caption的时候可以是依据LSTM，也可以是依据object learners，这个object learners是在格外的数据上进行训练的，可以识别出out-domain的物体。

# Introduction

考虑到现有模型最大的局限性就是在特定的数据集上进行训练，模型只能识别出有限的物体和生成有限的单词，不能够应用到实际场景中去，这项任务的困难之处有两点：1）怎样能扩展现有的词汇，2）怎样能让模型将识别出来的物体名称融合到caption中去。对于问题1，首先训练一个已有的目标检测器，这样就不限制与已有的词汇库，可以检测出更多的物体。对于问题2，运用pointing mechanism，控制何时直接将检测到的物体放在caption中，以及何时用decoder来生成单词，并且考虑一个句子中尽可能包含更多的物体。

# Model

