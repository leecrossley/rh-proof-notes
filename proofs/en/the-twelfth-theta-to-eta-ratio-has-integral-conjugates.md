# The twelfth theta-to-eta ratio has integral conjugates

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $\Lambda=\delta I$ be a discriminant-one host CM lattice and $M$ a number field containing its Weierstrass invariants $g_2,g_3$. For each embedding $\rho:M\hookrightarrow\mathbb C$ take the [conjugate lattice](the-conjugate-cubic-has-a-normalized-cm-ideal-lattice.md) $\Lambda_\rho=\omega_\rho(\mathbb Z+\tau_\rho\mathbb Z)$, with $\operatorname{Im}\tau_\rho>0$. Choose the half-period $t_\rho$ whose class has both $\mathcal O_K/2$-projections nonzero. Its even characteristic $(a_\rho,b_\rho)$ is the one in [the Jacobi expansion](a-jacobi-expansion-evaluates-the-scalar-theta-mean-square.md). Write $\Theta_\rho=\Theta_{a_\rho b_\rho}(0,\tau_\rho)$ and $\eta(\tau)=q^{1/12}\prod_{n\ge1}(1-q^{2n})$, where $q=e^{\pi i\tau}$ and $q^{1/12}=e^{\pi i\tau/12}$.

Then there exists a single nonzero algebraic integer $X\in M$ such that
$$
  |\rho X|=\left|\frac{\Theta_\rho}{\eta(\tau_\rho)}\right|^{12}
  \qquad\text{for every }\rho.
\tag{1}
$$
The normalized area is also
$$
  \operatorname{area}(\Lambda_\rho)
  =4\pi^2\operatorname{Im}\tau_\rho\,|\eta(\tau_\rho)|^4.
\tag{2}
$$
These are the two scalar identities needed before taking the logarithmic mean.

