




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



  <link crossorigin="anonymous" media="all" integrity="sha512-obSK9hAsy5L1SQtxCWtASzvugjRXE7LQzcyJ9PP+WjdBrG7CiqhWRw2+0+TgYueDN7o/2jkLjiSFBYoHB0XKQw==" rel="stylesheet" href="https://github.githubassets.com/assets/frameworks-a1b48af6102ccb92f5490b71096b404b.css" />
  

      
<div id="readme" class="Box-body readme blob js-code-block-container p-5 p-xl-6">
<article class="markdown-body entry-content container-lg" itemprop="text"><h1><a id="user-content-task2-数据读取与数据分析" class="anchor" aria-hidden="true" href="#task2-数据读取与数据分析"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Task2 数据读取与数据分析</h1>
<p>在上一章节，我们给大家简单介绍了赛题的内容和几种解决方案。从本章开始我们将会逐渐带着大家使用思路1到思路4来完成本次赛题。在讲解工具使用的同时，我们还会讲解一些算法的原理和相关知识点，并会给出一定的参考文献供大家深入学习。</p>
<h2><a id="user-content-数据读取与数据分析" class="anchor" aria-hidden="true" href="#数据读取与数据分析"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>数据读取与数据分析</h2>
<p>本章主要内容为数据读取和数据分析，具体使用<code>Pandas</code>库完成数据读取操作，并对赛题数据进行分析构成。</p>
<h3><a id="user-content-学习目标" class="anchor" aria-hidden="true" href="#学习目标"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>学习目标</h3>
<ul>
<li>学习使用<code>Pandas</code>读取赛题数据</li>
<li>分析赛题数据的分布规律</li>
</ul>
<h3><a id="user-content-数据读取" class="anchor" aria-hidden="true" href="#数据读取"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>数据读取</h3>
<p>赛题数据虽然是文本数据，每个新闻是不定长的，但任然使用csv格式进行存储。因此可以直接用<code>Pandas</code>完成数据读取的操作。</p>
<div class="highlight highlight-source-python"><pre><span class="pl-k">import</span> <span class="pl-s1">pandas</span> <span class="pl-k">as</span> <span class="pl-s1">pd</span>
<span class="pl-s1">train_df</span> <span class="pl-c1">=</span> <span class="pl-s1">pd</span>.<span class="pl-en">read_csv</span>(<span class="pl-s">'../input/train_set.csv'</span>, <span class="pl-s1">sep</span><span class="pl-c1">=</span><span class="pl-s">'<span class="pl-cce">\t</span>'</span>, <span class="pl-s1">nrows</span><span class="pl-c1">=</span><span class="pl-c1">100</span>)</pre></div>
<p>这里的<code>read_csv</code>由三部分构成：</p>
<ul>
<li>
<p>读取的文件路径，这里需要根据改成你本地的路径，可以使用相对路径或绝对路径；</p>
</li>
<li>
<p>分隔符<code>sep</code>，为每列分割的字符，设置为<code>\t</code>即可；</p>
</li>
<li>
<p>读取行数<code>nrows</code>，为此次读取文件的函数，是数值类型（由于数据集比较大，建议先设置为100）；</p>
</li>
</ul>
<p><a target="_blank" rel="noopener noreferrer" href="https://camo.githubusercontent.com/3cfb75e212d4e8259de4c4151e52b405dbe256de/68747470733a2f2f696d672d626c6f672e6373646e696d672e636e2f32303230303731343230333733303733392e706e67"><img src="https://camo.githubusercontent.com/3cfb75e212d4e8259de4c4151e52b405dbe256de/68747470733a2f2f696d672d626c6f672e6373646e696d672e636e2f32303230303731343230333733303733392e706e67" alt="task2_train_head" data-canonical-src="https://img-blog.csdnimg.cn/20200714203730739.png" style="max-width:100%;"></a></p>
<p>上图是读取好的数据，是表格的形式。第一列为新闻的类别，第二列为新闻的字符。</p>
<h3><a id="user-content-数据分析" class="anchor" aria-hidden="true" href="#数据分析"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>数据分析</h3>
<p>在读取完成数据集后，我们还可以对数据集进行数据分析的操作。虽然对于非结构数据并不需要做很多的数据分析，但通过数据分析还是可以找出一些规律的。</p>
<p>此步骤我们读取了所有的训练集数据，在此我们通过数据分析希望得出以下结论：</p>
<ul>
<li>赛题数据中，新闻文本的长度是多少？</li>
<li>赛题数据的类别分布是怎么样的，哪些类别比较多？</li>
<li>赛题数据中，字符分布是怎么样的？</li>
</ul>
<h4><a id="user-content-句子长度分析" class="anchor" aria-hidden="true" href="#句子长度分析"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>句子长度分析</h4>
<p>在赛题数据中每行句子的字符使用空格进行隔开，所以可以直接统计单词的个数来得到每个句子的长度。统计并如下：</p>
<div class="highlight highlight-source-python"><pre><span class="pl-c1">%</span><span class="pl-s1">pylab</span> <span class="pl-s1">inline</span>
<span class="pl-s1">train_df</span>[<span class="pl-s">'text_len'</span>] <span class="pl-c1">=</span> <span class="pl-s1">train_df</span>[<span class="pl-s">'text'</span>].<span class="pl-en">apply</span>(<span class="pl-k">lambda</span> <span class="pl-s1">x</span>: <span class="pl-en">len</span>(<span class="pl-s1">x</span>.<span class="pl-en">split</span>(<span class="pl-s">' '</span>)))
<span class="pl-en">print</span>(<span class="pl-s1">train_df</span>[<span class="pl-s">'text_len'</span>].<span class="pl-en">describe</span>())</pre></div>
<p>输出结果为：</p>
<pre><code>Populating the interactive namespace from numpy and matplotlib
count    200000.000000
mean        907.207110
std         996.029036
min           2.000000
25%         374.000000
50%         676.000000
75%        1131.000000
max       57921.000000
Name: text_len, dtype: float64
</code></pre>
<p>对新闻句子的统计可以得出，本次赛题给定的文本比较长，每个句子平均由907个字符构成，最短的句子长度为2，最长的句子长度为57921。</p>
<p>下图将句子长度绘制了直方图，可见大部分句子的长度都几种在2000以内。</p>
<div class="highlight highlight-source-python"><pre><span class="pl-s1">_</span> <span class="pl-c1">=</span> <span class="pl-s1">plt</span>.<span class="pl-en">hist</span>(<span class="pl-s1">train_df</span>[<span class="pl-s">'text_len'</span>], <span class="pl-s1">bins</span><span class="pl-c1">=</span><span class="pl-c1">200</span>)
<span class="pl-s1">plt</span>.<span class="pl-en">xlabel</span>(<span class="pl-s">'Text char count'</span>)
<span class="pl-s1">plt</span>.<span class="pl-en">title</span>(<span class="pl-s">"Histogram of char count"</span>)</pre></div>
<p><a target="_blank" rel="noopener noreferrer" href="https://camo.githubusercontent.com/656471f35c5df332c6ca027756cfd048324e5727/68747470733a2f2f696d672d626c6f672e6373646e696d672e636e2f32303230303731343230333833363930352e706e67"><img src="https://camo.githubusercontent.com/656471f35c5df332c6ca027756cfd048324e5727/68747470733a2f2f696d672d626c6f672e6373646e696d672e636e2f32303230303731343230333833363930352e706e67" alt="task2_char_hist" data-canonical-src="https://img-blog.csdnimg.cn/20200714203836905.png" style="max-width:100%;"></a></p>
<h4><a id="user-content-新闻类别分布" class="anchor" aria-hidden="true" href="#新闻类别分布"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>新闻类别分布</h4>
<p>接下来可以对数据集的类别进行分布统计，具体统计每类新闻的样本个数。</p>
<div class="highlight highlight-source-python"><pre><span class="pl-s1">train_df</span>[<span class="pl-s">'label'</span>].<span class="pl-en">value_counts</span>().<span class="pl-en">plot</span>(<span class="pl-s1">kind</span><span class="pl-c1">=</span><span class="pl-s">'bar'</span>)
<span class="pl-s1">plt</span>.<span class="pl-en">title</span>(<span class="pl-s">'News class count'</span>)
<span class="pl-s1">plt</span>.<span class="pl-en">xlabel</span>(<span class="pl-s">"category"</span>)</pre></div>
<p><a target="_blank" rel="noopener noreferrer" href="https://camo.githubusercontent.com/ea8ab6a105f74fa197f29cb09e5dfd97ae6a573e/68747470733a2f2f696d672d626c6f672e6373646e696d672e636e2f32303230303731343230333932393239362e706e67"><img src="https://camo.githubusercontent.com/ea8ab6a105f74fa197f29cb09e5dfd97ae6a573e/68747470733a2f2f696d672d626c6f672e6373646e696d672e636e2f32303230303731343230333932393239362e706e67" alt="task2_class_hist" data-canonical-src="https://img-blog.csdnimg.cn/20200714203929296.png" style="max-width:100%;"></a></p>
<p>在数据集中标签的对应的关系如下：{'科技': 0, '股票': 1, '体育': 2, '娱乐': 3, '时政': 4, '社会': 5, '教育': 6, '财经': 7, '家居': 8, '游戏': 9, '房产': 10, '时尚': 11, '彩票': 12, '星座': 13}</p>
<p>从统计结果可以看出，赛题的数据集类别分布存在较为不均匀的情况。在训练集中科技类新闻最多，其次是股票类新闻，最少的新闻是星座新闻。</p>
<h4><a id="user-content-字符分布统计" class="anchor" aria-hidden="true" href="#字符分布统计"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>字符分布统计</h4>
<p>接下来可以统计每个字符出现的次数，首先可以将训练集中所有的句子进行拼接进而划分为字符，并统计每个字符的个数。</p>
<div class="highlight highlight-source-python"><pre><span class="pl-k">from</span> <span class="pl-s1">collections</span> <span class="pl-k">import</span> <span class="pl-v">Counter</span>
<span class="pl-s1">all_lines</span> <span class="pl-c1">=</span> <span class="pl-s">' '</span>.<span class="pl-en">join</span>(<span class="pl-en">list</span>(<span class="pl-s1">train_df</span>[<span class="pl-s">'text'</span>]))
<span class="pl-s1">word_count</span> <span class="pl-c1">=</span> <span class="pl-v">Counter</span>(<span class="pl-s1">all_lines</span>.<span class="pl-en">split</span>(<span class="pl-s">" "</span>))
<span class="pl-s1">word_count</span> <span class="pl-c1">=</span> <span class="pl-en">sorted</span>(<span class="pl-s1">word_count</span>.<span class="pl-en">items</span>(), <span class="pl-s1">key</span><span class="pl-c1">=</span><span class="pl-k">lambda</span> <span class="pl-s1">d</span>:<span class="pl-s1">d</span>[<span class="pl-c1">1</span>], <span class="pl-s1">reverse</span> <span class="pl-c1">=</span> <span class="pl-c1">True</span>)

