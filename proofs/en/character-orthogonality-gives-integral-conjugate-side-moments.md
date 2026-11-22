# Character orthogonality gives integral conjugate-side moments

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Keep the split word-prime data $p=\pi\bar\pi$ and the period lattice $M$ of the original theta pair. Use a pair on which the conjugate side is seen. Put $u=\pi/\bar\pi$, so $u\bar u=1$ and $puM\subseteq M$. Let $B$ be the half-lattice with $guM\subseteq B$, $gu^{-1}B\subseteq M$, integral translation cocycle on $B$, and $g$ prime to $p$. Assume the bracket-twisted point moment law for translates of the vacuum $e$, with multiplier $u$ and denominator $N_0$ prime to $p$. For admissible $x$ integral at the primes dividing $\pi$, use the rational lift $t$ with $cgt\in M$ ($c$ prime to $p$) and $t-x\in p\operatorname{Hom}_P$ at these primes. Here $\operatorname{Hom}_P$ consists of maps from the localized source lattice to the localized target. Suppose the induced theta is $n^{-1}W(-t)\sum_{y\in R} W(y)e$, where $R$ represents $B/(B\cap M)$ and $0<n\mid[M:M\cap B]$. The finite theta formula is [the half-lattice indicator calculation](the-induced-theta-is-a-finite-period-translate-sum.md). Its jet table has integral closure in the unscaled normalized point tables for $x'$ with $x'-x\in p\operatorname{Hom}_P$ at every $P\mid\pi$.

### Reorganizing the finite sum

Choose representatives $R_2$ for $pB/(pB\cap M)$. Since $gpB\subseteq M$, each $y_2-t$, for $y_2\in R_2$, belongs to $M$ after multiplication by $cg$. Apply the bracket-twisted moments to these translates. Take $N_1=cg\prod_{y_2\in R_2}N_0(y_2)$, a common multiple prime to $p$, and let $R_1$ represent $N_1uM/(N_1uM\cap M)$. We have $N_1uM\subseteq B$. For $y\in B$, $gu^{-1}y\in M$, so $N_1gy\in N_1uM$. Using a Bézout relation for $N_1g,p$ gives $B=N_1uM+pB$. If $y_1+y_2\in M$ with $y_1\in N_1uM$, $y_2\in pB$, then $gy_1\in M$ and $py_1\in M$, giving $y_1\in M$. The two coset sets therefore give product representatives for the original sum. The vacuum is fixed by $W(M)$, and integrality of the cocycle on $B$ permits the regrouping.

For a fixed $y_2$, commuting $W(-t)$ past $W(y_1)$ writes its portion of the sum as
$$
\sum_{y_1\in R_1}\gamma_{y_2}\,\operatorname{brk}(y_1,-t)\,
    W(y_1)W(y_2-t)e ,
$$
where $\gamma_{y_2}$ is $1/n$ times a rational cocycle phase. Each $y_1$ is a translate allowed by the moment law for $y_2-t$ since $N_0(y_2)\mid N_1$. One may approximate all these jets simultaneously by that law. For any point $x'\in M$ in such an approximation, the weights are then multiplied by
$$
\lambda(\gamma_{y_2})\sum_{y_1\in R_1}\lambda(\operatorname{brk}(y_1,x'-t)).
$$
This formula uses the same approximating coefficients for every $y_1$ under consideration, which is why the finite moment closure is stated simultaneously in the point and jet indices.

### Support and normalization

Let $s=x'-t$. We have $N_1s\in M$. The bracket on $N_1uM$ is a character of its quotient by $M\cap N_1uM$. Indeed, if $y=N_1um$ also lies in $M$, then $N_1um,pu m\in M$ imply $um\in M$, and $\omega(y,s)=\omega(um,N_1s)$ is integral. The character is trivial precisely when $\omega(N_1um,s)$ is integral for every $m\in M$. Adjointness of scalar multiplication for $\omega$ and self-duality express this condition as $N_1\bar u s\in M$, or $N_1s\in uM$. Character orthogonality therefore makes the weight zero off this condition, and otherwise multiplies it by $|R_1|$. At $P\mid\pi$ the element $\pi$ generates the same localized ideal as $p$, whereas $\bar\pi,N_1$ are units. Thus $N_1s\in uM$ implies $s\in p\operatorname{Hom}_P$. Adding $t-x$ gives the desired residue condition.

Put $K_0=uM$. Its self-duality follows from $u\bar u=1$. The index $|R_1|=[K_0:K_0\cap M]=[M:M\cap K_0]$: multiplication by $N_1$ preserves the relative index because $pK_0\subseteq M$, and the two relative indices agree by the perfect alternating pairing of the quotients. As $gK_0\subseteq B$,
$$
n\mid[M:M\cap B]\mid[M:M\cap gK_0].
$$
Here $M\cap gK_0=g(M\cap K_0)$, since $pK_0\subseteq M$ and $g$ is prime to $p$. Hence the last index is $|R_1|$ times a power of $g$, since the period lattice is a free abelian group of finite rank. It follows that $|\,|R_1|/n\,|_p\le1$. Rational phases have norm one, so all surviving weights are integral. The finite sum over $y_2$ preserves closure and gives the stated result. Its support preserves the residue functional whenever $x$ did, because adding $p$ times a homomorphism changes its value by zero in the residue field.

### Lean correspondence

- [`char_sum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/RelIndexNeZeroOfSmul.lean#L186) gives the finite character filter, and [`clo_class`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/RelIndexNeZeroOfSmul.lean#L207) applies it simultaneously to the moment functions.
- [`relIndex_dvd`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/RelIndexNeZeroOfSmul.lean#L61) accounts for the prime-to-$p$ factor.
- [`moments_thInd`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/RelIndexNeZeroOfSmul.lean#L251) gives the unscaled conjugate-side closure, which [`type_bar`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MemSuppBarOfNe.lean#L248) uses before summing the actual weighted jet table.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
