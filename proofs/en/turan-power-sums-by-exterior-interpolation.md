# Turán's second power-sum theorem by exterior interpolation

[Chinese proof](../zh/%E5%A4%8D%E5%B9%82%E5%92%8C%E4%B8%BA%E4%BB%80%E4%B9%88%E5%9C%A8%E4%BB%BB%E4%BD%95%E8%BF%9E%E7%BB%AD%E9%98%B6%E6%95%B0%E6%AE%B5%E4%B8%AD%E9%83%BD%E6%9C%89%E5%A4%A7%E5%80%BC.md)

**Proposition.** Let $N\ge1$, $M\ge0$ be integers, $z_1,\ldots,z_N\in\mathbb C$, and $1\le i_0\le N$. There exists $j\in\{M+1,\ldots,M+N\}$ such that
$$
\left|\sum_{i=1}^N z_i^j\right|
\ge\left(\frac{N}{16e^2(M+N)}\right)^N |z_{i_0}|^j.
\tag{1}
$$
The $z_i$ may repeat.

## Separating the points by a circle

First normalize $\max_i|z_i|=1$. Set $\delta=N/(2(M+N))\in(0,1/2]$ and $D=(\delta/(2e))^N$. Some $r\in[1-\delta,1]$ satisfies $\prod_i|r-|z_i||\ge D$. To prove this, for $Q(r)=\prod_i(r-|z_i|)$ rescale $P(x)=Q(1-\delta/2+(\delta/2)x)/D$. The leading coefficient is $e^N>2^{N-1}$. If $|P|\le1$ on $[-1,1]$, subtract its leading term by considering $T_N-(2^{N-1}/e^N)P$, where $T_N(\cos v)=\cos(Nv)$. The Chebyshev recurrence gives leading coefficient $2^{N-1}$ for $T_N$. The difference has degree at most $N-1$ yet alternates signs at $\cos(j\pi/N)$ for $0\le j\le N$, requiring at least $N$ distinct zeros. This contradiction proves the product bound.

Let $S=\{i:|z_i|>r\}$, $T=\{i:|z_i|<r\}$, and $\ell=|S|\ge1$. No point has modulus $r$, and a point of modulus $1$ lies outside the circle. Define $P_S(w)=\prod_{i\in S}(w-z_i)$ and $F_T(w)=\prod_{i\in T}(w-z_i)$. On $|w|=r$ the reverse triangle inequality gives $|P_S(w)F_T(w)|\ge D$.

## Interpolating outside the circle

We use the following fact. Suppose $0<r\le1$, $r<|u_i|\le1$ for $1\le i\le\ell$, $P_*(w)=\prod_i(w-u_i)$, and $g$ is continuous on $|w|\ge r$, holomorphic on $|w|>r$ and tends to zero at infinity. If $|g(\zeta)|\le G|P_*(\zeta)|$ on $|\zeta|=r$, there is a polynomial $\sum_{j=0}^{\ell-1}c_j w^j$ taking value $g(u_i)$ at every $u_i$ and with $\sum_j|c_j|\le4^\ell rG$.

To see this, write $P_*=\sum_{k=0}^\ell a_k w^k$, so $\sum |a_k|\le2^\ell$. Expand
$$
\frac{P_*(\zeta)-P_*(w)}{\zeta-w}=\sum_{j=0}^{\ell-1} b_j(\zeta)w^j,\qquad
b_j(\zeta)=\sum_{k=j+1}^\ell a_k\zeta^{k-1-j}.
$$
On the circle $|b_j(\zeta)|\le2^\ell$. Take
$$
c_j=-\frac1{2\pi i}\oint_{|\zeta|=r}\frac{g(\zeta)}{P_*(\zeta)}b_j(\zeta)\,d\zeta
$$
with the circle oriented counterclockwise. At $w=u_i$ the quotient has numerator $P_*(\zeta)$, so the interpolation value is $-(2\pi i)^{-1}\oint g(\zeta)/(\zeta-u_i)d\zeta=g(u_i)$ by the residue theorem in the exterior annulus. The outer boundary term tends to zero as the radius tends to infinity by the decay of $g$. The inner boundary integral follows by approaching $r$ from above. Each $|c_j|\le rG2^\ell$, and $\ell\le2^\ell$ gives the coefficient bound.

Apply this with $P_*=P_S$ and $g(w)=1/(w^{M+1}F_T(w))$. This function is holomorphic outside the circle and tends to zero, and the product bound gives $G=(r^{M+1}D)^{-1}$. Multiplying the interpolating values by $z_i^{M+1}F_T(z_i)$ gives $1$ at each $i\in S$ and $0$ at each $i\in T$. Summing gives
$$
|S|=\sum_{j=0}^{\ell-1}c_j\sum_{i=1}^N z_i^{M+1+j}F_T(z_i).
$$
Let $B=\max_{M+1\le k\le M+N}|\sum_i z_i^k|$. The sum of absolute coefficients of $F_T$ is at most $2^{|T|}$. The largest power after expansion is $M+1+(\ell-1)+|T|=M+N$. Hence $1\le |S|\le4^\ell rG2^{|T|}B\le4^N B/(r^M D)$.

As $r\ge1-\delta=(1+N/(2M+N))^{-1}$, we have $r^M\ge e^{-N}$. Thus $B\ge4^{-N}e^{-N}D=(N/(16e^2(M+N)))^N$. For arbitrary $z_i$ with nonzero maximum modulus, normalize by a maximal-modulus $z_{i_1}$ and multiply the power sum back by $z_{i_1}^j$. Then $|z_{i_1}|\ge |z_{i_0}|$ gives (1). If all points are zero, any $j$ works.

## Lean correspondence

- `exists_prod_abs_sub_ge_on_segment` uses the Mathlib leading-coefficient bound for Chebyshev polynomials. `GlobalTheory.ExteriorInterpolation.interpolation` gives the exterior interpolation. [Product bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsProdAbsSubGeOnSegment.lean#L8) · [Interpolation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsInterpolationExteriorSmallCoeffs.lean#L224)
- `norm_sum_pow_mul_prod_le` and `core` expand the inner product, and `powerSum_second_main` completes the normalization and maximum. [Expansion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/TuranSecondMainTheoremPowerSumsUnitCoefficients.lean#L9) · [Conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/TuranSecondMainTheoremPowerSumsUnitCoefficients.lean#L205)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
