# 怎样从Kummer根的比值构造可用的加法特征

**命题（合并 `kolEx`、`kolHom`、`kolUnr`）。** 设 $M,F,n,r$ 为正整数，$M\mid F$，写 $G=G_{\mathbb Q}$、$K_j=\mathbb Q(\mu_j)$、$U=G_{K_F}$。固定本原 $M$ 次单位根 $\zeta$，取 $\delta\in G$ 在 $\mu_M$ 上作用为取 $a$ 次幂，其中 $a$ 是非负整数。设 $y\in K_{Fn}^{\times}$，在所有不在 $r$ 上方的有限素处为单位。要求对每个 $u\in U$ 都能在 $K_{Fn}$ 内找到 $z_u$ 满足

$$
z_u^M=u(y)/y.
 \tag{1}
$$

令 $P(x)=\delta(x)/x^a$，其中 $x\ne0$。那么存在唯一的连续加法同态 $\kappa:U\to\mathbb Z/M\mathbb Z$，对任何 $Y^M=y$ 及任何满足 (1) 的根 $z_u$，有

$$
\zeta^{\kappa(u)}
      =\frac{u(P(Y))}{P(Y)\,P(z_u)} .
 \tag{2}
$$

在所有 $p\nmid Frn$ 的惯性群上，$\kappa$ 为零。因为这些惯性群在 $U$ 内，这是一条有定义的条件。在式 (2) 中，指数取模 $M$ 的任意整数代表。Lean 把 $\kappa$ 声明为 $G$ 上的函数，但只对 $U$ 中的值有上述条件。这里的唯一性指限制到 $U$。

辅助素数长度证明需要一个系数在 $W=\operatorname{Frac}(O)/O$ 的同态 $\nu$。本篇后半段说明如何从 $\kappa$ 得到它，保留分歧范围并取得指定的共轭特征。式 (1) 来自项目应用于 Stickelberger 数域元素的 Kolyvagin 导数。 [长度估计为什么需要这些同态](%E9%80%90%E4%B8%AA%E5%8A%A0%E5%85%A5%E8%BE%85%E5%8A%A9%E7%B4%A0%E6%95%B0%E6%80%8E%E6%A0%B7%E6%8A%8A%E5%90%8C%E8%B0%83%E9%95%BF%E5%BA%A6%E5%8E%8B%E5%88%B0%E4%B8%80%E4%B8%AA%E8%B5%8B%E5%80%BC.md)

## 一、根的选择为何不影响取值

对任何非零 $x_1,x_2$，有 $P(x_1x_2)=P(x_1)P(x_2)$。若 $\xi\in\mu_M$，则 $P(\xi)=1$，因为 $\delta(\xi)=\xi^a$。因此两个非零数的 $M$ 次幂相等时，二者的 $P$ 值相等。特别地，式 (2) 中的 $P(Y)$ 和 $P(z_u)$ 都独立于所选根。式 (1) 所给根在 $K_{Fn}$，而所有 $\mu_M$ 也在该域中，所以其他根也在其中。

式 (2) 右边的 $M$ 次幂等于 $u(P(y))/(P(y)P(u(y)/y))$。$K_{Fn}/\mathbb Q$ 是阿贝尔扩张，故 $u$ 与 $\delta$ 在其中交换，$P(u(y))=u(P(y))$。用 $P$ 的乘法性，上述 $M$ 次幂为 $1$。所以右边是唯一的 $\zeta$ 的模 $M$ 次幂，得到 $\kappa(u)$。唯一性也随之成立。

对 $u,v\in U$，$(u(z_v)z_u)^M=(uv)(y)/y$。用它作为 $z_{uv}$。因为 $u$ 与 $\delta$ 在 $K_{Fn}$ 上交换，有 $P(u(z_v))=u(P(z_v))$。于是

$$
\zeta^{\kappa(uv)}
 =u\!\left(\frac{v(P(Y))}{P(Y)P(z_v)}\right)
                      \frac{u(P(Y))}{P(Y)P(z_u)}
 =\zeta^{\kappa(v)+\kappa(u)},
$$

后一等号用 $u$ 固定 $\mu_M$。这说明 $\kappa$ 加法。令 $H$ 为同时固定 $K_{Fn}$ 和 $P(Y)$ 的开子群。对 $h\in H$，有 $h(y)=y$，可取 $z_h=1$，式 (2) 就给 $\kappa(h)=0$。因此 $\kappa$ 在 $H$ 的陪集上常值，得到连续性。[根式构造第 7 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/KolEx.lean) · [加法与连续性第 45 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/KolHom.lean)

## 二、为何在指定范围外没有惯性取值

