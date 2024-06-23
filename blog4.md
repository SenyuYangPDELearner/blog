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
  opacity: 0.2;
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

# Cauchy积分定理的一个优雅证明

<font size="2" color="grey">发布于2024.3.14</font><br/>
今天是国际数学日，先祝你 $\pi$ day 快乐！数学当然离不开优雅，*Beauty is the first test*(Hardy). 复分析是数学中最优美的分支之一，那么本文介绍复分析的基本定理——Cauchy定理的一个灰常灰常优雅滴几何风证明.

> **Cauchy定理.** 给定$\mathbb{C}$上的单连通区域$\Omega$，并有分段$C^1$边界$\partial \Omega$. 设$f\in C^{2}(\Omega)\cap C^{1}(\bar{\Omega})$并在$\Omega$上*解析*(也称*全纯*)，则
>
> $$
> \int_{\partial\Omega}f \ dz=0
> $$

*证明*. 设

$$
\frac{\partial}{\partial z}:=\frac{1}{2}(\frac{\partial}{\partial x}-i\frac{\partial}{\partial z}),
$$

$$
\frac{\partial}{\partial \bar{z}}:=\frac{1}{2}(\frac{\partial}{\partial x}+i\frac{\partial}{\partial z})
$$

这组切向量也是切空间$T\Omega$的一组基. 与之对偶的$1-$形式为$dz=dx+idy,d\bar{z}=dx-idy\in T^*{\Omega}$. 

> **引理/练习.** 证明Cauchy-Riemann方程(即解析性)等价于 $\frac{\partial}{\partial \bar{z}}f=0$.

对任意$\zeta\in\Omega$，取$r>0$使得圆盘$B(\zeta,r)\subset\subset \Omega$. 那么$\frac{1}{z-\zeta}$在$\Omega_r:=\Omega\setminus B(\zeta,r)$上解析. 利用**Stokes定理**，

$$
\int_{\Omega_r}\frac{\partial}{\partial \bar{z}}g \ dz\wedge d\bar{z}=\int_{\partial \Omega_r} g \ dz.
$$

令$g=\frac{f}{z-\zeta}$可得

$$
\int_{\Omega_r} \frac{\frac{\partial}{\partial \bar{z}}f}{z-\zeta} \ dz\wedge d\bar{z}
$$

$$
=\int_{\partial\Omega} \frac{f}{z-\zeta} \ dz-i\int_{0}^{2\pi} f(\zeta+re^{i\theta}) \ d\theta.
$$

$f$解析，所以上式第一行恒为$0$. 令$r\to 0$，则最后一项收敛于$2\pi if(\zeta)$，我们得到著名的*Cauchy积分公式*. 再将$f$替换为$(z-\zeta)f$就证明了Cauchy定理.&ensp;$\Box$

*注*. 如果只要求$\partial \Omega$可求长，可以用一族$C^1$曲线从$\Omega$内部逼近$\partial \Omega$即可.

<hr style="height:1px">

&copy; Senyu Yang&emsp;<a href="." target="_self" >Next Dream...</a>
