### Obejct ： VIT 模型是我对接的主要业务、我必须要非常了解这个模型

### R: 懵，图像识别不是用的卷积神经网络吗，我看我们业务里还是
- 我感觉很懵、之前视觉不都是卷积模型做的吗，现在用VIT了？

### I： 是Google2020年提出的模型结构，用Transformer模型做图像识别
- 核心的创新点：1. 图像编码：把图像给切分成多个块，每个块编码成一个 Sequence.  转化成Sequence 信息后可以输入Transformer 模型。  转化为Transformer模型后，就可以长度堆叠的特别长，实验发现堆叠的越长、识别效果越好
  - [知乎链接](https://zhuanlan.zhihu.com/p/445122996)
  - [google github项目](https://zhuanlan.zhihu.com/p/445122996)

### D: 我知道VIT的模型结构了，他使用Tranformer 模型解决图像识别，是VLA\VLM等视觉相关大模型的视觉编码器。
- VIT 模型的基本结构: 
<img width="751" height="377" alt="image" src="https://github.com/user-attachments/assets/4a32216b-955e-41ea-a460-fc168d159aa3" />
