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
*连一刻都没有为GPA时代的结束哀悼，立刻赶到战场的是科研课题.*<br/>

**按：** Jean Bourgain爵士绝对属于当代最富创造力的一批数学家，在调和分析、偏微分方程、组合学、动力系统、数论等一众领域留下了不胜数的成果和洞见. 也许每个分析学工作者/爱好者都会在生命的某个阶段遇见Bourgain的工作和思想. 笔者第一次了解他的工作来源于Tao纪念Bourgain的文章"Exploring the toolkit of Jean Bourgain"，后来又接触了他在色散PDE上的部分工作，惊叹不已. 于是博客开启一个(不定期)连载系列，记录Bourgain笔下的瑰宝. <br/>

今天介绍Bourgain在1986如何用Fourier分析证明Frustenberg等人关于正密度集的Szemerédi型定理. 笔者主要参考了一下文献：<br>
&emsp;[1] J.  Bourgain, *A Szemerédi type theorem for sets of positive density in R^k* <br>
&emap;[2] T. Tao, *Exploring the toolkit of Jean Bourgain*<br/>

我们先介绍主要结果. 

>**定理1.** 

<hr style="height:1px">

&copy; Senyu Yang&emsp;<a href="." target="_self" >Next Dream...</a>
