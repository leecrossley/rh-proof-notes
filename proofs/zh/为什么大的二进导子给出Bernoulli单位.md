# 为什么大的二进导子给出 Bernoulli 单位

## 命题

设 $\ell$ 为素数，$d\ge1$，$4\mid\ell^d-1$，令 $Q=\ell^d$、$s=v_2(Q-1)$。取奇整数 $f\ge1$、整数 $n\ge0$，满足 $f4^s\le2^n$。设 $\phi,\xi$ 分别为模 $f,2^n$ 的 $\overline{\mathbb Q}_\ell$-值本原 Dirichlet 特征，且 $\operatorname{ord}\phi\mid Q-1$、$\phi(-1)\xi(-1)=-1$。将 $\chi=\phi\xi$ 视为模 $f2^n$ 的特征，非单位上的值取零。定义

$$
B_{1,\chi}=\frac{1}{f2^n}\sum_{a=0}^{f2^n-1} a\,\phi(a)\xi(a).
$$

则 $|B_{1,\chi}|_\ell=1$。这就是 `LemmaX`，用于 [剩余余闭链的消失](%E5%A4%A7%E7%9A%84%E4%BA%8C%E8%BF%9B%E5%AF%BC%E5%AD%90%E6%80%8E%E6%A0%B7%E4%BD%BF%E5%89%A9%E4%BD%99%E4%BD%99%E9%97%AD%E9%93%BE%E6%88%90%E4%B8%BA%E4%BD%99%E8%BE%B9%E7%95%8C.md)。证明的核心是：如果 Bernoulli 和的约化等于零，那么两个过滤后的有限和也同时为零。两和相减却只有两个边界项留下，它们的和为 $-2$。

## 一、把可能有分母的加权和改写成整数和

记 $N=2^n$、$m=n-s$、$R=f2^s$。由大小条件有 $m\ge s\ge2$ 和 $1<R\le2^m$。设 $\mathcal O$ 是 $\overline{\mathbb Q}_\ell$ 中范数不超过 $1$ 的环，$k$ 为其剩余域。令 $\mathcal B\subseteq\mathcal O$ 为约化被 $x\mapsto x^Q$ 固定的元素组成的子环。因为 $\operatorname{ord}\phi\mid Q-1$，$\phi$ 的值都属于 $\mathcal B$。而 $\ell$ 是奇数，$N^{-1}$ 也属于 $\mathcal B$。

对每个 $u\in\mathbb Z/N\mathbb Z$，定义

$$
S(u)=\sum_{\substack{0\le a<fN\\a\equiv u\ (N)}}\phi(a),
\qquad
A(u)=\sum_{\substack{0\le a<fN\\a\equiv u\ (N)}}a\phi(a).
$$

沿整段将 $a$ 向右平移 $ft$，$\phi$ 的周期保证其值不变，而首尾移入移出的项相隔 $fN$。因而 $S(u-ft)=S(u)$。又 $f$ 与 $N$ 互素，$S$ 为常数 $S_0$。对带权和做同样平移，$a$ 的线性权贡献 $ftS_0$，从另一端移入的项与移出的每个对应项在线性权上相差 $fN$，得到

$$
A(u)-A(u-ft)=ftS_0-fN
\sum_{\substack{0\le a<ft\\a\equiv u\ (N)}}\phi(a).
\tag{1}
$$

令 $g(u)=(A(u)-A(0))/(fN)$。虽然这个定义中可能除以 $\ell\mid f$，但取 $t\ge0$ 使 $u-ft=0\bmod N$，式 (1) 把 $g(u)$ 表成 $tS_0/N$ 减去若干 $\phi(a)$ 的和。因此 $g(u)\in\mathcal B$。当 $ft\le N$ 时，(1) 中的短和至多一项，故以 $[u]$ 为最小非负代表，

$$
g(u)-g(u-ft)=tS_0/N-\mathbf 1_{[u]<ft}\phi([u]).
\tag{2}
$$

因为 $\xi$ 本原且 $n\ge4$，其总和为零。按 $a\bmod N$ 分组后，可在加权和中把 $A(u)/(fN)$ 改成 $g(u)$，得到
$B_{1,\chi}=\sum_u \xi(u)g(u)$。所有项都在 $\mathcal O$ 中，所以已证明 $|B_{1,\chi}|_\ell\le1$。下文把这些函数全约化到 $k$，沿用原符号。用 $t=2^s$ 代入 (2)，记 $c=2^sS_0/N$ 的约化，得到

