# TianchiNLP--Text-Classificiaton
零基础⼊⻔NLP- 新闻⽂本分类学习笔记
Datawhale 零基础入门NLP - Task01̀: 赛题理解
学习目标
理解赛题背景与赛题数据
完成赛题报名和数据下载，理解赛题的解题思路

赛题数据
赛题以匿名处理后的新闻数据为赛题数据，数据集报名后可见并可下载。赛题数据为新闻文本，并按照字符级别进行匿名处理。整合划分出14个候选分类类别：财经、彩票、房产、股票、家居、教育、科技、社会、时尚、时政、体育、星座、游戏、娱乐的文本数据。

赛题数据由以下几个部分构成：训练集20w条样本，测试集A包括5w条样本，测试集B包括5w条样本。为了预防选手人工标注测试集的情况，我们将比赛数据的文本按照字符级别进行了匿名处理。

评测指标
评价标准为类别f1_score的均值，选手提交结果与实际测试集的类别进行对比，结果越大越好。

数据读取
使用Pandas库完成数据读取操作，并对赛题数据进行分析。

解题思路
赛题思路分析：赛题本质是一个文本分类问题，需要根据每句的字符进行分类。但赛题给出的数据是匿名化的，不能直接使用中文分词等操作，这个是赛题的难点。

因此本次赛题的难点是需要对匿名字符进行建模，进而完成文本分类的过程。由于文本数据是一种典型的非结构化数据，因此可能涉及到特征提取和分类模型两个部分。

思路1：TF-IDF + 机器学习分类器

思路2：FastText

思路3：WordVec + 深度学习分类器

思路3：WordVec + 深度学习分类器

思路4：Bert词向量
