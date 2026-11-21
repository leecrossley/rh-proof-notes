# From Dirichlet nonvanishing to RH

[中文主线](../zh/from-windows-to-rh.md) · [Reading and review status](../../STATUS.md)

## Statement

Suppose for every positive modulus $N$ and every Dirichlet character $\chi$ modulo $N$ that $L(s,\chi)\ne0$ whenever $\operatorname{Re}s>1/2$ and either $\chi$ is nonprincipal or $s\ne1$. Then the Riemann hypothesis holds for $\zeta$.

## Proof

Use the unique character $\mathbf 1$ modulo $1$. Its Dirichlet series is the zeta series, because $\mathbf 1(n)=1$ for every positive integer. Their meromorphic continuations agree. Hence the hypothesis at $N=1$ gives $\zeta(s)\ne0$ for $\operatorname{Re}s>1/2$ and $s\ne1$. The [reflection argument](rh-from-right-half-plane.md) gives RH.

The deduction is `Formalism.VW.rh_of_every`. Mathlib supplies the identity for the character modulo $1$. [Lean source](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GammaFactorNonvanishing/CritLine.lean#L29)

## Attribution

Adapted from Tam Nguyen Duc, [*The Riemann Hypothesis from EveryCharacter*](https://github.com/tamnd/riemann/blob/cd083b1483e1cad44bfd3430ac1ca8016f39e3e9/proof/steps/rh-of-every.md), under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). This version condenses the argument, makes the Dirichlet series identity explicit and adds links for this reading path. The upstream prose is marked as a draft. [Upstream license statement](https://github.com/tamnd/riemann/blob/cd083b1483e1cad44bfd3430ac1ca8016f39e3e9/README.md#licence)
