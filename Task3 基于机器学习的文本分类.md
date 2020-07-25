




<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
  <link rel="dns-prefetch" href="https://github.githubassets.com">
  <link rel="dns-prefetch" href="https://avatars0.githubusercontent.com">
  <link rel="dns-prefetch" href="https://avatars1.githubusercontent.com">
  <link rel="dns-prefetch" href="https://avatars2.githubusercontent.com">
  <link rel="dns-prefetch" href="https://avatars3.githubusercontent.com">
  <link rel="dns-prefetch" href="https://github-cloud.s3.amazonaws.com">
  <link rel="dns-prefetch" href="https://user-images.githubusercontent.com/">



  <link crossorigin="anonymous" media="all" integrity="sha512-YR0i2ZAJ3fFf7L2CvMny+FWH76iHZNNIcD1YX57o4cdBHev8ffMXOfzy5F/lpBJpLttwPahk3zY/8XXaRH12ew==" rel="stylesheet" href="https://github.githubassets.com/assets/frameworks-611d22d99009ddf15fecbd82bcc9f2f8.css" />
  
    <link crossorigin="anonymous" media="all" integrity="sha512-rRjA9My/PBBcaPVlqM+Itl3dsS0snuqXO9XFrSmJNNQz6okQW4a4+jBjpKxZQ4sTiaFtDS1hthUIhMDQSbbTpw==" rel="stylesheet" href="https://github.githubassets.com/assets/github-ad18c0f4ccbf3c105c68f565a8cf88b6.css" />
    
  

  <div id="readme" class="Box-body readme blob js-code-block-container p-5 p-xl-6">
    <article class="markdown-body entry-content container-lg" itemprop="text"><h1><a id="user-content-task3-基于机器学习的文本分类" class="anchor" aria-hidden="true" href="#task3-基于机器学习的文本分类"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Task3 基于机器学习的文本分类</h1>
