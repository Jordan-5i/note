# Abstract

考虑到生成的caption中不能保证一定有我们所关心物体，比如一个物体在图像中很不明显但确是我们所关心的，那么模型生成的caption很有可能没有那个物体，因此提出的模型用物体去指导caption的生成，利用两种不同方向 的LSTM

# Introduction

模型CGO以及选中的物体来生成对应的caption，这个选中的物体就是我们所希望它出现在caption中的，随后从选中的物体向左生成单词，和向右生成单词