# Killing the second Herr obstruction by grading and a polynomial

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E7%94%A8%E5%88%86%E6%AC%A1%E4%B8%8E%E5%A4%9A%E9%A1%B9%E5%BC%8F%E6%B6%88%E5%8E%BBHerr%E5%A4%8D%E5%BD%A2%E7%9A%84%E4%BA%8C%E6%AC%A1%E9%9A%9C%E7%A2%8D.md)

Let $\mathcal O$ be commutative, $A$ a commutative $\mathcal O$-algebra, $N\subseteq D$ a pair of $A$-modules, $p$ prime, $X,Q\in A$, and $M,a\ge0$ integers. Write $U=\{y\in D:Q^My\in N\}$. Let $\varphi,\gamma$ be commuting $\mathcal O$-linear operators on $D$, and define $d_1(y,z)=(\gamma-1)y-(\varphi-1)z$ on $U\times XN$. Assume $X$ acts injectively, and $X\delta=\gamma-1$ for an $\mathcal O$-linear operator $\delta$ preserving $U,N$. For $R(T)\in\mathcal O[T]$ and $C\in\mathcal O$ assume:

1. $\delta R(\delta)U\subseteq N$, and $N$ is saturated inside $U$ under both $p$ and $C$, meaning $py\in N$ or $Cy\in N$ for $y\in U$ implies $y\in N$.
2. $(\varphi-1)XN\subseteq U$ and $\varphi$ preserves $X^{a+1}N$.
3. For every $n\in N$ there are $x,m\in N$ with $CXn=(\gamma-1)Xx+X^{a+1}m$.
4. $1-\varphi$ maps $X^{a+1}N$ onto itself.

**Proposition.** If $w\in U$ and $p^j Xw$ belongs to the image of $d_1$ for some $j\ge0$, then so does $R(0)C Xw$.

Write $p^j Xw=d_1(y,Xn)$ and use hypothesis 3 to express $CXn$. Commutation gives
$$
Cp^j Xw=(\gamma-1)y'+(1-\varphi)X^{a+1}m,\qquad y'=Cy-(\varphi-1)Xx\in U .
$$
The last term equals $X^{a+1}m'$ with $m'\in N$. Cancel $X$ to obtain $Cp^j w=\delta y'+X^a m'$. Apply $R(\delta)$. The first term is in $N$ by hypothesis 1 and the second by $\delta N\subseteq N$. Since $R(\delta)w\in U$, saturation first removes $p^j$ and then $C$, giving $R(\delta)w\in N$.

Write $R(T)=R(0)+TR_1(T)$. Apply hypothesis 3 to $R(\delta)w$, and write its deep term using hypothesis 4:
$$
CX R(\delta)w=(\gamma-1)Xx_2+(1-\varphi)X^{a+1}z_2
$$
for $x_2,z_2\in N$. Subtract $CX\delta R_1(\delta)w$ to get $R(0)CXw=d_1(Xx_2-CR_1(\delta)w,X^{a+1}z_2)$. Both coordinates are allowed. The unknown initial $j$ is absent from this identity.

For unramified odd $\ell$, put $p=\ell$, $v_\ell(u-1)=1$, $u_1=u^{\ell-1}$, and $a=\lfloor M/(\ell-1)\rfloor$. The [operator equations](two-wach-operator-equations-from-grading-and-completeness.md) give $C=\prod_{i=1}^a(1-u_1^i)$ of valuation $a+v_\ell(a!)$, so $p$-saturation gives $C$-saturation. The comparison uses $R(T)=\prod_{j\in J}(T-(1-u^{-j})/\ell)$. The set $J$ contains the nonzero indices from the shifted filtration jumps. The graded comparison gives $\delta R(\delta)U\subseteq N$, with the extra $\delta$ handling eigenvalue zero. By the [unit power valuation](valuation-of-the-denominator-between-blocks.md), $v_\ell(R(0))=\sum_{j\in J}v_\ell(j)$. These valuations give the uniform exponent $e_U$, with $a_0=a+1$ used for its bound.

## Lean correspondence

- `C1`, `d1` and `TorsKilled` state the coordinate conditions. `claim_key` and `claim_fin` do the two steps in `torsionKilledCriterion_holds`. [Complex](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CoboundaryTransfers/Statement.lean#L61) · [Criterion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CoboundaryTransfers/GammaStableTransfers/TorsionKilledCriterionHolds.lean#L200)
- `lifta_core` combines the graded and period inputs with the polynomial and uses the valuation bound. [Application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/BaseChangePreservesUnitaryOf.lean#L1050)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
