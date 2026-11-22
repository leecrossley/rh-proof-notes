# Evaluating the arithmetic kernel gives the point kernel at representatives

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix the project's tied true-chain data with the admissibility and jet-rationality hypotheses, a word $u$, one of its indexed twists, a step $0\le i<m$, and representatives $c,c'$ of source and target classes. Write $K$ for the coefficient field and $\sigma:K\to\mathbb C$ for its fixed embedding. Let $F$ be a coefficient-field polynomial in the true weight space at $i$. Denote the arithmetic coefficient kernel at the two representatives by $k$, the complex point operator by $K_{\mathrm{pt}}$, and evaluation of a polynomial on the layer's frames by $\operatorname{ev}_i$, including the layer's determinant weight. Then
$$
K_{\mathrm{pt}}(c,c')\,\operatorname{ev}_i(F)
=\operatorname{ev}_{i+1}\bigl(k(c,c')F\bigr).
$$
The hypotheses include the normalized theta-vector law, the local lattice conditions and smoothness of the induced theta vectors, the rationality of the relevant kernel jets, the arithmetic box support and periodicity, and the tied determinant character identities. The statement compares the operators at representatives.

### The common polynomial

Let $a,b$ be the successive ranks, and denote the source and target true weight lists at each embedding $\tau$ by $\lambda_\tau,\lambda'_\tau$. Their determinant shifts are the last weights $d_\tau,d'_\tau$. If the sharp shift is $s'_\tau$ and the output divisor exponent is $s_\tau$, compatibility reads $n_\tau=d_\tau+s'_\tau$, $d'_\tau=-s_\tau$. Set $F^\sharp=F\prod_\tau\det(X_\tau)^{n_\tau}$. An evaluation of $F$ on an invertible frame already contains its determinant factor to exponent $d_\tau$. Multiplying it by the extra sharp factor of exponent $s'_\tau$ therefore gives exactly the evaluation of $F^\sharp$.

For a box representative $x$, let $\Theta_x$ be its induced theta, and let $\Xi(x)\in K$ be its coefficient. The box is a finite lattice quotient, and its indicator and weights are constant modulo the congruence lattice. The complex distribution kernel has the same expression $\sum_x\sigma(\Xi(x))\Theta_x$ by the finite theta induction identity. Thus its jet table is the same finite sum of the individual tables by linearity of each derivative. To see that the arithmetic table reads back this complex table, expand the substitution defining the jet operator on $F^\sharp$. Each entry of a parameter matrix has degree one in its embedding. The sum of the degrees of the parameters at $\tau$ is therefore the total degree of $F^\sharp$ there, namely $\sum_{j=1}^a(\lambda_{\tau,j}+s'_\tau)$. These are precisely the rationality degrees. For each term used by the operator, the arithmetic jet in $K$ embeds to the complex jet divided by the determinant-ideal character factor $\chi_F$. The embedding can be moved through the finite sum and the polynomial coefficients. Consequently the image of $k(c,c')F$ under coefficient embedding is the polynomial obtained by applying the complex jet table to $\sigma(F^\sharp)$ and multiplying by
$$
\sigma\!\left(m(c)m(c')^{-1}\right)\chi_F^{-1},
$$
where $m$ is the product of local determinant-character values of the framed lattice.

### The two scalar comparisons

The tied character identities identify this scalar with the point operator's source and target factors $\rho(c)\rho'(c')$. In the source proof each $\rho$ is first read as a local Hecke character on the determinant of its representative. The local-to-ideal character law reads the same determinant as an ideal-character value. The source and target occurrences of those ideal factors have the opposite powers prescribed by $\chi_F$, while the remaining terms give the source $m(c)$ and inverse target $m(c')^{-1}$. Thus they give the displayed scalar.

Finally the target frame formula of the point operator divides by the determinant to the power $s_\tau$, which is multiplication by the determinant to the power $d'_\tau$. This is exactly $\operatorname{ev}_{i+1}$ on the embedded arithmetic polynomial. Equality on every invertible target frame proves the claimed operator identity and supplies the representative comparison in [the pointwise valuation proof](coefficient-kernel-bounds-pass-to-all-word-prime-points.md).

### Lean correspondence

- [`map_kerOf`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/KmapOfOkOfVecP.lean#L96) identifies the finite arithmetic jet with the complex one at the required degrees.
- [`rhoIs`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/KmapOfOkOfVecP.lean#L271) compares the character factors. [`kmap_of_jet`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/KmapOfOkOfVecP.lean#L50) compares the sharp and target determinant weights.
- [`kmap_dat`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/TrueChainKernelEqPointKernelAtRepresentatives.lean#L14) applies both comparisons to the actual representatives, using the indicated true-chain hypotheses.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
