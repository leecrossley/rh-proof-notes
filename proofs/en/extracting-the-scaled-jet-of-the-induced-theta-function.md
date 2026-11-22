# Extracting the scaled jet of the induced theta function

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Use the arithmetic period lattice and split level $p c'$ of [the Heisenberg quotient calculation](the-split-prime-part-of-the-heisenberg-cosets.md), and the good CM curve, normalized theta and frame hypotheses of [the scaled theta estimate](the-two-split-embeddings-give-the-same-scaled-theta-bound.md). Suppose that the affine coset parameter $x$ of the induced theta function lies in $(c')^{-1}M_S$, where $M_S$ is the module of homomorphisms integral at the selected places. The lift of this parameter into the complex homomorphism space is $s_0$, with $c' s_0\in\Lambda$ by the [annihilator calculation for arithmetic lifts](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/AlgebraicTheory/AlgebraicTheoryProofs/KerHalf.lean#L78). The source denotes the resulting analytic function by $\Theta_{\rm ind}(z)=\mathrm{thInd}(S,N,N',p c',x)(z)$. For a multi-index $m$ in its $n=fab$ variables let $J_m$ denote the field-valued jet, with differentiation in the normalized directions $c_\tau$ of the arithmetic kernel. In the chosen coefficient embedding it is the complex normalized derivative if that value lies in the field, and zero otherwise. Then
$$
\bigl|\iota(J_m)\bigr|\,\bigl|\iota(\bar\pi)\bigr|^{|m|}\,|p|_p^{\,n}\le1.
\tag{1}
$$
Here $\iota$ on a field-valued jet means its given complex embedding followed by the chosen comparison with $\mathbb C_p$. The bound used for the arithmetic jet sum applies (1) at indices whose rationality has been established.

## The Fourier average for this coset

Identify the complex homomorphism space with $\mathbb C^n$ by listing its $n$ entries. The finite Heisenberg formula in the source expresses $\Theta_{\rm ind}$ in terms of a normalized theta section $\theta$ on $\Lambda$. Write $S_1,S_2$ for the $c'$-part and the $p$-part representatives as above, $h=|S_1|$, $Q=p^n$, and $\alpha$ for the quadratic phase. The formula at positive volume is
$$
\Theta_{\rm ind}(z)=\frac{\alpha(s_0)}{hQ}\sum_{k\in S_1}
 \alpha(k) U_{-s_0}U_k
 \left(\sum_{a\in S_2}\alpha(a)U_a\theta\right)(z).
\tag{2}
$$
The underlying sum over $B/(B\cap\Lambda)$ is independent of the representatives because the normalized theta is invariant under $\alpha(y)U_y$ for $y\in B\cap\Lambda$, and the semicharacter law makes $\alpha(y)U_y$ an action on $B$. Splitting the quotient by the two coprime orders gives the iterated sum in (2). The two inverse square roots of the volume in the analytic induction cancel the volume in its coefficient, leaving the reciprocal of the other Heisenberg index, which is $1/(hQ)$ by the two-sided character computation.

By the split lattice calculation $S_2$ represents $(\bar\pi/\pi)\Lambda/\bar\pi\Lambda$. Choose $S_b$ representing $\Lambda/\bar\pi\Lambda$ and define $\Psi$ on it to be $1/h$ on the unique zero coset representative and zero elsewhere. The coefficient $1/h$ is a $p$-adic unit. For any $b_0\in\bar\pi\Lambda$ and $a\in S_2$, write $b_0=\bar\pi \ell$, $a=(\bar\pi/\pi)\ell'$ with $\ell,\ell'\in\Lambda$. Hermitian sesquilinearity gives $e(b_0,a)=e(\pi\ell,\ell')\in\mathbb Z$, since $e$ is integral on $\Lambda$ and $\pi$ preserves $\Lambda$. Therefore the Fourier coefficient $\widehat\Psi(a)$ of the scaled theta estimate is exactly $1/(hQ)$. Its function $G$ is the inner sum of (2) multiplied by $1/(hQ)$.

By the Heisenberg translation law,
$$
\Theta_{\rm ind}=\sum_{k\in S_1} r_k U_{t_k}G,\quad
t_k=-s_0+k,\quad
r_k=\alpha(s_0)\alpha(k)\exp(-\pi_{\mathbb R} i e(-s_0,k)).
$$
We have $c' k,c' s_0\in\Lambda$, whence $c't_k\in\Lambda$. The quadratic phases of $s_0$ and $k$ are roots of unity, since their $(c')^2$-th powers are signs on $\Lambda$. Also $(c')^2 e(-s_0,k)$ is an integer, so the remaining phase is a root of unity. Thus $|\iota r_k|=1$. This is the prime-to-$p$ torsion and coefficient control required in the scaled theta estimate, with $N=c'$. If the normalizing volume is zero, the convention in the induced function makes it zero and (1) holds directly.

## The derivative calculation

The frame of the standard kernel expresses the diagonal matrix of the arithmetic normalizing directions $c_\tau$ as the product of the CM period directions with a matrix $M$ of coefficients of norm at most one. Multiply those entries by $\iota(\bar\pi)$. The resulting frame satisfies the hypothesis of the scaled theta estimate and induces the diagonal substitution with entries $\iota(\bar\pi c_\tau)$. Apply the estimate to (2). The $m$-th derivative at zero of a series is its coefficient multiplied by $\prod_\ell m_\ell!$. A diagonal substitution multiplies that coefficient by the product of the diagonal entries to the powers prescribed by $m$. Therefore we obtain exactly
$$
\left|p^n\,\iota(\bar\pi)^{|m|}
       \iota\!\left(\prod_{\ell}c_{\tau(\ell)}^{m_\ell}
       \partial^m\Theta_{\rm ind}(0)\right)\right|\le1 .
$$
The extra scalar dividing this derivative to define the field jet has norm one in the standard kernel. With that division the same bound holds, and the convention for a derivative outside the coefficient field also satisfies it. This proves (1) and supplies the input (2) in [the coset-level comparison](changing-the-coset-level-isolates-the-auxiliary-prime.md).

## Lean correspondence

- [`kernel_index_form`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/AlgebraicTheory/AlgebraicTheoryProofs/KernelIndexForm.lean#L14) expands the induced function and cancels the volume factors in (2).
- [`jetAtSplit_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/AlgebraicTheory/AlgebraicTheoryProofs/CardTwoSidedQuotient.lean#L349) chooses the two sets of representatives, constructs the Fourier weight supported on the zero coset, and applies the scaled estimate through the diagonal frame.
- [`jetAtSplit`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/AlgebraicTheory/LocNormScale.lean#L12) assembles the inputs. [`jetAtSplit_ambOf`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/KernelLocalFactors/SelfDualLatticeNorms.lean#L110) gives the form used on the arithmetic kernel.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
