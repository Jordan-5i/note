# 主要思想

之前word2vec的表示是浅层的，一个单词映射到Embedding的维度，并没有考虑单词的语境含义，而BERT堆叠transformer的encoder部分 $N$ 次，达到用深层次词向量来表示我们日常的单词，这个向量包含上下文的含义。

# 模型细节

模型的结构和transformer的encoder计算方式是一样的，只是堆叠了更多的层。我们使用的语料被处理成这种形式， [CLS]是每个句子对都有的，用[SEP]分割句子对：

`[CLS] my dog is cute [SEP] he likes playing [SEP]`

`[CLS] my dog [MASK] cute [SEP] he [MASK] playing [SEP]`

**模型的整个输入部分包含3个Embedding层：**

1. 之前一直用的Embedding层，作为词嵌入
2. Segment Embedding，因为bert的输入时句子对，第一个句子为A，第二个句子为B，那么单词属于A的是$E_A$, 单词属于B的就是$E_B$，主要让模型知道各个单词是属于哪个句子
3. Position Embedding， 用来描述词词的位置关系

**训练方式有两个策略：**

1. Masked Language Model

   将输入的单词随机用 [MASK] 掩盖掉，让模型去预测被mask掉的单词使用，这个策略就让模型有了对整个句子的理解，损失函数用cross-entry， input：（bs, seq_max, embed_dim)

2. Next Sentence Prediction

   将句子对随机的替换为和语料库当中的任意的一个句子，那么整个句子对有两种情况，一是所给的输入是连贯的句子对（IsNext），二是就是不连贯的（NotNext），让模型去判断，是个二分类问题。

所以，对整个模型来说， input：（bs, seq_max, embed_dim)，output：（bs, seq_max, embed_dim)， 利用output[ : ,  0] 也就是[CLS]位置上的Embedding经过linear层来判断 IsNext 还是 NotNext。预测mask掉的单词时，举个例子，如果input中第6 和第17个位置是[MASK]的Embedding，那么在output对应位置上经过linear层来预测。在实际操作中，是将output全部经过linear层将其映射到vocab维度，选择对应[MASK]位置上的预测结果，其他位置上都不计算损失。

# 优点

1. 利用双向的信息，可以构建某个单词的上下文信息
2. long-term dependency

# 缺点

1. 测试的时候，测试数据没有[MASK]，这导致训练和测试不一致
2. 缺乏生成能力，训练的时候只是预测[MASK]和NSP，没有生成任务
3. 针对每一个[MASK]预测时，没有考虑他们的相关性