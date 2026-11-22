# A prime-to-p lattice index transfers scaled derivatives

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Use the self-dual host theta lattice $\Lambda\subset\mathbb C^n$, its theta section $\theta$, an integral CM curve lattice $\mathcal L$ with good reduction at the odd prime $p\nmid d$, and a field identification $\iota:\mathbb C\cong\mathbb C_p$. Assume the [fourfold kernel identity](four-theta-copies-as-a-finite-sum-of-one-variable-translates.md#the-finite-average-after-translation) with isometry $g$, scalar of norm at most one, and corresponding lattices $\Gamma_b=g\Lambda^4$, $\Gamma_s=\mathcal L^{4n}$ with both relative indices finite and $I=[\Gamma_b:\Gamma_b\cap\Gamma_s]$ prime to $p$.

For each translate of $\theta$ at $t$, assume $\beta t,Mt\in\Lambda$ with $\beta$ a CM integer of $p$-adic norm one and $M>0$ an integer. Take a finite list $v_j$ of complex vectors with $v_j\mathcal L\subseteq\Lambda$, and a matrix of coefficients $A_{ji}\in\mathbb C_p$ with $|A_{ji}|\le|M|_p$. In the Taylor series of $U_t\theta$, transport the coefficients and substitute the linear forms with matrix $F$ whose $i$-th column is $\sum_j\iota(v_j)A_{ji}$. Then every derivative at zero is integral. The same holds for finite sums of these translates with integral coefficients and the same $\beta,M$, and for the value of any polynomial differential operator with integral coefficients. This is the torsion input `EtLoc` for the scaled split-prime estimate.

## Clear the index in the torsion points

In the fourfold identity for the translate $U_t\theta$, put $b=g(t,t,t,t)$. Its expression in the standard variables is a sum indexed by representatives $x\in\Gamma_b$ of the relative quotient. The coefficient is the normalized kernel scalar times $I^{-1/2}$, the semicharacter sign, and the phase $\exp(-\pi_{\mathbb R}i e(b,x))$ in the notation of the [two split cases](the-two-split-embeddings-give-the-same-scaled-theta-bound.md). The phase is a root of unity because $M b\in\Gamma_b$ and $e$ is integral on $\Gamma_b$. All these coefficients are therefore integral, regardless of the divisibility of $M$ by $p$.

On each independent coordinate the factor is the standard half-period theta translated to the coordinate of $b+x$. Since $\beta,M$ preserve $\Gamma_b$, and $\beta b,Mb\in\Gamma_b$, both $I\beta(b+x)$ and $IM(b+x)$ belong to $\Gamma_s$. Indeed multiplication by $I$ kills the relative quotient. Thus these translated coordinates are killed modulo the standard period lattice by $I\beta$ and $IM$. The first is still a CM unit in the chosen embedding and $|IM|_p=|M|_p$. By the [one-variable scaled derivative estimate](taking-a-logarithmic-derivative-pays-for-p-power-torsion.md), every coefficient of this fourfold product multiplied by its multi-index factorial and $M$ to its total degree has norm at most one. This holds for the whole sum as well. In other words the transported series of $(U_t\theta)^{\boxtimes4}(g^{-1}(M Y))$ has integral derivatives.

## Transport the linear forms

Let $v_{j,a}$ be $v_j$ in copy $a$ of the fourfold space, with the other copies zero. Because $v_j\mathcal L\subseteq\Lambda$ and $I\Gamma_b\subseteq\Gamma_s$, each coordinate of $I g v_{j,a}$ preserves $\mathcal L$ under scalar multiplication. A scalar preserving $\mathcal L$ satisfies the monic characteristic polynomial of its integer matrix on a lattice basis, so it is an algebraic integer and its $\iota$-image is integral. Since $I$ is a $p$-adic unit, every coordinate of $\iota(g v_{j,a})$ has norm at most one.

Use a separate copy of the variables for each of the four factors. In the standard variables $Y$ substitute the linear forms whose column at $(a,i)$ is
$$
\sum_j\iota(g v_{j,a})A_{ji}/M.
$$
Their coefficients are integral by the preceding bound and $|A_{ji}|\le |M|_p$. Linear substitution with integral coefficients preserves integral derivatives. Applying any sequence of partial derivatives to the substitution amounts to applying a product of linear combinations of partial derivatives of the original function, with integral coefficients, by the chain rule. Evaluating at zero proves this for every multi-index. The substitution into $g^{-1}(MY)$ yields the original four independent copies of the matrix $F$, since $g^{-1}$ cancels the $g$ in each displayed column. The transported series after this substitution is therefore the fourth tensor power of the single substituted translate in the statement.

Take an arbitrary multi-index $e$ of one copy. The derivative of the fourfold product at $(e,e,e,e)$ is the fourth power of the $e$-derivative of the single factor, since the variables are independent. Its integrality bounds that derivative by one. Finally finite sums with integral coefficients remain bounded by the ultrametric inequality, also when each term is multiplied by the integral coefficient of a monomial differential operator and then summed. This proves the asserted transfer.

## Lean correspondence

- [`tensor_integral_torsion`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/AlgebraicTheory/AlgebraicTheoryProofs/TensZEt.lean#L70) applies the translated fourfold identity and clears the two annihilators using the relative index.
- [`etLoc_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/AlgebraicTheory/AlgebraicTheoryProofs/TensorFourthPowerScaling.lean#L258) rescales by $M$, transports the frame and extracts the one-factor derivatives.
- [`EtLoc`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/AlgebraicTheory/StatementC.lean#L39) states the result used in the two split cases.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
