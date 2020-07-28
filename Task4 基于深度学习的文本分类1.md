




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
 
    
    
    
 
      
  <div id="readme" class="Box-body readme blob js-code-block-container p-5 p-xl-6">
    <article class="markdown-body entry-content container-lg" itemprop="text"><h1><a id="user-content-task4-基于深度学习的文本分类1" class="anchor" aria-hidden="true" href="#task4-基于深度学习的文本分类1"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Task4 基于深度学习的文本分类1</h1>
<p>在上一章节，我们使用传统机器学习算法来解决了文本分类问题，从本章开始我们将尝试使用深度学习方法。</p>
<h2><a id="user-content-基于深度学习的文本分类" class="anchor" aria-hidden="true" href="#基于深度学习的文本分类"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>基于深度学习的文本分类</h2>
<p>与传统机器学习不同，深度学习既提供特征提取功能，也可以完成分类的功能。从本章开始我们将学习如何使用深度学习来完成文本表示。</p>
<h3><a id="user-content-学习目标" class="anchor" aria-hidden="true" href="#学习目标"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>学习目标</h3>
<ul>
<li>学习FastText的使用和基础原理</li>
<li>学会使用验证集进行调参</li>
</ul>
<h3><a id="user-content-文本表示方法-part2" class="anchor" aria-hidden="true" href="#文本表示方法-part2"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>文本表示方法 Part2</h3>
<h4><a id="user-content-现有文本表示方法的缺陷" class="anchor" aria-hidden="true" href="#现有文本表示方法的缺陷"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>现有文本表示方法的缺陷</h4>
<p>在上一章节，我们介绍几种文本表示方法：</p>
<ul>
<li>One-hot</li>
<li>Bag of Words</li>
<li>N-gram</li>
<li>TF-IDF</li>
</ul>
<p>也通过sklean进行了相应的实践，相信你也有了初步的认知。但上述方法都或多或少存在一定的问题：转换得到的向量维度很高，需要较长的训练实践；没有考虑单词与单词之间的关系，只是进行了统计。</p>
<p>与这些表示方法不同，深度学习也可以用于文本表示，还可以将其映射到一个低纬空间。其中比较典型的例子有：FastText、Word2Vec和Bert。在本章我们将介绍FastText，将在后面的内容介绍Word2Vec和Bert。</p>
<h4><a id="user-content-fasttext" class="anchor" aria-hidden="true" href="#fasttext"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>FastText</h4>
<p>FastText是一种典型的深度学习词向量的表示方法，它非常简单通过Embedding层将单词映射到稠密空间，然后将句子中所有的单词在Embedding空间中进行平均，进而完成分类操作。</p>
<p>所以FastText是一个三层的神经网络，输入层、隐含层和输出层。</p>
<p><a target="_blank" rel="noopener noreferrer" href="https://camo.githubusercontent.com/4e01004146c81db5ee15df1b373374b3ff145bfa/68747470733a2f2f696d672d626c6f672e6373646e696d672e636e2f32303230303731343230343835363538392e706e67"><img src="https://camo.githubusercontent.com/4e01004146c81db5ee15df1b373374b3ff145bfa/68747470733a2f2f696d672d626c6f672e6373646e696d672e636e2f32303230303731343230343835363538392e706e67" alt="fast_text" data-canonical-src="https://img-blog.csdnimg.cn/20200714204856589.png" style="max-width:100%;"></a></p>
<p>下图是使用keras实现的FastText网络结构：</p>
<p><a target="_blank" rel="noopener noreferrer" href="https://camo.githubusercontent.com/d4f33365b75bdddd0c80a857dc1a9e99789f1600/68747470733a2f2f696d672d626c6f672e6373646e696d672e636e2f32303230303731343230343234393436332e6a7067"><img src="https://camo.githubusercontent.com/d4f33365b75bdddd0c80a857dc1a9e99789f1600/68747470733a2f2f696d672d626c6f672e6373646e696d672e636e2f32303230303731343230343234393436332e6a7067" alt="keras_fasttext" data-canonical-src="https://img-blog.csdnimg.cn/20200714204249463.jpg" style="max-width:100%;"></a></p>
<p>FastText在文本分类任务上，是优于TF-IDF的：</p>
<ul>
<li>FastText用单词的Embedding叠加获得的文档向量，将相似的句子分为一类</li>
<li>FastText学习到的Embedding空间维度比较低，可以快速进行训练</li>
</ul>
<p>如果想深度学习，可以参考论文：</p>
<p>Bag of Tricks for Efficient Text Classification, <a href="https://arxiv.org/abs/1607.01759" rel="nofollow">https://arxiv.org/abs/1607.01759</a></p>
<h3><a id="user-content-基于fasttext的文本分类" class="anchor" aria-hidden="true" href="#基于fasttext的文本分类"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>基于FastText的文本分类</h3>
<p>FastText可以快速的在CPU上进行训练，最好的实践方法就是官方开源的版本：
<a href="https://github.com/facebookresearch/fastText/tree/master/python">https://github.com/facebookresearch/fastText/tree/master/python</a></p>
<ul>
<li>pip安装</li>
</ul>
<pre><code>pip install fasttext
</code></pre>
<ul>
<li>源码安装</li>
</ul>
<pre><code>git clone https://github.com/facebookresearch/fastText.git
cd fastText
sudo pip install .
</code></pre>
<p>两种安装方法都可以安装，如果你是初学者可以优先考虑使用pip安装。</p>
<ul>
<li>分类模型</li>
</ul>
<div class="highlight highlight-source-python"><pre><span class="pl-k">import</span> <span class="pl-s1">pandas</span> <span class="pl-k">as</span> <span class="pl-s1">pd</span>
<span class="pl-k">from</span> <span class="pl-s1">sklearn</span>.<span class="pl-s1">metrics</span> <span class="pl-k">import</span> <span class="pl-s1">f1_score</span>

