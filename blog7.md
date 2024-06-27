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

# Bourgain的魔法：一道丘赛题与双线性Strichartz估计

<font size="2" color="grey">xxxx.xx.xx </font><br/>
*按：Jean Bourgain(1954-20180)绝对属于当代最富创造力的一批数学家，在诸多领域留下不胜数的成果和洞见. 也许每个分析学工作者都会在生命的某个阶段接触Bourgain的工作或思想. 这里是一个(不定期)连载系列，记录Bourgain的数学魔法.*

今年丘赛~~调和~~分析与~~偏~~微分方程方向笔试第三题出现了一个限制性Fourier变换的乘积估计. 还蛮希望丘赛往后可以多出些这类别开生面的问题~~毕竟这是本PDE民工排名最高的一次虽然离进决还是差一点点~~（笑）

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
\Vert u_1u_2\Vert_{L^2(\mathbb{R})}\leq C\Vert f_1\Vert_{L^2(\mathbb{R})} \Vert f_2\Vert_{L^2(\mathbb{R})}.
$$
>
>(提示. 尝试用Plancherel定理. ~~这不是废话吗~~)

学过色散方程的同学不难注意到，如果记 $x_1=x$ , $x_2=t $ , 问题等价于证明一维齐次Schrödinger方程

$$
i\partial_t u+\Delta u=0
$$

的Cauchy问题解 $u_1, u_2$ 的双线性Strichartz估计，其中初值的频率 $\psi f_1, \psi(10-\cdot )f_2$ 是分离的. S方程的解具有时间反演的对称性，于是时间 $t$ 可在整个 $\mathbb{R}$ 上取值. 所以笔者当时用Plancherel定理时是先对 $x_1$ 作Fourier变换，整理后再对 $x_2$ 作Fourier变换，一通换元就会得到 $\psi(\xi)f_1(\xi)\cdot \psi(10-\eta)f_2(\eta)$ 关于一个奇异项(换元时多出的Jacobi) $\vert \xi-\eta\vert$ 的积分，而恰好*频率的分离排除了奇点*，问题就解决了. 这些步骤我们在后面还会详细展开.<br/>

而今天的主题就是问题的背景：Bourgain在 $[1]$ 关于Schrödinger方程得到的 **bilinear Strichartz estimates** . Bourgain的成果出现在丘赛题还是很让人惊喜的. 主要的参考文献有<br>
&emsp;[1] J. Bourgain, *Refinements of Strichartz inequality and applications to 2D-NLS with critical nonlinearity*.<br>
&emsp;[2] J. Colliander, M. Keel, G. Staffilani, H. Takaoka, T, Tao, *The theory of nonlinear Schrödinger equations: part Ⅰ*.<br>

首先叙述Bourgain的结果. ~~由于笔者偷懒的缘故~~我们只考虑齐次情形.


>**定理1.**(Bourgain) 设 $n\geq 2$ , $u(t,x):=e^{it\Delta}u_0(x), v(t,x):=e^{it\Delta}v_0(x)$ . 则对任意 $\delta>0$ , 
>
$$
\Vert uv\Vert_{L_t^2L_x^2}\lesssim_{\delta} \Vert u_0\Vert_{\dot{H}^{-\frac{1}{2}+\delta}} \Vert v_0\Vert_{\dot{H}^{\frac{n-1}{2}-\delta}}
$$

Bourgain的估计

<hr style="height=1px”>

&copy; Senyu Yang&emsp;[Next Dream…](./)
