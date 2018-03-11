Apache Hadoop : 

是 Apache 开源组织的一个分布式计算开源框架，提供了一个分布式文件系统子项目 ( HDFS ) 和支持 MapReduce 分布式计算的软件架构。



Hadoop 的核心是 HDFS 及 MapReduce ，国人喜欢用 “ 分而治之 ” 来概括。



“ 分而治之 ” 

出自《 群经平议·周官二 》“ 巫马下士二人医四人 ”：“ 凡邦之有疾病者，疕疡者造焉 ，则使医分而治之 ，是亦不自医也 。” 简单点可以理解为分别治理的意思。



这类似于设计思维中的分类思想，例如：


UX 中的用户画像，给用户打 TAG ；

UED 的设计语言，分解设计目标，为不同的子目标设定设计规则；也可以用于分解设计元素，制定每种元素的设计策略；


UI & 平面设计，针对配色、构图、字体样式等有不同的考究；

UX 设计，关注功能、布局、使用路径、信息架构等的优化；

建筑／景观设计，分别关注空间、材质、功能、视线等的体验；



Hadoop广泛应用于大数据中，用于处理数百 GB 到 TB 或 PB 的数据。利用 HDFS ，集群 N 台普通计算机（ 如配置为硬盘 128 GB，内存 4 G ），形成一个硬盘为 N X 128 GB ，内存 N X 4 G 的 “ 大型 ” 计算机。Hadoop 在此扮演的是数据分发的角色，可以很方便的随时将原始数据的每一部分发送到群集中的多台计算机上进行保存，并计算。



计算的时候，使用 MapReduce 模型来将工作分成一组独立的任务来并行处理大量数据。



在 MapReduce 中，记录由被称为 Mappers 的任务隔离处理。然后将 Mappers 的输出结合到称为 Reducers 的第二组任务中，其中可以将来自不同映射器的结果合并在一起。



MapReduce 的例子——单词统计：

统计单词在不同文件中出现的次数。我们有2个文件：



foo.txt: Sweet, this is the foo file

bar.txt: This is the bar file



输出的结果应该是：

sweet 1

this  2

is    2

the   2

foo   1

bar   1

file  2
写成 MapReduce 的伪代码形式如下：

mapper (filename, file-contents):
  for each word in file-contents:
    emit (word, 1)
  
  
reducer (word, values):
  sum = 0
  for each value in values:
    sum = sum + value
  emit (word, sum)


Hadoop 不是数据库的替代品，而是一个计算框架，可以理解为就是个用于大数据的“计算器”。Hadoop 将数据存储在文件中，并且不会对它们编制索引。如果您想查找某些内容，则必须运行 MapReduce 作业以查看所有数据。这需要时间，并且意味着您不能直接使用 Hadoop 作为数据库的替代品。并且对于数据库的更新及更改数据的操作， Hadoop 都不支持。
