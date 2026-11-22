# Four theta copies as a finite sum of one-variable translates

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $p\ge5$ be prime, $\iota:\mathbb C\cong\mathbb C_p$ an abstract field isomorphism, and $\Lambda\subset\mathbb C$ a lattice with a period $\omega_0$ such that $\omega_0/2\notin\Lambda$. Let $f_0$ be the corresponding one-variable half-period theta $ \mathrm{th0}(\omega_0/2)$. On standard coordinates use the Hermitian form with matrix $\operatorname{area}(\Lambda)^{-1}I$. Let $H$ be the given Hermitian form on $\mathbb C^n$, $\Gamma$ its theta lattice, and $\theta$ an entire theta function for its prescribed signs. Write $\theta^{\boxtimes4}(z)=\prod_{a=1}^4\theta(z_a)$, using four independent $n$-tuples. Suppose:

- A complex-linear isometry $g$ from the direct sum of four copies of $H$ to the standard form takes $\Gamma^4$ to $\Gamma_b$. This lattice is self-dual for the alternating form $E=\operatorname{Im}H_{\rm std}$, and is commensurable with $\Gamma_s=\Lambda^{4n}$.
- The two relative indices are finite, and $I=[\Gamma_b:\Gamma_b\cap\Gamma_s]$ is prime to $p$. The sign functions in `StdData` satisfy: $\beta$ equals the product sign of $f_0$ on $\Gamma_s$, is a semicharacter on $\Gamma_b$, and $\beta(gx)$ is the product of the source signs. Here semicharacter means $\beta(x)=\pm1$ on the lattice and $\beta(x+y)=\beta(x)\beta(y)\exp(\pi i E(x,y))$ there.
- The defining fourth tensor identity is $\theta^{\boxtimes4}=e\,K$ with $|\iota(e)|\le1$, where $K(z)$ is the normalized theta average from $\Gamma_s$ to $\Gamma_b$ applied to $F_0=\prod_w f_0(z_w)$, and evaluated at $g z$.

Fix $t\in\mathbb C^n$ with $Nt\in\Gamma$ for some integer $N>0$ prime to $p$. Let $L$ be the height-two logarithm and $P=L^{-1}$, and $\phi$ a zero-constant phase. Assume the one-variable integral translation assertion: for every $s$ with $Ms\in\Lambda$ for an integer $M>0$ prime to $p$,
$$
V_s(T)=\exp(\phi(T))\,\iota\!\left(\operatorname{Tay}(U_s f_0)\right)(L(T))
$$
is integral. Let the given matrices $B',\gamma$ satisfy $\operatorname{diag}(B',B',B',B')\gamma=\iota(g^{-1})$. Define $\Theta(X)=\iota(\operatorname{Tay}(U_t\theta))(B' L(X))$, where $L(X)$ is evaluated separately in the $n$ variables. Then
$$
\Theta^{\boxtimes4}\big(P(\gamma L(Y))\big)=
\sum_x r_x\prod_w \big(\exp(-\phi(Y_w))\,V_{s_{x,w}}(Y_w)\big)
$$
with a finite sum and $p$-integral $r_x,V_{s_{x,w}}$. This is the product shape used to bound $\Theta$.

**The finite average after translation.** Choose representatives $x\in\Gamma_b$ of $\Gamma_b/(\Gamma_b\cap\Gamma_s)$. The average defining $K$ is
$$
K(z)=I^{-1/2}\sum_x \beta(x)(U_x F_0)(g z).
$$
In this expression any representatives may be used. If $x$ changes by a period in the intersection, the semicharacter identity and $U_\lambda F_0=\beta(\lambda)^{-1}F_0$ for $\lambda\in\Gamma_s$ preserve the summand by the translation composition identity. The fourfold translate of $\theta$ equals the simultaneous translate of its tensor product by $\tilde t=(t,t,t,t)$. Under $g$ that translation is $U_b$ for $b=g\tilde t$, by the isometry. On substituting $z=g^{-1}y$, the fourth tensor identity gives
$$
(U_t\theta)^{\boxtimes4}(g^{-1}y)
=\sum_x c_x\prod_w (U_{b_w+x_w}f_0)(y_w),
\quad c_x=e I^{-1/2}\beta(x)\exp(-\pi i E(b,x)).
$$
Indeed $U_bU_x=\exp(-\pi i E(b,x))U_{b+x}$, and the translation on the standard space is the product of the coordinate translations.

Now $Nb\in\Gamma_b$, so $NE(b,x)\in\mathbb Z$ by self-duality. The phase in $c_x$ is a root of unity. The sign is a unit, the inverse square root of $I$ has norm $1$ at $p$, and $\iota(e)$ has norm at most $1$, so $r_x=\iota(c_x)$ is integral. Also $N(b+x)\in\Gamma_b$ and multiplication by $I$ takes $\Gamma_b$ into $\Gamma_s$. Thus $NI(b_w+x_w)\in\Lambda$ for every standard coordinate $w$, and $p\nmid NI$. Set $s_{x,w}=b_w+x_w$. The one-variable translation assertion applies to every one of these shifts.

**Taking Taylor series.** All functions in the finite identity are holomorphic near the origin. Their Taylor series respect finite sums, products and linear substitution, since these operations agree on the convergent expansions there. Taking Taylor series, applying $\iota$ to coefficients, and inserting $y_w=L(Y_w)$ gives the stated expression. On the left $L(P(\gamma L(Y)))=\gamma L(Y)$; the frame identity makes the resulting argument $\iota(g^{-1})L(Y)$. On the right each factor is exactly $\exp(-\phi)V_{s_{x,w}}$. This proves the product formula.

**Lean correspondence.** The structure of the lattices and signs is [`StdData`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/ProductThetaMem.lean#L52). The translated finite average is [`quadraticSemicharacters_of_productThetaMem`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/CayleyGaussianIntegrals/QuadraticSemicharactersOfProductThetaMem.lean#L47). The norm and torsion checks followed by Taylor substitution are [`norm_coeff`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/CayleyGaussianIntegrals/NormLtOne.lean#L63) and [`quadraticSemicharacterIdentity_of_reformulated_of_taylorMv_of_repsExist_of_opUAnalytic`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/CayleyGaussianIntegrals/NormLtOne.lean#L124). The result is the `ThetaFourthTensorPowerProductShape` of [the formal statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/TorsionTranslationPowers/StatementN.lean#L28), using the frame equality [`IsFrameH`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/UniformGaussModels/UniformGaussModelConditionEquivalent.lean#L26). The [torsion recurrence](closing-the-torsion-translation-recurrence.md) proves the one-variable integral translation assertion. The [inert-prime normalization](normalizing-the-fourfold-kernel-at-an-inert-prime.md) and [block-projection frame](block-projections-construct-the-integral-unitary-frame.md) provide the arithmetic choices.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
