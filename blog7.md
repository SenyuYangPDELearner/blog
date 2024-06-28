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
  background-image: url(https://www.pnas.org/cms/10.1073/pnas.1901965116/asset/72a771ec-f108-4f4f-8004-087589844652/assets/graphic/pnas.1901965116fig01.jpeg);
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

# Bourgain的魔法：一道2024年丘赛题与双线性Strichartz估计

<font size="2" color="grey">2024.6.28 </font><br/>
*按：Jean Bourgain(1954-2018)绝对属于当代最富创造力的一批数学家，在诸多领域留下不胜数的成果和洞见. 也许每个分析学工作者都会在生命的某个阶段接触Bourgain的工作或思想. 这里是一个(不定期)连载系列，记录Bourgain的数学魔法.*

今年丘赛~~调和~~分析与~~偏~~微分方程方向笔试第三题出现了一个限制性Fourier变换的乘积估计. 还蛮希望丘赛往后可以多出些这类别开生面的问题~~毕竟是本PDE民工排名最高的一次~~（笑）

>**问题.** 设 $\psi(\xi)\in C_0^{\infty}(\mathbb{R})$ 紧支光滑 s.t. $\psi(\xi)=0$ , $\forall \vert\xi\vert\geq 1$. 设 $f_1(\xi)$ , $f_2(\xi)\in C_c^{\infty}(\mathbb{R})$ , 并定义 $u_1$ , $u_2: $ $\mathbb{R}^2\to\mathbb{C}$ , 
>
$$
u_1(x_1,x_2):=\int_{\mathbb{R}} \psi(\xi)f_1(\xi)e^{i\xi x_1}e^{i\xi^2 x_2} \ d\xi , 
$$
>
$$
u_2(x_1,x_2):=\int_{\mathbb{R}} \psi(10-\eta)f_2(\eta)e^{i\eta x_1}e^{i\eta^2 x_2} \ d\xi .
$$
>
>证明: 存在与 $\psi$ 有关但与 $f_1, f_2$ 无关的常数 $C$ s.t. 
>
$$
\Vert u_1u_2\Vert_{L^2(\mathbb{R}^2)}\leq C\Vert f_1\Vert_{L^2(\mathbb{R})} \Vert f_2\Vert_{L^2(\mathbb{R})}.
$$
>
>(提示. 尝试用Plancherel定理. ~~这不是废话吗~~)

学过PDE的同学不难注意到，如果记 $x_1=x$ , $x_2=t $ , 问题等价于证明一维齐次**Schrödinger方程**

$$
i\partial_t u+\Delta u=0
$$

的Cauchy问题解 $u_1, u_2$ 的双线性Strichartz估计，其中初值的频率 $\psi f_1, \psi(10-\cdot )f_2$ 是分离的. S方程的解具有时间反演的对称性，于是时间 $t$ 可在整个 $\mathbb{R}$ 上取值. 所以笔者当时用Plancherel定理时是先对 $x_1$ 作Fourier变换，整理后再对 $x_2$ 作Fourier变换，一通换元就会得到 $\psi(\xi)f_1(\xi)\cdot \psi(10-\eta)f_2(\eta)$ 关于一个奇异项(换元时多出的Jacobi) $\vert \xi-\eta\vert$ 的积分，而恰好*频率的分离排除了奇点*，问题就解决了. 这些步骤我们在后面还会详细展开.<br/>

而今天的主题就是问题的背景：Bourgain在[1]关于Schrödinger方程得到的 **bilinear Strichartz estimates** . Bourgain的成果出现在丘赛题还是很让人惊喜的. 主要的参考文献有<br>
&emsp;[1] J. Bourgain, *Refinements of Strichartz inequality and applications to 2D-NLS with critical nonlinearity*.<br>
&emsp;[2] J. Colliander, M. Keel, G. Staffilani, H. Takaoka, T, Tao, *The theory of nonlinear Schrödinger equations: part Ⅰ*.<br>

首先叙述Bourgain的结果. ~~由于笔者偷懒的缘故~~我们只考虑齐次情形.

>**定理.**(Bourgain) 设 $n\geq 2$ , $u(t,x):=e^{it\Delta}u_0(x), v(t,x):=e^{it\Delta}v_0(x)$ . 则对任意 $\delta>0$ , 
>
$$
\Vert uv\Vert_{L_t^2L_x^2}\lesssim_{\delta} \Vert u_0\Vert_{\dot{H}^{-\frac{1}{2}+\delta}} \Vert v_0\Vert_{\dot{H}^{\frac{n-1}{2}-\delta}}
$$

记 $s_1=-\frac{1}{2}+\delta$ , $s_2=\frac{n-1}{2}-\delta$ , $s_1+s_2=\frac{n}{2}-1$ . 由对称性，不妨设 $s_1\leq s_2$ , 这时Bourgain的估计对于高频的 $u$ 和低频的 $v$ 非常有用(这里会让人联想Bony仿积分解)，[2] 作如此评论：*This estimate shows in particular that there is little interaction between high and low frequencies*. <br/>

在证明前先给出经典的(简化版)Strichartz估计. 

$$
\Vert u \Vert_{L_t^4L_x^4}\lesssim \Vert u_0\Vert_{L^2}. 
$$

一般的Strichartz估计的证明可以在任何色散PDE教材中找到，非端点情形的证明主要是 $TT^*$ argument以及对 $L^{\infty}$ 衰减和 $L^2$ 守恒做插值. 我们还会看到丘赛问题的条件使我们可以绕开经典的Strichartz估计——所以并不超纲（笑）. <br/>

*证明*. 我们分为以下几步. <br> 

&emsp; *Step 1*. 根据对偶性，只需证明对任意 $g\in L^2(\mathbb{R}\times\mathbb{R}^n)$ , 

$$
\int_{\mathbb{R}\times\mathbb{R}^n} g(t,x)\cdot u(t,x)v(t,x) \ dxdt\lesssim \Vert g\Vert_{L^2(\mathbb{R}\times\mathbb{R}^n)} \Vert u_0\Vert_{\dot{H}^{s_1}} \Vert v_0\Vert_{\dot{H}^{s_2}}.
$$

先关于 $x$ 作Fourier变换，用Plancherel定理，再关于 $t$ 作Fourier变换，

$$
\int_{\mathbb{R}\times\mathbb{R}^n} g(t,x)\cdot u(t,x)v(t,x) \ dxdt
$$

$$
=\int_{\mathbb{R}\times\mathbb{R}^n} \mathcal{F}_x\left[ g\right] (t,\xi)\left[ \widehat{u}\star_{\xi}\widehat{v} \right](t, \xi) \ d\xi dt
$$

$$
=\int_{\mathbb{R}\times\mathbb{R}^n\times\mathbb{R}^n} \mathcal{F}_x\left[ g \right] (t,\xi)e^{it(\vert \eta\vert^2+\vert \xi-\eta\vert^2)} \widehat{u_0}(\eta)\widehat{v_0}(\xi-\eta) \ d\eta d\xi dt
$$

$$
=\int_{\mathbb{R}\times\mathbb{R}^n\times\mathbb{R}^n} \mathcal{F}_x \left[ g \right] (t,\xi_1+\xi_2)e^{it(\vert \xi_1\vert^2+\vert \xi_2\vert^2)} \widehat{u_0}(\xi_1)\widehat{v_0}(\xi_2) \ d\xi_1 d\xi_2 dt
$$

$$
=\int_{\mathbb{R}^n\times\mathbb{R}^n} \widehat{g}(\vert\xi_1\vert^2+\vert\xi_2\vert^2,\xi_1+\xi_2) \widehat{u_0}(\xi_1)\widehat{v_0}(\xi_2) \ d\xi_1 d\xi_2.
$$

Fourier变换是 $L^2$ 上的等距同构，所以定理等价于：对任意 $g\in L^2(\mathbb{R}\times\mathbb{R}^n)$ , 

$$
\int_{\mathbb{R}^n\times\mathbb{R}^n} g(\vert\xi_1\vert^2+\vert\xi_2\vert^2,\xi_1+\xi_2) \widehat{u_0}(\xi_1)\widehat{v_0}(\xi_2) \ d\xi_1 d\xi_2
$$

$$
\lesssim \Vert g\Vert_{L^2(\mathbb{R}\times\mathbb{R}^n)} \Vert u_0\Vert_{\dot{H}^{s_1}} \Vert v_0\Vert_{\dot{H}^{s_2}}.
$$

i.e.

$$
I:=\int_{\mathbb{R}^n\times\mathbb{R}^n} g(\vert\xi_1\vert^2+\vert\xi_2\vert^2,\xi_1+\xi_2) \vert\xi_1\vert^{-s_1}\widehat{u_0}(\xi_1)\vert\xi_2\vert^{-s_2}\widehat{v_0}(\xi_2) \ d\xi_1 d\xi_2
$$

$$
\lesssim \Vert g\Vert_{L^2(\mathbb{R}\times\mathbb{R}^n)} \Vert u_0\Vert_{L^2} \Vert v_0\Vert_{L^2}.
$$

这里duality argument的妙处在于把时间频率从震荡因子中取出. <br>

&emsp; *Step 2*. 由 $s_1\leq s_2$ , 只需考虑频率 $\xi_1\geq \xi_2$ , 否则对 $I$ 乘以 $\vert\frac{\xi_2}{\xi_1}\vert^{s_2-s_1}\geq 1$ 即可. 进一步，当 $\vert \xi_1\vert\leq 4\vert \xi_2\vert$ 时 i.e. 初值的频率是**comparable**: $\vert\xi_1\vert \sim \vert \xi_2\vert$ , 则可以调整 $s_1, s_2$ s.t. $s_1=s_2=s'=\frac{n-4}{2}$ , 于是再由对偶性，估计成立等价于

$$
\Vert uv\Vert_{L_t^2L_x^2}\lesssim \Vert u_0\Vert_{\dot{H}^{s'}} \Vert v_0\Vert_{\dot{H}^{s'}}.  
$$

而 $\Vert uv\Vert_{L_t^2L_x^2} \leq \Vert u\Vert_{L_t^4L_x^4} \Vert v\Vert_{L_t^4L_x^4}$ , 由经典的Strichartz估计即得证. (注意这里使用了 $n\geq 2\Rightarrow s'\geq 0$ , 所以丘赛题作为 $n=1$ 情形必须要求初值的频率是seperate) <br>

&emsp; *Step 3.* 现在只需考虑频率**seperate**的情形：$\vert\xi_1\vert > 4\vert\xi_2\vert$ . $\vert\xi_1\vert \geq 4\vert\xi_2\vert$ . 对 $\xi_1, \xi_2$ 作Littlewood-Paley分解

$$
\widehat{u_0} =\sum_N \widehat{u_0}_N, \widehat{v_0}=\sum_N\sum_{M\leq -1} \widehat{v_0}_{M+N},
$$

下标 $N\in\mathbb{Z}$ 代表频率支撑在 $2^{N-1}\leq \vert \cdot\vert \leq 2^{N+1}$ 上，$M\leq -1$ 由seperate条件给出. (注意到丘赛问题中 $s_1=s_2=0$ 且初值频率紧支 , 所以无需做L-P分解.) 因此只需估计每个

$$
I_{M,N}:=\int_{\mathbb{R}^n\times\mathbb{R}^n} g(\vert\xi_1\vert^2+\vert\xi_2\vert^2,\xi_1+\xi_2) \vert\xi_1\vert^{-s_1}\widehat{u_0}_N(\xi_1)\vert\xi_2\vert^{-s_2}\widehat{v_0}_{M+N}(\xi_2) \ d\xi_1 d\xi_2
$$

$$
\sim 2^{-N(s_1+s_2)}2^{-Ms_2}\int_{\mathbb{R}^n\times\mathbb{R}^n} g(\vert\xi_1\vert^2+\vert\xi_2\vert^2,\xi_1+\xi_2) \widehat{u_0}_N(\xi_1)\widehat{v_0}_{M+N}(\xi_2) \ d\xi_1 d\xi_2
$$ 

为了得到 $\Vert g\Vert_{L^2(\mathbb{R}\times\mathbb{R}^n)}$ , 这里需要做换元: 令 $u=\xi_1+\xi_2\in \mathbb{R}^n$ , $v=\vert \xi_1\vert^2+\vert\xi_2\vert^2\in \mathbb{R}_+$ . 这里的自由度只有 $n+1$ 个，所以还需引入新的变量. 注意到 $\mathbb{R}^n\times\mathbb{R}^n$ 可以被以下区域覆盖(上标代表坐标分量)

$$
\Lambda_{j, k}:=\{ (\xi_1,\xi_2): \vert\xi_1^j\vert \sim \vert \xi_1\vert,  \vert\xi_2^k\vert \sim \vert \xi_2\vert \} , \ 1\leq j,k\leq n.
$$

由对称性，我们只需考虑 $\Lambda_{1,1}$ $\colon \vert \xi_1^1\vert\sim \vert\xi_1\vert$ , $\vert \xi_2^1\vert\sim\vert \xi_2\vert$ . 记 $\xi_2=(\xi_2^1, \tilde{\xi_2})$ , 并选取 $\tilde{\xi_2}$ 作为新变量. 固定$\tilde{\xi_2}$ , 则 

$$
\vert \xi_1\vert^2+\vert\xi_2^1\vert^2-v+\vert \tilde{\xi_2}\vert^2=0,
$$

$$
\xi_1+\xi_2^1\mathbf{e}_1-u=\mathbf{0}.
$$

记左式为向量值函数 $F(\xi_1, \xi_2^1; u, v)$ , 计算得(相差一个正负号)

$$
\det \frac{\partial F}{\partial (\xi_1, \xi_2^1)}=2 \vert \xi_1^1\pm \xi_2^1\vert, \det \frac{\partial F}{\partial (u,v)}=1.
$$

频率seperate, 所以前者 $\sim \xi_1^1$ . (注意到丘赛问题是 $n=1$ 情形，所以无需选择 $\tilde{\xi_2}$ 这个步骤，计算上方便很多.) 由隐函数定理即得

$$
d\xi_1d\xi_2^1= J\ dudv , \ J\sim 2^{-N}, 
$$

总之，$\Lambda_{1,1}\cap \{ \vert \xi_1\vert> 4\vert \xi_2\vert\}$ *绕开了* $J$ *的奇点*. 于是

$$
\int_{\mathbb{R}^n\times\mathbb{R}^n} g(\vert\xi_1\vert^2+\vert\xi_2\vert^2,\xi_1+\xi_2) \widehat{u_0}_N(\xi_1)\widehat{v_0}_{M+N}(\xi_2) \ d\xi_1 d\xi_2
$$

$$
=\int_{\mathbb{R}^{n-1}}d\tilde{\xi_2} \ \int_{\mathbb{R}_+\times\mathbb{R}^n} g(v,u) \widehat{u_0}_N(\xi_1(u,v))\widehat{v_0}_{M+N}(\xi_2(u,v)) \ J\ dudv 
$$

$$
\leq \Vert g\Vert_{L^2} \int_{\mathbb{R}^{n-1}}d\tilde{\xi_2} \ \left( \int_{\mathbb{R}_+\times\mathbb{R}^n} \vert \widehat{u_0}_N(\xi_1(u,v))\widehat{v_0}_{M+N}(\xi_2(u,v)) J\vert ^2\ dudv \right) ^{1/2}
$$

$$
=\Vert g\Vert_{L^2} \int_{\mathbb{R}^{n-1}}d\tilde{\xi_2} \ \left( \int_{\mathbb{R}\times\mathbb{R}^n} \vert\widehat{u_0}_N(\xi_1)\widehat{v_0}_{M+N}(\xi_2)\vert^2 \ \vert J\vert \ d\xi_1d\xi_2^1 \right) ^{1/2}
$$

$$
\lesssim 2^{-N/2} \Vert g\Vert_{L^2}\cdot 2^{(M+N)(n-1)/2} \Vert \widehat{u_0}_N\Vert_{L^2} \Vert \widehat{v_0}_{M+N}\Vert_{L^2}, 
$$

所以 

$$
I_{M,N}\lesssim 2^{N(-s_1-s_2+n/2-1)} 2^{M(-s_2+\frac{n-1}{2})} \Vert g\Vert_{L^2}\Vert \widehat{u_0}_N\Vert_{L^2} \Vert \widehat{v_0}_{M+N}\Vert_{L^2}
$$

$$
 =\Vert g\Vert_{L^2}\Vert \widehat{u_0}_N\Vert_{L^2} \left( 2^{-M\delta} \Vert \widehat{v_0}_{M+N}\Vert_{L^2}\right) .
$$  

由Plancherel定理，(离散卷积的)Young不等式和 $\delta>0$ 可得

$$
I\ \lesssim \Vert g\Vert_{L^2}\sum_{N} \Vert \widehat{u_0}_N\Vert_{L^2}\left(\sum_{M\leq -1}  2^{-M\delta}  \Vert \widehat{v_0}_{M+N}\Vert_{L^2}\right)
$$

$$
\lesssim \Vert g\Vert_{L^2}\left(\sum_{N} \Vert \widehat{u_0}_N\Vert_{L^2}\right)  \Vert 2^{-M\delta}\Vert_{l_{M\leq 1}^1} \left(\sum_N \Vert \widehat{v_0}_N\Vert_{L^2}\right)
$$

$$
\lesssim \Vert g\Vert_{L^2}\Vert u_0\Vert_{L^2}\Vert v_0\Vert_{L^2}.
$$

综上，$n\geq 2$ 以及 $\left( n=1 \wedge \text{seperate条件}\right)$ 的齐次bilinear Strichartz estimate成立！ &emsp; $\Box$ <br/>

*注*. 非齐次情形可以用Duhamel原理和Minkowski积分不等式得到非齐次bilinear Strichartz estimate

$$
\Vert uv\Vert_{L_t^2L_x^2} \lesssim_{\delta} (\Vert u_0\Vert_{\dot{H}^{-1/2+\delta}}+\Vert (i\partial_t+\Delta)u\Vert_{L_t^1\dot{H}_x^{-1/2+\delta}}) 
$$

$$
\times (\Vert v_0\Vert_{\dot{H}^{\frac{n-1}{2}-\delta}}+\Vert (i\partial_t+\Delta)v\Vert_{L_t^1\dot{H}_x^{\frac{n-1}{2}-\delta}}).
$$

<hr style="height=1px">

&copy; Senyu Yang&emsp;[Next Dream…](./)
