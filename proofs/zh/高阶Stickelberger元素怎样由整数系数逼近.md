# 高阶 Stickelberger 元素怎样由整数系数逼近

要控制上同调，项目一端需要高阶 Bernoulli 值写成的群环元素，另一端需要能作用在类群上的整数下取整系数。下面证明相同的群环元素在分圆层升高时，用这些整数系数可以任意精确地逼近。

## 命题

取素数 $\ell$、正整数 $N$ 且 $\ell\mid N$、整数 $e\ge0$、与 $N$ 互素的正奇整数 $a$。令 $k=e+1$，$G_L=(\mathbb Z/L\mathbb Z)^\times$，给定有限阿贝尔群 $\Gamma$ 和群同态 $\phi:G_N\to\Gamma$。对每个 $m\ge0$ 写 $M=N\ell^m$，令 $\phi_M:G_M\to\Gamma$ 为约化到模 $N$ 后应用 $\phi$。$[b]_L$ 表示模 $L$ 的最小非负代表，$[g]$ 表示群环的基元。

对 $L=N$ 或 $M$，记 $\phi_L$ 为相应同态，定义

$$
\begin{aligned}
H_{L,k}(x)&=\frac{L^{k-1}}k B_k(x/L),\\
\Theta_L&=-\sum_{b\in G_L}H_{L,k}([b]_L)[\phi_L(b)^{-1}],\\
Y_L&=(1-a^k[\phi_L(a)^{-1}])\Theta_L,\\
J_{L,a}(b)&=\frac{a[a^{-1}b]_L-[b]_L}{L},\qquad
C_{L,a}(b)=\frac{a-1}{2}-J_{L,a}(b),\\
Q_M&=-\sum_{b\in G_M}[b]_M^e\,C_{M,a}(b)\,[\phi_M(b)^{-1}].
\end{aligned}
$$

$J_{L,a}(b)$ 为整数，$C_{L,a}(b)$ 也由 $a$ 为奇数得为整数。Lean 中 $Y_L$ 叫 `yEl`，$C_{L,a}$ 叫 `Eone`，$Q_M$ 叫 `ytEl`。那么 $Y_N$ 的各系数都在 $\mathbb Z_\ell$ 中。若把它们组成的 $\mathbb Z_\ell[\Gamma]$ 元素写成 $z$，则对每个 $r\ge0$，

$$
Q_M\equiv z\pmod{\ell^r\mathbb Z_\ell[\Gamma]}
\quad\text{只要}\quad
m\ge r+v_\ell\!\left(2k\prod_{p\le k+1}p\right)+1 .
\tag{1}
$$

这里 $p$ 遍历素数。源码的 `congr` 给出某个足够大的 $m$ 并统一适用于之后各层，证明选的阈值就是 (1)。

## 升层后有理群环元素相同

令 $D=\ell^m$，那么每个 $t\in G_N$ 的提升的代表恰为 $[t]_N+jN,\ 0\le j<D$。这些数都是模 $M$ 的单位，因为 $M,N$ 有相同素因子。它们的群环基元标号相同。由 Bernoulli 多项式的分布公式，

$$
\sum_{j=0}^{D-1}H_{ND,k}([t]_N+jN)
=\frac{(ND)^{k-1}}k D^{1-k} B_k([t]_N/N)
=H_{N,k}([t]_N).
$$

于是 $\Theta_M=\Theta_N$。前乘的修正因子也是相同的，因为 $\phi_M(a)=\phi(a)$，故 $Y_M=Y_N$。这个等式需要提升的单位集合包含整条纤维。若升层加入新素因子，则改用含 Euler 因子的模数变换公式。[分布公式与升模](%E4%B8%8B%E5%8F%96%E6%95%B4%E7%B3%BB%E6%95%B0%E6%80%8E%E6%A0%B7%E7%BB%99%E5%87%BA%E5%B9%BF%E4%B9%89Bernoulli%E6%95%B0%E7%9A%84%E8%B5%8B%E5%80%BC.md)

## 同一层的逐项同余

置 $P_k=\prod_{p\le k+1}p$ 及 $D_k=2kP_k$。Bernoulli 多项式展开及 $P_kB_j(0)\in\mathbb Z$（$0\le j\le k$）给出

$$
H_{M,k}(x)=\frac{x^k}{kM}-\frac{x^{k-1}}2+\frac{M}{kP_k}w_x,\qquad w_x\in\mathbb Z.
\tag{2}
$$

式 (2) 在 $k=1$ 时第三项为零。该展开和 Bernoulli 分母已在相邻译稿证明。[逐项展开](%E4%B8%8B%E5%8F%96%E6%95%B4%E7%B3%BB%E6%95%B0%E6%80%8E%E6%A0%B7%E7%BB%99%E5%87%BA%E5%B9%BF%E4%B9%89Bernoulli%E6%95%B0%E7%9A%84%E8%B5%8B%E5%80%BC.md)

令 $x=[b]_M,\ y=[a^{-1}b]_M,\ j=J_{M,a}(b)$，所以 $ay=x+Mj$。乘开修正因子，在第二项中将索引乘 $a$，可将 $Y_M$ 写成

$$
Y_M=-\sum_{b\in G_M}
\bigl(H_{M,k}(x)-a^kH_{M,k}(y)\bigr)[\phi_M(b)^{-1}].
$$

对括号用 (2)。首项差为 $(x^k-(x+Mj)^k)/(kM)$。二项式展开的一次项给出 $-jx^{k-1}$，余项属于 $\frac{M}{k}\mathbb Z$。第二项差为 $\frac12(a(x+Mj)^{k-1}-x^{k-1})$，模 $\frac M2\mathbb Z$ 等于 $\frac{a-1}{2}x^{k-1}$。最后 (2) 的余项之差还在 $\frac{M}{kP_k}\mathbb Z$。所以

$$
H_{M,k}(x)-a^kH_{M,k}(y)-x^{k-1}C_{M,a}(b)\in\frac{M}{D_k}\mathbb Z.
\tag{3}
$$

逐项求和仍有同样的误差，即 $Y_M-Q_M\in\frac{M}{D_k}\mathbb Z[\Gamma]$。如果 $m$ 达到 (1)，则 $v_\ell(M)\ge r+v_\ell(D_k)$，于是每个误差系数都在 $\ell^r\mathbb Z_\ell$ 中。取 $r=0$ 首先得到 $Y_N=Y_M$ 的系数都在 $\mathbb Z_\ell$，再取任意 $r$ 就得 (1)。由此在任意被 $\ell^r$ 消去的模上，$Q_M$ 和 $z$ 给同一个算子。

## Lean 对照与证明范围

- [`yLevel`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/YLevel.lean#L76) `yLevel` 第 76 行按约化的纤维使用 Bernoulli 分布公式。[`yNear`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/YNear.lean#L10) `yNear` 第 10 行将同一层的逐项误差合成群环误差。[升层](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/YLevel.lean) · [同一层逼近](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/YNear.lean)
- [`congr`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/NearLevel.lean#L24) `congr` 第 24 行得到整系数的 $\ell$ 进提升和 (1)。[极限同余](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/NearLevel.lean) · [群环系数定义，第 11–47 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/StickelbergerElements/CoefMapSingle.lean) · [逐项同余](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/StickelbergerElements/TwistedBernoulliValueCongrPowMulFirst.lean)

本篇按源码对读。未重新编译或查询传递公理。
