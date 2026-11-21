# Weighted norm power classes in matrix group homology

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E6%8A%8A%E5%8A%A0%E6%9D%83%E8%8C%83%E6%95%B0%E7%9A%84%E5%B9%82%E7%B1%BB%E9%80%81%E8%BF%9B%E7%9F%A9%E9%98%B5%E7%BE%A4%E5%90%8C%E8%B0%83.md)

## Statement

Let $L$ be totally imaginary with $F/L,\ell,c,\nu,\zeta,\gamma$ satisfying `Lay` from [twisted character counting](counting-twisted-characters-with-class-groups-and-units.md). Take $k\ge0$ and write $M=2k+3$, $q=\ell^\nu$, $a=(1+\ell^c)^{k+1}$ and $b=2k+2+M(c+M)$. Require $M<\ell^c$ and $M<r_2(L)$. Let $S\subset F^\times$ be finite with each $\mathrm{div}(\alpha)=(\gamma^{-1}-a)\mathfrak d_\alpha$ and the classes of $N_a(\alpha)^{\ell^b}$ modulo $q$th powers pairwise distinct. Here $N_a(\alpha)=\prod_{j=0}^{\operatorname{ord}(\gamma)-1}\gamma^j(\alpha)^{a^j}$. Then
$$
\#S\le q^{r_2(L)}
\big|\operatorname{Tor}H_M(\mathrm{GL}_{2M+4}(O_L),\mathbb Z)\big|
\big|\operatorname{Tor}H_{M-1}(\mathrm{GL}_{2M+4}(O_L),\mathbb Z)\big|.
$$
This is `SFew`.

## Finite-field functionals and global cycles

Set $A=\mathbb Z/q\mathbb Z$. Chains are the usual bar chains and cycles are chains with zero boundary. Over a finite field $K$ with primitive $q$th root $\zeta_K$, take any homomorphism $v:K^\times\to A$. The family `Fam` of `STheta` gives functionals $\theta_V$ on degree-$M$ chains of $\mathrm{GL}(V)$ for finite-dimensional $K$-vector spaces. Condition `IsAdd` says they kill boundaries, are preserved by linear isomorphisms, and add on direct sums of representations evaluated on cycles. For `HasVal`, start with the designated cyclic degree-$(M-1)$ cycle $z_{q,k}$, mapped by $1\mapsto\zeta_K^x$ to scalar matrices. The conjugation prism for $g\in\mathrm{GL}(V)$ is the chain homotopy inserting $g$ at the successive positions, with boundary the difference of the conjugate and original chains. On this degree-$M$ chain, the functional has value $x^{k+1}v(\det g)$.

Reduce matrices along a surjection $O_L\to K$ to obtain a functional $\Phi_N$ on degree-$M$ chains of $\mathrm{GL}_N(O_L)$. It kills boundaries, retains values on cycles upon adjoining identity blocks, and multiplies values by $d$ upon repeating $d$ identical blocks. The last two facts follow from additivity and the vanishing of positive-degree homology for the trivial group.

The [global cycle construction](../zh/%E6%80%8E%E6%A0%B7%E6%8A%8A%E6%89%AD%E6%9B%B2%E4%B8%BB%E5%9B%A0%E5%AD%90%E5%8F%98%E6%88%90%E4%B8%80%E4%B8%AA%E5%85%A8%E5%B1%80%E5%91%A8%E6%9C%9F.md) `SClass` gives, for each admissible $\alpha$, a size $N_\alpha$, an $M$-cycle $y_\alpha$ over $O_L$ and $b_\alpha\in O_F\setminus\{0\}$. For any finite-field reduction $O_F\to K$ where $O_L\to K$ is onto and $b_\alpha$ survives, $N_a(\alpha)$ reduces to a unit $u$. Then for every such family of functionals,
$$
\Phi_{N_\alpha}(y_\alpha)=P v(u),\qquad
P=\prod_{\substack{0\le j<M\\ j\ne k+1}}
\big((1+\ell^c)^{k+1}-(1+\ell^c)^j\big)
$$
in $A$. The cycle and the exclusion element are chosen before the reduction.

## Power classes are detected by the values

Use primes $\mathfrak p$ of $F$ avoiding $b_\ast=\ell\prod_{\alpha\in S}b_\alpha$ with $O_L\to K_\mathfrak p$ surjective. The root of unity remains primitive, since a primitive $\ell$th root reducing to one would force $\ell=0$ by its cyclotomic polynomial. The multiplicative residue group is cyclic of order divisible by $q$, so choose $v_\mathfrak p$ with kernel its $q$th powers. Map $\alpha$ to the vector of $\ell^{2k+2}\Phi_{N_\alpha,\mathfrak p}(y_\alpha)$ at these primes.

Equal vectors for $\alpha,\alpha'$ imply $\ell^{2k+2}P(v_\mathfrak p(u)-v_\mathfrak p(u'))=0$. Each factor of $P$ is an $\ell$-unit times a difference $(1+\ell^c)^d-1$ with $1\le d<M<\ell^c$, of valuation $c+v_\ell(d)<c+M$. Thus $P$ divides $\ell^{M(c+M)}$ in $A$. Multiply by the remaining factor to get $v_\mathfrak p((u/u')^{\ell^b})=0$. In particular $\beta=(N_a(\alpha)/N_a(\alpha'))^{\ell^b}$ is a $q$th power in these residue fields.

For global detection, take $x^q=\beta$ and $E=F(x)$. It is Galois over $F$ as $\mu_q\subset F$. Each $\sigma\in\operatorname{Gal}(E/F)$ is realized, up to choice of place, at a good prime with prime residue field in $F$ by degree-one Chebotarev. For example, extend $\sigma$ to the Galois closure over $\mathbb Q$ and choose Frobenius equal to the extension. Since it fixes $F$, the corresponding place of $F$ has degree one. This ensures $O_L$ maps onto its residue field. Exclude ramified primes, $\ell$, and primes where $\beta$ is not a unit. The residue polynomial has all its roots in that field because it has one root and all of $\mu_q$. Hence Frobenius fixes the reduction of $x$. The ratio $\sigma(x)/x$ is a $q$th root of unity, and reduction is injective on these, so $\sigma(x)=x$. Therefore $x\in F$. The hypothesized distinct global classes make the value-vector map injective.

## Counting the vectors

Combine the finite-field functionals into one vector-valued family. It still kills boundaries, preserves stabilization, and adds repeated blocks. The [Bockstein and rank estimate `SUpper`](bockstein-and-stable-rank-count-cycle-values.md) bounds the number of distinct $\ell^j$-scaled degree-$(j+1)$ values for even $j$ with $j+1<r_2(L)$ by $q^{r_2(L)}$ times the two torsion orders at rank $2(j+1)+4$. Take $j=2k+2$. The injection now gives the asserted bound.

## Lean correspondence

- [`STheta`, `SClass`, `SUpper` and `SFew`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/LemmaKOfSteps.lean#L55) give the interfaces. [`Fam`, `IsAdd` and `HasVal`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/HasVal.lean) give the finite-field functionals.
- [`sThetaOf`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/SThetaOf.lean), [`sPhi`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/PiRepApply.lean#L82) and [`sClassOf`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/SClassOf.lean#L21) construct the functionals, reductions, and cycles.
- [`sFewOf` and `pe_dvd`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/EtaleCohomology/CyclotomicDiscriminants/SFewOfCut.lean) combine the estimates, using [global power detection](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/EtaleCohomology/CyclotomicDiscriminants/SDetectCut.lean#L101).

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
