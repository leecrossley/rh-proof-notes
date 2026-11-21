# The local log derivative from zeros in a disk

[Chinese proof](../zh/%E5%9C%86%E7%9B%98%E9%87%8C%E7%9A%84%E9%9B%B6%E7%82%B9%E6%80%8E%E6%A0%B7%E6%8E%A7%E5%88%B6%E5%AF%B9%E6%95%B0%E5%AF%BC%E6%95%B0.md)

**Disk lemma.** Fix $0<r<R<1$. There is a constant $C=C(r,R)>0$ with the following property. Let $f$ be holomorphic on a neighborhood of the closed unit disk, with $f(0)\ne0$ and $|f|\le M$ there. Set
$$
S=\{w:|w|\le R,\ f(w)=0\},\qquad
m_w=\operatorname{ord}_w f,\qquad L=\log(M/|f(0)|).
$$
Then $S$ is finite, $\sum_{w\in S}m_w\le C(1+L)$, and every $z$ with $|z|\le r$ and $f(z)\ne0$ satisfies
$$
\left|\frac{f'(z)}{f(z)}-\sum_{w\in S}\frac{m_w}{z-w}\right|\le C(1+L).
\tag{1}
$$

## Removing the zeros

By the identity theorem the zeros are isolated, and the radius-$R$ disk is compact. Let $J=\sum_{w\in S}m_w$. Removing the vanishing Taylor factors writes $f(z)=g(z)\prod_{w\in S}(z-w)^{m_w}$ with $g$ holomorphic near the closed unit disk and nonzero for $|z|\le R$. On $|z|=1$ the equality $|1-\bar w z|=|z-w|$ permits applying the maximum modulus principle to
$$
G(z)=g(z)\prod_{w\in S}(1-\bar w z)^{m_w}.
$$
Thus $|g(0)|=|G(0)|\le M$. Since $|f(0)|=|g(0)|\prod_{w\in S}|w|^{m_w}\le MR^J$, we have $J\le L/(-\log R)$.

On the unit circle $|z-w|\ge1-R$, so $|g(z)|\le M/(1-R)^J$, and this bound holds inside by the maximum modulus principle. Let $K=1+L-J\log(1-R)>0$. As $|g(0)|\ge|f(0)|$, we have $|g(z)|\le |g(0)|e^K$. On $|z|<R$, take the primitive $h$ of $g'/g$ with $h(0)=0$. Differentiating $g e^{-h}$ gives zero, so $g(z)=g(0)e^{h(z)}$ and $\Re h(z)\le K$. The map $h/(2K-h)$ is holomorphic, vanishes at zero, and has modulus at most $1$ because $|2K-h|^2-|h|^2=4K(K-\Re h)\ge0$. Schwarz's lemma on the disk of radius $R$ gives $|h(u)|\le2K|u|/(R-|u|)$.

For $|z|\le r$, put $d=(R-r)/2$. On the circle about $z$ of radius $d$, $|u|\le R-d$ and hence $|h(u)|\le2KR/d$. Cauchy's estimate gives $|g'/g(z)|\le2KR/d^2$. The product rule gives $f'/f=\sum m_w/(z-w)+g'/g$. With the bound on $J$ above, one possible common constant for (1) and the zero count is
$$
C=\frac{1}{-\log R}
+\frac{8R}{(R-r)^2}\left(1+\frac{-\log(1-R)}{-\log R}\right).
$$
The Lean proof uses a Borel–Carathéodory estimate in its bound on $g'/g$. The Schwarz-lemma argument gives that estimate in the form needed here.

## Scaling the disk

If $F$ is holomorphic near the closed disk with center $c$ and radius $a>0$, with $|F|\le M$ and $F(c)\ne0$, apply (1) to $f(z)=F(c+az)$. The zeros $W=c+aw$ keep their multiplicities, and lie in $|W-c|\le aR$. For $s=c+az$ the expression on the left of (1) is $a$ times the modulus of $F'(s)/F(s)-\sum_W m_W/(s-W)$. This gives the project lemma `disc` for $|s-c|\le ar$. The zero count is unchanged.

## Application to the vertical strip

The project uses the following [polynomial growth bounds](l-function-growth-from-finite-differences.md) with absolute constants. For every nonprincipal $\chi$ modulo $q\ge1$ and $\Re z\ge-7/4$,
$$
|L(z,\chi)|\le B q^4(|z|+2)^4.
$$
For $\zeta_1(z)=(z-1)\zeta(z)$, continued with $\zeta_1(1)=1$, one has $|\zeta_1(z)|\le B'(|z|+2)^5$ there. A lower bound on the disk center follows from the inverse Dirichlet series. For $\sigma=\Re z>1$ absolute convergence gives $L(z,\chi)\sum_{n\ge1}\mu(n)\chi(n)n^{-z}=1$ since $\sum_{d\mid n}\mu(d)=0$ for $n>1$. The inverse series has modulus at most $\sigma/(\sigma-1)$ by the integral test, so $|L(z,\chi)|\ge(\sigma-1)/\sigma$. This includes modulus $1$.

For $s=\sigma+it$ with $-1\le\sigma\le2$, set $c=2+it$, $a=15/4$, $r=4/5$, and $R=14/15$. Then $ar=3$, $aR=7/2$, and $|s-c|\le ar$. On the outer disk $\Re z\ge-7/4$ and $|z|+2\le4(|t|+2)$. For nonprincipal $\chi$ the center value is at least $1/2$ in modulus, and we can use $M=256B[q(|t|+2)]^4$. The scaled formula gives, with $S_t$ the zeros in $|w-c|\le7/2$,
$$
\sum_{w\in S_t}m_w\ll\log(q(|t|+2)),\qquad
\left|\frac{L'(s,\chi)}{L(s,\chi)}-\sum_{w\in S_t}\frac{m_w}{s-w}\right|
\ll\log(q(|t|+2))
$$
when $L(s,\chi)\ne0$. For $\zeta_1$ the center value is also at least $1/2$, since $|c-1|\ge1$. Use $M=(B'+1)[4(|t|+2)]^5$. The multiset of zeros of $\zeta_1$ consists of the zeros of $\zeta$ with their multiplicities, and the point $1$ contributes none. Thus for $\zeta(s)\ne0$ and $s\ne1$ the same argument gives
$$
\sum_{w\in S_t}m_w\ll\log(|t|+2),\qquad
\left|\frac{\zeta'(s)}{\zeta(s)}+\frac1{s-1}-\sum_{w\in S_t}\frac{m_w}{s-w}\right|
\ll\log(|t|+2).
$$
The term $1/(s-1)$ comes from differentiating the factor $s-1$.

## Lean correspondence

- `exists_factor_order` removes one zero, and `GlobalTheory.LogDerivZeros.main` proves the disk lemma using `norm_logDeriv_le`. [One factor](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsFactorOrder.lean#L7) · [Error](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/NormOneSubConjMul.lean#L49) · [Disk lemma](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/NormOneSubConjMul.lean#L125)
- `norm_LFunction_ge` supplies the center bound. [Center](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/TsumOneDivRpowLe.lean#L62) · [Dirichlet growth](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SummableNinePowMulInvSqSucc.lean#L269) · [Zeta growth](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/NormSubOneMulRiemannZetaLe.lean#L188)
- `disc`, `logDeriv_LFunction_strip`, and `GlobalTheory.ZetaWide.main` give the scaled and strip versions. The latter verifies orders of vanishing using `order_zeta₁_eq`. [Scaling](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LogDerivLFunctionStrip.lean#L9) · [Dirichlet strip](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LogDerivLFunctionStrip.lean#L73) · [Zeta strip](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ImportsMore.lean#L90)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
