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


#### Reflection: 大概懂了逻辑，但是其中有些难点的很难懂

#### I： API 体系
- 1、megatron 库本质的代码在 megatron/core 文件夹下，安装 megatron-core 实际就是把这个文件夹安装到 python的调用路径了。可以通过  `from megatron.core.xxx import` 里面的相关函数
- 2、里面有一些封装的很成熟的API
  - models ：  里面有  `GPT\BERT\T5` 的主流大模型，可以通过调用快速创建一个这种大模型
  - tensor_parallel : 里面有 Tensor 并行的一些相关API（这个并行策略比较成熟、已经封装成成熟API）
  - pipeline_parellel ：流水线并行相关API（这个并行策略比较成熟、已经封装成成熟API）
  - transformer: transformer 相关的结构(Attention\MLP)、transformer block/layer 等结构(支持快速注册一个或多个 transformer)
  - fusion： 定义了一些融合算子、用于训练加速
 
  - 比较难得： context_parallel(还没有封装成API，比较难理解)、encoder-decoder-parallelism(还没有封装成API，仅支持部分模型类型)、MOE 的模型定义和并行(合在一起、而且没有独立的API）
  - 还有一些没有写在文档里的API： eg. cuda_graph 等加速API(代码里有，但是API文档里没说，估计是可以调用的)
- 3. 我的感觉： megatron 解决了主流大模型的快速注册(model/dataset/checkpoint)、大集群训练(并行 DP\PP\CP\EP\TP\EDP等)、Fusion/Quant等加速策略。  但现在这个代码仓的更新速度超级快、API 体系还不稳定
 
#### D：难点是 DD/PP/TP/CP/EP/EDP  (写出一个demo)六种并行方式我都要懂、MOE (自己定义出来一个)的模型结构我得懂，我是真的不懂

- 明天写各种并行的 `demo/moe` 的模型结构的 `demo` . 然后明天结束 megatron 的学习
