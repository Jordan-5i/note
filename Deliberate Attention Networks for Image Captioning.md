# Abstract

提出了一种deliberation action，生成的caption先经过第一个LSTM，粗略生成caption，接着将第一个LSTM的隐含状态和图像信息传到第二个LSTM上，生成更加精准的caption。