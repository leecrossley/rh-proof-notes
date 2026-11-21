# Perron积分怎样截出素数幂和

设 $\Lambda(n)$ 为 von Mangoldt 函数，$\chi$ 为模 $q$ 的狄利克雷特征。

**命题。** 存在绝对常数 $C>0$，使对每个整数 $q\ge1$、模 $q$ 特征 $\chi$ 及实数 $u,T$ 满足 $u\ge2,\ 2\le T\le2u$，写 $c=1+1/\log u$，就有

$$
\left|
  \sum_{1\le n\le u}\Lambda(n)\chi(n)-
  \frac1{2\pi}\int_{-T}^{T}
  -\frac{L'}{L}(c+it,\chi)\frac{u^{c+it}}{c+it}\,dt
 \right|
 \le C\left(\frac{u\log^2 u}{T}+\log u\right).
 \tag{1}
$$

求和上端是闭的，若 $u$ 为整数也包括 $n=u$。这是截断显式公式中把算术和变成复积分的那一步。

## 一、一个复积分怎样近似阶跃函数

对实数 $y>0,\ c>0,\ T\ge1$，令

$$
K_T(y;c)=\frac1{2\pi}\int_{-T}^{T}\frac{y^{c+it}}{c+it}\,dt .
$$

先证在 $y\ne1$ 时

$$
|K_T(y;c)-\mathbf1_{y>1}|\le
 3y^c\min\big(1,(T|\log y|)^{-1}\big).
 \tag{2}
$$

记 $a=\log y$。当 $a<0$，把固定高度的竖线段 $\Re s=c$ 向右闭合到 $\Re s=B$，$B>c$，两条横边在 $\Im s=\pm T$。积分核为 $e^{as}/s$。矩形内没有极点，且当 $B\to\infty$ 时右边竖线积分的绝对值 $\le2T e^{aB}/B\to0$。横边各自的绝对值至多 $\frac1T\int_c^B e^{ax}\,dx\le y^c/(T|a|)$。当 $a>0$，改向左闭合到 $-B$，矩形内只有 $s=0$ 的一阶极点，留数为 $1$。左边竖线积分趋于零，两条横边各有同样的界 $\frac1T\int_{-B}^c e^{ax}\,dx\le y^c/(T|a|)$。两种情况将原积分写成 $(2\pi i)^{-1}\int e^{as}\,ds/s$，得误差至多 $y^c/(\pi T|a|)$。

在 $T|a|\le1$ 时改写积分核为 $y^c[(c+it)^{-1}+(e^{iat}-1)/(c+it)]$。第一项积分为 $2\arctan(T/c)$，由虚部奇性和实部 $c/(c^2+t^2)$ 的积分得到。第二项的模至多 $|a|$，因为 $|e^{iat}-1|\le |at|$ 且 $|c+it|\ge|t|$。所以 $|K_T(y;c)|\le y^c(\pi+2T|a|)/(2\pi)$。而 $\mathbf1_{y>1}\le y^c$，这给 (2) 的另一条界。由两种情况，(2) 成立。

在 $y=1$ 时 $K_T(1;c)=\arctan(T/c)/\pi$，故与闭端点值 $1$ 的误差至多 $1$。下文记

$$
E(y)=|K_T(y;c)-\mathbf1_{y\ge1}|.
$$

包括 $y=1$ 在内，总有 $E(y)\le3 y^c$ 且 $E(y)T|\log y|\le3y^c$。

## 二、在绝对收敛区交换积分与级数

记 $\ell=\log u\ge\log2$、$c=1+1/\ell$，令 $a_n=\Lambda(n)\chi(n)$。由 Euler 乘积取对数导数有 $-L'/L(c+it,\chi)=\sum_{n\ge1}a_n n^{-c-it}$。因为 $|a_n|\le\log n$ 且 $c>1$，在该线段上一致绝对收敛。乘 $u^{c+it}/(c+it)$ 仍可交换积分与级数，所得就是 $\sum_{n\ge1}a_n K_T(u/n;c)$。于是 (1) 左边至多

$$
\sum_{n\ge1}(\log n)E(u/n).
 \tag{3}
$$

## 三、远离 $u$ 的项用绝对收敛，靠近 $u$ 的项用调和和

当 $n\le u/2$ 或 $n\ge2u$ 时，$|\log(u/n)|\ge\log2$。且 $u^c=eu$，故这部分 (3) 至多常数乘

$$
\frac{u}{T}\sum_{n\ge1}\frac{\log n}{n^{1+1/\ell}}.
$$

对 $x\ge0$ 有 $x e^{-x/(2\ell)}\le 2\ell$，代入 $x=\log n$。再用 $\sum_{n\ge1}n^{-1-1/(2\ell)}\le1+2\ell$，由积分比较得到上述量 $\ll u\ell^2/T$。

当 $u/2<n<2u$ 时，$(u/n)^c\le2^c\le8,\ \log n\le2\ell$。对 $n\ne u$，由 $(\log x)'=1/x$ 在 $u,n$ 之间至少为 $1/(2u)$，有 $|\log(u/n)|\ge|u-n|/(2u)$。设 $N=\lfloor u\rfloor$。对 $n=N,N+1$ 用 $E(u/n)\le3(u/n)^c$，其总贡献 $\ll\ell$。其他项满足

$$
\frac1{|u-n|}\le
 \begin{cases}
   1/(N-n),&n\le N-1,\\
   1/(n-N-1),&n\ge N+2 .
 \end{cases}
$$

各侧都可用 $\sum_{k\le N+1}1/k\le1+\log(N+1)\ll\ell$ 控制。由 $E(u/n)\ll u/(T|u-n|)$，距离贡献总共 $\ll u\ell^2/T$。合并得 (1)。保留 $n=N,N+1$ 两项单独估计，使结论对任意实数 $u$ 成立，包括极接近整数的情况。

## Lean 对照

- `GlobalTheory.PerronKernel.far_neg`、`far_pos` 用左右两种矩形，`near` 用反正切及振荡差。第 346 行 `truncated_perron_kernel` 给 (2)。[第 228、259、291、346 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/TruncatedPerronKernel.lean#L228)
- `GlobalTheory.PerronPsi.kernel_bound` 处理 $y=1$，`interchange` 给级数交换。`far_term`、`near_term`、`sum_w` 对应两组估计。主命题 `truncated_perron_psi` 在第 436 行。[第 7、70、223、269、321、436 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/TruncatedPerronPsi.lean#L7)
- 本稿为源码对读。由 (1) 得到显式公式还要移线、估计新边界并计入零点留数。
