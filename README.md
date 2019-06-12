# paperReaderNote
用来记录自己研究僧阶段读取的论文，做一记录吧，在2019.05.01，有了这个记录的想法，但是一直却没有去做，最近正好没事，就拿出来一起好好开始自己的科研之路吧
# 前言
自己从2018.7.12来到这里，一直开始跟着师兄做一个关于文本的项目，目前该项目已经完结，自己也积累了一些工程上的开发技术，但是在论文上却一直没有一个研究生该有的样子。也学之前真的有想着划水过去毕业就好了，然后找一个工作，做一个卑微的人就好。后来遇见了林老师，让我深深的知道，如果只是这样的科研，那未来可期不过是自己骗自己的谎言。

所以，在研究生的过程中，去把它过得充实，然后不断的去努力，未来才可以掌握在自己手里，就想打王者一样，与其说队友坑，不如把输出掌握在自己手里，宁可钻石局5法师的重开，也不远将自己最擅长的输出，放在队友手里，最后要么carry全场，要么被喷。科研也一样，我不想让自己的命运，安安稳稳的划在别人的手里，我会将输出握在我自己的手里。

所以，加油！

# 论文
## 1. A Biterm Topic Model for Short Texts(BTM).pdf
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
## 2.Automatic Labeling of Topic Models Using Text Summaries.pdf
   - 作者简介：万小军，北京大学自然语言处理研究所负责人，主要是文本摘要
   - 内容概要：本文首次提出了给主题模型跑出来的抽象的topic，进行主题实际意义的命名。以前有人尝试过用 单词，短语，和图像来进行直观的主题的主题描述，还有抽取抽取句子作为主题的描述。本文定义了怎样的主题label是更好的，只要是 主题label和主题词的高相关性，高概括性，不同topic之间的高区分性。本文提出了基于子模优化的算法进行候选句子的筛选。
   - 创新点： 
       1. 首次提出了用文本摘要进行主题打标签
       2. 基于子模优化的文本摘要生成算法
   - 对比实验
       1. MEAD：使用启发的策略进行发现和第一个句子相似的每个句子分数
       2. LEXRank：就是句子的pageRank 算法
       3. REL：子模函数最大化
      - 标签比较：词标签，短语标签，句子标签
   - 指标：
       1. 候选句子的选择：主要靠KL散度进行来进行选择
       2. 主题摘要：主要靠增益递减的子模函数来进行选择。
       3. 定义了相关性函数 KL散度，余弦相似
       4. 定义了概括性函数
       5. 定义了区别性函数
       6. 定义了贪心的选择算法，根据2,3,4的定义相加构成的子模函数
      ###### 总结
      之前我们有尝试去解决这个topic lable的问题，尝试的办法，采用了单词的短语的形式，做法上可能相对简单，通过人工命名部分抽象名词，通过词林扩展的形式扩充好单词，采用余弦相似度和jacard相似度来进行topic的命名，这样实现的是一个半自动话的主题命名方式。今天看到万老师的这一篇文章，可以说是有了很大的了解。

