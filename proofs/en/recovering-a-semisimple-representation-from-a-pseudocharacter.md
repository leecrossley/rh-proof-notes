# Recovering a semisimple representation from a pseudocharacter

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E4%BB%8E%E4%BC%AA%E7%89%B9%E5%BE%81%E7%9A%84%E8%BF%B9%E6%81%A2%E5%A4%8D%E5%8D%8A%E5%8D%95%E8%A1%A8%E7%A4%BA.md)

## Statement

Let $G$ be a group, $k$ algebraically closed of characteristic zero, $d\ge0$, and $T:G\to k$ satisfying the [three pseudocharacter identities](limit-traces-retain-the-polynomial-identities-of-representations.md). There is a semisimple $\rho:G\to\mathrm{GL}_d(k)$ with trace $T$. For topological $G,k$ with continuous $T$, the representation is continuous.

## The trace-pairing quotient

Extend $T$ linearly to $k[G]$. Cyclicity extends by bilinearity and the alternating identity by multilinearity. The radical $I=\{x:T(xy)=0\ \forall y\}$ is a two-sided ideal by associativity and cyclicity. The induced $S$ on $R=k[G]/I$ keeps the identities and has nondegenerate multiplication pairing.

For $x\in R$ set $e_j=A_j(S;x,\ldots,x)/j!$. Group the permutation sum for $A_{d+1}(S;y,x,\ldots,x)$ by the cycle containing $y$. If $j$ of the $x$ positions lie on this cycle, there are $d!/(d-j)!$ orders and sign $(-1)^j$, with the remaining positions contributing $A_{d-j}$. Thus $0=d!\sum_{j=0}^d(-1)^j e_{d-j}S(yx^j)$. Multiplying by $(-1)^d/d!$ and using nondegeneracy gives $p_x(x)=0$ for the monic $p_x(X)=\sum_{j=0}^d(-1)^{d-j}e_{d-j}X^j$. Hence $R$ is algebraic.

If all $S(u^m)=0$ for $m\ge2$, only singleton cycles survive in $A_{d+1}(S;u,\ldots,u)$, so $S(u)^{d+1}=0$. If $z^N=0$, apply this descending in $u=z^j$ for $j=N-1,\ldots,1$ to obtain $S(z)=0$. Therefore if all $yx$ are nilpotent, all $S(yx)=0$ and $x=0$.

For idempotent $e$, the recurrence gives $A_{d+1}(S;e,\ldots,e)=\prod_{j=0}^d(S(e)-j)=0$. If $S(e)=0$, set $v=ey$ for arbitrary $y$, so $ev=v$. In $A_{d+1}(S;e,\ldots,e,v)$ the first term of each recurrence vanishes and each replacement keeps the remaining arguments, giving $(-1)^dd!S(v)=0$. Nondegeneracy forces $e=0$. Thus every nonzero idempotent has positive integer trace. For orthogonal idempotents their sum is idempotent, so at most $d$ occur. The [finite-dimensional semisimplicity criterion](the-nondegenerate-trace-algebra-has-at-most-square-dimension.md) applies.

## Block action and continuity

By Artin–Wedderburn, $R\simeq\prod_i M_{n_i}(k)$. On a block $S$ is a scalar multiple $m_i$ of the matrix trace: off-diagonal units and differences of diagonal units are commutators, which $S$ kills. The coefficient $m_i$ is the trace of a rank-one idempotent, so is a nonnegative integer, with $\sum_i m_i n_i=S(1)=d$. Let each block act in $m_i$ copies of its standard representation and compose with the group algebra quotient. Group elements remain invertible, yielding a semisimple $d$-dimensional representation of trace $T$.

On the algebra spanned by $\rho(G)$ the trace pairing is nondegenerate, since on each surviving block it is ordinary trace pairing times a positive integer. Choose a basis $\rho(g_i)$. The injection $X\mapsto(\operatorname{tr}(X\rho(g_i)))_i$ has a fixed linear left inverse. At $X=\rho(g)$ its coordinates are $T(gg_i)$, continuous in $g$. Thus the matrix entries of $\rho$ are continuous, as are those of its inverse by $g\mapsto g^{-1}$.

## Lean correspondence

- [`cayleyHamilton`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CayleyHamilton.lean), [nilpotent trace vanishing](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/PseudoCharacterEqZeroOfIsNilpotent.lean) and [idempotent traces](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/PseudoCharacterApplyIdempotentNatLe.lean) give the three quotient properties.
- [`traceKer` and `exists_ssRep`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/FiniteSemisimple.lean#L40) give the quotient and block representation. [`continuous_of_continuous_trace`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ContinuousOfContinuousTrace.lean) gives continuity.
- [`exists_limit_rep`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsLimitRep.lean#L14) assembles trace approximation, identities and semisimple reconstruction.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