<p>在上一章节，我们对赛题的数据进行了读取，并在末尾给出了两个小作业。如果你顺利完成了作业，那么你基本上对<code>Python</code>也比较熟悉了。在本章我们将使用传统机器学习算法来完成新闻分类的过程，将会结束到赛题的核心知识点。</p>
<h2><a id="user-content-基于机器学习的文本分类" class="anchor" aria-hidden="true" href="#基于机器学习的文本分类"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>基于机器学习的文本分类</h2>
<p>在本章我们将开始使用机器学习模型来解决文本分类。机器学习发展比较广，且包括多个分支，本章侧重使用传统机器学习，从下一章开始是基于深度学习的文本分类。</p>
<h3><a id="user-content-学习目标" class="anchor" aria-hidden="true" href="#学习目标"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>学习目标</h3>
<ul>
<li>学会TF-IDF的原理和使用</li>
<li>使用sklearn的机器学习模型完成文本分类</li>
</ul>
<h3><a id="user-content-机器学习模型" class="anchor" aria-hidden="true" href="#机器学习模型"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>机器学习模型</h3>
<p>机器学习是对能通过经验自动改进的计算机算法的研究。机器学习通过历史数据<strong>训练</strong>出<strong>模型</strong>对应于人类对经验进行<strong>归纳</strong>的过程，机器学习利用<strong>模型</strong>对新数据进行<strong>预测</strong>对应于人类利用总结的<strong>规律</strong>对新问题进行<strong>预测</strong>的过程。</p>
<p>机器学习有很多种分支，对于学习者来说应该优先掌握机器学习算法的分类，然后再其中一种机器学习算法进行学习。由于机器学习算法的分支和细节实在是太多，所以如果你一开始就被细节迷住了眼，你就很难知道全局是什么情况的。</p>
<p>如果你是机器学习初学者，你应该知道如下的事情：</p>
<ol>
<li>机器学习能解决一定的问题，但不能奢求机器学习是万能的；</li>
<li>机器学习算法有很多种，看具体问题需要什么，再来进行选择；</li>
<li>每种机器学习算法有一定的偏好，需要具体问题具体分析；</li>
</ol>
<p><a target="_blank" rel="noopener noreferrer" href="https://camo.githubusercontent.com/d8e9a12417a2a2a754a874af0ae163bb1bddbb0b/68747470733a2f2f696d672d626c6f672e6373646e696d672e636e2f32303230303731343230333232333235332e6a7067"><img src="https://camo.githubusercontent.com/d8e9a12417a2a2a754a874af0ae163bb1bddbb0b/68747470733a2f2f696d672d626c6f672e6373646e696d672e636e2f32303230303731343230333232333235332e6a7067" alt="machine_learning_overview" data-canonical-src="https://img-blog.csdnimg.cn/20200714203223253.jpg" style="max-width:100%;"></a></p>
<h3><a id="user-content-文本表示方法-part1" class="anchor" aria-hidden="true" href="#文本表示方法-part1"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>文本表示方法 Part1</h3>
<p>在机器学习算法的训练过程中，假设给定$N$个样本，每个样本有$M$个特征，这样组成了$N×M$的样本矩阵，然后完成算法的训练和预测。同样的在计算机视觉中可以将图片的像素看作特征，每张图片看作hight×width×3的特征图，一个三维的矩阵来进入计算机进行计算。</p>
<p>但是在自然语言领域，上述方法却不可行：文本是不定长度的。文本表示成计算机能够运算的数字或向量的方法一般称为词嵌入（Word Embedding）方法。词嵌入将不定长的文本转换到定长的空间内，是文本分类的第一步。</p>
<h4><a id="user-content-one-hot" class="anchor" aria-hidden="true" href="#one-hot"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>One-hot</h4>
<p>这里的One-hot与数据挖掘任务中的操作是一致的，即将每一个单词使用一个离散的向量表示。具体将每个字/词编码一个索引，然后根据索引进行赋值。</p>
<p>One-hot表示方法的例子如下：</p>
<div class="highlight highlight-source-python"><pre>句子<span class="pl-c1">1</span>：我 爱 北 京 天 安 门
句子<span class="pl-c1">2</span>：我 喜 欢 上 海</pre></div>
<p>首先对所有句子的字进行索引，即将每个字确定一个编号：</p>
<div class="highlight highlight-source-python"><pre>{
	<span class="pl-s">'我'</span>: <span class="pl-c1">1</span>, <span class="pl-s">'爱'</span>: <span class="pl-c1">2</span>, <span class="pl-s">'北'</span>: <span class="pl-c1">3</span>, <span class="pl-s">'京'</span>: <span class="pl-c1">4</span>, <span class="pl-s">'天'</span>: <span class="pl-c1">5</span>,
  <span class="pl-s">'安'</span>: <span class="pl-c1">6</span>, <span class="pl-s">'门'</span>: <span class="pl-c1">7</span>, <span class="pl-s">'喜'</span>: <span class="pl-c1">8</span>, <span class="pl-s">'欢'</span>: <span class="pl-c1">9</span>, <span class="pl-s">'上'</span>: <span class="pl-c1">10</span>, <span class="pl-s">'海'</span>: <span class="pl-c1">11</span>
}</pre></div>
<p>在这里共包括11个字，因此每个字可以转换为一个11维度稀疏向量：</p>
<pre><code>我：[1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
爱：[0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0]
...
海：[0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1]
</code></pre>
<h4><a id="user-content-bag-of-words" class="anchor" aria-hidden="true" href="#bag-of-words"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Bag of Words</h4>
<p>Bag of Words（词袋表示），也称为Count Vectors，每个文档的字/词可以使用其出现次数来进行表示。</p>
<div class="highlight highlight-source-python"><pre>句子<span class="pl-c1">1</span>：我 爱 北 京 天 安 门
句子<span class="pl-c1">2</span>：我 喜 欢 上 海</pre></div>
<p>直接统计每个字出现的次数，并进行赋值：</p>
<div class="highlight highlight-source-python"><pre>句子<span class="pl-c1">1</span>：我 爱 北 京 天 安 门
转换为 [<span class="pl-c1">1</span>, <span class="pl-c1">1</span>, <span class="pl-c1">1</span>, <span class="pl-c1">1</span>, <span class="pl-c1">1</span>, <span class="pl-c1">1</span>, <span class="pl-c1">1</span>, <span class="pl-c1">0</span>, <span class="pl-c1">0</span>, <span class="pl-c1">0</span>, <span class="pl-c1">0</span>]

句子<span class="pl-c1">2</span>：我 喜 欢 上 海
转换为 [<span class="pl-c1">1</span>, <span class="pl-c1">0</span>, <span class="pl-c1">0</span>, <span class="pl-c1">0</span>, <span class="pl-c1">0</span>, <span class="pl-c1">0</span>, <span class="pl-c1">0</span>, <span class="pl-c1">1</span>, <span class="pl-c1">1</span>, <span class="pl-c1">1</span>, <span class="pl-c1">1</span>]</pre></div>
<p>在sklearn中可以直接<code>CountVectorizer</code>来实现这一步骤：</p>
<pre><code>from sklearn.feature_extraction.text import CountVectorizer
corpus = [
    'This is the first document.',
    'This document is the second document.',
    'And this is the third one.',
    'Is this the first document?',
]
vectorizer = CountVectorizer()
vectorizer.fit_transform(corpus).toarray()
</code></pre>
<h4><a id="user-content-n-gram" class="anchor" aria-hidden="true" href="#n-gram"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>N-gram</h4>
<p>N-gram与Count Vectors类似，不过加入了相邻单词组合成为新的单词，并进行计数。</p>
<p>如果N取值为2，则句子1和句子2就变为：</p>
<pre><code>句子1：我爱 爱北 北京 京天 天安 安门
句子2：我喜 喜欢 欢上 上海
</code></pre>
<h4><a id="user-content-tf-idf" class="anchor" aria-hidden="true" href="#tf-idf"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>TF-IDF</h4>
<p>TF-IDF 分数由两部分组成：第一部分是<strong>词语频率</strong>（Term Frequency），第二部分是<strong>逆文档频率</strong>（Inverse Document Frequency）。其中计算语料库中文档总数除以含有该词语的文档数量，然后再取对数就是逆文档频率。</p>
<pre><code>TF(t)= 该词语在当前文档出现的次数 / 当前文档中词语的总数
IDF(t)= log_e（文档总数 / 出现该词语的文档总数）
</code></pre>
<h3><a id="user-content-基于机器学习的文本分类-1" class="anchor" aria-hidden="true" href="#基于机器学习的文本分类-1"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>基于机器学习的文本分类</h3>
<p>接下来我们将对比不同文本表示算法的精度，通过本地构建验证集计算F1得分。</p>
<h4><a id="user-content-count-vectors--ridgeclassifier" class="anchor" aria-hidden="true" href="#count-vectors--ridgeclassifier"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Count Vectors + RidgeClassifier</h4>
<div class="highlight highlight-source-python"><pre><span class="pl-k">import</span> <span class="pl-s1">pandas</span> <span class="pl-k">as</span> <span class="pl-s1">pd</span>

<span class="pl-k">from</span> <span class="pl-s1">sklearn</span>.<span class="pl-s1">feature_extraction</span>.<span class="pl-s1">text</span> <span class="pl-k">import</span> <span class="pl-v">CountVectorizer</span>
<span class="pl-k">from</span> <span class="pl-s1">sklearn</span>.<span class="pl-s1">linear_model</span> <span class="pl-k">import</span> <span class="pl-v">RidgeClassifier</span>
<span class="pl-k">from</span> <span class="pl-s1">sklearn</span>.<span class="pl-s1">metrics</span> <span class="pl-k">import</span> <span class="pl-s1">f1_score</span>

<span class="pl-s1">train_df</span> <span class="pl-c1">=</span> <span class="pl-s1">pd</span>.<span class="pl-en">read_csv</span>(<span class="pl-s">'../input/train_set.csv'</span>, <span class="pl-s1">sep</span><span class="pl-c1">=</span><span class="pl-s">'<span class="pl-cce">\t</span>'</span>, <span class="pl-s1">nrows</span><span class="pl-c1">=</span><span class="pl-c1">15000</span>)

<span class="pl-s1">vectorizer</span> <span class="pl-c1">=</span> <span class="pl-v">CountVectorizer</span>(<span class="pl-s1">max_features</span><span class="pl-c1">=</span><span class="pl-c1">3000</span>)
<span class="pl-s1">train_test</span> <span class="pl-c1">=</span> <span class="pl-s1">vectorizer</span>.<span class="pl-en">fit_transform</span>(<span class="pl-s1">train_df</span>[<span class="pl-s">'text'</span>])

<span class="pl-s1">clf</span> <span class="pl-c1">=</span> <span class="pl-v">RidgeClassifier</span>()
<span class="pl-s1">clf</span>.<span class="pl-en">fit</span>(<span class="pl-s1">train_test</span>[:<span class="pl-c1">10000</span>], <span class="pl-s1">train_df</span>[<span class="pl-s">'label'</span>].<span class="pl-s1">values</span>[:<span class="pl-c1">10000</span>])

<span class="pl-s1">val_pred</span> <span class="pl-c1">=</span> <span class="pl-s1">clf</span>.<span class="pl-en">predict</span>(<span class="pl-s1">train_test</span>[<span class="pl-c1">10000</span>:])
<span class="pl-en">print</span>(<span class="pl-en">f1_score</span>(<span class="pl-s1">train_df</span>[<span class="pl-s">'label'</span>].<span class="pl-s1">values</span>[<span class="pl-c1">10000</span>:], <span class="pl-s1">val_pred</span>, <span class="pl-s1">average</span><span class="pl-c1">=</span><span class="pl-s">'macro'</span>))
<span class="pl-c"># 0.74</span></pre></div>
<h4><a id="user-content-tf-idf---ridgeclassifier" class="anchor" aria-hidden="true" href="#tf-idf---ridgeclassifier"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>TF-IDF +  RidgeClassifier</h4>
<pre><code>import pandas as pd

from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.linear_model import RidgeClassifier
from sklearn.metrics import f1_score

train_df = pd.read_csv('../input/train_set.csv', sep='\t', nrows=15000)

tfidf = TfidfVectorizer(ngram_range=(1,3), max_features=3000)
train_test = tfidf.fit_transform(train_df['text'])

clf = RidgeClassifier()
clf.fit(train_test[:10000], train_df['label'].values[:10000])

val_pred = clf.predict(train_test[10000:])
print(f1_score(train_df['label'].values[10000:], val_pred, average='macro'))
# 0.87
</code></pre>
<h3><a id="user-content-本章小结" class="anchor" aria-hidden="true" href="#本章小结"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>本章小结</h3>
<p>本章我们介绍了基于机器学习的文本分类方法，并完成了两种方法的对比。</p>
<h3><a id="user-content-本章作业" class="anchor" aria-hidden="true" href="#本章作业"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>本章作业</h3>
<ol>
<li>尝试改变TF-IDF的参数，并验证精度</li>
<li>尝试使用其他机器学习模型，完成训练和验证</li>
</ol>
</article>
 
  </body>
</html>