$$
g(u)-g(u-R)=c-\mathbf 1_{[u]<R}\phi([u]).
\tag{3}
$$

## 二、取 Frobenius 幂能过滤单位根阶

用一个一般事实。若 $z_i=0$ 或 $z_i^{2^n}=1$，且 $b_i^Q=b_i$，由 $\sum_i z_i b_i=0$ 可推出

$$
\sum_{i:\ z_i^{2^s}=1}z_i b_i=0 .
\tag{4}
$$

事实上，$Q=1+2^s a$ 且 $a$ 为奇数。每次平方使 $v_2(Q^{2^j}-1)$ 增加 $1$，所以 $Q\bmod 2^n$ 生成全部模 $2^s$ 余 $1$ 的单位，共 $2^{n-s}$ 个。对原和作 $Q$ 的反复 Frobenius 幂，可把各 $z_i$ 的指数改为任何 $1+2^s j$，$0\le j<2^{n-s}$，仍有和为零。将这些等式相加，单个 $z_i\ne0$ 对应的系数为 $z_i\sum_j(z_i^{2^s})^j$。几何和在 $z_i^{2^s}\ne1$ 时为零，否则为 $2^{n-s}z_i$。因为 $\ell\ne2$，可除以 $2^{n-s}$，得 (4)。

反设 $B_{1,\chi}$ 约化为零。对任意奇单位 $y$ 模 $N$，由乘法换元和 $\xi(y)\ne0$ 得 $\sum_x \xi(x)g(xy)=0$。因此 (4) 给

$$
\sum_{x\in E}\xi(x)g(xy)=0,\qquad E=\{x:\xi(x)^{2^s}=1\}.
\tag{5}
$$

## 三、对两个平移相减

本原性给 $\xi(1+2^{n-1})=-1$，约化后仍成立。模 $2^n$ 的奇单位唯一写成 $(-1)^\epsilon5^j$，且 $\xi(5)$ 的阶为 $2^{n-2}$，因为 $5^{2^{n-3}}\equiv1+2^{n-1}\pmod{2^n}$。若 $x\in E$，则 $2^{m-2}\mid j$，故 $x\equiv1$ 或 $-1\bmod2^m$，仍包括 $m=2$。

对 (5) 取 $y=1$ 和 $y=1-R$，两者都是奇单位。按 $x\bmod2^m$ 分两类做差。因为 $2^s\mid R$，若 $x\equiv1\bmod2^m$，则 $x(1-R)\equiv x-R\bmod N$。式 (3) 产生 $+\xi(x)c$，并有边界项 $-\xi(x)\phi([x])$ 当 $[x]<R$ 时出现。因 $R\le2^m$，这个区间里唯一模 $2^m$ 余 $1$ 的代表为 $1$，只留下 $-\xi(1)\phi(1)=-1$。

若 $x\equiv-1\bmod2^m$，则 $x(1-R)\equiv x+R\bmod N$。式 (3) 用在 $x+R$，产生 $-\xi(x)c$，以及 $\xi(x)\phi([x+R])$ 当 $[x+R]<R$ 时的边界项。唯一满足条件的代表为 $[x+R]=R-1$，对应 $x=-1$。其贡献是 $\xi(-1)\phi(R-1)=\xi(-1)\phi(-1)=-1$，用到 $f\mid R$ 和乘积特征为奇。

所有含 $c$ 的项相消。用 $u_*=1+2^{n-1}$ 乘 $E$ 的元素，保留其模 $2^m$ 的符号，也保留 $\xi(x)^{2^s}=1$，但让 $\xi(x)$ 变号。于是两和的差只剩 $-1-1=-2\ne0$，与 (5) 矛盾。故 $B_{1,\chi}$ 的约化非零，即为单位。

## Lean 对照

- [`lx_partial`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/LxPartial.lean#L15) 展开分组和平移，给式 (1) 至 (3) 所用的差分。[`sum_filter_two_pow_roots_eq_zero_of_sum_eq_zero`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/SumFilterTwoPowRootsEqZeroOfSumEqZero.lean#L4) 对应式 (4)。
- [`lx_core`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/LxCore.lean#L65) 取两个过滤和相减。源码用二进整除引理证明 $E$ 中元素为模 $2^m$ 的 $\pm1$，上面用 $5$ 生成的循环因子书写。
- [`lemmaX`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/LemmaX.lean#L78) 合成约化、差分和非消失。本篇为发布版源码对照，按本原奇特征的加权和定义计算一次 Bernoulli 值。
