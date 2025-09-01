### Object:  走读 `megatron` 代码结构


## 20250829
- 链接: [megatron项目](https://github.com/NVIDIA/Megatron-LM)、[项目文档](https://docs.nvidia.com/megatron-core/developer-guide/latest/user-guide/index.html#quick-start) 

##### Object: 大概看下 megatron 的代码量，代码结构，API体系
##### Reflection: 他的代码量感觉很少、结构让我感觉不可思议、但仔细想想又觉得非常巧妙
##### I：他和传统的训练框架不同点在哪里、为什么这么设计呢
- 1、看项目的 `install` ： 看安装依赖、可以知道他大概属于哪一层应用 。只依赖 pytorch， 说明 是基于 `pytorch` 搭建的`分布式训练体系`.
- 2、看项目的 `test`: 看单元测试，可以知道 项目`要解决的问题/拥有的特性`。核心测试位于 `megatron\tests\unit_tests\` 中。
  -  看`test`分布后我觉得他想做的事情： 1. 分布式训练: 数据并行、流水线并行、张量并行。 2、 大模型： 模型定义、后训练、模型存储和转换(成`trt`部署格式)
- 3、看代码结构： 功能代码位于 `megatron` 和 `megatron\core`。 基本和 `test` 文件夹下的内容结构一致。 说明就是要开发如上的功能
- 4、 看API 体系: https://docs.nvidia.com/megatron-core/developer-guide/latest/api-guide/index.html。 里面的`API`不多，这才是使用`megatron`的核心， 得背的滚瓜烂熟才能为我所用

##### D： 我得详细得研究一下他的API体系，都有哪些API


## 20250901


- 链接: [megatron项目](https://github.com/NVIDIA/Megatron-LM)、[项目文档](https://docs.nvidia.com/megatron-core/developer-guide/latest/user-guide/index.html#quick-start) 、[API文档](https://docs.nvidia.com/megatron-core/developer-guide/latest/api-guide/index.html)


##### Object： 今天学会所有的 API 

