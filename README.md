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
       2. 基于子模优化的文本摘要生成算法  $f(A+C)-f(A) > f(B+C)+f(B)$，说明A优与B，具体的子模函数[介绍][<https://blog.csdn.net/s1102379635/article/details/8524397>]
- 对比实验  
       1. MEAD：使用启发的策略进行发现和第一个句子相似的每个句子分数  
       2. LEXRank：主要通过句子之间的县四度的判断对文本和词汇进行分类，以句子为节点，构造标量图，节点间的连线代表句子的相似程度（权重，用余弦相似度衡量$f(i,j) = \frac{S_i\dot S_j}{|S_i||S_j|}$），句子不相似就没有边(相似度大于一定的阈值)，在对每句话进行评分时，充分考虑顶点的度和权重，即句子的核心性和相关程度大小，然后超过一定阈值的就作为文章关键句子，更加详细的[介绍][<https://blog.csdn.net/Silience_Probe/article/details/80699986>]
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
        - 典型的句子选择算法是 最大边缘相关（maximum marginal relevance(MMR)）算法，详细的[描述][<https://blog.csdn.net/eliza1130/article/details/24033161>]
        - 概率的办法就是在概率分布和输入的单词评估之间 最小化KL(Kullback-Leibler)散度，也为相对熵。[详见][<https://baike.baidu.com/item/%E7%9B%B8%E5%AF%B9%E7%86%B5/4233536?fr=aladdin>]
        - 最广泛的还是整合线性规划（ILP），目标在受限的情况下最大化覆盖率。
     3. 句子标准化：对选出的句子进行修改和压缩，形成总结性的句子。根据第二部选择出的句子可能包含重复和不必要的信息。  
        - 有两种方法解决这类问题： 流水线是抽取，基于规则的压缩。
          在单文档的摘要中保证句子在原来文档中的顺序；在多文档的摘要中则要重排顺序。经典的重排句子的策略是句子权重图或者是基于时间戳和位置的时间排序算法。
  - 评估策略：（好的摘要易读和有高概括性）
    - ROUGE(Recall-oriented Understudy for Gisty Evalustion)：ROUGE基于摘要中n元词(n-gram)的共现信息来评价摘要，是一种面向n元词召回率的评价方法。基本思想为由多个专家分别生成人工摘要，构成标准摘要集，将系统生成的自动摘要与人工生成的标准摘要相对比，通过统计二者之间重叠的基本单元(n元语法、词序列和词对)的数目，来评价摘要的质量。通过与专家人工摘要的对比，提高评价系统的稳定性和健壮性.[详细][<https://blog.csdn.net/mch2869253130/article/details/89810974>].  
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
    - RNN：双向的GRU(门循环单元)编码，单项的GRU解码
    - RNN context：seq2seq框架，attention机制捕获信息

### 9.Generating Summaries with Topic Templates and Structured Convolutional Decoders.pdf

- 年份：2019 ACL
- 内容介绍：  
  多文本的长文本摘要，根据摘要和文本主题的相关，依据Encoder-decoder框架，设计了一个CNN用来编码，LSTM作为句子水平的解码和分层的CNN文档水平的解码，一个三层结构，细分了每个段落的主题，最后生成一个全局上的文本摘要，使得摘要内容的覆盖性更高。
- 创新点：
  - 考虑了文本的内容结构和句子水平和文档水平的主题
  - 采用了CNN而不是RNN
- 数据集：WIKICATSUM数据集（代码和数据集 <https://github.com/lauhaide/WikiCatSum>）,包含公司，动物，电影三个数据集。
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
  具体见<https://cloud.tencent.com/developer/article/1098856>的介绍
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
  使用了英文的标注Gigaword语料集，下载地址 <https://github.com/harvardnlp/sent-summary>
- Baseline
  - 本文的代码< <http://www4.comp.polyu.edu.hk/~cszqcao/> > (目前似乎访问不了)
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
- 内容介绍：本文介绍了一种基于句子关系图的多文档摘要（MDS），利用了基于关系的[图卷积神经网络（GCN）][<https://www.jianshu.com/p/89fbed65cd04?winzoom=1>]，句子的表示使用了RNN来获得输入节点的特征（也就是句子的embedding），通过逐层传播，GCN生成句子高级的隐藏层特征，用来评估重要性（salience estimation），然后使用贪心的形式抽取刚刚得到表示的句子同时避免冗余性。
- 创新点
- 数据集：DUC数据集，
- Baseline
- 评价指标
  - Rouge
  