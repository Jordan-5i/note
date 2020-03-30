# Abstract

根据目前的方法只是将图像和句子进行注意，而忽略到了自身与自身的注意，提出了将transformer扩展成Multi-modal Transformer

# Introduction

解决三个问题：

1. 目前的注意力是object-to-word，忽略了object-to-object，和word-to-word之间的注意力

2. 当前的模型是浅层的，不能很好地理解物体之间的关系
3. region-based visual features 不能覆盖图像中所有物体，导致不能准确的生成单词