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

# 调和分析：Littlewood-Paley定理的随机化证明

<font size="2" color="grey">2024.5.12</font><br/>
收到预录取通知啦，终于有时间记点东西(但还是鸽了半个月). Littlewood-Paley定理等频率分解技术是调和分析，PDE等领域中的重要工具. L-P定理的传统证明基于向量值的奇异积分算子，而在上星期的波方程讨论班上笔者提到一个基于随机化(randomization technique)思想的美妙证明，在此详细介绍一下. 文章主要参考W. Schlag的[讲义](https://gauss.math.yale.edu/~ws442/harmonicnotes_old.pdf).

先引进一些对象以便给出L-P定理的叙述.

>**练习/引理1.** 存在径向非负的$\psi\in C_0^{\infty}(\mathbb{R}^n)$ s.t. $\mathrm{supp} \ \psi\subset \mathbb{R}^n\setminus\{0\}$，且对于任意$x\neq 0$, 
>
>$$
\sum_{j\in\mathbb{Z}} \psi(2^{-j}x)=1,
$$
>
>其中至多两项非零.<br>

*注*. 上式称为单位*二进分解*(dyadic decomposition).<br/>

我们简记$\psi_j=\psi(2^{-j}\cdot)$，并定义*频率局部化*算子

$$
\Delta_j\colon \Delta_jf=\mathcal{F}^{-1}(\psi_j\hat{f}),
$$

i.e. $\psi_j$是$\Delta_j$的乘子. 由Plancherel定理(能量恒等式)，对$f\in L^2(\mathbb{R}^n)$，

$$
\Vert f\Vert_{L^2}^2\approx \sum_{j\in\mathbb{Z}} \Vert \Delta_jf\Vert_{L^2}^2.
$$ 

如果定义*Littlewood-Paley平方函数*

$$
Sf:=\left( \sum_{j\in \mathbb{Z}} \vert \Delta_j\vert^2 \right)^{1/2},
$$

那么有$\Vert f\Vert_{L^2}\approx \Vert Sf\Vert_{L^2}$. 而L-P定理进一步断言：

>**L-P定理.** 设$f\in L^p(\mathbb{R}^n)$, $p\in (1,\infty)$，则$ Sf\in L^p(\mathbb{R}^n)$，且
>
>$$
\Vert f\Vert_{L^p}\approx_p \Vert Sf\Vert_{L^p}.
$$

*注*. 我们知道$L^p(\mathbb{R}^n)$, $p\neq 2$不是内积空间，而Littlewood-Paley分解在频率空间上给出$L^p$一个几乎正交的分解.<br/>

现在做一些随机化工具的准备. 给定一列独立同分布的随机变量$\\{ r_j\\}_{j=\mathbb{Z}}$ s.t. 

$$
\mathbb{P}[r_j=1]=\mathbb[r_j=-1]=1/2.
$$

下面是一个类似于中心极限定理的结果.

>**引理2.** 给定任意正整数$N$ 与$\\{ a_j \\}_{j=1}^N\subset \mathbb{R}$，则对任意$\lambda>0$有
>
>$$
 \mathbb{P}\left[ \left\vert \sum_{j=1}^{n}r_ja_j\right\vert >\lambda\left(\sum_{j=1}^{N}  a_j^2\right)^{1/2}\right]
$$
>
>$$
\leq 2e^{-\lambda^2/2}
$$

*证明*. 令随机变量$S_N=\sum_{j=1}^{N}r_ja_j$，$\sigma^2=\sum_{j=1}^{N}a_j^2$，则对任意$t\in\mathbb{R}$，

$$
0\leq\mathbb{E}e^{tS_N}=\prod_{j=1}^{N}\mathbb{E}e^{tr_ja_j}=\prod_{j=1}^{N} \cosh (ta_j).
$$

由一个简单的不等式$\cosh x\leq e^{x^2/2}$可得

$$
\mathbb{E}e^{tS_N}\leq e^{t^2\sigma^2/2}
$$

由Markov不等式，

$$
\mathbb{P}[S_N>\lambda\sigma]=\mathbb{P}[e^{tS_N}>e^{t\lambda\sigma}]
$$

$$
\leq e^{t^2\sigma^2/2-t\lambda\sigma}.
$$

令$t=\lambda/\sigma$，右式即取得最小值$e^{-\lambda^2/2}$，注意到这里出现Gauss函数和CLT的关系. 同理可得$\mathbb{P}[S_N<-\lambda\sigma]\leq e^{-\lambda^2/2}$，所以

$$
\mathbb{P}[\vert S_N\vert >\lambda\sigma]\leq 2e^{-\lambda^2/2}，
$$

引理得证.&emsp;&emsp;$\Box$

利用引理1可以得到著名的*Khinchin不等式*.

>**引理3.** 对任意$p\in [1,\infty)$，$N\in \mathbb{N}$与$\\{ a_j \\}_{j=1}^N\subset \mathbb{R}$，
>
>$$
 \mathbb{E}\left[\vert \sum_{j=1}^N r_ja_j\vert^p\right] \approx_p \left( \sum_{j=1}^{N} a_j^2\right)^{p/2}.
$$

*证明*. 不妨作正规化：$\sigma^2=1$. 计算得

$$
\mathbb{E}\vert S_N\vert^p = p\int_{0}^{\infty} \lambda^{p-1}\mathbb{P}[S_N>\lambda\cdot 1]
$$

$$
=:C_p<\infty. 
$$

上界得证. 对于下界，首先注意到$p=2$时左右两式恒等：

$$
\mathbb{E}\left|\sum_{j = 1}^{N}r_{j}a_{j}\right|^{2} = \mathbb{E}\left[\sum_{j,k}r_{j}r_{k}a_{j}a_{k}\right] 
$$

$$
= \sum_{j = 1}^{N}|a_{j}|^{2} = 1
$$

于是由概率空间的有限测度性和Hölder不等式可知

$$
\left(\mathbb{E}\left|\sum_{j = 1}^{N}r_{j}a_{j}\right|^{p}\right)^{1/p}\leq 1,\ 1\leq p\leq 2,
$$

$$
\left(\mathbb{E}\left|\sum_{j = 1}^{N}r_{j}a_{j}\right|^{p}\right)^{1/p}\geq 1,\ p\geq 2.
$$

所以$p\geq 2$的情形已得证. 当$p<2$时，我们采用经典的对偶论证(duality argument). 由Hölder不等式有

$$
\left(\mathbb{E}\left|\sum_{j = 1}^{N}r_{j}a_{j}\right|^{p}\right)^{1/p}\left(\mathbb{E}\left|\sum_{j =1}^{N}r_{j}a_{j}\right|^{p'}\right)^{1/p'}
$$

$$
\geq \left(\mathbb{E}\left|\sum_{j =1}^{N}r_{j}a_{j}\right|^{2}\right)=1.
$$

其中$1/p+1/p'=1, p'>2$. 再对$p'$项作上界估计即可.&emsp;&emsp;$\Box$

这里解释一下建立上述引理的动机. 首先在一般情形下$l^1$和$l^2$是不能相互控制的，但上述引理指出在*平均意义*下$l^2$可以等价于$l^1$.而$l^1$范数内部是各项直接相加，加法结构更易于处理.  另外对取值在$\mathbb{C}$上的$a_j$可以通过以上引理和三角不等式建立相同的结果.<br/>  

现在回到L-P定理的证明，我们首先先建立著名的*Mikhlin乘子定理*.

>**定理.** 令$m:\mathbb{R}^n\setminus\\{0\\}\to \mathbb{C}$ 满足对任意$\xi\neq 0$，
>
>$$
\vert \partial^{\gamma}m(\xi)\vert\lesssim \vert\xi\vert^{-\vert\gamma\vert},\ \forall \vert\gamma\vert\leq n+2.
$$
>
>那么对任意$p\in (1,\infty)$都有($\widehat{\cdot}$, $\mathcal{F}^{-1}[\cdot]$分别代表Fourier变换和Fourier逆变换)
>
>$$
\Vert\mathcal{F}^{-1}[m\widehat{f}]\Vert_{L^p}\lesssim_p \Vert f\Vert_{L^p},\ \forall f\in\mathcal{S},
$$
>
>即乘子$M_m$可延拓为$(p,p)$有界算子.

*证明概要*. Fourier乘子$m$对应了物理空间上的卷积核$K:\ \hat{K}=m$. 根据奇异积分(singular integral)理论，对$K$作径向二进分解后验证其满足Calderon-Zygmund条件

$$
\vert K(x)\vert\lesssim \vert x\vert^{-n},\ \vert \nabla K(x)\vert\lesssim \vert x\vert^{-n-1}
$$

即可.&emsp;&emsp;$\Box$

至此我们给予L-P定理最后一击.

*L-P定理的证明*. 对于之前构造的$\\{ r_j \\}$，可以直接验证随机化乘子

$$
m_N(\xi):=\sum_{j=-N}^{N}r_j\psi_j(\xi)
$$

满足Mikhlin乘子定理的条件，而且常数系数关于$r_j$和$N$一致有界. 于是由引理2和乘子定理，

$$
\int_{\mathbb{R}^n} \vert Sf\vert^p
$$

$$
\lesssim \limsup_{N\to \infty} \mathbb{E} \left[ \int_{\mathbb{R}^n}\vert \sum_{j=-N}^{N}r_j\Delta_jf\vert^p \right]
$$

$$
\lesssim_p \Vert f\Vert_{L^p}^p, 
$$

上界估计得证. 下界估计依然由对偶论证得到：一个细节是由于L-P分解不是完全正交的分解，这里我们还需要取另一个支集“稍宽”的$\tilde{\psi}\in C_0^{\infty}$，并定义相应的频率局部化算子$\tilde{\Delta}_j$使得

$$ 
\tilde{\Delta}_j\Delta_j=\Delta_j,\ \forall j\in\mathbb{Z},
$$

例如$\tilde{\Delta}\_j=\Delta_{j-1}+\Delta_j+\Delta_{j+1}$. 因此对$f,g\in\mathcal{S}$，

$$
\vert\int_{\mathbb{R}^n} fg\vert
$$

$$
=\vert\sum_j \int_{\mathbb{R}^n} \Delta_jf\cdot g\vert
$$

$$
=\vert\sum_j \int_{\mathbb{R}^n} \tilde{\Delta}_j\Delta_jf\cdot g\vert
$$

$$
=\sum_j \vert\int_{\mathbb{R}^n} \Delta_jf\tilde{\Delta}_jg\vert
$$

$$
\leq \int_{\mathbb{R}^n} \left(\sum_j\vert \Delta_jf\vert^2\right)^{1/2} \left( \sum_j\vert \tilde{\Delta}_jg\vert^2\right)^{1/2}
$$

$$
\leq \Vert Sf\Vert_p\Vert Sg\Vert_{p'}
$$

$$
\lesssim \Vert Sf\Vert_p\Vert g\Vert_{p'},
$$

其中$1/p+1/p'=1$，第四行用Plancherel定理，第七行用L-P定理的上界估计. 再由$L^p$的对偶性可知$\Vert f\Vert_p\lesssim \Vert Sf\Vert_p$.&emsp;&emsp;$\Box$

于是我们用随机化的<font color="purple">魔法</font>做出了一个<font color="pink">奇迹</font>般的证明呢（笑）

<hr style="height:1px">

&copy; Senyu Yang&emsp;<a href="." target="_self" >少女祈祷中...</a>
