# RH from the right half-plane

[中文主线](../zh/from-windows-to-rh.md#3-反射到右半平面) · [Reading and review status](../../STATUS.md)

## Statement

Assume $\zeta(u)\ne0$ for every $u\in\mathbb C$ with $\operatorname{Re}u>1/2$ and $u\ne1$. Then every zero of $\zeta$ other than the negative even integers, with the pole at $1$ excluded, has real part $1/2$.

## Proof

Let $s$ be such a zero. The hypothesis excludes $\operatorname{Re}s>1/2$. Suppose $\operatorname{Re}s<1/2$, and write $u=1-s$. Then $\operatorname{Re}u>1/2$. Since $\zeta(0)=-1/2$, we have $s\ne0$, so $u\ne1$. The real-part inequality also excludes all nonpositive integers as values of $u$. These are the conditions needed for Mathlib's functional equation:

$$
\zeta(s)=2(2\pi)^{-u}\Gamma(u)\cos(\pi u/2)\zeta(u).
$$

The complex power is nonzero, $\Gamma$ is nonzero in this half-plane, and $\zeta(u)$ is nonzero by hypothesis. A vanishing cosine would give $u=2k+1$ and $s=-2k$ for an integer $k$. If $k<0$, then $\operatorname{Re}s\ge2$. If $k=0$, then $s=0$. If $k>0$, then $s$ is a negative even integer. Each possibility contradicts the choice of $s$. Thus all factors on the right are nonzero, contrary to $\zeta(s)=0$. The remaining real part is $1/2$.

## Source and attribution

Adapted from Tam Nguyen Duc, [*The Riemann Hypothesis from the right half-plane*](https://github.com/tamnd/riemann/blob/cd083b1483e1cad44bfd3430ac1ca8016f39e3e9/proof/steps/rh-of-right.md), under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Changes include a condensed statement and proof, a new source link and placement in the bilingual reading path. The upstream prose is marked as a draft. [Upstream license statement](https://github.com/tamnd/riemann/blob/cd083b1483e1cad44bfd3430ac1ca8016f39e3e9/README.md#licence)

The Lean declaration is `Formalism.VW.rh_of_right`. It applies the Mathlib functional equation `riemannZeta_one_sub` to $u=1-s$. [Lean source](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GammaFactorNonvanishing/RhOfRight.lean#L5)
