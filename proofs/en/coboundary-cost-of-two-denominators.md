# Two copies of the block denominator bound the coboundary length

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E4%BD%99%E8%BE%B9%E7%95%8C%E6%9C%80%E5%A4%9A%E5%B8%A6%E8%B5%B0%E4%B8%A4%E4%BB%BD%E5%9D%97%E9%97%B4%E5%88%86%E6%AF%8D.md)

**Proposition.** Let $A$ be a ring with central coefficients $T'$, $r:G\to A^\times$ a representation and $\chi:G\to(T')^\times$ a character. Let $M$ be a left $A$-module whose compatible $\mathcal O$-module is $(K/\mathcal O)^d$ for a DVR $\mathcal O$ with fraction field $K$. Let $G$ act by $u(g)=\chi(g)^{-1}r(g)$. Suppose $E\in A$, $\delta\in T'$ satisfy $E^2=\delta E$, with a finite expression $E=\sum_{g\in J}t_g r(g)$, $t_g\in T'$. Put $\tau=\sum_{g\in J}t_g\chi(g)$. Assume $E$ acts by zero, and $\tau,\delta$ by the same nonzero scalar $\Delta\in\mathcal O$. Set $y(g)=(u(g)-1)E$ and let $Y$ be their left ideal. For every $A$-linear $f:Y\to M$, $z_f(g)=f(y(g))$ is a cocycle. If $z_f(g)=(u(g)-1)v$ for all $g$, then $\Delta^2v=0$. Consequently the submodule of these cocycles lying in the coboundaries has length at most $2d\operatorname{ord}_{\mathcal O}(\Delta)$.

Since $u$ is a representation, $y(gh)=y(g)+u(g)y(h)$. Applying $f$ proves the cocycle identity. Now form
$$
y_*=\sum_{g\in J}t_g\chi(g)y(g)=(E-\tau)E.
$$
Since $\tau$ is central and $E^2=\delta E$, we have $Ey_*=\delta y_*$. Under the coboundary assumption the same sum in $M$ gives $f(y_*)=(E-\tau)v=-\Delta v$. Applying $f$ to $Ey_*=\delta y_*$ gives $0=Ef(y_*)=\Delta f(y_*)=-\Delta^2v$. The coboundaries in question are thus in the image of $M[\Delta^2]$ under the coboundary map. Since $(K/\mathcal O)[\Delta^2]\simeq\mathcal O/(\Delta^2)$, the length of the image is at most $2d\operatorname{ord}(\Delta)$.

For $\phi:N\to M$ with $N$ the [column relation module](column-dimension-detects-outside-representations.md), restrict along $Y\to N$ to obtain $f$. The kernel of $\phi\mapsto z_f$ consists exactly of maps vanishing on $Y$, since the $y(g)$ generate $Y$. The zero and higher blocks have $E=0$ and use the stated bound. Block one has trivial $u$, so its coboundaries vanish.

## Lean correspondence

- `StatementPsi.ycoc_mul` and `colPsi` give the cocycle. `colPsiKer` identifies the kernel, and `cobColumn` proves the annihilator. [Cocycle](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/StatementPsi.lean#L33) · [Kernel](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/BlockRhoFull.lean#L11) · [Annihilator](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/BlockRhoFull.lean#L51)
- `mid_bound` uses the torsion length to bound the submodule of coboundaries. [Length](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/LengthEqKerAddRange.lean)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