<span class="pl-en">print</span>(<span class="pl-en">len</span>(<span class="pl-s1">word_count</span>))
<span class="pl-c"># 6869</span>

<span class="pl-en">print</span>(<span class="pl-s1">word_count</span>[<span class="pl-c1">0</span>])
<span class="pl-c"># ('3750', 7482224)</span>

<span class="pl-en">print</span>(<span class="pl-s1">word_count</span>[<span class="pl-c1">-</span><span class="pl-c1">1</span>])
<span class="pl-c"># ('3133', 1)</span></pre></div>
<p>从统计结果中可以看出，在训练集中总共包括6869个字，其中编号3750的字出现的次数最多，编号3133的字出现的次数最少。</p>
<p>这里还可以根据字在每个句子的出现情况，反推出标点符号。下面代码统计了不同字符在句子中出现的次数，其中字符3750，字符900和字符648在20w新闻的覆盖率接近99%，很有可能是标点符号。</p>
<div class="highlight highlight-source-python"><pre><span class="pl-s1">train_df</span>[<span class="pl-s">'text_unique'</span>] <span class="pl-c1">=</span> <span class="pl-s1">train_df</span>[<span class="pl-s">'text'</span>].<span class="pl-en">apply</span>(<span class="pl-k">lambda</span> <span class="pl-s1">x</span>: <span class="pl-s">' '</span>.<span class="pl-en">join</span>(<span class="pl-en">list</span>(<span class="pl-en">set</span>(<span class="pl-s1">x</span>.<span class="pl-en">split</span>(<span class="pl-s">' '</span>)))))
<span class="pl-s1">all_lines</span> <span class="pl-c1">=</span> <span class="pl-s">' '</span>.<span class="pl-en">join</span>(<span class="pl-en">list</span>(<span class="pl-s1">train_df</span>[<span class="pl-s">'text_unique'</span>]))
<span class="pl-s1">word_count</span> <span class="pl-c1">=</span> <span class="pl-v">Counter</span>(<span class="pl-s1">all_lines</span>.<span class="pl-en">split</span>(<span class="pl-s">" "</span>))
<span class="pl-s1">word_count</span> <span class="pl-c1">=</span> <span class="pl-en">sorted</span>(<span class="pl-s1">word_count</span>.<span class="pl-en">items</span>(), <span class="pl-s1">key</span><span class="pl-c1">=</span><span class="pl-k">lambda</span> <span class="pl-s1">d</span>:<span class="pl-en">int</span>(<span class="pl-s1">d</span>[<span class="pl-c1">1</span>]), <span class="pl-s1">reverse</span> <span class="pl-c1">=</span> <span class="pl-c1">True</span>)

