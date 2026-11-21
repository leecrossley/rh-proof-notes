# 下取整系数怎样给出广义Bernoulli数的赋值

**命题（[`zEval`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/ZeNorm.lean#L163)，`UpperTheory.V.ML.zEval`）。** 令 $\ell$ 为奇素数，$O\subseteq\overline{\mathbb Q}_\ell$ 为有限于 $\mathbb Z_\ell$ 的离散赋值环，$f\ge1,\ e\ge1,\ k=e+1$。设 $\psi$ 是模 $f$ 的本原狄利克雷特征，值在 $O$ 中，满足 $\psi(-1)=(-1)^k$。写 $G=G_{\mathbb Q}$，用单位根作用定义 $\psi_G:G\to O^\times$，即 $\psi_G(g)=\psi(t)$，其中 $g$ 在 $\mu_f$ 上取 $t$ 次幂。令 $\alpha=\varepsilon_\ell^{-e}\psi_G^{-1}$，并假定存在 $g\in G$ 使 $\alpha(g)-\varepsilon_\ell(g)$ 为单位。对 $P_k=\prod_{p\le k+1}p$，记

$$
B_{k,\psi}= f^{k-1}\sum_{u=1}^f\psi(u)B_k(u/f),\qquad a=fP_k B_{k,\psi}.
$$

$B_k(X)$ 是通常的 Bernoulli 多项式，$B_1(X)=X-1/2$。给定 $a\in O$ 取上述值及任意非零 $a_0\in O$，则存在 $m\ge1$，令 $F=(f/\ell^{v_\ell(f)})\ell^m$，并可取 $0\le b<F$ 及对每个 $t\in(\mathbb Z/F\mathbb Z)^\times$ 的提升 $\sigma_t\in G$（在 $\mu_F$ 上取 $t$ 次幂）。令

$$
z=\sum_t \theta_b(t)\alpha(\sigma_t)^{-1},\qquad
 \theta_b(t)=\left\lfloor\frac{b[t]}{F}\right\rfloor
                 -\left\lfloor\frac{b[-t]}{F}\right\rfloor .
$$

则 $a_0z\mid\ell^m,\ z\mid a$。另外有如下两项同余。对固定所有 $\mu_F$ 的 $g$，$\alpha(g)\equiv1\bmod\ell^mO$。对在 $\mu_F$ 上取逆的 $g$，$\alpha(g)\equiv-1\bmod\ell^mO$。

这些正是辅助素数长度估计的输入。$z\mid a$ 使最终的长度至多为 $v_O(a)$，而任意 $a_0$ 的条件保证可对所有扭结层使用这一结论。[辅助素数的长度估计](%E9%80%90%E4%B8%AA%E5%8A%A0%E5%85%A5%E8%BE%85%E5%8A%A9%E7%B4%A0%E6%95%B0%E6%80%8E%E6%A0%B7%E6%8A%8A%E5%90%8C%E8%B0%83%E9%95%BF%E5%BA%A6%E5%8E%8B%E5%88%B0%E4%B8%80%E4%B8%AA%E8%B5%8B%E5%80%BC.md)

## 一、把 Bernoulli 多项式的前两项单独留下

写 $D_k=2kP_k$，并记 $H_{F,k}(x)=F^{k-1}B_k(x/F)/k$。对 $0\le j\le k$，$P_k B_j(0)$ 是整数。理由是 $B_0(0)=1,\ B_1(0)=-1/2$，奇数 $j>1$ 时 $B_j(0)=0$。对正偶数 $j$，von Staudt–Clausen 定理说

$$
B_j(0)+\sum_{\substack{p\ {\rm prime}\\p-1\mid j}}\frac1p\in\mathbb Z.
$$

每个这样的 $p$ 都不超过 $j+1\le k+1$，故它的分母被 $P_k$ 清掉。展开 $B_k(X)=\sum_{j=0}^k\binom{k}{j}B_j(0)X^{k-j}$，得到对每个整数 $x\ge0$

$$
H_{F,k}(x)=\frac{x^k}{kF}-\frac{x^{k-1}}2+\frac{2F}{D_k}z_x,
 \qquad z_x\in\mathbb Z.
 \tag{1}
$$

后几项有至少一次 $F$，因为第 $j$ 项清去 $kP_k$ 后含 $F^{j-1}$ 而 $j\ge2$。同一个展开也表明 $fP_k B_{k,\psi}$ 是 $O$ 中的元素。[清分母第 8 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/Primden.lean) · [展开第 8 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/StickelbergerElements/StickelbergerBernoulliCoeffExpansionModDenominat.lean)

现在假定 $b$ 与 $F>1$ 互素。对每个单位 $t\bmod F$，令 $u=[t]$，$y=[bt]$，$j=\lfloor bu/F\rfloor$。有 $bu=y+Fj$，且 $0<u,y<F$。由于 $[-t]=F-u$，后者乘以 $b$ 后的余数是 $F-y$，它的商是 $b-j-1$，所以

$$
\theta_b(t)=2j-(b-1).
 \tag{2}
$$

把 $y=bu-Fj$ 代入二项展开，$y^k=(bu)^k-kFj(bu)^{k-1}\bmod F^2$，而 $y^{k-1}=(bu)^{k-1}\bmod F$。用这两个整数同余和 (1) 展开，得

$$
D_k\!\left[b^{k-1}\theta_b(t)u^{k-1}
       +2\bigl(H_{F,k}(y)-b^k H_{F,k}(u)\bigr)\right]\in F\mathbb Z .
 \tag{3}
$$

具体地，(1) 的首项相减再乘 $2$，留下 $-2j(bu)^{k-1}$，余项乘 $D_k$ 后在 $F\mathbb Z$ 中。其次项同样留下 $(b-1)(bu)^{k-1}$。二者恰好与 (2) 给出的项抵消。这样在系数层面解释了为什么要从两个下取整数相减。

## 二、把系数同余加权求和

设 $\ell^m\mid F$，取任意模 $F$ 的特征 $\chi$（在项目陈述中还要求 $\chi(-1)=(-1)^k$）。设

$$
S_b=\sum_{t\in(\mathbb Z/F\mathbb Z)^\times}
                \theta_b(t)[t]^{k-1}\chi(t),\qquad
 B_{k,\chi}=F^{k-1}\sum_{u=1}^F\chi(u)B_k(u/F).
$$

在 (3) 各项乘 $\chi(bt)$ 并求和。因为 $t\mapsto bt$ 置换单位，$H_{F,k}(y)$ 的和正是 $B_{k,\chi}/k$，而 $H_{F,k}(u)$ 的和是 $\chi(b)B_{k,\chi}/k$。因此对归一化绝对值 $|\ell|_\ell=\ell^{-1}$，有

$$
\left|D_k\left(b^{k-1}\chi(b)S_b
       -2\big(\chi(b)b^k-1\big)\frac{B_{k,\chi}}k\right)\right|_\ell
 \le|\ell^m|_\ell .
 \tag{4}
$$

右边来自 $F$ 的整除性。每个 $\chi(bt)$ 是单位根，模为 $1$，非阿基米德三角不等式让有限求和保持相同误差。这个计算本身也说明为何 (4) 中的奇偶性假设没有进入求和步骤，奇偶性会在下一节保证原 Bernoulli 数非零。[逐项与求和第 10、44、103 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/GenBUnits.lean)

## 三、放大模数会保留所需的绝对值

先说明两条 Bernoulli 数的输入。第一条是 $B_{k,\psi}\ne0$。由于特征值都是代数单位根，可将它们所在的数域嵌入 $\mathbb C$。对本原复特征且 $\psi(-1)=(-1)^k$，源码使用

$$
L(1-k,\psi)=-B_{k,\psi}/k,\qquad
 |L(1-k,\psi)|=
 \frac{2(k-1)! f^{k-1/2}}{(2\pi)^k}|L(k,\psi^{-1})|.
$$

前式是特殊值公式，后式是本原特征的函数方程的这个整数点版本。这里 $k\ge2$，所以右边的 $L$ 值由绝对收敛的 Euler 乘积知非零，再通过嵌入回到原系数域。两条解析公式在本篇作为输入。[特殊值第 7 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/BLprim.lean) · [函数方程第 13 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/FeLFunctionConstMul.lean) · [传到任意特征零域第 25 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/BNzany.lean)

第二条是改模公式。若 $M$ 为 $f$ 的倍数，$\psi^{(M)}$ 在模 $M$ 的单位上取 $\psi$ 的值，其他点为零，则

$$
B_{k,\psi^{(M)}}=B_{k,\psi}\prod_{p\mid M}\bigl(1-\psi(p)p^{k-1}\bigr).
 \tag{5}
$$

证明先从 $f$ 改到 $fp$。暂用周期为 $f$ 的值 $\psi(u)$ 作整段求和。Bernoulli 多项式倍乘公式
$\sum_{j=0}^{p-1}B_k((x+j)/p)=p^{1-k}B_k(x)$
使这一整段仍等于 $B_{k,\psi}$。倍乘公式可由 $t e^{xt}/(e^t-1)$ 的生成函数和有限几何级数直接比较系数得到。再从整段求和扣除 $p\mid u$ 的项。写 $u=pv$，这些项恰给 $\psi(p)p^{k-1}B_{k,\psi}$。若 $p\mid f$，这一步已经是零。逐个加入素因子即得 (5)，重复出现的素数只在第一次加入时产生新因子。[添一个素因子第 45 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/DirichletCharacterLevelRaising.lean) · [合并全部素因子第 55 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/GeneralizedBernoulliChangeLevel.lean)

取 $F=(f/\ell^{v_\ell(f)})\ell^m$ 且 $m\ge v_\ell(f)$，于是 $f\mid F$。对 $\chi=\psi^{(F)}$，(5) 里的 $p\mid f$ 给因子 $1$。唯一可能新出现的素数是 $\ell$，其因子也有 $\ell$ 进绝对值 $1$，因为 $k-1\ge1$，$|\psi(\ell)\ell^{k-1}|_\ell<1$。故

$$
|B_{k,\chi}/k|_\ell=|B_{k,\psi}/k|_\ell>0 .
 \tag{6}
$$

## 四、用一个单位把同余变成精确的赋值

选择 $m\ge\max(1,v_\ell(f))$ 足够大，使

$$
|\ell^m|_\ell< |a_0|_\ell\,|D_k|_\ell\,|B_{k,\psi}/k|_\ell.
 \tag{7}
$$

右边为正，且 $|a_0|_\ell\le1,\ |D_k|_\ell\le1$。用命题中使 $\alpha(g)-\varepsilon_\ell(g)$ 为单位的 $g$，取它在 $\mu_F$ 上的指数 $b$ 的标准代表元，故 $(b,F)=1$。分圆特征模 $\ell^m$ 等于 $b$，而 $\psi_G(g)=\chi(b)$。乘以单位 $-\alpha(g)^{-1}$ 后，单位条件变为 $\varepsilon_\ell(g)\alpha(g)^{-1}-1$ 是单位。它模 $\ell^mO$ 等于 $\chi(b)b^k-1$，所以后者也是单位。

因 $\ell$ 为奇数，$2$ 是单位。式 (4)、(6)、(7) 说明 $b^{k-1}\chi(b)S_b$ 与 $2(\chi(b)b^k-1)B_{k,\chi}/k$ 的距离严格小于后者的模。因此两者同模，而 $b^{k-1}\chi(b)$ 是单位，得到

$$
|S_b|_\ell=|B_{k,\psi}/k|_\ell.
$$

对每个 $t$，提升 $\sigma_t$ 的作用还给 $\alpha(\sigma_t)^{-1}\equiv[t]^{k-1}\chi(t)\bmod\ell^mO$。所以 $|z-S_b|_\ell\le|\ell^m|_\ell<|S_b|_\ell$，得到精确等式

$$
|z|_\ell=|B_{k,\psi}/k|_\ell .
 \tag{8}
$$

这一步用的是严格小于。仅有非严格的误差界，无法排除加法中的抵消。

由 (7)、(8) 得 $|\ell^m|_\ell<|a_0z|_\ell$。又因 $a=fP_kB_{k,\psi}$ 而 $f,P_k,k$ 是整数，有 $|a|_\ell\le|B_{k,\psi}|_\ell\le|z|_\ell$。在 $O$ 中，绝对值越小，离散赋值越大，所以分别得 $a_0z\mid\ell^m$ 和 $z\mid a$。最后，若 $g$ 固定 $\mu_F$，$\varepsilon_\ell(g)\equiv1\bmod\ell^m$ 且 $\psi_G(g)=1$。若 $g$ 在 $\mu_F$ 上取逆，$\varepsilon_\ell(g)\equiv-1\bmod\ell^m$，$\psi_G(g)=(-1)^k$，而 $e+k$ 为奇数。代入 $\alpha=\varepsilon_\ell^{-e}\psi_G^{-1}$，即得命题中两项同余。

## Lean 对照

- [`zCong`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/GenBUnits.lean#L103) `zCong` 将 (3) 汇总为 (4)。`b_primden` 清 Bernoulli 数的分母，`stickelbergerBernoulliCoeff_expansion_mod_denominator` 保留前两项。[同余第 103 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/GenBUnits.lean) · [Bernoulli 系数展开](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/StickelbergerElements/StickelbergerBernoulliCoeffExpansionModDenominat.lean)
- [`zEval`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/ZeNorm.lean#L163) `zEval` 中的 `ze_gen` 保持模数放大时的绝对值，`ze_an` 给严格误差下的绝对值相等，`ze_dat` 给最后两项同余。`normO` 把归一化绝对值与 $O$ 的离散赋值对应。[合成第 163 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/ZeNorm.lean) · [归一化第 10 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/SelmerTransport/NormO.lean)

本篇按源码对读。正文展开了有限求和和 $\ell$ 进赋值的主要推理。Bernoulli 分母、Dirichlet $L$ 特殊值与函数方程是明写的输入。所列定理的内核重放及传递公理状态未查。
