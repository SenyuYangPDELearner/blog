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
  background-image: url(https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQgBA_vJZU-QJZ2ZyiJQ0zo2xmpT2qMGT6gTw&s);
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

# Bourgain的魔法：一个Szemerédi型定理的Fourier证明

<font size="2" color="grey">2024.6.xx</font><br/>
*按：Jean Bourgain(1954-2018)绝对属于当代最富创造力的一批数学家，在诸多领域留下不胜数的成果和洞见. 也许每个分析学工作者都会在生命的某个阶段接触Bourgain的工作或思想. 这里是一个(不定期)连载系列，记录Bourgain的数学魔法.*<br/>

今天介绍Bourgain在1986年基于Fourier分析对Furstenberg等人关于正密度集的Szemerédi型定理的证明，从中可以感受到调和分析在组合学中的威力. 笔者主要参考了以下文献：<br>
&emsp;[1] J.  Bourgain, *A Szemerédi type theorem for sets of positive density in R^k* <br>
&emsp;[2] T. Tao, *Exploring the toolkit of Jean Bourgain*<br/>

我们先介绍主要结果. 

>**定理1.**(Furstenberg, Katznelson, Weiss) 设可测集 $A\subset R^2$ 有上界密度 $\delta=\delta(A)\>0$ , 则存在 $l_0\>0$ s.t. 对*任意* $l\geq l_0$ , 存在 $x,y\in A$ , $\vert x-y\vert =l$ . 这里上界密度
>
>$$
\delta(A):=\limsup_{R\to +\infty} \frac{\vert A\cap B_R \vert}{\vert B_R\vert}, 
$$
>
>$\vert \cdot\vert$ 是Lebesgue测度，$B_R$ 是原点为中心，$R$ 为半径的圆盘.

粗略地说，只要集合在平面上足够"稠密"，那么集合中所有点对的距离取遍充分大的正实数. Bourgain证明的第一步是将结论定量化( quantitative formulation )，以便硬分析工具的介入. 

>**定理2.**(Bourgain) 设可测集 $B\subset [0,1]^2$ , $\vert A\vert\geq \delta\>0$ . 则存在充分小的 $t_1$ 和充分大的 $J$，使得对分划$0\<t_J\<t_{J-1}\<...\<t_1\<1$ s.t. $t_{j+1}\leq t_j/2$ ，存在有 $1\leq j\leq J$ , 
>
$$
\int_{\mathbb{R}^2}\int_{S^1} 1_A(x) 1_A(x+t_j\omega) \ d\sigma(\omega)dx \gtrsim \delta^2. \tag{1}
$$

*定理2 $\Rightarrow$ 定理1*. 假设定理1不成立，则存在 $0<l_1<l_2<...<l_J<...$ s.t. $\vert x-y\vert\neq l_k, \forall x,y \in  A, k\in\mathbb{N}$ . WLOG, 设 $l_{k+1}\geq 2l_{k}$ . 由上界密度定义，存在 $R>t_J$ s.t. $\vert A\cap B_R\vert\geq \delta R^2$ . 令 $B:= \frac{1}{R}\cdot A\subset [0,1]^2$ ,  $t_j=l_{J+1-j}/R$ , 则 $B$ 符合定理2条件，但根据假设，对任意 $1\leq j\leq J$ , $(1)$ 恒为 $0$ , 矛盾 ！因此定理2就是定理1的定量化. &emsp; $\Box$ <br/>

下面着手定理2的证明. 由Plancherel定理我们变换到频率空间上，

$$
\int_{\mathbb{R}^2}\int_{S^1} \widehat{1_A}(x) \widehat{1_A}(x+t_j\omega) \,d\sigma(\omega)dx
$$  

$$
=\int_{S^1}\int_{\mathbb{R}^2} \vert \widehat{1_A}(\xi)\vert^2 e^{it_j\omega\cdot\xi} \,d\xi d\sigma(\omega)
$$

$$
=\int_{\mathbb{R}^2} \vert \widehat{1_A}(\xi)\vert^2 \widehat{\sigma}(t_j\xi) \,d\xi. \tag{2}
$$

接下来非常标准地做频率分解：

- 低频项 $\vert\xi\vert\leq \epsilon t_j^{-1}$ :

- 高频项 $\vert\xi\vert\geq (\epsilon t_j)^{-1}$ : 

- 中间项 $\epsilon t_j^{-1}\< \vert \xi\vert\< (\epsilon t_j)^{-1}$ : 

综上，存在充分小的 $\epsilon$ s.t. $(2)\geq C\vert A\vert^2-\epsilon^{1/2}\vert A\vert-\epsilon^1\vert A\vert \gtrsim \delta^2$ . Bourgain的魔法奏效了！&emsp; $\Box$

<hr style="height:1px">

&copy; Senyu Yang&emsp;<a href="." target="_self" >Next Dream...</a>
