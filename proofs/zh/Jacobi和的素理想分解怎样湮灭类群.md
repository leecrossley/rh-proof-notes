# Jacobi 和的素理想分解怎样湮灭类群

**命题（[`coef`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/StickelbergerTheorem/ImportsAlt.lean#L9)）。** 对任意正整数 $M$，设 $K/\mathbb Q$ 由一个本原 $M$ 次单位根 $\zeta$ 生成，$G=(\mathbb Z/M\mathbb Z)^\times$，记 $\sigma_t(\zeta)=\zeta^t$。用加法记 $C=\mathrm{Cl}(\mathcal O_K)$，以 $\langle u\rangle_M$ 表示 $u\bmod M$ 的最小非负代表。对每个 $x\in C$，有下列两个结论。

1. 对每个 $k\in\mathbb N$，有 $\sum_{t\in G}\lfloor k\langle t\rangle_M/M\rfloor\,\sigma_t^{-1}x=0$。
2. 给定整数值函数 $a,b:G\to\mathbb Z$。若 $Mb(t)=\sum_{s\in G}a(s)\langle st\rangle_M$ 对所有 $t$ 成立，则 $\sum_{t\in G}b(t)\sigma_t^{-1}x=0$。

第二项是[分圆塔类群界](%E5%88%86%E5%9C%86%E5%A1%94%E7%9A%84%E7%B1%BB%E7%BE%A4%E7%A7%A9%E6%80%8E%E6%A0%B7%E5%BE%97%E5%88%B0%E7%BB%9F%E4%B8%80%E4%B8%8A%E7%95%8C.md)中用的 Stickelberger 湮灭形式。它从第一项推出，第一项的系数则由加法进位给出。

## 一、在同一个素数上计算所有共轭的整除性

先给定 $p\nmid M$ 及 $K$ 中一个素理想 $\mathfrak p\mid p$，要求 $\mathcal O_K/\mathfrak p=\mathbb F_p$。令 $\pi:\mathcal O_K\to\mathbb F_p$ 为降约。因为 $p\nmid M$，降约在 $M$ 次单位根上单射。若一个这样的根 $\eta\ne1$ 化为 $1$，则 $1+\cdots+\eta^{M-1}=0$ 降约成 $M=0$，矛盾。故 $M\mid p-1$。置 $d=(p-1)/M$，定义特征 $\chi:\mathbb F_p^\times\to\mu_M\subset K$，使 $\pi(\chi(x))=x^d$，并令 $\chi(0)=0$。每个 $x^d$ 都是一个 $M$ 次单位根，且都可唯一提升，故 $\chi$ 可乘且有阶 $M$。

对每个 $t\in G$，写 $\mathfrak p_t=\sigma_t^{-1}\mathfrak p$，它是 $\pi\circ\sigma_t$ 的核。不同 $t$ 给出不同的素理想。若两个核相同，两张送到 $\mathbb F_p$ 的满射同因子化在一个大小为 $p$ 的剩余域，且该剩余域到 $\mathbb F_p$ 的同构唯一，故两张映射相同。对 $\zeta$ 求值，再用 $\pi(\zeta)$ 的阶数，便得两个 $t$ 相同。各 $\mathfrak p_t$ 都在 $p$ 上方，且范数为 $p$，所以由次数 $[K:\mathbb Q]=|G|$ 或取理想范数，得到

$$
(p)=\prod_{t\in G}\mathfrak p_t .
 \tag{1}
$$

取 $a,b\in\mathbb Z/M\mathbb Z$ 且 $a,b,a+b\ne0$。构造代数整数

$$
J_{a,b}=\sum_{x\in\mathbb F_p}\chi(x)^{\langle a\rangle_M}
                                  \chi(1-x)^{\langle b\rangle_M}.
$$

它整除 $p$。为看出这一点，在一个复嵌入下令 $\alpha=\chi^{\langle a\rangle_M}$，$\beta=\chi^{\langle b\rangle_M}$。三者 $\alpha,\beta,\alpha\beta$ 都非平凡。定义 $\tau(\alpha)=\sum_x\alpha(x)e^{2\pi ix/p}$，特征在 $0$ 处补零。直接展开 $|\tau(\alpha)|^2$ 并写 $x=ty$（$y\ne0$），内和 $\sum_{y\ne0}e^{2\pi i(t-1)y/p}$ 等于 $p-1$ 若 $t=1$，否则为 $-1$。用 $\sum_t\alpha(t)=0$ 得 $|\tau(\alpha)|^2=p$。另外按 $x+y=w$ 重排 $\tau(\alpha)\tau(\beta)$。$w=0$ 的和因 $\alpha\beta$ 非平凡而为零，$w\ne0$ 时将 $x,y$ 同除以 $w$，得到

$$
\tau(\alpha)\tau(\beta)=J_{a,b}\tau(\alpha\beta).
$$

所以 $J_{a,b}\overline{J_{a,b}}=p$。共轭的 Jacobi 和仍为 $\mathcal O_K$ 中的元素，因此得到整除。

在 $\mathfrak p_t$ 处降约 $J_{a,b}$，由 $\sigma_t$ 在单位根上的作用，得到

$$
\sum_{x\in\mathbb F_p}x^i(1-x)^j,\qquad
 i=d\langle at\rangle_M,\quad j=d\langle bt\rangle_M .
$$

这两个指数均正且小于 $p-1$。将 $(1-x)^j$ 二项式展开。对 $1\le r<2(p-1)$，幂和 $\sum_x x^r$ 只有 $r=p-1$ 时非零，其值为 $-1$，可从 $\mathbb F_p^\times$ 的循环性得出。因此上面的和只有 $i+j\ge p-1$ 时才可能非零，这时恰有一项，系数为 $-(-1)^{p-1-i}\binom j{p-1-i}$。由于 $0\le p-1-i\le j<p$，该系数在 $\mathbb F_p$ 中非零。故

$$
J_{a,b}\in\mathfrak p_t
 \quad\Longleftrightarrow\quad
 \langle at\rangle_M+\langle bt\rangle_M<M.
 \tag{2}
$$

这是没有进位的条件。

## 二、把进位变成一个类群关系

令 $\mathrm{car}_M(u,v)=1$ 若 $\langle u\rangle_M+\langle v\rangle_M\ge M$，否则为 $0$。因 $J_{a,b}\mid p$ 且 (1) 无重因子，(2) 表明主理想 $(J_{a,b})$ 是所有不进位的 $\mathfrak p_t$ 的乘积。再用 (1) 除以它，所有进位的 $\mathfrak p_t$ 的乘积也为主理想。如果 $a=0$ 或 $b=0$，没有进位，结论也成立。如果 $a,b\ne0$ 但 $a+b=0$，则各 $t$ 都进位，直接用 (1)。所以

$$
\sum_{t\in G}\mathrm{car}_M(at,bt)\,\sigma_t^{-1}[\mathfrak p]=0
 \quad \text{对任意 }a,b\bmod M.
 \tag{3}
$$

要用于任意 $x\in C$，需取一个 $p\nmid M$ 的一次素理想代表 $x$。源码 `degOne` 所用的类域论和 Chebotarev 特例如下。对任意数域 $F$ 的有限 Galois 扩张 $E/F$、任意共轭类 $\mathcal C\subseteq\mathrm{Gal}(E/F)$、任意有限排除集，存在排除集外一个 $F$ 的有限素处，其剩余域在有理素数上次数为 $1$，在 $E/F$ 中不分歧，Frobenius 共轭类为 $\mathcal C$。应用到 $K$ 的 Hilbert 类域，由 Artin 同构，Frobenius 可以指定为 $x$ 的像。去除 $M$ 的素因子上方的有限多个素处，便得到这样的 $\mathfrak p$。因此 (3) 中可把 $[\mathfrak p]$ 换成任意 $x$。

## 三、将进位累加为下取整

对每个 $t\in G$，商与余数相加有恒等式

$$
\left\lfloor\frac{(k+1)\langle t\rangle_M}{M}\right\rfloor
 =\left\lfloor\frac{k\langle t\rangle_M}{M}\right\rfloor+\mathrm{car}_M(kt,t).
$$

从 $k=0$ 起归纳，每步用 (3)，即得命题第一项。

为证第二项，取 $M>1$，$M=1$ 时 $\langle st\rangle_M=0$ 直接结束。设

$$
B=\sum_s a(s)\langle s\rangle_M,\qquad
 F(t)=\sum_s a(s)\left\lfloor\frac{\langle s\rangle_M\langle t\rangle_M}{M}\right\rfloor .
$$

将每个 $\langle st\rangle_M$ 换成乘积减去 $M$ 倍的下取整，假设给出 $M(b(t)+F(t))=B\langle t\rangle_M$。取 $t=1$ 得 $M\mid B$，于是 $b(t)=(B/M)\langle t\rangle_M-F(t)$。右侧每个下取整项都由第一项湮灭类群。第一项取 $k=M$ 还给出 $\langle t\rangle_M$ 的湮灭，遂得第二项。

## Lean 对照

- [`redRoot`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/StickelbergerTheorem/RedRoot.lean#L6)、[`teich`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/StickelbergerTheorem/ImportsTer.lean#L6) 给单位根降约及特征提升，[`splitInj`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/StickelbergerTheorem/SplitInj.lean#L7)、[`splitProd`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/StickelbergerTheorem/SplitProd.lean#L8) 给 (1)。[`jacDvd`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/StickelbergerTheorem/JacDvd.lean#L6) `jacDvd` 通过 Gauss 和恒等式得到 $J_{a,b}\mid p$。[`ffsum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/StickelbergerTheorem/FfsumPow.lean#L42)、[`jacobi`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/StickelbergerTheorem/Jacobi.lean#L18) 给有限域幂和以及 (2)。[单位根降约第 6 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/StickelbergerTheorem/RedRoot.lean) · [Jacobi 和第 18 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/StickelbergerTheorem/Jacobi.lean) · [有限域幂和第 42 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/StickelbergerTheorem/FfsumPow.lean)
- [`carryPrime`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/StickelbergerTheorem/CarryPrime.lean#L10) `carryPrime` 给 (3)，[`degOne`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/StickelbergerTheorem/DegOne.lean#L8) `degOne` 用 Artin 与 Chebotarev 取代表，[`carryAll`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/StickelbergerTheorem/CarryAll.lean#L9) `carryAll` 传给任意类。[进位第 10 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/StickelbergerTheorem/CarryPrime.lean) · [取代表第 8 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/StickelbergerTheorem/DegOne.lean) · [Chebotarev 的一次素处版本第 17 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ChebotarevDegreeOne.lean)
- [`combFloor`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/StickelbergerTheorem/CombFloor.lean#L22)、[`comb`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/StickelbergerTheorem/ZpowSumEqProd.lean#L6) `combFloor`、`comb` 分别对应第三节的累加及系数整除，[`coef`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/StickelbergerTheorem/ImportsAlt.lean#L9) `coef` 合并两项。[下取整第 22 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/StickelbergerTheorem/CombFloor.lean) · [整系数第 6 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/StickelbergerTheorem/ZpowSumEqProd.lean) · [合成第 9 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/StickelbergerTheorem/ImportsAlt.lean)

本篇按源码对读，普通类域论及一次素处的 Chebotarev 结论是第二节的标准输入。所列声明的内核重放及传递公理状态未查。
