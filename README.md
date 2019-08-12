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

- 作者简介：万小军，北京大学自然语言处理研究所负责人，主要是文本摘要
- 内容概要：本文首次提出了给主题模型跑出来的抽象的topic，进行主题实际意义的命名。以前有人尝试过用 单词，短语，和图像来进行直观的主题的主题描述，还有抽取抽取句子作为主题的描述。本文定义了怎样的主题label是更好的，只要是 主题label和主题词的高相关性，高概括性，不同topic之间的高区分性。本文提出了基于子模优化的算法进行候选句子的筛选。
- 创新点:  
       1. 首次提出了用文本摘要进行主题打标签  
       2. 基于子模优化的文本摘要生成算法  
- 对比实验  
       1. MEAD：使用启发的策略进行发现和第一个句子相似的每个句子分数  
       2. LEXRank：就是句子的pageRank 算法  
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
   2. Yahoo！Answers. <http://answers.yahoo.com/>
- 总结：本文通过长文本来解决短文本的稀疏性问题的解决，提出的纯度的评估准则，后来作为评估主题的一个重要的手段。
最近的自己真的是浪得很，一方面是一位懒，一方卖弄是因为总是被各种事打扰，没有细心去读了论文，真是罪过啊！！！

### 5. Recent_Advances_in_Document_Summarization.pdf  

- 内容描述：这是一篇关于最近几年先进的文本摘要或者文本总结的综述性论文，完整翻译见<https://blog.csdn.net/jinhao_2008/article/details/78695508>
  
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
        - 典型的句子选择算法是 最大边缘相关（maximum marginal relevance(MMR)）算法，详细的描述见<https://blog.csdn.net/eliza1130/article/details/24033161>
        - 概率的办法就是在概率分布和输入的单词评估之间 最小化KL(Kullback-Leibler)散度，也为相对熵。详见 <https://baike.baidu.com/item/%E7%9B%B8%E5%AF%B9%E7%86%B5/4233536?fr=aladdin>
        - 最广泛的还是整合线性规划（ILP），目标在受限的情况下最大化覆盖率。
     3. 句子标准化：对选出的句子进行修改和压缩，形成总结性的句子。根据第二部选择出的句子可能包含重复和不必要的信息。  
        - 有两种方法解决这类问题： 流水线是抽取，基于规则的压缩。
          在单文档的摘要中保证句子在原来文档中的顺序；在多文档的摘要中则要重排顺序。经典的重排句子的策略是句子权重图或者是基于时间戳和位置的时间排序算法。
  - 评估策略：（好的摘要易读和有高概括性）
    - ROUGE(Recall-oriented Understudy for Gisty Evalustion)：ROUGE基于摘要中n元词(n-gram)的共现信息来评价摘要，是一种面向n元词召回率的评价方法。基本思想为由多个专家分别生成人工摘要，构成标准摘要集，将系统生成的自动摘要与人工生成的标准摘要相对比，通过统计二者之间重叠的基本单元(n元语法、词序列和词对)的数目，来评价摘要的质量。通过与专家人工摘要的对比，提高评价系统的稳定性和健壮性.详细见<https://blog.csdn.net/mch2869253130/article/details/89810974>.  
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
    详细介绍 <https://blog.csdn.net/qq_25222361/article/details/78694617>，感谢这位博主，通俗易懂，很好理解

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
    - RNN：双向的GRU编码，单项的GRU解码
    - RNN context：seq2seq框架，attention机制捕获信息