<span class="pl-c"># 转换为FastText需要的格式</span>
<span class="pl-s1">train_df</span> <span class="pl-c1">=</span> <span class="pl-s1">pd</span>.<span class="pl-en">read_csv</span>(<span class="pl-s">'../input/train_set.csv'</span>, <span class="pl-s1">sep</span><span class="pl-c1">=</span><span class="pl-s">'<span class="pl-cce">\t</span>'</span>, <span class="pl-s1">nrows</span><span class="pl-c1">=</span><span class="pl-c1">15000</span>)
<span class="pl-s1">train_df</span>[<span class="pl-s">'label_ft'</span>] <span class="pl-c1">=</span> <span class="pl-s">'__label__'</span> <span class="pl-c1">+</span> <span class="pl-s1">train_df</span>[<span class="pl-s">'label'</span>].<span class="pl-en">astype</span>(<span class="pl-s1">str</span>)
<span class="pl-s1">train_df</span>[[<span class="pl-s">'text'</span>,<span class="pl-s">'label_ft'</span>]].<span class="pl-s1">iloc</span>[:<span class="pl-c1">-</span><span class="pl-c1">5000</span>].<span class="pl-en">to_csv</span>(<span class="pl-s">'train.csv'</span>, <span class="pl-s1">index</span><span class="pl-c1">=</span><span class="pl-c1">None</span>, <span class="pl-s1">header</span><span class="pl-c1">=</span><span class="pl-c1">None</span>, <span class="pl-s1">sep</span><span class="pl-c1">=</span><span class="pl-s">'<span class="pl-cce">\t</span>'</span>)

<span class="pl-k">import</span> <span class="pl-s1">fasttext</span>
<span class="pl-s1">model</span> <span class="pl-c1">=</span> <span class="pl-s1">fasttext</span>.<span class="pl-en">train_supervised</span>(<span class="pl-s">'train.csv'</span>, <span class="pl-s1">lr</span><span class="pl-c1">=</span><span class="pl-c1">1.0</span>, <span class="pl-s1">wordNgrams</span><span class="pl-c1">=</span><span class="pl-c1">2</span>, 
                                  <span class="pl-s1">verbose</span><span class="pl-c1">=</span><span class="pl-c1">2</span>, <span class="pl-s1">minCount</span><span class="pl-c1">=</span><span class="pl-c1">1</span>, <span class="pl-s1">epoch</span><span class="pl-c1">=</span><span class="pl-c1">25</span>, <span class="pl-s1">loss</span><span class="pl-c1">=</span><span class="pl-s">"hs"</span>)

