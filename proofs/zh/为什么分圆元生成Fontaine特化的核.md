# 为什么分圆元生成 Fontaine 特化的核

## 命题

设 $\ell$ 是素数，$C=\mathbb C_\ell$ 是 $\mathbb Q_\ell$ 的代数闭包的完备化，$A=W(\mathcal O_{C^\flat})$ 是倾斜整数环的 Witt 向量环。对 $x\in\mathcal O_{C^\flat}$，记 $x^\sharp\in\mathcal O_C$ 为去倾斜的乘法映射，$[x]$ 为其 Teichmüller 提升。Fontaine 特化 $\theta:A\to\mathcal O_C$ 把 $[x]$ 送到 $x^\sharp$。取一套相容的本原分圆根 $\zeta_{\ell^n}$，令 $\varepsilon=(1,\zeta_\ell,\zeta_{\ell^2},\ldots)$ 是相应倾斜元。写 $e=\varepsilon^{1/\ell}$，令

$$
\xi=1+[e]+\cdots+[e]^{\ell-1}.
$$

则 $\theta(a)=0$ 当且仅当 $\xi\mid a$ 在 $A$ 中成立。下文使用倾斜的基本结构：$\mathcal O_{C^\flat}$ 是特征 $\ell$ 的完美赋值环，赋值可由 $\sharp$ 读出，且 $A$ 是 $\ell$-进分离完备的，$A/\ell A=\mathcal O_{C^\flat}$。[FontaineThetaEqZeroIffFontaineXiElementDvd.lean:19](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/FontaineThetaEqZeroIffFontaineXiElementDvd.lean#L19) · [AinfFacts.lean:20](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/DualLattices/AinfFacts.lean#L20)

倾斜作为赋值域的描述和 $\sharp$ 的极限公式见 Scholze 的引理 3.4。同一个分圆生成元可在 Bhatt、Morrow、Scholze 的例 3.16 核对。[Scholze, Perfectoid Spaces](https://arxiv.org/pdf/1111.4914#page=15) · [Bhatt–Morrow–Scholze, Integral $p$-adic Hodge theory](https://www.math.uni-bonn.de/people/scholze/integralpadicHodge.pdf#page=25)

## 证明

先用任意相容的 $\ell$ 次根取得 $\lambda\in\mathcal O_{C^\flat}$ 使 $\lambda^\sharp=\ell$。令 $q=\ell-[\lambda]$，显然 $\theta(q)=0$。若 $\theta(a)=0$，记 $\bar a\in\mathcal O_{C^\flat}$ 为 Witt 第零分量。可写 $a=[\bar a]+\ell a_1$，故 $\bar a^\sharp\in\ell\mathcal O_C$。赋值 $v$ 归一化为 $v(\ell)=1$，并由 $v(x)=v(x^\sharp)$ 传到倾斜上。于是 $v(\bar a)\ge1=v(\lambda)$，所以 $\bar a$ 在倾斜整数环中被 $\lambda$ 整除。即 $a$ 模 $\ell$ 被 $q$ 的像 $-\lambda$ 整除。提升这一次的商，得到

$$
a=q b_0+\ell a',\qquad \theta(a')=0.
$$

后一式由 $\theta(q)=0$ 及 $\mathcal O_C$ 无 $\ell$-挠得到。重复求商得到 $a-q\sum_{j<n}\ell^j b_j\in\ell^n A$。求和在 $A$ 中收敛，由分离性得 $a=q\sum_{j\ge0}\ell^j b_j$。因此 $q$ 已是 $\ker\theta$ 的生成元。[DvdOfCoeffZero.lean:201](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/DualLattices/DvdOfCoeffZero.lean#L201)

现在因为 $\theta([e])=\zeta_\ell$，等比和给 $\theta(\xi)=0$。于是 $\xi=qu$ 对某个 $u\in A$ 成立。模 $\ell$ 时，在特征 $\ell$ 的环中有

$$
\overline{\xi}=(e-1)^{\ell-1},\qquad
\bar q=-\lambda.
$$

为证明 $u$ 是单位，只须证明 $v(e-1)=1/(\ell-1)$。

为此，若 $\zeta$ 的阶恰为 $\ell^j$（$j\ge1$），则它的剩余为 $1$，因为在特征 $\ell$ 的剩余域中 $X^{\ell^j}-1=(X-1)^{\ell^j}$。对每个与 $\ell$ 互素的 $a>0$，$(\zeta^a-1)/(\zeta-1)$ 是 $1+\zeta+\cdots+\zeta^{a-1}$，剩余为 $a\bmod\ell$，因此是单位。所有本原 $\ell^j$ 次根到 $1$ 的距离相同。又

$$
\Phi_{\ell^j}(1)=\prod_{\substack{1\le a\le\ell^j\\ \ell\nmid a}}(1-\zeta^a)=\ell,
$$

所以 $v(\zeta-1)=1/(\ell^{j-1}(\ell-1))$。倾斜的差 $e-1$ 的 $\sharp$ 值是 $(\zeta_{\ell^{n+1}}-1)^{\ell^n}$ 的极限；每项的赋值都是 $1/(\ell-1)$。因为绝对值连续，极限仍有这个赋值。这证明 $v(e-1)=1/(\ell-1)$。

因此 $v(\bar u)=v(\overline{\xi})-v(\lambda)=0$。$\bar u$ 是倾斜整数环中的单位，故 $u$ 在 $A$ 中也是单位。具体可先提升一个模 $\ell$ 的逆元，再用 $\ell$-进几何级数改成真正逆元。所以 $(\xi)=(q)=\ker\theta$，命题得证。

## Lean 对照

- `kerTheta` 先用可去倾斜为 $\ell$ 的元素造出生成元 $\ell-[\lambda]$。`xiNu` 计算 $e-1$ 的赋值，比较两个生成元模 $\ell$ 的坐标，并由单位判据换到分圆生成元。[DvdOfCoeffZero.lean:201](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/DualLattices/DvdOfCoeffZero.lean#L201) · [ValUntiltESubOne.lean:119](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/DualLattices/ValUntiltESubOne.lean#L119) · [同文件:202](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/DualLattices/ValUntiltESubOne.lean#L202)
- `ker_theta_eq_span_xi`、`theta_eq_zero_iff_xi_dvd` 将这一结论用于工程的晶体比较。[FontaineThetaEqZeroIffFontaineXiElementDvd.lean:19](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/FontaineThetaEqZeroIffFontaineXiElementDvd.lean#L19) · [分幂包络与统一分母](%E4%B8%BA%E4%BB%80%E4%B9%88%E6%99%B6%E4%BD%93%E6%95%B4%E7%8E%AF%E5%9C%A8%E6%AF%8F%E5%B1%82deRham%E6%88%AA%E6%96%AD%E9%83%BD%E6%9C%89%E7%BB%9F%E4%B8%80%E5%88%86%E6%AF%8D.md)

状态为源码对读。另行未重新编译。正文以倾斜赋值的基本性质简写逐坐标的整除验证。
