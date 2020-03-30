# Abstract

在baby talk这篇文章的思想上出发，用RNN生成句子模板，句子中空缺的部分是需要用object detectors检测出来的视觉单词填入其中，这就保证了一些单词在训练的caption中没有是没有出现过的。比如，object detectors检测出来某个区域是teddy，而对应的caption中并没有teddy这个词。

# Introduction