# Abstract

典型的注意力机制很难识别等效的视觉信号尤其是在预测高度抽象的单词时，比如skiing，RNN模型在设计复杂的注意力来整合视觉和语义属性时会变得不灵活，提出EnTangled Attention用于同时处理语义和视觉信息，以及Gated Bilateral Controller (GBC)处理多模态信息的交互

# Introduction

由于语义鸿沟的存在，并不是每个单词都有对应的视觉信号，尤其是抽象概念的词，有一些工作研究了semantic attention，但是其本质模型还是RNN，他很难去记忆许多时间步之前的内容。因此提出EnTangled Attention和Gated Bilateral Controller （GBC）来同时探究visual and semantic information