<span class="pl-en">print</span>(<span class="pl-s1">word_count</span>[<span class="pl-c1">0</span>])
<span class="pl-c"># ('3750', 197997)</span>

<span class="pl-en">print</span>(<span class="pl-s1">word_count</span>[<span class="pl-c1">1</span>])
<span class="pl-c"># ('900', 197653)</span>

<span class="pl-en">print</span>(<span class="pl-s1">word_count</span>[<span class="pl-c1">2</span>])
<span class="pl-c"># ('648', 191975)</span></pre></div>
<h3><a id="user-content-数据分析的结论" class="anchor" aria-hidden="true" href="#数据分析的结论"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>数据分析的结论</h3>
<p>通过上述分析我们可以得出以下结论：</p>
<ol>
<li>赛题中每个新闻包含的字符个数平均为1000个，还有一些新闻字符较长；</li>
<li>赛题中新闻类别分布不均匀，科技类新闻样本量接近4w，星座类新闻样本量不到1k；</li>
<li>赛题总共包括7000-8000个字符；</li>
</ol>
<p>通过数据分析，我们还可以得出以下结论：</p>
<ol>
<li>
<p>每个新闻平均字符个数较多，可能需要截断；</p>
</li>
<li>
<p>由于类别不均衡，会严重影响模型的精度；</p>
</li>
</ol>
<h3><a id="user-content-本章小结" class="anchor" aria-hidden="true" href="#本章小结"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>本章小结</h3>
<p>本章对赛题数据进行读取，并新闻句子长度、类别和字符进行了可视化分析。</p>
<h3><a id="user-content-本章作业" class="anchor" aria-hidden="true" href="#本章作业"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>本章作业</h3>
<ol>
<li>假设字符3750，字符900和字符648是句子的标点符号，请分析赛题每篇新闻平均由多少个句子构成？</li>
<li>统计每类新闻中出现次数对多的字符</li>
</ol>
</article>
</div>

</body>
</html>

