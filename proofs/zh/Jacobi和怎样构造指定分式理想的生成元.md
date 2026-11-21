# Jacobi 和怎样构造指定分式理想的生成元

辅助 Kummer 特征所用的数域元素 $X_d$ 必须有指定的素处赋值。本篇证明这样的元素存在，并说明从一个 $\mathbb F_p$ 上的 Jacobi 和怎样读出全部赋值。

## 命题

给定整数 $N\ge1$、$0\le b<N$，令 $K_N=\mathbb Q(\mu_N)$，整数环为 $\mathcal O_N$。记 $G_N=(\mathbb Z/N\mathbb Z)^\times$，$\sigma_t$ 为在 $\mu_N$ 上取 $t$ 次幂的自同构，$c=\sigma_{-1}$ 为复共轭。对模 $N$ 的类 $t$，以 $[t]_N$ 表示它在 $[0,N-1]$ 的代表。定义

$$
\theta_{N,b}(t)=
\left\lfloor\frac{b[t]_N}{N}\right\rfloor-
\left\lfloor\frac{b[-t]_N}{N}\right\rfloor,\qquad
\mathfrak a_t=\sigma_t^{-1}(\mathfrak a).
$$

对任意非零整理想 $\mathfrak a\subseteq \mathcal O_N$，存在 $X\in K_N^\times$ 使

$$
Xc(X)=1,\qquad (X)=\prod_{t\in G_N}\mathfrak a_t^{\,\theta_{N,b}(t)}.
\tag{1}
$$

这里 $(X)=X\mathcal O_N$ 是主分式理想，允许右端有负指数。Lean 用 $\texttt{IsX}$ 记录 (1)。对给定 $\mathfrak a$，任意两个这样的 $X$ 相差一个阶整除 $2N$ 的单位根。

## 先在一次素理想上构造

令 $\mathfrak p$ 是 $\mathcal O_N$ 的素理想，其剩余域为 $\mathbb F_p$，且 $p\nmid N$。设 $\pi:\mathcal O_N\to\mathbb F_p$ 为约化。单位根在约化下保持阶，因此 $\mu_N$ 同构到 $\mathbb F_p^\times$ 中的 $N$ 阶子群。令 $D=(p-1)/N$。对 $x\in\mathbb F_p^\times$，定义 $\chi(x)\in\mu_N$ 为 $x^D$ 的唯一提升，并置 $\chi(0)=0$。这是一个阶恰为 $N$ 的乘法特征。分圆域在 $p\nmid N$ 时不分歧，素处的 Frobenius 是在 $\mu_N$ 上取 $p$ 次幂。因 $p\equiv1\bmod N$，$p$ 完全分裂为互不相同的 $\mathfrak p_t=\sigma_t^{-1}\mathfrak p$，$t\in G_N$。

对 $1\le j<b$，定义 Jacobi 和

$$
J_j=\sum_{x\in\mathbb F_p}\chi(x)\chi(1-x)^j\in\mathcal O_N.
$$

上游的单个 Jacobi 和计算在[Stickelberger 湮灭译稿第一节](Jacobi%E5%92%8C%E7%9A%84%E7%B4%A0%E7%90%86%E6%83%B3%E5%88%86%E8%A7%A3%E6%80%8E%E6%A0%B7%E6%B9%AE%E7%81%AD%E7%B1%BB%E7%BE%A4.md)已展开。它说，对所有 $a_1,a_2\in\mathbb Z/N\mathbb Z$ 且 $a_1,a_2,a_1+a_2\ne0$，令 $J_{a_1,a_2}=\sum_x\chi(x)^{[a_1]_N}\chi(1-x)^{[a_2]_N}$。则 $J_{a_1,a_2}c(J_{a_1,a_2})=p$，而对每个 $t\in G_N$，有 $J_{a_1,a_2}\in\mathfrak p_t$ 当且仅当 $[a_1t]_N+[a_2t]_N<N$。前一式由三个 Gauss 和的绝对值给出，后一式将 $J_{a_1,a_2}$ 约化为 $\sum_x x^{D[a_1t]_N}(1-x)^{D[a_2t]_N}$，二项式展开中恰在两指数之和达到 $p-1$ 时出现一个非零项。

取 $a_1=1,a_2=j$，此时 $1\le j<b<N$，故三项均非零。从 $J_j\mid p$ 以及 $p$ 不分歧，$J_j$ 在各 $\mathfrak p_t$ 的赋值恰为 $0$ 或 $1$。把进位条件改写为两个下取整之差，则

$$
v_{\mathfrak p_t}(J_j)=
1-\left(\left\lfloor\frac{(j+1)[t]_N}{N}\right\rfloor-
          \left\lfloor\frac{j[t]_N}{N}\right\rfloor\right).
