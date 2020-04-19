# Abstract

关注的问题是image caption模型在生成下一个时间步的单词时，只考虑当前的单词和当前的图像信息。所以采用两个模块，分别是Look Back和Predict Future，Look Back是将前一时刻的注意力信息引入到当前，Predict Future 是还继续预测下一个时刻的单词，这个论文的思路和之前做过的Future Cost想法有点类似。

