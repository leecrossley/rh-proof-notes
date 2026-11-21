# The Hecke polynomials determine the semisimple Galois representations

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E7%9B%B8%E5%90%8C%E7%9A%84Hecke%E5%A4%9A%E9%A1%B9%E5%BC%8F%E5%86%B3%E5%AE%9A%E5%8D%8A%E5%8D%95Galois%E8%A1%A8%E7%A4%BA.md)

**Proposition.** Let $F$ be CM with maximal real subfield $F^+$, and let $\mathcal O$ be the project's complete coefficient DVR of characteristic-zero fraction field $k$. At each point $x$ of a finite set let $P_{x,w}$ be the Hecke polynomial at each allowed prime $w$ split in $F/F^+$ and outside the finite exclusions. Suppose $r_x,r'_x:G_F\to\mathrm{GL}_d(\mathcal O)$ are continuous and semisimple over $k$, and $\det(T-r_x(\sigma_w))=P_{x,w}(T)=\det(T-r'_x(\sigma_w))$ for the stipulated Frobenius lifts. Then at every $x$ there is $P_x\in\mathrm{GL}_d(k)$ with $P_xr_x(g)=r'_x(g)P_x$ for all $g\in G_F$. These representation hypotheses are `GoodR`.

## From the allowed primes to all group elements

If the traces differ at some $g$, continuity gives an open normal subgroup $H$ of finite index with distinct traces everywhere on $Hg$. Chebotarev for the finite extension fixed by $H$ supplies primes with Frobenius in the conjugacy class of $gH$, of positive Dirichlet density. Primes of absolute residue degree at least two have bounded sum of reciprocal norms, since above each rational prime $p$ there are at most $[F:\mathbb Q]$ terms with norm at least $p^2$. Removing them and finitely many ramified or excluded primes preserves the positive density. Choose the prime above $w$ in the finite extension so its Frobenius is the specified element $gH$. This gives the degree-one instance of the project input `Cheb`. [MIT 18.785, lecture 28, Theorem 28.9 and the degree-one application](https://ocw.mit.edu/courses/18-785-number-theory-i-fall-2021/mit18_785f21_lec28.pdf#page=6)

Take an algebraic integer $a$ not fixed by complex conjugation $c$ and exclude primes dividing $c(a)-a$. A remaining degree-one prime $w$ cannot be fixed by $c$, since $c$ would act trivially on the prime field $\mathcal O_F/w$ and force $c(a)-a\in w$. Thus $w$ is split over $F^+$ and its chosen Frobenius is allowed. The next-to-leading coefficients of the two polynomials show the traces agree at this lift in $Hg$, a contradiction. The traces agree everywhere.

## Semisimple modules of equal trace

For a characteristic-zero field $k$, suppose finite-dimensional semisimple modules $V,W$ of a unital $k$-algebra $A$ have equal traces on every $a\in A$. If there is a nonzero map in either direction, its image is isomorphic to a common nonzero direct summand by semisimplicity. Remove that summand and induct on total dimension, as the remaining traces agree. It remains to consider zero Hom spaces in both directions.

Put $M=V\oplus W$ and let $p$ project to $V$. Every $A$-linear endomorphism of $M$ commutes with $p$. For a $k$-basis $(v_i)$ of $M$, let $I=\{(av_i)_i:a\in A\}\subseteq M^d$, where $d=\dim_k M$. If $(pv_i)_i\notin I$, semisimplicity of $M^d/I$ gives a simple summand detecting its nonzero image, isomorphic to a summand of $M$. Hence there is an $A$-linear map $\lambda:M^d\to M$ vanishing on $I$ and nonzero on $(pv_i)_i$. With component maps $\lambda_i$, we would have
$$
\lambda((pv_i)_i)=\sum_i\lambda_i(pv_i)=p\sum_i\lambda_i(v_i)=0
$$
since $(v_i)\in I$. Thus some $a$ acts as $p$. Its traces on $V,W$ are $\dim_k V,0$, so $V=0$ by characteristic zero. Equality at $1$ gives $W=0$. This completes the induction. Apply it to $k[G_F]$ using linearity of the trace equality. The isomorphisms in the original bases give the $P_x$ over $k$.

## Lean correspondence

- `eq_univ_of_frob` and `isRx_unique` give trace equality and uniqueness, and `PointRepConj.main` writes the equivalence as conjugacy. [Trace](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/T2SpaceCoefficientRing.lean#L166) · [Conjugacy](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/PointGaloisRepsConjugateOverFractionField.lean#L29)
- `finrank_eq_zero_of_hom` uses density for the projection and `exists_equiv_of_trace_eq` uses the summand induction. `cheb_holds` supplies the project Chebotarev input. [Trace criterion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/NonemptyLinearEquivOfCharpolyEq.lean#L138) · [Chebotarev](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ChebotarevDegreeOne.lean#L66)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