<span class="pl-s1">val_pred</span> <span class="pl-c1">=</span> [<span class="pl-s1">model</span>.<span class="pl-en">predict</span>(<span class="pl-s1">x</span>)[<span class="pl-c1">0</span>][<span class="pl-c1">0</span>].<span class="pl-en">split</span>(<span class="pl-s">'__'</span>)[<span class="pl-c1">-</span><span class="pl-c1">1</span>] <span class="pl-k">for</span> <span class="pl-s1">x</span> <span class="pl-c1">in</span> <span class="pl-s1">train_df</span>.<span class="pl-s1">iloc</span>[<span class="pl-c1">-</span><span class="pl-c1">5000</span>:][<span class="pl-s">'text'</span>]]
<span class="pl-en">print</span>(<span class="pl-en">f1_score</span>(<span class="pl-s1">train_df</span>[<span class="pl-s">'label'</span>].<span class="pl-s1">values</span>[<span class="pl-c1">-</span><span class="pl-c1">5000</span>:].<span class="pl-en">astype</span>(<span class="pl-s1">str</span>), <span class="pl-s1">val_pred</span>, <span class="pl-s1">average</span><span class="pl-c1">=</span><span class="pl-s">'macro'</span>))
<span class="pl-c"># 0.82</span></pre></div>
<p>此时数据量比较小得分为0.82，当不断增加训练集数量时，FastText的精度也会不断增加5w条训练样本时，验证集得分可以到0.89-0.90左右。</p>
<h3><a id="user-content-如何使用验证集调参" class="anchor" aria-hidden="true" href="#如何使用验证集调参"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>如何使用验证集调参</h3>
<p>在使用TF-IDF和FastText中，有一些模型的参数需要选择，这些参数会在一定程度上影响模型的精度，那么如何选择这些参数呢？</p>
<ul>
<li>通过阅读文档，要弄清楚这些参数的大致含义，那些参数会增加模型的复杂度</li>
<li>通过在验证集上进行验证模型精度，找到模型在是否过拟合还是欠拟合</li>
</ul>
<p><a target="_blank" rel="noopener noreferrer" href="https://camo.githubusercontent.com/3c19cda9d91954875be0b59abe99fad024552d29/68747470733a2f2f696d672d626c6f672e6373646e696d672e636e2f32303230303731343230343430333834342e706e67"><img src="https://camo.githubusercontent.com/3c19cda9d91954875be0b59abe99fad024552d29/68747470733a2f2f696d672d626c6f672e6373646e696d672e636e2f32303230303731343230343430333834342e706e67" alt="train_val" data-canonical-src="https://img-blog.csdnimg.cn/20200714204403844.png" style="max-width:100%;"></a></p>
<p>这里我们使用10折交叉验证，每折使用9/10的数据进行训练，剩余1/10作为验证集检验模型的效果。这里需要注意每折的划分必须保证标签的分布与整个数据集的分布一致。</p>
<pre><code>label2id = {}
for i in range(total):
    label = str(all_labels[i])
    if label not in label2id:
        label2id[label] = [i]
    else:
        label2id[label].append(i)
</code></pre>
<p>通过10折划分，我们一共得到了10份分布一致的数据，索引分别为0到9，每次通过将一份数据作为验证集，剩余数据作为训练集，获得了所有数据的10种分割。不失一般性，我们选择最后一份完成剩余的实验，即索引为9的一份做为验证集，索引为1-8的作为训练集，然后基于验证集的结果调整超参数，使得模型性能更优。</p>
<h3><a id="user-content-本章小结" class="anchor" aria-hidden="true" href="#本章小结"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>本章小结</h3>
<p>本章介绍了FastText的原理和基础使用，并进行相应的实践。然后介绍了通过10折交叉验证划分数据集。</p>
<h3><a id="user-content-本章作业" class="anchor" aria-hidden="true" href="#本章作业"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>本章作业</h3>
<ul>
<li>阅读FastText的文档，尝试修改参数，得到更好的分数</li>
<li>基于验证集的结果调整超参数，使得模型性能更优</li>
</ul>
</article>
  </div>


</html>

