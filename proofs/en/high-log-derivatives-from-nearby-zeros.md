# High log derivatives from nearby zeros

[Chinese proof](../zh/%E9%AB%98%E9%98%B6%E5%AF%B9%E6%95%B0%E5%AF%BC%E6%95%B0%E6%80%8E%E6%A0%B7%E6%94%BE%E5%A4%A7%E9%82%BB%E8%BF%91%E9%9B%B6%E7%82%B9.md)

For each integer $q\ge1$, character $\chi\bmod q$, integer $k\ge0$, and $\Re s>1$, write
$$
D_k(\chi;s)=\frac1{k!}\sum_{n\ge1}\Lambda(n)\chi(n)(\log n)^k n^{-s}.
$$
This is `derSeries` with character coefficients. Let $Z_\chi(t)$ be the zeros of $L(s,\chi)$ in $|w-(2+it)|\le3$, omitting the principal pole, and let $m_w$ be their analytic multiplicities.

**Proposition.** There exists an absolute $C>0$ such that for every $q,\chi,k$ as above, $t\in\mathbb R$ and $1<\sigma\le2$, the set $Z_\chi(t)$ is finite, $\sum_{w\in Z_\chi(t)} m_w\le C\log(q(|t|+2))$, and at $s=\sigma+it$,
$$
\left|D_k(\chi;s)-\frac{\mathbf1_{\chi=\chi_0}}{(s-1)^{k+1}}+
\sum_{w\in Z_\chi(t)}\frac{m_w}{(s-w)^{k+1}}\right|
\le\frac{C\log(q(|t|+2))}{\sigma^k}.
\tag{1}
$$
The set of zeros is fixed across all $k$.

## A bounded holomorphic remainder

Let $F=L(\cdot,\chi)$ in the nonprincipal case and $F=(s-1)L(s,\chi_0)$ in the principal case, continuing at $1$. The latter is $(s-1)\zeta(s)\prod_{p\mid q}(1-p^{-s})$ and has nonzero value $\prod_{p\mid q}(1-p^{-1})$ at $1$. In both cases $F$ is entire and has exactly the relevant zeros with their original multiplicities.

On $\Re z\ge-7/4$, the [finite-difference growth bounds](l-function-growth-from-finite-differences.md) give $|F(z)|\le Bq^5(|z|+2)^5$ for an absolute $B$. For the principal case use $1+p^{7/4}\le p^3$ in each extra factor, so the product is at most $q^3$. With $a=2+it$ and $X=q(|t|+2)$, the disk $|z-a|\le15/4$ lies in this range with $|z|+2\le4(|t|+2)$. Thus $|F|\le1024 B X^5$ there, while $|F(a)|\ge1/2$ by the inverse Euler product and $|a-1|\ge1$.

Use the [scaled disk lemma](local-log-derivative-from-disk-zeros.md) with relative radii $R=4/5$, $r=2/3$. The zero radius is $3$, and the radius for the remainder bound is $5/2$. Thus the total multiplicity is $O(\log X)$ and
$$
g(z)=F'(z)/F(z)-\sum_{w\in Z_\chi(t)}m_w/(z-w)
$$
is bounded by $O(\log X)$ at nonzero points of $F$ within radius $5/2$. Each possible pole of $F'/F$ in this disk is canceled by the displayed fraction, by dividing out the corresponding local Taylor factor. Thus $g$ extends holomorphically and the same bound holds throughout the open disk.

## Differentiating on a smaller disk

The closed radius-$\sigma$ disk centered at $s=\sigma+it$ lies within distance $(2-\sigma)+\sigma=2$ of $a$. Cauchy's estimate there gives $|g^{(k)}(s)|/k!\ll\log X/\sigma^k$. In the Euler half-plane the identity $(-L'/L)^{(k)}=(-1)^k k!D_k$ follows by termwise differentiation, with local comparison to $\sum_{n\ge2}(\log n)^{k+1}n^{-1-\epsilon}$. The log derivative $F'/F$ adds $1/(s-1)$ when $\chi$ is principal. Each reciprocal has $k$th derivative $(-1)^k k!$ times its $(k+1)$st power. Substitute these into the Cauchy bound to get (1). At $s=2+it$ the remainder has $2^{-k}$ decay, while a nearby zero at the same height has a denominator close to $1$.

## Lean correspondence

- `extend`, `cauchy` and `derSeries_eq` give the holomorphic remainder, derivative bound and series identification. [Extension](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/IteratedDerivLogDerivDirichletLViaNearbyZeros.lean#L10) · [Cauchy estimate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/IteratedDerivLogDerivDirichletLViaNearbyZeros.lean#L47) · [Series](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/IteratedDerivLogDerivDirichletLViaNearbyZeros.lean#L103)
- `growth_triv` and `exists_entire` handle the principal case, and `main` gives (1). The Chinese note records replay of the upstream growth and disk inputs. [Growth](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/IteratedDerivLogDerivDirichletLViaNearbyZeros.lean#L119) · [Conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/IteratedDerivLogDerivDirichletLViaNearbyZeros.lean#L222) · [Forwarding statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/IteratedDerivLogDerivDirichletLViaNearbyZerosStatement.lean#L8)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
