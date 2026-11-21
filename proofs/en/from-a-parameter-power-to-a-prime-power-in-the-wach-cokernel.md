# Replacing a parameter power by a prime power in the Wach cokernel

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E6%8A%8AWach%E4%BD%99%E6%A0%B8%E4%B8%AD%E7%9A%84%E5%8F%82%E6%95%B0%E5%B9%82%E6%8D%A2%E6%88%90%E7%B4%A0%E6%95%B0%E5%B9%82.md)

**Proposition.** Let $\ell\ge3$ be prime, $A$ a commutative $\mathbb Z_\ell$-algebra, and $N'\subseteq N\subseteq D$ be $A$-modules. Suppose $X\in A$ is injective on $D$, $\gamma$ is semilinear over an $\mathbb Z_\ell$-endomorphism $\gamma_A$, and
$$
(\gamma-1)N\subseteq XN,\qquad(\gamma-1)N'\subseteq XN',\qquad
\gamma_A(X)\equiv uX\bmod X^2A .
$$
Here $u\in\mathbb Z_\ell^\times$ has order $\ell-1$ modulo $\ell$ and $v_\ell(u^{\ell-1}-1)=1$. If $X^sN\subseteq N'$ for $s\ge0$, then for $0\le j\le s$,
$$
\ell^{d_\ell(j,s)}X^jN\subseteq N',\qquad
d_\ell(j,s)=\sum_{j<k\le s,\ \ell-1\mid k}(1+v_\ell(k)).
$$
In particular $X^H N\subseteq N'$ implies $\ell^{e_W}N\subseteq N'$ for $e_W=\lfloor H\ell/(\ell-1)^2+3+\log_\ell(H+1)\rfloor$.

Suppose $cX^{i+1}N\subseteq N'$ with $c\in\mathbb Z_\ell$. Expand $(\gamma-1)(cX^{i+1}n)$ using $\gamma(n)\equiv n\bmod XN$ and the linear term of $\gamma_A(X)$. The result is $cX^{i+1}((u^{i+1}-1)n+Xn_2)$ for some $n_2\in N$. Since the input was in $N'$, the result belongs to $XN'$. Cancel $X$ and remove the term $cX^{i+1}n_2$ already in $N'$. Hence $c(u^{i+1}-1)X^iN\subseteq N'$. Iterate from $s$ down to $j$. The accumulated product has factors $u^k-1$ for $j<k\le s$.

For $\ell-1\nmid k$ the factor is a unit. For $k=(\ell-1)b$, the [power valuation formula](valuation-of-the-denominator-between-blocks.md) gives $v_\ell(u^k-1)=1+v_\ell(b)=1+v_\ell(k)$. Remove the unit part of the product to get the claimed containment. With $b_0=\lfloor j/(\ell-1)\rfloor$ and $b_1=\lfloor s/(\ell-1)\rfloor$ the cost is $b_1-b_0+v_\ell(b_1!)-v_\ell(b_0!)$. Counting multiples of $(\ell-1)\ell^i$, each count is strictly less than $(s-j)/((\ell-1)\ell^i)+1$. For $s\le H$ at most $1+\log_\ell(H+1)$ such levels can contribute. Thus $d_\ell(j,s)<(s-j)\ell/(\ell-1)^2+1+\log_\ell(H+1)$, also with no contributing levels. This is bounded by the stated $e_W$ for $j=0,s=H$.

For a coefficient component of the Wach cokernel, use $N$ for the target, $N'$ for the source image and $X=\pi$ for the original parameter. The Hodge jump bound supplies $X^H N\subseteq N'$. Passing to tame invariants costs no additional power of $\ell$, because any lift of a tame invariant can be averaged over a group of order $\ell-1$.

## Lean correspondence

- `descent_reduces_level` and `mem_span_of_frobenius_mem_span` apply $\gamma-1$ and iterate; `cost_formula_holds` and `cost_bound` compute the cost. [Descent](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/LagrangeExtensionCocycles/ExtensionCocycleProofs/MemSpanOfFrobeniusMemSpan.lean#L193) · [Cost](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/LagrangeExtensionCocycles/ExtensionCocycleProofs/TotallyRealRoots.lean#L7)
- `unit_lemma_case_a_unconditional` combines the estimates and `coreWA_of` applies to the Wach cokernel. [Unit lemma](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/LagrangeExtensionCocycles/ExtensionCocycleProofs/TotallyRealRoots.lean#L121) · [Cokernel](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/FrobeniusPowUniformizerFactorisation.lean#L3486)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
