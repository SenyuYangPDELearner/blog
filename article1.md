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

# 张灯结彩：如何照亮球的外表面

<font size="2" color="grey">2024.2.12</font><br/>
首先祝你2024龙年万事顺遂，平安健康！这篇短文是博客的创刊号兼春节特辑，主题正如标题所示，下面用较严格的语言叙述它：

> 在$3$维欧氏空间$\mathbf{R}^3$中有一个单位球$B$(球心在原点，半径为$1$), 请问**在$B$外至少需要多少个点光源才能照亮它的整个外表面**(二维单位球面$S^2$)？

先做一些猜测. 直觉上，如果使用最少的光源，那么光源的位置应该分布得足够均匀来提高利用率. 一个点是$0$维的，两个点确定一条$1$维线段，三个点确定一个$2$维三角形，它们对于$\mathbf{R}^3$中的球面来说并不那么“均匀”. 四个点光源就相当自然了：正四面体及其内切球就是所求的模型. 

那么少于四盏灯到底可行么？我们对点光源个数$n$分类讨论. 很快就会发现，一个点光源能照亮的区域严格包含于一个半球面的内部，其面积严格小于$S^2$表面积的一半, 所以$n=1,2$肯定不行. <br/>

$n=3$时情况会更微妙些. 根据球的对称性，我们可以不失一般地先把两个点光源安排在赤道所在平面上，由前面的观察，它们照亮的区域就是两个球帽的并. 关键在于球的两个极点都没有被照亮，而一个被照亮的球帽至多覆盖其中一个极点(希望读者可以自己动手画图或者尽力想象哦)，所以三盏灯确实不够. 问题解决.<br/><br/>

解决了吗？确实，但这么一个初等的解法并不值得写一篇短文啦(笑) 我们看到初等证明是相当“几何”的：始终在围绕球帽的形状和大小进行讨论. 令人惊讶的是，一些“柔软”的**拓扑障碍**在我们的问题中发挥了作用. 先摆出一个科普程度很高的拓扑学定理：

> **定理.**(Borsuk-Ulam) 设连续映射$f: S^2\to \mathbf{R}^2$，则存在$S^2$上的一对对径点$x,-x$被映为同一个点.

倘若把地球看作$S^2$，$\mathbf{R}^2$的坐标是温度和气压$(T,p)$，就能得到许多科普文献吸引眼球的表述：地球上任何时刻都存在一对对径点，两点处的温度和气压都相等. 定理的严格证明依赖于同调群(homology group)和映射度(degree)的概念，可能需要一学期的本科拓扑学课程才能讲清楚，这里自然无法展开. 不过著名的数学科普up主[3Blue1Brown](https://space.bilibili.com/88461692?spm_id_from=333.337.0.0)在[这期视频](https://www.bilibili.com/video/BV1Jt411s7qs/?spm_id_from=333.999.0.0&vd_source=eb12aac9760d525558e62246371ef768)中给出了一个较形象的“证明”以及在组合学上的惊人应用，很有参考价值. 我们只需记住，尽管定理中包含了对径点等几何概念，但它的证明却是拓扑的. <br/>

下面关注一个有趣的推论：

> **定理.**(Lusternik-Schnirelmann) 若$S^2$被三个闭集所覆盖，则至少有一个闭集包含一对对径点.

*注.* 一个更令人惊讶的事实是，这个推论和B-U定理是[等价](https://math.uchicago.edu/~may/REU2017/REUPapers/Dougherty.pdf)的！<br/>

*证明.* 把上述闭集记为$F_i(i=1,2,3)$. 我们引入一个巧妙的构造，令映射$f:S^2\to \mathbf{R}^2$,

$$
f(x)=(\mathrm{dist}(x,F_1), \mathrm{dist}(x,F_2))
$$

其中$\mathrm{dist}(x,F)$表示点$x$与闭集$F$的距离：

$$
dist(x,F)=\min\{\left\lvert x-y\right\rvert\mid y\in F\}.
$$
 
所以$f$是连续映射(熟悉数学分析的读者应该能自己证明$\mathrm{dist}(x,F)$的存在性和$f$的连续性啦). 根据B-U定理，存在$x\in S^2$，$f(x)=f(-x)$.<br/>
    (i) 如果$x\in F_1$($x\in F_2$同理)，则$0=\mathrm{dist}(x,F_1)=\mathrm{dist}(-x,F_1)$，所以$-x\in F_1$；<br/>
    (ii) 如果$x\notin F_1\cup F_2$，则$\mathrm{dist}(-x,F_i)=\mathrm{dist}(x,F_i)>0, i=1,2$. 所以$x,-x\in F_3$.<br/>
综上述，一定存在一个$F_i$包含一对对径点.  $\Box$
<br/>

让我们回到原来的问题. 只需注意到每个点光源照亮的区域确实是一个闭集，而且**不可能包含一对对径点**，我们就可以轻松地反证：$n=3$的情形无法照亮整个球面！$n=1,2$可以同样地证明，请读者自己尝试. 至此我们运用拓扑的魔法给出了问题的另一个证明(^^<br/>

<br/>
[少女祈祷中...](https://senyuyangpdelearner.github.io/blog)

<hr style="height:0.5">
<font size="2" color="grey">&copy;SenyuYangPDElearner</font>
