# Group-ring differences isolate one slope

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E7%94%A8%E7%BE%A4%E7%8E%AF%E7%9A%84%E5%B7%AE%E5%88%86%E5%8F%AA%E4%BF%9D%E7%95%99%E4%B8%80%E4%B8%AA%E6%96%9C%E7%8E%87.md)

## Statement

Let $\ell$ be prime, $0\le c\le\nu$, $q=\ell^\nu$, $w=\ell^c$, $\kappa=1+w$, and $0\le M<w$. Fix $t_0\in\{0,\ldots,M\}$. Write $[a]$ for basis elements of the integral group ring of $A=\mathbb Z/q\mathbb Z$ with multiplication $[a][b]=[a+b]$. Set
$$
P(X)=\prod_{j=0}^{M-1}(X-\kappa^j)=\sum_{i=0}^M p_iX^i,\qquad
V=\sum_{i=0}^M p_i[\kappa^i].
$$
For $t=0,\ldots,M$ let $\phi_t:\mathbb Z[A^2]\to\mathbb Z[A]$ send $[(a,b)]$ to $[a+tb]$. Then some $\eta$ has $\phi_{t_0}(\eta)=V$ and $\phi_t(\eta)=0$ for $t\ne t_0$. This is `SEta` in the [lattice and cycle construction](building-a-global-cycle-from-a-twisted-principal-divisor.md), where the coefficients of $\eta$ set ideal powers in each block.

## Proof

On $\mathbb Z[X]$ let $T(f)(X)=f(X^\kappa)$ and $U=X^w-1$. We have $T(f)\equiv f\bmod U$ and
$$
T(U)=U(1+X^w+\cdots+(X^w)^{\kappa-1}),
$$
whose quotient is $\kappa$ modulo $U$. Thus $(T-\kappa^j)(U^j g)\in U^{j+1}\mathbb Z[X]$. Starting with $X$, apply $T-\kappa^j$ for $j=0,\ldots,M-1$ to see that $\sum_i p_i X^{\kappa^i}$ is divisible by $U^M$. Substituting $[1]$ for $X$ gives $([w]-[0])^M\mid V$.

For $t\ne t_0$, let $h=t_0-t$. Since $0<|h|\le M<w$, $v_\ell(h)<c$, so $h$ divides $w$ in $A$. Write $w=rh$ with a nonnegative representative $r$. Then $[w]=[h]^r$, and $[h]-[0]$ divides $[w]-[0]$. Using the $M$ factors yields
$$
V=\prod_{t\ne t_0}\bigl([t_0-t]-[0]\bigr)\,Q
$$
for some $Q$ in the group ring. Write $\iota$ for the embedding by $a\mapsto(a,0)$ and set
$$
\eta=\prod_{t\ne t_0}\bigl([(0,1)]-[(t,0)]\bigr)\,
\iota([-\sum_{t\ne t_0}t]Q).
$$
For each other slope its own factor maps to zero. At $t_0$ every factor maps to $[t]\bigl([t_0-t]-[0]\bigr)$ and the shift cancels the product of $[t]$. The result is $V$. For $M=0$ the empty products are units and the formula gives $[(1,0)]$.

## Lean correspondence

- [`SEta`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/LemmaKOfSteps.lean#L71) is proved by [`exp_step`, `exp_dvd`, `alg_dvd` and `sEta`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/ExpStep.lean#L17).
- [`cJoin`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/LatticeBlockClasses/CJoin.lean) uses this to distinguish the retained slope from the others.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
