### Object:  走读 `megatron` 代码结构


## 20250829
- 链接: [megatron项目](https://github.com/NVIDIA/Megatron-LM)、[项目文档](https://docs.nvidia.com/megatron-core/developer-guide/latest/user-guide/index.html#quick-start) 

##### Object: 大概看下 megatron 的代码量，代码结构，API体系
##### Reflection: 他的代码量感觉很少、结构让我感觉不可思议、但仔细想想又觉得非常巧妙
##### I：他和传统的训练框架不同点在哪里、为什么这么设计呢
- 1、看项目的 `install` ： 看安装依赖、可以知道他大概属于哪一层应用 。只依赖 pytorch， 说明 是基于 `pytorch` 搭建的`分布式训练体系`.
- 2、看项目的 `test`: 看单元测试，可以知道 项目`要解决的问题/拥有的特性`。核心测试位于 `megatron\tests\unit_tests\` 中。
  -  看`test`分布后我觉得他想做的事情： 1. 分布式训练: 数据并行、流水线并行、张量并行。 2、 大模型： 模型定义、后训练、模型存储和转换(成`trt`部署格式)

```bash
a2a_overlap ：不知道是啥
data ：数据集
dist_checkpoint : 分布式上的模型存储
distributed： 数据并行
export/trtllm： 模型转换(转为部署格式)
fusion: 加速
inference：前向推理
models： 模型定义
pipeline_parallel： 流水线并行
post_training：后训练
ssm：不知是啥
tensor_parallel： 张量并行
transformer： transformer模型
```
3、

##### D： 我得详细得研究一下他的API体系，都有哪些API
