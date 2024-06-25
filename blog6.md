<style>
.bjimg{
  position: fixed;
  top: 0;
  left: 0;
  width:100%;
height:100%;
min-width: 1000px;
z-index:-10;
zoom: 1;
  background-image: url();
  background-repeat: no-repeat;
  background-size: contain;
  background-position: center 0;
  opacity: 0.3;
  }
</style>
<head>
<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
    <script type="text/x-mathjax-config">
        MathJax.Hub.Config({
            tex2jax: {
            skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
            inlineMath: [['$','$']]
            }
        });
    </script>
</head>
<div class="bjimg"></div>

# Bourgain的数学：一个Szemerédi型定理的Fourier证明

<font size="2" color="grey">2024.6.xx</font><br/>
*按：Jean Bourgain绝对属于当代最富创造力的一批数学家，在一众领域留下了不胜数的成果和洞见. 也许每个分析学工作者都会在生命的某个阶段遇见Bourgain的工作和思想. 笔者第一次知道他是在T. Tao的纪念文章 "Exploring the toolkit of Jean Bourgain"，后来又接触到他在色散PDE的部分工作，惊叹不已. 于是博客开启一个(不定期)连载系列，记录Bourgain的分析魔法.*<br/>

今天介绍Bourgain在1986基于Fourier分析对Furstenberg等人关于正密度集的Szemerédi型定理的证明. 主要参考了一下文献：<br>
&emsp;[1] J.  Bourgain, *A Szemerédi type theorem for sets of positive density in R^k* <br>
&emap;[2] T. Tao, *Exploring the toolkit of Jean Bourgain*<br/>

我们先介绍主要结果. 

>**定理1.**(Furstenberg, Katznelson, Weiss) 设可测集 $A\subset R^2$ 有上界密度 $\delta=\delta(A)\>0$ , 则存在 $l_0$ s.t. 对*任意* $l\geq l_0$ , 存在 $x,y\in A$ , $\vert x-y\vert =l$ . 这里上界密度
>
>$$
\delta(A)=\limsup_{R\to +\infty} \frac{\vert A\cap B_R \vert}{\vert B_R\vert}, 
$$
>
>$\vert \cdot\vert$ 是Lebesgue测度，$B_R$ 是原点为中心，$R$ 为半径的圆盘.

粗略地说，只要集合在平面上足够"稠密"，那么集合中所有点对的距离取遍充分大的正实数. Bourgain证明的第一步是将结论定量化( quantitative formulation )，以便硬分析工具的介入. 

<hr style="height:1px">

&copy; Senyu Yang&emsp;<a href="." target="_self" >Next Dream...</a>
