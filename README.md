# paperReaderNote

用来记录自己研究僧阶段读取的论文，做一记录吧，在2019.05.01，有了这个记录的想法，但是一直却没有去做，最近正好没事，就拿出来一起好好开始自己的科研之路吧 ~~~~

不去努力，不去尝试，未来可期，不过是一纸空谈！

## 前言

自己从2018.7.12来到这里，一直开始跟着师兄做一个关于文本的项目，目前该项目已经完结，自己也积累了一些工程上的开发技术，但是在论文上却一直没有一个研究生该有的样子。也学之前真的有想着划水过去毕业就好了，然后找一个工作，做一个卑微的人就好。后来遇见了燕哥，也是极其幸运的，说的未来可期，如果不去努力，不过是自己骗自己的谎言。

所以，在研究生的过程中，去把它过得充实，然后不断的去努力，未来才可以掌握在自己手里，就想打王者一样，与其说队友坑，不如把输出掌握在自己手里，宁可钻石局5法师的重开，也不愿将自己最擅长的输出，放在队友手里，最后要么carry全场，要么被喷。科研也一样，我不想让自己的命运，安安稳稳的划在别人的手里，我会将输出握在我自己的手里。

所以，加油！

## 论文

### 1. A Biterm Topic Model for Short Texts(BTM).pdf

- 内容概要：这是针对短文本主题模型的论文，属于 主题模型  族的论文。主要描述了短文本上的主题分析。
- 创新点：  
    1. LDA主要是用单个词，作为基本的处理单元，但是BTM这里是使用了次对的形式，来作为其操作的基本单元，及时了该词对只有一个主题，然后服从了狄利克雷的先验假设分布，其余过程和LDA类似 ,在推断过程依然采用了Gibbs采样的推断过程。
    2. 通过设置窗口的大小，将窗口内的词对两两组合构成词对，解决了短文上数据文档级别的单词贡献的的数据稀疏想问题  
- 对比实验
    1. 标准LDA  
    2. Mixtrue of unigrams 这个也是假设了一个或者词只有一个topic，而非多个topic
- 指标
    1. 主题质量通过主题连贯性来进行检验，在短文本和正规文本上做了实验
    2. 通过其他的手段来定量的分析，聚类通过 纯度Purity，互信息NMI(Normalized Mutual Information), ARI(Adjust Rand Index)三个指标判断主题模型对下游任务的影响
    3. 质量分析，通过计算LDA和BTM 得到的主题词的余弦相似度来判定其差异

### 2. Automatic Labeling of Topic Models Using Text Summaries.pdf

