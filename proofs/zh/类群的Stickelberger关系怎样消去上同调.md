# 类群的 Stickelberger 关系怎样消去上同调

项目需要一个群环元素消去一阶上同调类。这一论证先到高一些的分圆层，那里可以用类群的整数消去关系，再把结果传回原来的上同调。过渡损失一个 Euler 函数因子。

## 命题

令 $N\ge1$、$K_N=\mathbb Q(\mu_N)$，设数域 $E\subseteq K_N$。给定素数 $\ell\mid N$、$e\ge1$、与 $N$ 互素的正奇整数 $a$。若 $\ell=2$，另假设 $E\supseteq\mu_4$。记 $\Gamma=\operatorname{Gal}(E/\mathbb Q)$、$W=\mathbb Q_\ell/\mathbb Z_\ell$、$S=\{v:v\mid\ell\}$。取任意由 $E$ 的 $S$ 和其绝对素处提升组成的局部模型，令 $\Sha(E,e)$ 为 $H^1(G_{E,S},W(-e))$ 到各 $v\in S$ 的局部限制的核。这里 $W(-e)$ 的作用为分圆特征 $\varepsilon_\ell^{-e}$。

记 $\rho:(\mathbb Z/N\mathbb Z)^\times\to\Gamma$ 为分圆自同构限制到 $E$，$\phi(b)=\rho(b)^{-1}$。令 $z\in\mathbb Z_\ell[\Gamma]$ 是

$$
Y=\left(1-a^{e+1}[\phi(a)^{-1}]\right)
 \left(-\sum_{b\in(\mathbb Z/N\mathbb Z)^\times}
\frac{N^e}{e+1}B_{e+1}([b]_N/N)[\phi(b)^{-1}]\right)
\tag{1}
$$

的逐系数 $\ell$ 进整数提升。方括号 $[b]_N$ 为最小非负代表，$[g]$ 为群环基元。这个提升存在，见高阶 Stickelberger 元素的同余。则对每个 $x\in\Sha(E,e)$，

$$
z\cdot(\varphi(N)x)=0 .
\tag{2}
$$

这里 $\varphi$ 是 Euler 函数。群环的作用来自 $E/\mathbb Q$ 的 Galois 群对扭结上同调的共轭作用。[整系数提升](%E9%AB%98%E9%98%B6Stickelberger%E5%85%83%E7%B4%A0%E6%80%8E%E6%A0%B7%E7%94%B1%E6%95%B4%E6%95%B0%E7%B3%BB%E6%95%B0%E9%80%BC%E8%BF%91.md)

## 类群上的整数关系

给定任意正整数 $M$ 和与 $M$ 互素的正奇数 $a$。对模 $M$ 的单位 $b$，设

$$
J(b)=\frac{a[a^{-1}b]_M-[b]_M}{M},\qquad C(b)=\frac{a-1}{2}-J(b).
$$

对 $K_M$ 的任意理想类 $A$，用加法写类群，有

$$
\sum_{b\in(\mathbb Z/M\mathbb Z)^\times} C(b)\,\sigma_b^{-1} A=0 .
\tag{3}
$$

为证这一式，应用已译的 Stickelberger 湮灭关系：若整数函数 $B(b)$ 满足 $MB(b)=\sum_s A_s[sb]_M$，其中 $A_s\in\mathbb Z$ 且 $s$ 遍历单位，则 $\sum_bB(b)\sigma_b^{-1}$ 消去类群。这里取 $B=J$，用两项 $s=a^{-1},1$ 及系数 $a,-1$，就得到 $J$ 的作用为零。常数项对应类群的范数算子 $\sum_b\sigma_b^{-1}$。任取分式理想代表，所有共轭理想的乘积是其到 $\mathbb Q$ 的理想范数再延拓，故为主理想。两项合起来证明 (3)。[Stickelberger 湮灭关系的完整证明](Jacobi%E5%92%8C%E7%9A%84%E7%B4%A0%E7%90%86%E6%83%B3%E5%88%86%E8%A7%A3%E6%80%8E%E6%A0%B7%E6%B9%AE%E7%81%AD%E7%B1%BB%E7%BE%A4.md)

若 $M>2$，一个从 $G_{K_M}$ 到离散加法群的连续同态 $F$，如在所有有限惯性群上为零，就可以写成 $F=\lambda\circ\mathrm{Art}$。这里 $\mathrm{Art}:G_{K_M}\twoheadrightarrow\mathrm{Cl}(\mathcal O_{K_M})$ 是先限制到 Hilbert 类域，再用算术 Artin 同构的逆，$\lambda$ 是类群上的群同态。用的是 $K_M$ 全虚，故没有额外的实处条件。Artin 对共轭的相容性可在 Frobenius 上看出。对全局自同构 $\sigma_b$ 的任意绝对提升 $\widetilde\sigma_b$，$\mathrm{Art}(\widetilde\sigma_b^{-1}u\widetilde\sigma_b)=\sigma_b^{-1}\mathrm{Art}(u)$，因为它把每个素理想的算术 Frobenius 送到共轭素理想的 Frobenius。因此 (3) 给出

$$
\sum_{b\in(\mathbb Z/M\mathbb Z)^\times} C(b)\,
F(\widetilde\sigma_b^{-1}u\widetilde\sigma_b)=0
\qquad (u\in G_{K_M}).
\tag{4}
$$