\tag{2}
$$

令 $J=\prod_{1\le j<b}J_j$。若 $b=0$ 或 $b=1$，则 $J=1$ 且 $\theta_{N,b}=0$。若 $b\ge2$，对 (2) 求和并对消两项下取整，得到 $v_{\mathfrak p_t}(J)=b-1-\lfloor b[t]_N/N\rfloor$。所以取 $X_{\mathfrak p}=c(J)/J$，其在 $\mathfrak p_t$ 的赋值恰为 $\theta_{N,b}(t)$，在 $p$ 以外的赋值为零。由于 $c^2=1$，它满足 $X_{\mathfrak p}c(X_{\mathfrak p})=1$。至此证明一次素理想的情形。

## 从一次素理想到任意理想

用到的一次素理想供给如下。对任意数域 $K$、任意理想类 $C$ 和任意有限个要避开的非零素理想，都存在一个避开它们、属于 $C$、剩余域为 $\mathbb F_p$ 的非零素理想。Lean 的 $\texttt{degOne}$ 调用一次素处版 Chebotarev，将其应用到 Hilbert 类域。按算术 Artin 同构，理想类 $C$ 是指定的 Frobenius，故 Chebotarev 选出的素理想有理想类 $C$。[一次素理想供给，第 8 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/StickelbergerTheorem/DegOne.lean)

给定 $\mathfrak a\ne0$，取 $\mathfrak p$ 属于 $[\mathfrak a]^{-1}$，避开 $N$ 上方的素理想，使 $\mathfrak a\mathfrak p=(y)$，其中 $0\ne y\in\mathcal O_N$。对任意这样的 $y$，定义

$$
A_{N,b}(y)=\prod_{t\in G_N}\sigma_t^{-1}(y)^{\theta_{N,b}(t)}.
\tag{3}
$$

各因子生成对应的 $(y)_t$，于是 $A_{N,b}(y)$ 满足 $\mathfrak a\mathfrak p$ 版本的理想条件。复共轭把 $t$ 换成 $-t$，而 $\theta_{N,b}(-t)=-\theta_{N,b}(t)$，故 $c(A_{N,b}(y))=A_{N,b}(y)^{-1}$。因此取 $X=A_{N,b}(y)/X_{\mathfrak p}$，相除即得 (1)。

## 生成元之间的差

若 $X_1,X_2$ 都满足 (1)，则 $u=X_2/X_1$ 是整数环单位，且 $uc(u)=1$。在每个复嵌入下，$c$ 都对应复共轭，所以所有共轭的 $|u|$ 都为 $1$。对每个 $n\ge1$，$u^n$ 的最小多项式次数有界，根的模为 $1$，故整数系数也一致有界。只有有限多个可能的多项式及其根，所以两个正次幂相等。这证明 $u$ 是单位根。若 $u$ 的阶为 $h$，则 $K_N$ 包含 $\mu_h$，因而包含 $\mu_{\mathrm{lcm}(N,h)}$。分圆域的次数公式迫使 $\varphi(\mathrm{lcm}(N,h))=\varphi(N)$。在 $N$ 的倍数中，增加已有素因子的指数或加入新奇素数都会增大 $\varphi$，唯一可能的变化是 $N$ 为奇数时乘 $2$。所以 $h\mid2N$。

## Lean 对照与核验状态

- [`xJac`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/XJacPowNe.lean#L130) $\texttt{xJac}$ 第 130 行给出 $c(J)/J$。同文件中 $\texttt{xJac\_one}$ 第 33 行给出单个 Jacobi 和整除 $p$ 及 (2) 的进位条件。$\texttt{jacDvd}$ 是整除的单独证明，共用的 Gauss 和推导见已译的 Stickelberger 湮灭证明。[Jacobi 和与赋值](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/XJacPowNe.lean) · [整除输入](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/StickelbergerTheorem/JacDvd.lean)
- [`xMul`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/XMulConjIMul.lean#L57) $\texttt{xMul}$ 第 57 行包括主理想公式 (3) 及乘除规则。[`xEx`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/XEx.lean#L12) $\texttt{xEx}$ 第 12 行用一次素理想将其降到任意非零理想。[`xUniq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/XUniqConj.lean#L41) $\texttt{xUniq}$ 第 41 行给出单位根的唯一性界。[主理想](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/XMulConjIMul.lean) · [存在](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/XEx.lean) · [唯一性](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/XUniqConj.lean)

以上声明为源码对读。本文把 Hilbert 类域的 Artin 同构和一次素处版 Chebotarev 作为经典输入，未作单项内核重放或传递公理查询。
