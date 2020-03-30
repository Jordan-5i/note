# Abstract

应用到image caption中的transformer还有待更深入的探索，提出的模型提高了图像编码和语言生成两个阶段，通过先验知识学习图像区域间关系的多层次表示，在解码阶段使用类似网格的连接方式挖掘底层和高层特征。

# Introduction

图像区域以及他们的关系被多层次的编码，将低层和高层关系考虑进来，在建模他们的关系时，模型使用memory  vectors 来学习和编码先验知识。在句子生成时使用了多层结构，利用低层-高层视觉关系而不是仅仅从视觉编码中得到一个输入。

# Model

Encoder
$$
Attention(Q,K,V)=softmax(\frac{QK^T}{\sqrt{d}}V)\\
S(X) = Attention(W_qX, W_kX, W_vX)\\ 
\mathcal{M}_{mem}(X) = Attention(W_qX,K,V )\\ 
K = [W_kX,M_k]\\
V = [W_vX;M_v]
$$



Decoder

$$
\mathcal{M}_{mesh}(\hat{\mathcal{X}}, Y)=\sum_{i=1}^n\alpha_i\mathcal{C}(\hat{\mathcal{X^i}},Y)\\
\mathcal{C}(\hat{\mathcal{X^i}},Y)=Attention(W_qY, W_k\hat{\mathcal{X^i}}, W_v\hat{\mathcal{X^i}})\\
\alpha_i=W_i[Y, \mathcal{C}(\hat{\mathcal{X^i}},Y)]+b_i
$$