**The theta constants and half-period differences.** First use the lattice $\mathbb Z+\tau\mathbb Z$. The three even theta constants have product $2\eta(\tau)^3$, and the derivative with respect to $w$ of the odd theta at $0$ has absolute value $2\pi|\eta(\tau)|^3$. Here is the normalization check from the Jacobi products. For the even characteristics $00,01,10$, their products over $n\ge1$ have common factors $\prod_n(1-q^{2n})$, with additional factors $\prod_n(1+q^{2n-1})^2,\ \prod_n(1-q^{2n-1})^2,\ 2q^{1/4}\prod_n(1+q^{2n})^2$ respectively. On multiplying, the extra products cancel except $2q^{1/4}$: use $(1+q^{2n})(1-q^{2n})=1-q^{4n}$, and split the even powers $2n$ into the classes $4n$ and $4n-2$. The result is $2\eta^3$. For the odd theta the sine factor $\sin(\pi w)$ has derivative $\pi$ at zero, and its other factors at zero give $\prod_n(1-q^{2n})^3$ and a scalar of modulus $2|q|^{1/4}$, yielding the derivative magnitude. [Jacobi's product formulas](https://dlmf.nist.gov/20.5.i)

Let $u,v,w$ be the three nonzero half-period classes, with $w=u+v$. For any such half-period $s$, write $\Theta_s$ for the corresponding even constant. Put $A_s=(U_s S)(0)$, with $S$ the canonical modified sigma for the unscaled lattice. The odd theta times $e^{\pi z^2/(2\operatorname{Im}\tau)}$ has the same signs and the same simple zeros as the modified sigma. Since their ratio is an entire doubly periodic function, they are proportional. Dividing by the derivative at zero gives exactly $S$. For $s=(r+l\tau)/2$ with $r,l\in\{0,1\}$, completion of the square in the shifted odd theta gives the magnitude $e^{\pi l^2\operatorname{Im}\tau/4}|\Theta_s|$. The Gaussian converting the shifted odd theta to $A_s$ contributes $e^{-\pi(\operatorname{Im}s)^2/\operatorname{Im}\tau}$, which cancels that exponential. Therefore
$$
|A_s|=\frac{|\Theta_s|}{2\pi|\eta|^3}.
$$
The [sigma addition identity](closing-the-torsion-translation-recurrence.md) gives
$$
A_{u+v}A_{u-v}=A_u^2A_v^2\bigl(\wp(v)-\wp(u)\bigr).
$$
The Gaussian factors agree on the two sides by $H(u+v,u+v)+H(u-v,u-v)=2H(u,u)+2H(v,v)$. Since $u-v$ and $u+v$ differ by a period, $|A_{u+v}|=|A_{u-v}|=|A_w|$. Using the product $2\eta^3$ yields
$$
|\wp(u)-\wp(v)|=\pi^2|\Theta_w|^4.
\tag{3}
$$

**The area and the algebraic root.** The three values $e_i$ of $\wp$ at the nonzero half-periods are distinct and are roots of $P(X)=X^3-AX-B$ with $A=g_2/4,\ B=g_3/4$. In particular $\Delta=16\prod_{i<j}(e_i-e_j)^2$. Applying (3) to the three pairs in the unscaled lattice, the absolute discriminant is
$$
16\pi^{12}\,|\Theta_u\Theta_v\Theta_w|^8=(2\pi)^{12}|\eta|^{24}.
$$
Scaling the lattice by $\omega$ multiplies $\Delta$ by $\omega^{-12}$ and the area by $|\omega|^2$. At discriminant one this gives $|\omega|^2=4\pi^2|\eta|^4$ and proves (2).

Let $e=e_t=\wp_\Lambda(t)$ for the distinguished half-period of the original lattice, and $Y=P'(e)=3e^2-g_2/4\ne0$. Then $X=Y^{-3}$ belongs to $M$. In fact $e$ is algebraic as a root of $P$. Every automorphism of $\overline{\mathbb Q}$ fixing $M$ preserves the lattice invariants and the class whose two CM projections are nonzero, so fixes $e$. This gives $e\in M$, and applying any $\rho$ gives $\rho(e)=\wp_{\Lambda_\rho}(t_\rho)$. The derivative $Y$ is the product of the two differences from $e_t$ to the other two roots. Their magnitudes on $\omega_\rho(\mathbb Z+\tau_\rho\mathbb Z)$ are the corresponding quantities in (3) times $|\omega_\rho|^{-2}$. Thus $|\rho Y|^3=\big|\eta(\tau_\rho)/\Theta_\rho\big|^{12}$ by the product $2\eta^3$ and the discriminant-one scaling. This proves the conjugate magnitude identity (1).

To see integrality without a sign choice for the theta constants, put $U=e-e_j,\ V=e-e_k$ for the other roots. Then $UV=Y,\ U+V=3e$, so $U^2-UV+V^2=3A$ and $(U-V)^2=3A-Y$. Consequently $\Delta=16Y^2(3A-Y)$. With $T=-\Delta/Y^3$ one has $T-16=-48A/Y=-12g_2/Y$, which gives
$$
  (T-16)^3=jT,\qquad j=1728g_2^3/\Delta.
$$
At $\Delta=1$, $T=-X$. By the CM singular-modulus theorem $j$ is an algebraic integer. This monic cubic implies that $X$ is integral over $\mathbb Z$. This gives the single integer required before taking the product over all embeddings. [The singular modulus input](discriminant-normalization-gives-a-good-model-for-p-at-least-five.md)

**Lean correspondence.** The Jacobi product, derivative at zero and half-period differences are used to assemble [`thetaWeberStatement_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/JacobiProductOfThetaWeber.lean#L28). The discriminant and area formulas are [`discrEta`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LatticeDiscriminantEqWeierstrassDiscr.lean#L24) and [`periodEta`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LatticeDiscriminantEqWeierstrassDiscr.lean#L60). The half-period algebraic value and reciprocal cube are used in [`exists_integral_theta_ratio`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DecoratedLatticeProofs/ExistsIntegralThetaEtaTwelfthPowerConjugates.lean#L19). The source proves modulus and integrality in [`modulus`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsIntegralPeriodElement.lean#L168) and [`integral`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsIntegralPeriodElement.lean#L234). The cubic calculation above applies the signed Weber equation directly to the derivative of the cubic at the chosen root.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
