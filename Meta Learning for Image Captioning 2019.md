# Abstract

RL 在image caption上的应用并不能生成更好的caption，尤其是在caption的内容和新颖性上

# Introduction

利用RL训练模型，会出现比较差的句子，它的CIDEr分数很高，为此提出了元学习的方法，最大化真实caption的概率以及最大化生成caption的reward，这两个任务同时采用不同的gradient steps，这样就能在每个任务中都到达最优解