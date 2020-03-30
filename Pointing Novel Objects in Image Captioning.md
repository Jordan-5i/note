# Abstract

在训练image caption模型的时候，模型只认识in-domain的物体，对out-domain的物体几乎不了解，因此解决的思路是扩展vocabulary，和在生成caption的时候可以是依据LSTM，也可以是依据object learners，这个object learners是在格外的数据上进行训练的，可以识别出out-domain的物体。