- 年份： 2016 ACL
- 作者简介：万小军，北京大学自然语言处理研究所负责人，主要是文本摘要
- 内容概要：本文首次提出了给主题模型跑出来的抽象的topic，进行主题实际意义的命名。以前有人尝试过用 单词，短语，和图像来进行直观的主题的主题描述，还有抽取抽取句子作为主题的描述。本文定义了怎样的主题label是更好的，只要是 主题label和主题词的高相关性，高概括性，不同topic之间的高区分性。本文提出了基于子模优化的算法进行候选句子的筛选。
- 创新点:  
       1. 首次提出了用文本摘要进行主题打标签  
       2. 基于子模优化的文本摘要生成算法  $f(A+C)-f(A) > f(B+C)+f(B)$，说明A优与B，具体的子模函数[介绍](<https://blog.csdn.net/s1102379635/article/details/8524397>)
- 对比实验  
       1. MEAD：使用启发的策略进行发现和第一个句子相似的每个句子分数  
       2. LEXRank：主要通过句子之间的县四度的判断对文本和词汇进行分类，以句子为节点，构造标量图，节点间的连线代表句子的相似程度（权重，用余弦相似度衡量$f(i,j) = \frac{S_i\dot S_j}{|S_i||S_j|}$），句子不相似就没有边(相似度大于一定的阈值)，在对每句话进行评分时，充分考虑顶点的度和权重，即句子的核心性和相关程度大小，然后超过一定阈值的就作为文章关键句子，更加详细的[介绍](<https://blog.csdn.net/Silience_Probe/article/details/80699986>)
       3. REL：子模函数最大化  
  标签比较：词标签，短语标签，句子标签  
- 指标：  
       1. 候选句子的选择：主要靠KL散度进行来进行选择  
       2. 主题摘要：主要靠增益递减的子模函数来进行选择。  
       3. 定义了相关性函数 KL散度，余弦相似  
       4. 定义了概括性函数  
       5. 定义了区别性函数  
       6. 定义了贪心的选择算法，根据2,3,4的定义相加构成的子模函数

#### 总结

之前我们有尝试去解决这个topic lable的问题，尝试的办法，采用了单词的短语的形式，做法上可能相对简单，通过人工命名部分抽象名词，通过词林扩展的形式扩充好单词，采用余弦相似度和jacard相似度来进行topic的命名，这样实现的是一个半自动话的主题命名方式。今天看到万老师的这一篇文章，可以说是有了很大的了解。

### 3. generative-adversarial-nets.pdf

- 内容概要：本文首次提出了生成对抗的神经网络，也就是大名鼎鼎的GAN，当时主要用于图像的生成，论文介绍的GAN主要有两个部分组成，一个是生成神经网络，一个是判别神经网络。生成网络用与捕获数据的分布，判别神经网络，主要判断采样训练数据的真实的可能性，所以生成过程是以最大化的生成数据分布的过程，判别过程是一个最小化判别误差的过程，最后构成了最大最小化的游戏。两个过程都有多层感知机构成，论文对比说明了该框架和目前存在的一些两段的神经网络的区别。
- 创新点：  
   1. 首次提出了生成对抗神经网络
   2. 克服了其他神经网络的随机性的问题，提出了该网络满足两个玩家的各自的策略均等的。
- 总结：  
  因为目前本人水平有限，该论文写的简单，但是很深奥，只能了解个大概的思想，不能够体会到其具体的精妙之处，以后还需要多积累一些之后再来读，会有不一样的体会。

### 4. Short_and_Sparse_Text_Topic_Modeling_via_Self-Aggregation.pdf

- 内容概要：本文主要描述了一个解决短文本的数据的数据稀疏性问题的更加广义的解决办法，提出了通过短文本在主题推断时的自聚合得到的一个广义的解决方案。自聚合是通过广义的主题的亲和度而不是其他论文的启发式的策略，使得该模型更加适应多样性的短文本。实验在两个真实实验数据集上进行实验。
- 创新点：  
    1. 解决了数据的稀疏性问题：通过更多有用的单词共现信息被有效的短文本版相似的主题聚类所创建，同时假设了每个短文本一定是采样来自一篇的伪长文本  
    2. 提出了两个新的评估准则。一个是互信息的评估，一个是最大化alignment的摘要主题，也就是纯度作为一个新的评估准则。
- 模型：
    主要分为两段的生成过程，第一段的假设就是标准的LDA假设，去生成一个标准的文档集合。第二段就是利用前一段生成的长文本来生成短文本，也就是每个短文本是一个长文本的多项式采样过程  
    推断过程还是通过Gibbs采样的过程。
- 数据集：
   1. NIPS：NIPS COFFERCE PAPER
   2. Yahoo！Answers. [地址](<http://answers.yahoo.com/>)
- 总结：本文通过长文本来解决短文本的稀疏性问题的解决，提出的纯度的评估准则，后来作为评估主题的一个重要的手段。
最近的自己真的是浪得很，一方面是一位懒，一方卖弄是因为总是被各种事打扰，没有细心去读了论文，真是罪过啊！！！

### 5. Recent_Advances_in_Document_Summarization.pdf  

- 内容描述：这是一篇关于最近几年先进的文本摘要或者文本总结的综述性论文，[完整翻译](<https://blog.csdn.net/jinhao_2008/article/details/78695508>)
  
  - 什么是好的摘要或者总结？ 覆盖单文本或多文本（每个聚类）的重要信息，并且不重复，语法上连贯。
  - 目前的方法：主要来提高概念覆盖，信息多样，内容相关性。同时也在尝试句子压缩和生成。
  - 文本摘要分类：单一文档，和多文档（或者说是单一文本的聚类，如lda的结果）
  - 区别：
       1. 抽取总结：从原生的文本中抽取出一些重要的句子凭借起来作为总结
       2. 摘要总结：用不同的单词构成的句子来描述文档内容的信息，而不是抽取原句。这也是生成摘要。
- 目前方法介绍：
  - 经典的方法：句子水平的操作。如句子压缩，句子重组。大致有如下三个要素：
     1. 句子分数：每个句子计算一个分数，预留最重要的信息。
         - 早期的无监督的方式，主要是通过频率和中心化进行来计算分数。 有计算单词的概率，
         - 发展到有基于图摘要的框架，如pagerank衍生出来的TextRank等算法。
         - 在中心化（高于一定的阈值的tfidf的单词构成）的算法中，句子分数是定义为基于和中心句的不同特征包含余弦相似度的之和。  
         - 概率主主题模型是基于单词共现的信息，例如hLDA算法，所有这些的共同点都是从文档中抽出重复信息最高的句子。在噪声很大的文本中就抽不到了。  
         - 目前一些机器学习的算法应用到该领域。给定一个句子和其对应分数lable进行训练回归模型，然后直接预测句子得分。或者是一些排名的算法来给句子排名。后来隐马尔科夫，条件随机场和SVM都会用来抽取摘要，但是这种方法严重的依赖与训练集的大小。查询类的摘要主要计算查询的句子和每个句子之间的相似度。
     2. 句子筛选:选取最能代表文章中心的句子作为代表。
        - 根据第一步句子得到的分数，最直接的方式是选取分数高的句子，但这个现象在多文档摘要中会使得重复的信息严重。
        - 典型的句子选择算法是 最大边缘相关（maximum marginal relevance(MMR)）算法，详细的[描述](<https://blog.csdn.net/eliza1130/article/details/24033161>)
        - 概率的办法就是在概率分布和输入的单词评估之间 最小化KL(Kullback-Leibler)散度，也为相对熵。[详见](<https://baike.baidu.com/item/%E7%9B%B8%E5%AF%B9%E7%86%B5/4233536?fr=aladdin>)
        - 最广泛的还是整合线性规划（ILP），目标在受限的情况下最大化覆盖率。
     3. 句子标准化：对选出的句子进行修改和压缩，形成总结性的句子。根据第二部选择出的句子可能包含重复和不必要的信息。  
        - 有两种方法解决这类问题： 流水线是抽取，基于规则的压缩。
          在单文档的摘要中保证句子在原来文档中的顺序；在多文档的摘要中则要重排顺序。经典的重排句子的策略是句子权重图或者是基于时间戳和位置的时间排序算法。
  - 评估策略：（好的摘要易读和有高概括性）
    - ROUGE(Recall-oriented Understudy for Gisty Evalustion)：ROUGE基于摘要中n元词(n-gram)的共现信息来评价摘要，是一种面向n元词召回率的评价方法。基本思想为由多个专家分别生成人工摘要，构成标准摘要集，将系统生成的自动摘要与人工生成的标准摘要相对比，通过统计二者之间重叠的基本单元(n元语法、词序列和词对)的数目，来评价摘要的质量。通过与专家人工摘要的对比，提高评价系统的稳定性和健壮性.[详细](<https://blog.csdn.net/mch2869253130/article/details/89810974>).  
      当然还有其他的自动文摘的评测办法，论文一提而过。
  - 目前方法介绍  
   文本摘要要求信息覆盖，连贯性，不冗余，和简洁性。基于查询的文本摘要还是计算查询和语句的相似度和overlap度。
    - 基于ILP的概念提高：基于频率的改进
    - 子模函数最大化的多样性改进：
    - 句子连贯性的改进：连贯性分数可通过话语图(dicourse graph).
- 未来的发展趋势和方向  
  1. 建立新的数据集，目前数据集的质量不高
  2. 提出新的摘要评价方法，ROUGE有时候不能很好的评估
  3. 基于文档理解形成的摘要，包含更多的重要信息，而不是高频词的堆砌
  4. 端到端神经网络架构摘要总结：表示学习的神经网络
  5. 大规模的总结，如事件发现的概要概括
  6. 有用户交互的摘要
  7. 多模态的摘要，语音，视频，图像等
  8. 非因子问题答案的总结，对一个问题进行总结回答。

### 6. Exploring Text Links for Coherent Multi-Document Summarization.pdf

- 内容综述  
  目前存在的方法都是抽取关键的信息，但是忽略了连贯性，生成式的摘要可读性差。  
  传统的办法分为两种，一种是基于显著性（关键性）信息的方法，一种是基于连贯性的方法：
  - 基于显著性（关键）信息的方法  
    句子重排序，面临的是无法处理时序的文本。主要有以下几个方法
    - MMR（1998年Carbonell and Goldstein）提出，简单概述为 抽取的句子，句句重要，句句不重复。在冗余性和相关性之间权衡。  
    - Rank methods.如TextRank,Lexrank还有各种变种。利用文本单元构建一张图，用rank算法来抽取top的句子构成摘要、
    - 优化方法（本文是之一）。目标函数遵循一定的限制，找到一个最优的子集
    - 最大覆盖方法（maximum coverage methods，2009）.形式化成最大背包问题（MKMC），句子右concept（也就是words）构成，抽取摘要就是抽取一个句子子集，受到摘要长度的限制。可以看成是整数规划的问题（ILP），2009有人提出获得近似解的办法，2011 Lin and Bilmes为文本摘要设计了子模函数（分成两部分，包含覆盖率和多样性两部分）
    - 还有 基于中心化的方法（2004），最小支配子集(2010).
  - 基于连贯性的方法  
    句子重组生成连贯的摘要，丰富的语义和句法特征被用来找到最优的排列（2001,2004,2010）.缺点在于：句子筛选过程只考虑信息，不考虑连贯性。所以后来考虑能够在句子筛选过程考虑连贯性，开始主要通过话语图（篇章分析），后来研究话语树上的背包问题，但是这中话语树不能扩展到多文档的摘要上。后来构建了图带代表话语关系。  
    最近的基于话语分析的神经网络（抽取丰富的特征）提供了新的思路来解决摘要抽取。

- 创新点
  1. 本文提出了一种基于图的方法来探索文本和产生的连贯性摘要之间的关系。
  2. 本文的方法可以找到一个能够表示最关键信息的一个最连惯性的句子序列来表示。
  3. 考虑了实体之间的关系，权重最长路径模型可以提高摘要质量。
  4. 不需要话语分析。

- 算法思想  
  在筛选句子的时候同是应当同等的考虑句子的连贯性，重要性，冗余性。根据1995 Grosz和1998 Walker提出的中心化的理论。文本的连贯性的实质是通过描述实体（名词和代词）之间的关系，所以不一定要通过话语分析（篇章分析，话语图，话语树）来进行连贯性的抽取  
  根据中心化理论，有如下假设：  
  1. 文本中连续提到的实体是连贯的
  2. 主要的实体起着重要的语法作用，例如句子的主题和目标。
  所以了连贯性主要包括什么实体以及实体之间的角色变换。2008年提出用实体网格表示一个文本。这里的定义参见论文的描述。
  - 摘要模型：
    摘要是基于全局连贯性和局部连贯性，全局连贯性复杂度高，局部连贯性复杂度低。
    - 问题定义：K个文档总有n个句子，不区分内部文件和文件间的关系。构建一张图，包含n个节点（代表每个句子），每个节点分配一个cost score = 该点的句子包含的单词数，有向权重边连接这些节点，给有向边分配 gain score = 评估分数包含信息和路径上句子序列连贯性。将问题转成寻找最长的路径即可。为解决冗余性，删除一些相似的边构成非完全图。
    - 考虑全局连贯性的摘要：计算每个句子序列的分数，也就是最大化该路径上句子序列的权重。score（seq）的定义集结合了连贯性，重要性和冗余性，看论文原文介绍。其中重要的有一个实体角色状态转移概率矩阵
    - 考虑局部连贯性的摘要：加入了两个假的节点，start和end节点。将问题转成整数规划问题，具体的过程看论文。
- 实验数据集与评价指标
  - 数据集：DAU2004 summarization dataset，实体权重由逻辑回归学习得到（2009 Takamura and Okumura）
  - 评价指标：
    - ROUGE: 用来评价覆盖性，是否包含最关键的信息，但是对连贯性不敏感，ROUGE-1和人类标注有更高的相关性。
    - 人工抽样：让语言学家来判断，原始的方法和我们的方法哪个更连贯。
- 总结：本文的写作通俗易懂。首次提出了解决摘要的连贯性（coherence）的的解决办法，首次不使用话语分析就可实现连惯性的摘要

## 这几天好像又懒了

### 7.Learning to Encode Text as Human-Readable Summaries using Generative Adversarial Networks.pdf

- 年份： 2018-EMNLP
- 内容介绍
  本文在压缩输入的句子自动潜在空间表示方面，人很难理解，本文提出了训练自动编码输入的句子可以人类可读，从而实现不成对的摘要总结。
- 创新点
  生成人类可读的摘要，并且是无监督的
- 模型介绍
  - 本文介绍了一种模型，该模型由生成器G，判别器D,和重构器R构成。G和R是seq2seq模型，给生成器喂一个长的句子，输出一个包含内容重要信息的短句子，扔给D去判断和真是句子的差别的大小，利用R能够通过这个短句子构建输入的长句子。G和D构成GAN神经网络的训练。  
  在整个训练过程中，最小化重构损失，最大话的回报。
  - 关于GAN的训练，可以有WGAN（梯度惩罚），最大化D的损失，最小化G的损失。Self-Critic Adversarial REINFORCE方法，核心的方法是用LSTM来当D，评估当前的G的输出结果，包含Self-Critic Generator 和 Discriminator 2两部分。
- 数据集
  - English Gigaword : 这是一个每个文章有对应title的的数据集
  - CNN/Daily Mail dataset:长文本摘要数据集，并且对应的有摘要
  - Chinese Gigaword： 长文本摘要数据集，包含摘要和新闻。
- 评估手段
  - ROUGE-n gram系列，S1是预测的句子，S2为标注好的句子
    - ROUGE-1：1-gram,每个单词，定义为= （S1和S2的交集）/(len(S2))
    - ROUGE-2： 2-gram，连续的两个单词构成。定义和一一样，但是这里是2-gram的交集和S2的2-gram的长度
    - ROUGE-L：L代表最长子序列，（单字哈）
    [详细介绍] (<https://blog.csdn.net/qq_25222361/article/details/78694617>)，通俗易懂，很好理解

### 8.Improving Semantic Relevance for Sequence-to-Sequence Learning of Chinese Social Media Text Summarization

- 年份： 2017-ACL
- 内容介绍：
  本文基于Encoder-Decoder框架，加入门控的attention机制，利用余弦相似函数增强输出的摘要和原文的语义相关性。抽取式的摘要，语义相关性高，生成式的语义相关性不高。
- 创新点：
  短文本的摘要适合Encoder-Decoder框架，但是以前的方法，侧重句法和连贯性，并不关注语义相关性。本文就提出了增强语义相关性。
  - 门控的注意力机制来捕获信息
  - 加入相似性判断来优化损失函数
- 模型介绍
  基于Encoder-Decoder框架加入了a gate attention 和 相似度函数好 度量生成的的句子和原句的相似度，是的使得生成的句子能够有更好的语义。
- 数据集
  - LCSTS（Large Scale Chinese Short Text Summarization Dataset）:中文新闻数据集，带有摘要的数据
- 评估
  - Baseline：
    - RNN：双向的GRU(门循环单元)编码，单项的GRU解码
    - RNN context：seq2seq框架，attention机制捕获信息

### 9.Generating Summaries with Topic Templates and Structured Convolutional Decoders.pdf

- 年份：2019 ACL
- 内容介绍：  
  多文本的长文本摘要，根据摘要和文本主题的相关，依据Encoder-decoder框架，设计了一个CNN用来编码，LSTM作为句子水平的解码和分层的CNN文档水平的解码，一个三层结构，细分了每个段落的主题，最后生成一个全局上的文本摘要，使得摘要内容的覆盖性更高。
- 创新点：
  - 考虑了文本的内容结构和句子水平和文档水平的主题
  - 采用了CNN而不是RNN
- 数据集：WIKICATSUM数据集（[代码和数据集](<https://github.com/lauhaide/WikiCatSum>)）,包含公司，动物，电影三个数据集。
- 评价指标
  - ROUGE分数
  - 人工评估分数
  
### 10. Neural_Extractive_Text_Summarization_with_Syntactic_Compression.pdf

- 年份 2019
- 内容介绍：  
  本文介绍了一种基于神经网络的文本摘要抽取和句法压缩的系统模型，进行的是单一文本摘要；
  - 抽取：
  - 句法压缩：删除一些无用的信息（这里指词），这类的方法大概都是 句法解析驱动，当然也有使用端到端的神经网络模型；
      这里包含一个压缩的阈值参数，传统的压缩规则根据句法的规则，如同位语名词短语，相关分句和副词，动名词短语。介词短语，
- 模型介绍
  - 句子抽取选择，选择k个句子，使用双向的LSTM编码句子或者文档的，利用卷基层和最大池化层来抽取每个句子的表示，解码阶段使用一个序列的LSTM来解码，具体的步骤见论文描述
  - 文本压缩，移除固定的短语或者单词，压缩使用一个二分类，决定一个单词删还是不删，用启发式的重复数据删除，减少冗余性
  - 后面又提出了一个改进的模型，前K句作为候选的模型（LEAD BASELINE），LEADDEDUP使用启发重复数据删除来选择K句，JECS为结合了抽取和压缩摘要一起。
- 创新点
  - 抽取文本的摘要，使用了神经网络来抽取，传统的都是句子排序和关键字权重
  - 句法上压缩抽取出来的句子，得到更短的句子作为文档的摘要，这里的压缩使用一个二分类决定这个词保留还是不保留。
- 数据集(3个新闻数据集)
  - the New York Times corpus(NYT):
  - CNN：
  - Daily-mail(DM)：
  分词工句使用了斯坦福的CoreNLP分词器。
- Baseline：
  - 抽取式：
    - NeuSum: seq2seq模型预测一个句子序列从文档中选不选择。（本文和这个类似）
    - Refresh：抽取模型的句子排序分数
    - BanditSum：抽取摘要作为 语境问题 处理
    - LatSum：用额外的生成压缩模块的潜在抽取模型
  - 生成式：
    - PointGenCov：复制和覆盖机制
    - FARS：摘要重写模型（抽取的top句，重写）
    - CBDec：seq2seq模型，在解码阶段有所提高模型
- 评价指标
  - ROUGE
  - F1去近似Rouge
  - 语法评价指标：
        - 1. 使用了Amazon Mechanical Turk
        - 2. 人为分析
  
### 11. Affinity-Preserving Random Walk for Multi-document summaries.pdf

- 年份: 2017 EMNLP
- 内容介绍：
  本文主要介绍了一种以图的排名为基础给句子打分的算法，著名的有PageRank.本文是多文档抽取式的摘要方法，本文的算法是亲和度预留的随机游走算法（通过吸收随机游走模型预留句子关系的亲和度），并且介绍了在随机游走过程中可调整的算法去适应不同限制的摘要任务。  
  - 多文档一般都会超过一个主题，所以有通用的多文档的摘要（主要信息，无偏）和topic-focused的多文档主题（偏向主题分布）。通用多文档摘要：显著性（中心句）+ 差异性（最短的能覆盖最多信息或者说不同的层面的句子）。而基于主题的摘要会多一个 相关性的，要求摘要的句子和主体分布相关。
  - 亲和度预留的随机游走算法是是基于图的排名的算法，考虑了从整个句子亲和度的全局信息收集计算。和以前的基于图的排名方法不同的是，本文在吸收随机游走模型中加入了全局正则化来转换句子亲和矩阵到句子转换矩阵和形成句子分数。

- 创新点：
  - 保留了文档原来的亲和关系
  - 提出了可调整的亲和预留随机游走算法去克服在随机游走过程中的多样性限制
- 传统随机游走算法
  [具体介绍](<https://cloud.tencent.com/developer/article/1098856>)
- 模型介绍：本文亲和度预留随机游走算法
- BaseLine：只列以图排序的算法系统
  - Cont. LexPageRank：2004年提出，主要从特征向量计算计算句子的显著性，类似于PageRank，亲和矩阵转成行随机矩阵，用来当做随机游走的权重图。
  - CRASSHOPPER：侧重在摘要的多样性的限制，避免了冗余性，该算法基于吸收游走过程产生唯一的句子当做摘要。
  - DivRank：均衡高排名句子之间的突出性和多样性，强化随机游走过程
  - APRW
  - AAPRW  
  其他的算法不在列出，具体看论文实验部分
- 数据集
  - DUC 2003:通用摘要数据集
  - DUC 2004:聚焦主题的摘要数据集
- 评价指标
  - ROUGE-1:反映了摘要的覆盖性
  - ROUGE-2：效果最好，反映了摘要的流畅性
  - ROUGE-4
  
### 12. Bottom-Up Abstractive Summarization.pdf

- 年份：2018 EMNNLP
- 内容介绍：
  - 本文介绍了一个基于神经网络的内容筛选的二步走的摘要生成方式，利用了很少的数据+自底向上的注意力机制限制模型去选择单词和短语。
  - 两段的过程为：先选择文中的关键短语，在释义他们，构成摘要。本文的筛选过程是将这个框架当成一个序列标注任务来处理，决定给每一个词是不是应该出现在摘要中。
  - 本文还是从单词级别上来做摘要内容抽取，这里建简化了以下，利用的0,1标签。无监督的，对齐文档和摘要，
  - 对于词的表示（100dim）：分为两部分，一部分是（Glove）预训练好的词向量，一部分是（Elmo）训练好的上下文的单词向量
  - 对于自底向上的模型：主要是pointer-generator模型。（神经网络复制模型是复制一个长句子或者整句话）先在整个数据集上去训练一个pointer-generator，在推测阶段在生成掩码，内容选择器选择计算每个字符串的选择概率；这个概率被用来修改复制机分布来仅仅包含由选择器区别出来的。
  - 推断过程：增加了长度惩罚（避免选出的词太多）和覆盖惩罚（避免包含的关键信息太少，避免重复）
- 创新点：
  - 提出了自底向上的内容筛选器
  - 训练所需要的数据很少
- 数据集（标准的新闻数据集）
  - CNN-DM：
  - NYT：
- 评价指标
  - ROUGE-1
  - ROUGE-2:分数最高，说明摘要更加的流利
  - ROUGE-4

### 13.Retrieve_Rerank_and_Rewrite_Soft_Template_Based_Neural_Summarization.pdf

- 年份是：2018 ACL
- 内容介绍：（更详细的介绍参考了 [博客](https://blog.csdn.net/appleml/article/details/89306681)）
seq2seq模型目前还有很多缺点，本文所做实验表明：
  - （1）生成的文本过短，3%的摘要不超过3个词
  - （2）随着生成序列的增加，生成性能急剧恶化
  - （3）重复生成某个词
  - （4）侧重于复制原文  
也就是说基于原文自由式生成的摘要的seq2seq模型目前效果还不甚满意，所以本文想要结合摘要模板做生成，又由于传统的基于模板的文本摘要也有如下缺陷：
  - （1）构建模板非常耗时
  - （2）需要有专业的领域知识
  - （3）开发各个领域的所有摘要模板不现实  
受基于检索的对话系统的启发，作者认为相似文本的摘要作为软模板，用于指导当前文本生成摘要有指导，所以本文的做法是：seq2seq+soft template
本文的方法有三个模块，分别是Retrieve, Rerank以及Rewrite:
  - Retrieve: soft template,使用了基于lucene的检索IR分析平台来进行挑选出句子作为软模板，默认选择30个，验证集和测试集只挑选最相似的一个作为soft template.
  - Rerank: 双向lstm编码输入句子x和模板r，再利用用Bilinear network 预测输入 x 和软模板 r 的相似度，在Retrieve阶段保留了30个候选软模板，所以30个不同的软模板 r 分别与 x 计算相似度， 所以需要对30个软模板进行排序
  - Rewrite:通过上一步的Rerank步骤后，我们从30个候选软模板中挑选出了最和输入句子 x 相似度最高的软模板 r, 由于软模板 r 是其他训练输入句子的摘要，并且 r 中包含的命名实体可能在句子 x 中可能从未出现过，所以 r 不能粗鲁的认为是 x 的 摘要，但是可以依据模板 r 指导句子 x 的 摘要生成。基于此，本文引入了可以具有重写能力的seq2seq model.首先，将句子的隐状态信息和模板的隐状态信息进行拼接，然后送入一个标准的attention seq2seq 框架去生成一个输出序列的隐状态，然后经过一个softmax layer预测摘要中的词（注意一次只生成一个词，类似于机器翻译）
  - 学习阶段：本文将Rerank和Rewrite两个联合训练，所以损失函数由两部分组成，在Rerank中，使用交叉熵损失函数，在Rewrite阶段，最大化评估概率。
- 创新点：
  - 结合了软模板来克服seq2seq的不足点
  - 扩展seq2seq模型框架来知道模板排序和生成模板摘要
  - 第一次使用基于检索的IR和seq2seq结合
- 数据集
  使用了英文的标注Gigaword语料集，[下载地址](<https://github.com/harvardnlp/sent-summary>)
- Baseline
  - 本文的[代码](<http://www4.comp.polyu.edu.hk/~cszqcao/>) (目前似乎访问不了)
  - ABS:用CNN编码+神经网络语言模型（NNLM）解码生成摘要句子
  - ABS+：计入hand-crafted特征平衡抽取和生成摘要
  - RAS-Elman：ABS的扩展模型，用卷积神经注意力编码+RNN解码
  - Featseq2seq：完整的seq2seq RNN模型，加入hand-crafted（如POS tag and NER）来增强编码表示
  - Luong-NMT：神经机器翻译模型，包含两层LSTM,每层500个隐状态
  - OpenNMT：用OpenNMT实现标准的注意力seq2seq模型
  - FTSum：编码抽取到的原文来提高生成摘要的置信和信息量
- 评估手段
  - ROUGE用来评估摘要的覆盖量（信息量）
  - 摘要质量评估：
    - LEN_DIF: 长度不同，影响了可读性和稳定性
    - LESS_3: 生成少于3个单词的摘要，可读性差
    - COPY： 从原文复制单词占比，比例越大就说明需要压缩
    - NEW_NE: 未出现的命名实体数目，直觉上会带来不合理，用斯坦福的coreNLP工具来识别

### 14.Graph-based_Ranking_Algorithms_for_Sentence_Extraction.pdf

- 年份: 2004
- 内容介绍：
  介绍了基于图排序的各个算法，并且进行了评估，都是无监督的自动摘要抽取，本文介绍了TextRank
- 常见的图排序算法实现句子抽取
  - Kleinberg's HITS 算法：根据作者引用度来排序的迭代算法，对每个顶点，计算两个分数，分别为：“authority”分数和“hub“分数。
  - Position Power Function ：计算了顶点的出度和入度的分数，相互对应
  - PageRank（用于网页的引用分析）：具体的计算公式为：$PR(V_i) = (1-d)+d*\Sigma_{V_j \in (V_i的入度集合)}\quad \frac{PR(V_j)}{|V_j的出度大小|}$ ，其中$d$为阻尼系数，其中PR值为随机初始化，不会影响最终的结果，但迭代论述不同可能会影响最后的结果。
  - TextRank：（局部的选择/决策）:构建成带权重的图，无监督，给出了所有句子的排序
- 常见的图分类
  - 无向图：上述都是基于有向图的算法，都可有转成完全无线图来片跑，也就是节点的出度=入度，收敛曲线，无向图和有向图差不多有重合
  - 权重图：更具两句话之间的相似度作为权重，$Similarity(S_i,S_j)= \frac{两句话共同包含的单词数}{log(|S_i|+log(S_j))}$
- 数据集
  - DUC 2002（Document Understanding Evaluation）
- 评估手段
  - ROUGE

### 15.Towards_Opinion_Summarization_of_Customer_Reviews.pdf

- 年份：2018 ACL Workshop
- 内容介绍：本文是一篇综述类的文章，主要介绍了在用户评价观点上进行文本摘要总结的一些基于神经网络的基本方法，同时阐述了未来的发展方向，目前方法存在的问题。
  - 目前的信息过载，客户读不完，商家没时间全部浏览（只读最相关的），做文本摘要有助于制作决定（商家改进）和相关判断（用户买不买）
  - 文本摘要是从一个或者多个文本中，生成出不长于原文本但是可以表示原文本的信息的句子集合。
  - Encoder-Decoder框架在句子水平生成摘要，借鉴了机器翻译任务的架构（目前很流行），RNN编码（带卷积的注意力机制）
  - 2014年Ferreira提出句子聚类，去除冗余性和信息多样性问题。利用文本表示来将输入转成图模型，代表句子之间的4类关系。
  - 一个不常用的技术（AMR（Abstract Meaning Representation））,基于这个算法提出了treebank for AMR（liu 2015）,将原文解析成一个AMR图，接着将该图转成输出生成摘要图
  - 点生成架构（和第12篇论文都是用高级的 pointer-Generator架构）
  - RNN来训练文本表示
  - 用户观点总结：基于特征摘要生成（有抽取句子，tfidf，MMR（关于主题句子）） ，2010 Ganesan提出基于图框架的生成摘要，后来发展到基于属性，领域等多部方法。
    - 2017Lovinger提出了Gist，主要从文本中挖掘出观点摘要
  - QA观点总结
    - 2014 wang 提出子模函数框架 -> 基于查询的摘要，不同的主题被编码成不同的子模函数
    - 2015 Guo 提出了结合大众观点和专家观点来构建相反的输出，解决对话中用户更关心的问题。
- 未来发展方向
  - 研究领域不要限于新闻媒体文章，目前就是这个
  - 应该发展多语言的摘要，不只有英文
  - 用户生成的内容总结有噪音和语法问题，可能包含相反的观点，观点挖掘和语义分析目前发展不全
  - 用户观点基于特定时间的转换，研究不足，缺乏大的数据集
  - 评估手段太过单一，目前有ROUGE和人工评估（费时费力）
- 研究方法推荐：三步走的研究方法
  - 属性检测： 首先确定用户说的是哪一个方面的问题，然后利用词分布式向量进行分类，本文打算使用双向的LSTM结合卷积注意力机制去区分文本的属性
  - 观点特征聚类：根据属性不同聚类，将所有句子的观点全部区分开来，每个流行的观点都必须包含在内
  - 句子生成：利用神经网络架构去生成基于聚类属性和句子极性（表达的情感）的句子。

### 16.Graph-based_Neural_Multi-document_Summarization.pdf

- 年份：2017 CoNLL
- 内容介绍：本文介绍了一种基于句子关系图的多文档摘要（MDS），利用了基于关系的[图卷积神经网络（GCN）](<https://www.jianshu.com/p/89fbed65cd04?winzoom=1>)，句子的表示使用了RNN来获得输入节点的特征（也就是句子的embedding），通过逐层传播，GCN生成句子高级的隐藏层特征，用来评估重要性（salience> estimation），然后使用贪心的形式抽取刚刚得到表示的句子同时避免冗余性。
  - 基于图的多文档总结（MDS）：LexRank基于句子特征向量
  - 基于神经网络的摘要：句子压缩，RNN Encoder-Decoder（加入注意力机制），评估相关性和重要性
- 创新点：
  - 不要费力的句子编码解码框架
  - 利用句子关系图
- 本文方法
  - 两步走：1. 句子重要性评估 2. 句子选择
    - 句子重要性评估：先建立句子关系图（使用了门控循环神经网络（GRU（Gate Recurrent Unit））），最后的隐藏状态作为句子的Embedding，然后在有句子Embedding的句子关系图上利用图卷积网络（GCN）来产生最后的句子Embedding作为整个图的表示. 用最后的句子Embedding去评估了之前每个节点的句子的重要性分数。第二层的GRU表示为整个类的Embedding，过程和上述类似。
    - 根据每句话的重要性分数，然后利用贪心的办法选择出长度限制的摘要。
  - 聚类上的图表示：3中办法的句子关系的权重边连接。
    - 第一种
      1. 标准的余弦相似度 $siliarity = \frac{S_i \cdot S_j}{|S_i| \cdot |S_j|}$,其中$S_i,S_j$分别为句子i,j的Embedding。
      2. tf-idf余弦相似,先用tfidf求得关键子，再得到关键词的频率向量（词袋模型），在根据余弦公式计算。详细的[描述](<https://www.cnblogs.com/wxiaoli/p/6940702.html>)
    - 第二种
      - G-Flow系统：利用句子的对话关系作为图表示（Approximate Discouse Graph（ADG）），构建边是通过构建对话关系指示, 比如动名词，事件/实体连续.....
      - 缺点：缺乏多样性的权重分配。
    - 第三种
      - 提出了PDG（Personal Discouse Graph):主要是个性化的特征，其他计算办法和ADG类似，只是规则上不一样了
- 数据集：DUC数据集，在DUC2001,2002上训练，DUC2003上验证,DUC2004上测试
- Baseline
  - 按照三种边权值不同的构建进行实验。
- 评价指标
  - Rouge

### 17.CN91基于主题约束的篇章级文本生成方法研究

- 内容介绍  
  本文提出一种基于主题约束的篇章级文本自动生成模型。该模型针对用户输入的主题描述语句，采用 $Twitter LDA$ 概率主题模型提取若干主题词；然后采用 Word2Vec 词向量余弦相似度计算方法对主题词进行关键词扩展；接着对扩展后的关键词集进行Kmeans主题聚类，形成文章主题规划；最后，采用基于注意力机制的循环神经网络（双向的LSTM和），利用每个聚类中的关键词信息约束每个段落生成的文本内容。 根据每个主题聚类生成一个段落，生成主题多方面的文本信息，实现篇章级文本生成。该模型依据主题关联程度为每个关键词设置不同的权重，从而控制生成文本的主题分布。 另外，模型采用一种改进的注意力评分机制，依据前文与每个主题的相似度调整注意力评分，可以平衡多个主题的影响。为了提高主题词在生成文本中的出现可能性，针对主题词添加一个生成概率附加项
- 创新点
  - 将主题模型引入进来明确的文章主题
  - 利用RNN模型进行语句通顺性调整

### 18.Unsupervised Semantic Abstractive Summarization.pdf

- 年份：2018 ACL Student Research  Workshop
- 内容介绍  
  - 本文介绍了一种为SAS（Semantic Abstract Summarization）开发的新的的pipeline，首先生成句子的AMR（Abatrsct Meaning Representation）图，然后通过该图来总结子图，最后从这个总结子图中生成最后的摘要。
  - 详细介绍：
    - AMR：试图捕获一个句子中“谁在对谁干什么（who is doing what to whom）”，AMR表示由根，无环，标签，有向图构成。边表示语义概念关系，节点代表概念。
    - 本文提供了一个可供选择的方法使用AMR来生成抽象总结。人类写总结的过程是先写下关键短语，然后指出他们的关系，接着组织这些数据。所以本文先找到最重要的实体/事件（entities/events）,接着区分重要的实体/事件之间的关系,最后捕获信息通过选择这些关系。
    - 本文Pipeline过程：[代码](<https://github.com/shibhansh/Unsupervised-SAS>)
      - 文档转成AMR图：具有相同实体的节点合并使用了共指消解（co-reference resolution）技术，包含统计、规则、神经网络。
      - 总结图抽取：1. 先找到关键的节点，利用的tfidf找到n个重要的节点 2. 找到节点之间的重要的关系。本文利用了启发式（利用共现性），靠近根节点任意两节点的路径 3. 捕获周围的信息。用OpenIE Banko来捕获，选择最大的关系元祖。
      - 总结生成：从抽取的AMR图来生成。
- 创新点
  - 更容易理解的生成AMR图的过程。使用了共指消解（co-reference resolution）和源节点（Meta Nodes）
  - 关键的子图抽取无监督的算法
- 数据集：
  - proxy report section of the AMR Bank Knight et al.(2014) 完全不知道的一个数据集：提供了为新闻文章极其摘要的人类生成的AMR图。
- 评价指标
  - 准确率、召回率、F1值
  - ROUGE分数

### 19.Toward_Abstractive_Summarization_Using_Semantic_Representations.pdf

- 年份 2018 arxiv
- 内容介绍
  - 本文提出了一个新的摘要生成办法，利用AMR（abstract Meaning Representation），原文本解析成一个AMR图，然后转成一个摘要图，摘要就从这个图里产生。也就是一种图到图的转换，本框架是数据驱动训练。本文[代码](<https://github.com/summarization/semantic_summ>)
  - [详细介绍](<https://blog.csdn.net/cx943024256/article/details/86556507>)
  - 本文流程：1. 先将一个文本的句子解析成AMR图 2.合并这些句子的AMR图合并成一个总图（本文的重点，当做一个[结构预测1](<https://zhuanlan.zhihu.com/p/41165572>)和[结构话预测2](<https://zhuanlan.zhihu.com/p/39745877>)，就是序列的输出是结构化的数据（如序列，图，树，图等）） 3. 从整体上生成摘要
  - 第2步重点合并AMR的图，也就是合并相同的节点，为保证联通性，增加了一个无意义的ROOT节点，有向，无环的句子语法图。第一步作者使用了JAMR工具进行构建句子的AMR图
  - 总图生成：主要包含4个部分 Collapsing、Merging、Expansion、Subgraph Prediction
    - Collapsing: 将由多个节点构成的命名实体或时间实体看作是一个单独的节点。比如（人A，名字，李四）就是由三个节点构成的命名实体，他就可以被视为一个节点。
    - Merging:在所有句子中，出现的同一个节点（比如李四在两个句子中都出现），都合并为一个节点。同时与他们想关联的边以及标记都连接到这个新的节点上。最后，新建一个新的根节点，并将这个根节点连接到所有句子各自原先的根节点上，将多个句子连接成新的总图.
    - Expansion: 每个句子中，添加新的节点给所有可能存在关系的节点对。比如 the dog running in the garden就可以得到the dog is in the garden 的新内容
    - Subgraph Prediction:作者将这个问题看做是一个结构化预测问题，然后使用整数线性规划（ILP）的方式进行子图约束，之后使用支持向量机对上面的系数进行学习，最终可得到提取到的最优的子图。
  - 文本生成：之前就已经有了基于统计的方法，但是到发文日都没有一个以使用AMR进行机器翻译为目标的系统。所以作者只是使用启发式的方法生成了一个词袋
  - 创新点
    - 首次利用了AMR进行摘要生成，实体共指消歧解决节点合并，但依然存在节点合并不全的问题。
  - 数据集
    - proxy report 数据集：带人工标注的AMR图和摘要：从English Gigaword corpus选择单篇新闻得到的标注数据集。
  - 评估手段：Rouge-1
  
### 20.Features_in_Extractive_Supervised_Single-document_Summarization_Case_of_Persian_News.pdf

- 年份： 2019 arXiv preprint
- 内容介绍
  - 本文提出了波斯语的的一个抽取摘要的办法，利用特征在抽取监督单文摘要方面的研究。因为抽取式的办法更为简单，不用生成句子，抽取式更加流行，核心在与句子分数排序，本文讲文本特征整合成每个句子的向量。基本的流程是 监督抽取摘要 -> 排序机排序句子 -> 选取top-n句作为句子摘要。
  - 整合文本特征：监督的抽取式摘要分为两段：
    - Learning Phase:如何排序句子分数，采用MSE（均方误差mean square error）和R2（coefficient of determination）评估
      - 特征抽取：文档敏感（document-aware features）和文档不敏感（document-unaware features），如文档的属性
        - document-unaware features：  
          1. 句子位置：认为开头和结尾的句子更有可能是摘要。
          2. 句子长度：定义不清楚，一个固定的句子长度，例如15个单词，在一些文章为长句，在一些文档文档短句
          3. 名词比率：名词形容词动词副词的比率
          4. 数字实体比率：讲道理应该是更低的权重
          5. 暗示词：如in conclusion/overall等词,更有可能是中心句（摘要句）
        - document-aware features
          1. 余弦位置：$pos(index) =  \frac{cos(\frac{2\pi*idnex}{T-1})+\alpha-1}{\alpha}$ 其中index为用整数表示的第几句话，T为文档的总数，$\alpha$为微调参数。这个值取值范围为 $[0,1]$
          2. 相对句子长度：$Relative Length(s) = \frac{|s|}{\frac{\sigma_{i=1}^{n}|s_i|}{n}}$,其中n为文档的句子树，$s_i$为第i句，这个比率大于1认为是长句
          3. TF-ISF：句子的频繁项，类似于 TF-IDF一样
          4. POS特征：词性标注特征，名词，动词，形容词，副词，量词。定义为$ratio = \frac{句子中动词的个数}{文档中动词的个数}$
        - 明确的文档特征
          1. 文档句子：文档句子数量参与排序，包含暗示单词的句子
          2. 文档单词数：文档的单词个数 决定了文档的长度。
          3. 主题类别：政治经济
      - 目标分配：每个特征向量需要一个目标值，系统学会如何给句子排序。本文采用了回归的方式来训练模型
    - Summarization Phase：从Learning Phase 排序句子得到摘要，采用了ROUGE评估
      - 特征抽取：分词，去停词，常见步骤
      - 句子排序：为每个句子预测一个0到1之间的值
      - 句子选择：解决可读性，按照文章句子出现的顺序排列，顺带考虑切断句子长度
- 创新点
  - 考虑了文档的每个属性，增加了精确的文档特征（如文档属性）
- 数据集
  - Pasokh数据集：包含100条波斯新闻，每条有5个摘要，6个类别，文档长度4-150句
  
### 21. Gather customer concerns from online product reviews – A text summarization approach.pdf

- 年份： 2009 Expert Systems with Applications
- 内容介绍：
  - 这是一个系统类的应用，该论文首次见个自动摘要的技术应用到了观点挖掘，情感分析中，一般的只是进行正负性的判断，为购买者和开发者提供建议。本文办法如下：
    - 去停词，和还原词性
    - 主题区分：主要是要通过一个频繁单词序列的寻找，只要是一个迭代的找到用户观点中共现信息的频繁序列，有点像Aprior算法，
    - MMR抽取得到候选句子：将观点句子分在主题下面，然后MMR抽取下重要的句子
    - 后选句子排序：根据用户id来排序候选的句子（每个观点用用户的id来标记）
  
### 22. Sentence_Ordering_and_Coherence_Modeling_using_Recurrent_Neural_Networks.pdf

- 年份：2018 AAAI
- 内容介绍
  - 想法来自于作者想要去表示更深层的句子表示，然后联想到去建立句子的连贯性（局部连贯性和全局连贯性）的模型，使用循环网络解决句子的顺序问题。也就是学会句子集合的结构。
  - 本文利用了RNN去来解决句子顺序问题。编码部分使用了set Encoder (set2seq框架)，解码使用了Pointer network. 本文的过程分为3段：read，process，write。
    - 分数函数：和窗口网络的类似，考虑了双线性的分数函数
    - 对比句子：把握整体的理解
    - 连贯模型：定义连贯性分数为偏序函数
  - 顺序区分：主要当成一个二分类的任务
  - 句子顺序：捕获高级的句子的逻辑结构
  - 句子顺序和摘要
- 创新点：
  - 捕获句子的顺序的有用文本表示
  - 可视化捕获句子段落结构的高水平的逻辑结构的模型
- 数据集：
  - Accidents and Earthquakes new reports(顺序区分实验数据集)
  - NIPS Abstract、ACL Abstrsct、NSF Abstract（句子顺序 实验数据集）
  - DailyMail、CNN dataset（句子顺序和摘要 实验数据集，使用了Rouge 评估）
- Baseline
  - Entity Grid：实体网格表示实体关系（[工具](<bitbucket.org/melsner/browncoherence>)）
  - Seq2Seq:
  - 窗口网络：
  - RNN解码：

### 23. Global_Encoding_for_Abstractive_Summarization.pdf

- 年份： 2108 ACL short paper
- 内容介绍：
  - 本文主要解决了seq2seq模型产生的摘要的重复性和语义无关的问题。本文提出了用卷积门控单元来增强文章的内容表示，达到捕获文章的中心信息。编码使用了双向的LSTM，解码使用了无向的LSTM解码。本文的方法就在编码的部分实现
  - 本文的代码参参见[代码](<https://www.github.com/lancopku/Global-Encoding>)
- 创新点
  - 解决的摘要的单词重复性和语义无关的问题
- 数据集
  - LCSTS:来自新浪微博的大量短文本的摘要
  - English Gigaword: 标注的新闻数据集
- Baseline见文章的内容。其实在之前的论文里面也有介绍过，不在赘述。

### 24. Multi‑Task Learning for Abstractive and Extractive Summarization

- 年份 2019 Data Science and Engineering
- 内容介绍
  - 本文主要介绍了联合抽取和生成摘要，形成多任务学习，抽取式是内容重要信息（句子分数）的评估，生成式是连贯性的评估。1. 分层次的文档编码，先用双向的GRU来进行单词编码，再用双向的GRU编码句子，形成一个层次话的编码，然后共享该编码 2. 基于解码的分层注意力 3. 一个抽取器构成该框架的三个部分。多任务学习体现在，解码的负对数损失函数+抽取句子的交叉上损失函数+文章注意力的l2损失。
- 创新点
  - 层次化的表示,捕捉了局部和全局的信息
  - 多任务的学习办法，生成摘要为主要的任务，抽取摘要为辅助任务，联合训练使用了多任务学习
- 数据集
  - CNN：
  - DailyMail：
  
### 25. Twitter_Summarization_Based_on_Social_Network_and_Sparse_Reconstruction-AAAI-2018

- 年份 2018 AAAI
- 内容介绍
  - 本文主要是解决社交媒体（推特）所关心的话题的基本信息。通过话题导向摘要（topic-oriented）来解决问题。传统的摘要的手段不适合短文本和有噪声的文本（这是短文本的特性），本文借鉴了社交理论中表达一致性（express consistence：指一个人一段时间内的博文和某一特定主题有关）和表达传播性（express contagion：一个人会向其朋友传播该主题），构建了社交网络和洗漱重构框架，推文之间的关系描述为社交正则化，可以指导稀疏重构（选择一条推文表达一个特定的话题），这考虑了稀疏性和覆盖性，同时设计了多样性正则，主要移除冗余性.
  - 在算法的设计过程中，使用了不只推文内容，而且用了用户关系矩阵，推文推文矩阵等信息。
- 创新点
  - 定义了社交摘要问题，验证了表达一致性和表达传播性两个社交理论
  - 推文水平的一个网络信息的稀疏重构
- 实验部分：找的志愿者来进行选择每个话题下最重要的博文，最后生成的用来Rouge来评估。
- 数据集
  - 推特数据集：[数据集](<https://wiki.illinois.edu/wiki/display/forward/Dataset-UDI-TwitterCrawl-Aug2012>)
- Baseline：参见文章的内容的介绍

### 26. Faithful_to_the_Original_ Fact-Aware_Neural_Abstractive_Summarization

- 年份：2018 AAAI
- 内容介绍
  - 本文发现在生成式摘要的过程中，有30%左右的摘要包含了虚假的的事实。本文想要改进这个生成式摘要包含虚假信息的问题，本文通过利用OpenIE来抽取一段文本中的事实关系，用三元组来表示（主，谓，宾）来描述一个事实，然后通过讲原文本和描述事实的文本，进行双编码（BiGRU），然后在解码阶段（单项RNN），利用双注意力机制（原文本注意力和事实描述注意力），进行生成文本（一个词接着一个词）。
- 创新点
  - 增强了生成摘要的事实描述问题
  - 建立了双注意力模型
  - 事实描述是对原文的一个压缩，可以促进生成摘要的信息度
- 数据集
  - English Gigaword：新闻数据集，标题就是摘要
- 评估手段
  - ROUGE:ROUGE-L和可读性相关
- Baseline(以下的详细描述见论文)
  - ABS
  - ABS+
  - RAS-Elman
  - Feats2s
  - Luong-NMT
  - att-s2s

### 27. Facts That Matter.pdf

- 年份： 2018 EMNLP
- 内容介绍 [代码](<https://github.com/mponza/SalIE>)
  - 本文介绍了一种事实突出任务，提出了SALIE，无监督和与知识无关的
  - SALIE：（Salient Information Extraction），主要是用来抽取原文本中的突出事实，主要不满足相关性和多样性。事实为基本的原子单元，利用pageRank来检测事实的相关性，利用聚类来检测事实的多样性。
    - 事实相关性：第一步事实为节点（有MINIE(2017年提出的开放式信息抽取系统)抽取得到），第二步边的权重，使用的是word2vec，语义相似度，第三步：相关先验性。第四步：相关性计算，利用pagerank计算
    - 事实多样性：就是聚类
- 创新点
  - 首次提出事实突出性任务
  - 提供了SALIE系统
- 数据集
  - NYT（New York Times）：新闻文章
- 评估手段
  - Rouge
- 缺点
  - 本文没有考虑事实的正确性，只是抽取到事实和人工的摘要进行ROUGE分析

### 28. Unity in Diversity_ Learning Distributed Heterogeneous Sentence Representation for Extractive Summarization-AAAI-2018.pdf
  
- 年份 2018 AAAI
- 内容介绍
  - 本文主要抽取摘要的句子语义和句子组成结构的特征来捕获文档的非独立特征表示，称做HNet。
  - 本文的模型架构
    - CSTI：捕获全局，局部，组成依赖（短语），和句子的关键信息。该部分组成：卷积编码（捕获n-gram的特征，最大池化获得特征向量），双向lstm树索引（Bidirectional Long Short Term Memory Tree Indexer：在句子语义和组成层面捕获文档的独立特征）。
      - 卷积编码：解决长依赖问题，有效压缩表示，有效的句子分类
      - 双向lstm树索引：叶子和非叶子结点的操作
    - Extractor：从给定的句子中抽取文档的特征。考虑了，句子位置，词频，平均词频，idf，最大idf
    - Regression Layer：预测句子分数并且句子排序。传统的的句子监督句子重要性的分数衡量。
    - 移除冗余句子：判断句子的相似性，最后使用了曼哈顿距离衡量。
- 创新点
  - 使用CNN来捕获文档的句子语义和句子结构组成特征
  - 去除抽取式的重复的句子
  - 利用转换学习克服了缺乏多文档摘  数据的问题
- 数据集
  - Daily Mail数据集：
  - DUC数据集发：[下载地址](<http://duc.nist.gov/data.html>)
- BaseLine
  - 主要是在DUC数据集上的一些表现性能好的baseline，见文章的描述。

### 29. Guided_Neural_Language_Generation_for_Abstractive_Summarization.pdf

- 年份 2018 EMNLP short paper
- 内容介绍
  - 本文介绍了一种利用AMR来引导神经语言生成进行抽象摘要。分为两步1. 恢复AMR缺失但是NLG却需要的信息；2.提高摘要质量。解决办法1.建立边缘信息的概率分布（probability distribution of the side infomation）；2.在自然语言生成（NLG）步骤时，用该分布来引导seq2seq+注意力模型。
  - 这部分的细节，没有看太懂，介绍的不详细
  - 代码 [本文代码](<https://github.com/sheffieldnlp/AMR2Text-summ>)
- 数据集
  - Rroxy Report section from the AMR dataset

### 30. A_Bayesian_Method_to_Incorporate_Background_Knowledge_during_automatic_text_summarization.pdf

- 年份 2014 ACL
- 内容介绍：
  - 本文介绍了一种认为摘要的背景只是很重要，所以加入基于贝叶斯发现的模型，即该模型可以决定了是哪一块的文本是改变这个人的想法。很简单的道理，就是说随着背景知识的增加，一个人的想法会改变。本文提出了两种摘要，一种是通用型摘要：用随机的大数据新闻文章做为背景知识，一种是更新型摘要：小数据集特定主题的新闻文章作为背景知识。
  - 贝叶斯发现（Bayesian surprise）：定义见文章第三部分。
  - 抽取摘要的算法：
    1. 计算单词的分数：根据单词的类型，单词的surprise度为单词的KL散度
    2. 计算句子分数：由单词组成句子分数
    3. 句子选择：选择一个分数高的句子，则把该句包含的主题词分数给设置成0（为了避免冗余）.然后重新运行1,2两步，直到达到摘要句子的长度
  - 贝叶斯发现保持了关于背景的多假设，主题词的计算是一个二项分布的
  - 通用型：使用了多文档输入（DUC2004），背景使用了English Gigaword corpus
  - 更新型：使用了TAC 2009，保证A比B输入的时间迟。
- 创新点
  - 直接模拟了人的观点，人如何基于背景知识区别一个主题或者事件的重要程度
- 数据集
  - [DUC 2004](<https://www-nlpir.nist.gov/projects/duc/index.html>)
  - [TAC 2009](<https://tac.nist.gov/>)
  - English Gigawords
- 评估手段
  - Rouge： Rouge-1，Rouge-2
- Baseline
  - 有$KL_{back}$,$TS_{sum}$等，具体看文章的介绍.

### 31. Extract_with_Order_for_Coherent_Multi_Document_Summarization.pdf

- 年份 2017 ACL
- 内容介绍：本文解决了一个多文档抽取式摘要的句子排序（句子位置）的连贯性问题，以此来增加可读性。使用关键短语的连续向量表示。
  - 句子抽取的过程是先去停词，然后使用了预训练的词向量E，一句话的表示就是$S = \sum_{w \in S} TF(w,S)*E[idx[w]]$其中idx[w]就是词的索引，TF(w,S)代表一个单词在一句话中的出现次数。第二个是计算句子$S_i,S_j$之间的相似度，这里定义了两句之间的命名实体之间的相似性$NESim(S_i,S_j) = \frac{|NE(S_i) \cap NE(S_j)|}{min(|NE(S_i)|,|NE(S_j)|)}$,其中$NE(S_i)$代表就是利用NLTK提取到的命名实体，同时余弦相似度$CosSim(S_i,S_j)$,最后得到两个句子之间的相似度
  $$Sim(S_{i},S_j) = \lambda * NESim(S_i,S_j) + (1-\lambda)*CosSim(S_i,S_j)$$
  - 利用TextRank（本来相似度是字典重合的相似度）算法进行抽取句子，利用上述的相似度替换了TextRank的权重。初始化设置每个节点的分数为1，更新规则为
  $$Rank(S_i) = (1-d)+\sum_{S_j \in N(S_i)}\frac{Sim(S_i,S_j)}{\sum_{S_k \in N(S_j)}Sim(S_j,S_k)} Rank(S_j)$$
  其中$N(S_i)$代表句子$S_i$的邻接节点,d=0.85.
  - 句子聚类：使用了2014年Murtagh提出的分层聚集聚类的算法。将句子聚在一起。
  - 句子选择：在约束限制下进行整数规划限制ILP，来进行选择句子。抽取关键的短语（词或短语，包含了主题的信息）利用了[RAKE](<https://github.com/aneesha/RAKE>)来提取句子的关键短语。
  - 句子排序，以前是利用句子位置和时间戳信息，这次定义了连惯性的
    $$Coherence(D) = \frac{\sum_{i=1}^{n-1}Sim(S_i,S_{i+1})}{n-1} $$
- 创新点
  - 多文档抽取的句子连贯性解决
  - 提出了一个句子相似性的计算
- 数据集
  - DUC 2004
- BaseLIne
  - 见文章描述，lexRank，GreedyKL等等。
  
### 32. Global_Optimization_under_Length_Constraint_for_Neural_Text_Summarization.pdf

- 年份： 2019 ACL
- 内容介绍
  - 本文介绍了一种在长度限制条件下的全局优化的算法GOLC，以前有两种优化方式，分别是最大似然估计（MlE）和最小风险训练（MRT）。生成式的摘要存在不关注长度限制的问题，并且目前长度限制下的效果不好。所有本文提出了，修改了长度限制下的的损失函数的问题，最后将三种方式进行对比。
- 创新点
  - 新的长度限制下的全局优化的算法
- 数据集
  - CNN/Daily Mail:新闻文档包含多文档摘要
  - Mainichi Shibun Newspapers: a Japanese single document summarization.
- BaseLine
  - LEAD：抽取全文的前三句
  - PG：基于LSTM的标准点生成网络
  - PG w/ LE : PG的扩展，在训练的过程中，考虑了和参考摘要之间的剩余长度。
  - LC：卷积的编码-解码控制长度。包含了词的位置和位置embedding.

### 33. Autoencoder as Assistant Supervisor: Improving Text Representation for Chinese Social Media Text Summarization

- 年份： 2018年 ACL
- 内容介绍
  - 本文介绍了基于seq2seq，提出自动编码作为辅助的手段，提高摘要的分数.[代码][<https://github.com/lancopku/superAE>]
  - 具体的思路：就是通过监督自动编码的方式将参考摘要和原文本学习自动编码，提高文本的内部表示，最小化参考摘要和原文之间的距离，采用了对抗学习的办法（扔进去判别器进行判断），然后联合了三个损失函数来进行学习。
- 数据集
  - LCSTS： 大型中文语料集
  - Amazon Fine Foods Reviews Corpus: 用户标签作为评价的摘要，主要用来判断本文提出提出的这个语义是不是增强表示了
  