取 $p\nmid Frn$ 及其一个绝对素处。该素处的惯性群固定分圆域 $K_{Fn}$，因此对 $u\in I_p$，可在 (2) 取 $z_u=1$。$Y$ 在 $p$ 上方每个处都为单位，因为 $Y^M=y$ 且 $p\nmid r$。同样 $\delta(Y)$ 是单位，所以 $P(Y)$ 也是。由于惯性在剩余域作用平凡，$u(P(Y))/P(Y)\equiv1$ 于所取处的极大理想。

如果一个 $M$ 次单位根 $\xi$ 在剩余域等于 $1$，且 $p\nmid M$，它只能是 $1$。否则 $(\xi-1)\sum_{j=0}^{M-1}\xi^j=0$ 给几何和为零，约化后得到 $M=0$ 的矛盾。这里 $p\nmid M$ 来自 $M\mid F$ 与 $p\nmid F$。应用于 (2)，即得 $\kappa(u)=0$。[惯性消失第 16 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/KolUnr.lean)

## 三、按特征加权得到共轭律

**命题（`nuIs` 的应用）。** 设 $O$ 为交换环、$W$ 为 $O$-模，$w\in W$ 满足 $Mw=0$。设 $\beta:G\to O^\times$ 在 $U$ 上同余于 $1\bmod MO$。对每个 $t\in(\mathbb Z/F\mathbb Z)^\times$，取 $\sigma_t$ 在 $\mu_F$ 上取 $t$ 次幂。给定连续加法同态 $\kappa:U\to\mathbb Z/M\mathbb Z$，并假设在所有 $p\nmid d$ 的惯性群中为零，其中 $F\mid d$ 且 $d>0$。定义

$$
\nu(u)=\sum_{t\in(\mathbb Z/F\mathbb Z)^\times}
           \kappa(\sigma_t^{-1}u\sigma_t)\,\beta(\sigma_t)w .
 \tag{3}
$$

在被 $M$ 消去的模上，模 $M$ 的整数标量可用任意代表元。则 $\nu$ 连续、加法、被 $M$ 消去，在 $p\nmid d$ 的惯性群上为零，并满足

$$
\nu(gug^{-1})=\beta(g)\nu(u).
 \tag{4}
$$

连续性、加法和消去条件逐项成立。惯性群经共轭仍是同一个有理素数上方的惯性群，故 $p\nmid d$ 时所有项均为零。为证明 (4)，记 $b$ 为 $g$ 在 $\mu_F$ 上作用的指数。在求 $\nu(gug^{-1})$ 时，将 $t$ 换为 $bs$。此时 $\sigma_{bs}=g\sigma_s h_s$ 对某个 $h_s\in U$ 成立，因为两边在 $\mu_F$ 上的指数一致。因此

$$
\kappa(\sigma_{bs}^{-1}gug^{-1}\sigma_{bs})
    =\kappa(h_s^{-1}\sigma_s^{-1}u\sigma_s h_s)
    =\kappa(\sigma_s^{-1}u\sigma_s),
$$

最后用了 $\kappa$ 是加法同态。另一方面 $\beta(h_s)w=w$，所以 $\beta(\sigma_{bs})w=\beta(g)\beta(\sigma_s)w$，提取 $\beta(g)$ 得 (4)。这里没有除以 $\varphi(F)$，对 $\ell\mid\varphi(F)$ 也有效。

在实际调用中，$M=\ell^m$，$\beta=\varepsilon_\ell\alpha^{-1}$，$d=Frn$。因为 $U$ 固定 $\mu_M$ 且 $\alpha|_U\equiv1\bmod M$，对 $\beta$ 的要求成立。由前两节和 (3) 即得到源码的 `IsNu`。[加权求和第 23 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/ValAddSmul.lean)

## Lean 对照与证明范围

- `IsKol` 的定义是选择根 $Y$ 并要求对每个 $u\in U$ 存在满足 (1)、(2) 的 $K_{Fn}$ 内的根。[`kolEx`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/KolEx.lean#L7) `kolEx` 负责存在性，[`kolHom`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/KolHom.lean#L45) `kolHom` 给任意根的公式与连续加法性，[`kolUnr`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/KolUnr.lean#L16) `kolUnr` 给分歧范围。[定义第 76 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/IsAdmissiblePrimeListNil.lean)
- `nu` 即 (3)，[`nuIs`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/ValAddSmul.lean#L23) `nuIs` 给 (4) 和其他性质，[`nuSysEx`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/NuSysEx.lean#L79) `nuSysEx` 在对每个列表构造 $\nu_L$ 后调用它。[汇总第 79 行及各列表的验证](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/NuSysEx.lean)

本篇为源码对读。列出了从根式条件 (1) 到具有分歧范围的特征的证明。条件 (1) 由项目的 `derInv` 另行提供。[根式条件的入口第 212 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/DerInv.lean)
