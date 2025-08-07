### 模块1:图结构与节点表示（Graph Representation & Embedding）
* Random Walk optimization
  * 模拟节点之间的游走，学习节点之间的连接概率
  * 应用于图嵌入方法如DeepWalk, node2vec.
* Skipgram with Negative Sampling
  * 类似于NLP中的word2vec
  * 目标：预测邻居节点，优化节点嵌入
  * Negative Sampling：减少计算复杂度
* 0-1 Loss/Classification Loss
  * Binary classification 的标准损失函数
  * 与softmax输出相关
* Softmax输出
  * 用于讲模型输出变为概率分布
  * 在节点分类，词预测等任务中使用
* 节点嵌入只学习局部结构？
  * 是的，随机游走类方法主要是学习局部邻居关系（局部结构）
  * 图卷积网络（GCN）也有类似特点
  
---
### 模块2:数据可视化(Data Visualization Techniques)
* Bar Chart（柱状图）：显示类别型变量的分布
* Scatterplot（散点图）：显示两个数值变量之间的关系，用于寻找**相关性**
* Connected Scatterplot： 相邻点用线连接，显示时间序列或趋势
* SPLOM(Scatterplot Matrix):多变量散点图矩阵，显示所有变量两两之间的关系
* Parallel Coordinates Plot(PCP):高维数据可视化，每个维度是一条轴，记录为一条穿过多轴的线。**轴顺序可影响可读性**
---
### 模块3: 降维与高维可视化(Dimensionality Reduction & Manifold Learning)
* PCA（主成分分析）
  * 线形方法，找到最大方差方向
  * 适用于数据较线形的降维
* t-SNE
  * 非线形降维，保留局部结构
  * 常用与2D可视化聚类结果
* Manifold Learning
  * 如Isomap，LLE
  * 假设高维数据分布在低维锥流形上，尝试“展平”结构
---
### 模块4: 多维索引结构(Multi-Dimensional Index Structures)
* kd-Tree
  * 二叉树，内节点保存分裂值，叶子节点保存数据
  * 插入时可能需要向上分裂
  * 适用于静态数据，小规模查询
* Multiple Key Index
  * 在一个属性的索引后再链接另一个属性的索引
  * 类似复合索引，但复杂度高，空间大
* B-Tree/B+Tree
  * 所有数据都存储在叶节点，内节点之做导航
  * 支持范围查询，顺序访问
---
### 模块5: 并行数据库系统与分布式查询(Parallel Databases & Distributed Querying)
* 并行架构
  * Shared Memory：多个CPU，共享内存
  * Shared Disk：多个节点，共享磁盘
  * Shared Nothing：每个节点独立CPU/内存/磁盘
* 并行策略
  * Inter-query Parallelism：多个查询同时进行
  * Pipeline Parallelism：查询各步骤并行处理
  * Data Parallelism：对用一个任务不同数据处理
* 数据分区方式
  * Round Robin：均匀分布。无语义联系
  * Hash Partitioning：按**Key**分组
  * Range Partitioning：按值区间划分
* 并行操作示例
  * 并行排序，过滤，连接，聚合
  * Equi-join：按join键哈希分区，各节点本地join
  * MapReduce：分成Map(映射)--> Shuffle(聚合键)-->Reduce(归约)
* 并行ML工作流
  * **矩阵乘法**是关键操作
  * 按row/column切分矩阵进行分布式计算
---
### 模块6:信息检索与索引结构(Information Retrieval & Indexing)
* Tokenization:将文本拆分为基本单元（词语，符号）
* Posting List：记录每个词在哪些文档中出现
* Lexicon/Dictionary
  * 存储词的信息，如词频，词ID，倒排列表位置
  * 可是hash，B+Tree实现
* Boolean Retrieval：使用**AND**,**OR**,**NOT**组合关键词检索
---
### 模块7:信息检索评估指标(IR Evaluation Metrics)
* Precision(查准率)：正确结果数/检索结果总数
* Recall(差全率)： 正确结果数/实际相关文档数
* Hit@K：检索前K个结果中至少有一个相关的（1 or 0）
* P@K（Precision at K）：前K个结果中的相关文档比例
* Average Precision（MAP）：每个相关文档的位置precision值平均
* Mean Reciprocal Rank（MRR）：第一个相关结果的倒数的平均值
* nDCG
  * 加权考虑相关性等级+结果排名
  * 位置越靠前越重要，相关性等级越高贡献越大