## 在有限层使用 (4)

固定 $x\in\Sha(E,e)$。连续余闭链的定义域紧而值域离散，所以像有限。$W$ 的每个元素都被某个 $\ell$ 的幂消去，取有限个指数的最大值，得 $x$ 和其代表元均被某个 $\ell^r$ 消去。

令 $U_\infty=\ker\varepsilon_\ell\subset G_E$，以 $F_x:U_\infty\to W$ 记 $x$ 在这个群上的限制。按有限层延拓，$F_x$ 延拓为某个 $G_{E(\mu_{\ell^j})}$ 上的连续加法同态 $F_j$，并在有限惯性群上为零。[限制和延拓的证明](%E6%80%8E%E6%A0%B7%E6%8A%8A%E5%88%86%E5%9C%86%E5%A1%94%E4%B8%8A%E7%9A%84%E4%B8%8A%E5%90%8C%E8%B0%83%E9%99%90%E5%88%B6%E5%8F%98%E6%88%90%E6%9C%89%E9%99%90%E5%B1%82%E7%89%B9%E5%BE%81.md)

取 $m\ge\max\{r,j,2\}$ 并令 $M=N\ell^m$。限制 $F_j$ 到 $G_{K_M}$ 后仍在所有有限惯性群上为零，可以在 (4) 中用它。记 $\rho_M$ 为 $\rho$ 升到模 $M$ 的同态，整数算子为

$$
Q_M=-\sum_{b\in(\mathbb Z/M\mathbb Z)^\times} [b]_M^e C(b)\,[\rho_M(b)].
\tag{5}
$$

对 $u\in U_\infty\cap G_{K_N}$，它同时固定 $\mu_N$ 和所有 $\ell$ 幂阶单位根，故固定 $\mu_M$。对 $b$ 选在 $\mu_M$ 上作用为 $b$ 次幂的绝对提升 $\widetilde\sigma_b$，并写 $w_b=\widetilde\sigma_b^{-1}u\widetilde\sigma_b$。它仍在 $U_\infty\cap G_{K_M}$。根据 Galois 群作用的定义，$[\rho_M(b)]x$ 在 $U_\infty$ 上的限制于 $u$ 的值为

$$
\varepsilon_\ell(\widetilde\sigma_b)^{-e}F_x(w_b).
$$

因为 $\ell^m\mid M$，$\varepsilon_\ell(\widetilde\sigma_b)\equiv[b]_M\bmod\ell^m$。同时 $F_x(w_b)$ 被 $\ell^m$ 消去。将 (5) 的系数代入时，$[b]_M^e$ 恰抵消分圆扭曲 $\varepsilon_\ell(\widetilde\sigma_b)^{-e}$。于是

$$
F_{Q_Mx}(u)=-\sum_b C(b)F_j(w_b)=0 .
\tag{6}
$$

最后等号正是 (4)。到这里得到的消失范围是 $U_\infty\cap G_{K_N}$。该计算只需 $a$ 与 $N\ell$ 互素，源码 `resKill` 正在这个一般性下证明 (6)。

## 用 Euler 函数传回原来的上同调

取 $m$ 还达到高阶整数逼近的阈值，使 $Q_M\equiv z\bmod\ell^r$。这是同一有限群环中的比较，$[\phi(b)^{-1}]=[\rho(b)]$ 保证索引一致。因为 $\ell^r x=0$，有 $Q_Mx=zx$。于是 (6) 给出 $F_{zx}$ 在 $U_\infty\cap G_{K_N}$ 为零。

对任意 $u\in U_\infty$，它在 $\mu_N$ 上给出一个模 $N$ 的单位。该单位的 $\varphi(N)$ 次幂等于 $1$，故 $u^{\varphi(N)}\in U_\infty\cap G_{K_N}$。由于 $F_{zx}$ 是加法同态，

$$
F_{\varphi(N)zx}(u)=\varphi(N)F_{zx}(u)=F_{zx}(u^{\varphi(N)})=0.
$$

在 $e\ge1$ 和二进附加条件下，限制到 $U_\infty$ 的映射单射，故 $\varphi(N)zx=0$。这就是 (2)。因此 $\varphi(N)$ 的损失来自将消失从固定 $\mu_N$ 的群传到更大的群。

## Lean 对照与证明范围

- [`clKill`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/ClKill.lean#L17) `clKill` 第 17 行证明 (3)，[`homKill`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/HomKill.lean#L9) `homKill` 第 9 行经 Hilbert 类域和 Artin 共轭把它变成 (4)。[类群算子](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/ClKill.lean) · [无分歧特征](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/HomKill.lean)
- [`resKill`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/ResKill.lean#L14) `resKill` 第 14 行把扭结的分圆因子约掉，得到 (6)。[有限层消失](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/ResKill.lean) · [有限层的分圆特征同余](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/FixLev.lean) · [每个类的扭结指数](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/ContinuousToTorsionBounded.lean)
- [`totKill`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/TotKill.lean#L22) `totKill` 第 22 行用 $\varphi(N)$ 和限制单射传回上同调，[`zKill`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/ZKill.lean#L9) `zKill` 第 9 行用整系数逼近完成 (2)。[乘 Euler 函数](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/TotKill.lean) · [主结论](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/ZKill.lean)

本篇按源码对读。Hilbert 类域的 Artin 同构是经典输入。未重新编译或查询传递公理。
