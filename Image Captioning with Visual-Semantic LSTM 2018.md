# Abstract

提出visual-semantic的机制，就是能很好的识别一些物体的特征，比如dog，它的semantic是a running dog,  dog eats. 这个同以往的注意力来说，不单单关注物体是什么，还关注这个物体相关的动作和属性。通过两个LSTM，一个是visual lstm，另一个是semantic lstm。

# Model

重点理解一下这个式子：
$$
p_i^{w_k} = 1-\prod_{j\in b(i)}(1-p_{ij}^{w_k})
$$
其中 $p_i^{w_k}$ 表示图像 $i$ 包含单词 $w_k$ 的概率，$w_k$ 是图像的属性，$p_{ij}^{w_k}$ 表示在图像 $i$ 中区域 $j$ 上包含单词 $w_k$ 的概率，$b(i)$ 是图像 $i$ 的所有区域数目。

举个例子：

caption：a man is working on a computer

attributes: man working  on computer 

如果图像上某个区域中有man，那么  $p_{i1}^{man}$ 就接近1， 其他位置  $p_{i2}^{man}$ ，  $p_{i3}^{man} \dots$ 就相对较小，对于图像 $i$ 来说  $p_{i}^{man}$ 的值就大。如果所有区域上都有man，那么$p_{i}^{man}$ 就越大，表明man是这个图像的属性的概率大，反之就小。

那么图像 $i$ 的所有属性的概率组成的向量就构成semantic features
$$
A = (p_i^{w_0},p_i^{w_1},\dots,p_i^{w_{m-1}})
$$
$m$ 是图像 $i$ 的属性数目。