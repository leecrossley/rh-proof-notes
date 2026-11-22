# The character normalization at a served site is a unit

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix a positive inert site with $p\ge5$, a step $j<m$, a source class representative $L$ at layer $j$, and an admitted target lattice tuple $L'$ at layer $j+1$. Use the site's embedding $\lambda:\overline{\mathbb Q}\to\mathbb C_p$. Write $M_v=v_m(v,j+1)$ for the difference of even and odd exponent sums on the orbit $v$, and let $\ell_v(-)$ be the signed lattice length at that orbit. Define
$$
D=\sum_v M_v(\ell_v(L')-\ell_v(L)).
$$
The actual kernel character scalar $s_G$ is algebraic, and $|p^D\lambda(s_G)|_p=1$. This gives the algebraicity and weak bound required of the site's normalized kernel scalar.

### Norms on the determinant torus

Let $E/F$ be the site's CM extension, with involution $x\mapsto\bar x$. Let $U_1$ consist of finite ideles $x$ with $x\bar x=1$, and $U_{\rm int}$ consist of ideles integral and invertible at every finite place. The step character $\mu=\mu_{j+1}$ is algebraic and multiplicative on $U_1$. It has its specified infinity type $e(\tau)$ on principal norm-one ideles, and takes finite-order values on $U_1\cap U_{\rm int}$ by the finite-order law for the unitary quotient. At a positive site the CM embeddings occur in Frobenius orbits; consecutive slots alternate between $\rho_v z$ and $\rho_v\bar z$, followed in each slot by a Witt Frobenius and a field embedding. These maps carry integral units to integral units and take $p$ to $p$. Thus for $z\bar z=1$, the norm at slot $s$ is $|p|_p^{(-1)^s\operatorname{ord}_v(z)}$. The system exponents at the step differ from the type exponents by a constant on each orbit. Each orbit here has equal numbers of even and odd slots, so this common shift cancels. Multiplying the powers yields
$$
|\lambda(\mu(z))|_p=|p|_p^{\sum_v M_v\operatorname{ord}_v(z)}.
$$

The map from finite ideles to fractional ideals sends an idele to its local orders and has kernel $U_{\rm int}$. If $h$ is the order of the finite ideal class group, $x^h=a k_0$ with $a\in E^\times$ and $k_0\in U_{\rm int}$. Divide this equality by its conjugate. The left hand side becomes $x^{2h}$. The factors on the right are $z=a/\bar a$ and $k=k_0/\bar k_0$, both norm one, with $k$ integral and invertible. By multiplicativity and the finite-order law, $|\lambda(\mu(x))|_p^{2h}=|\lambda(\mu(z))|_p$. At every $v$, $\operatorname{ord}_v(z)=2h\,\operatorname{ord}_v(x)$. Taking the $2h$-th root proves the same norm formula for $x$.

The two determinant ideles $x_L,x_{L'}$ belong to $U_1$ and have orders $-\ell_v(L),-\ell_v(L')$ in the matched local determinant lattices. The sign is the convention of length for a lattice relative to the reference lattice. It follows that the ratio $\mu(x_{L'})/\mu(x_L)$ has norm $|p|_p^{-D}$.

### The remaining factors

For each of the two kernel lattices the other factors of $s_G$ are integer powers of the ideal character $\chi$ evaluated on the determinant ideal relative to the standard lattice. This includes the two factors in the quotient denoted $\mathrm{chiFac}$. Admissibility makes both determinant ideals norm one. For such an ideal $\mathfrak a$, take a positive power $\mathfrak a^k=(z)$ with $z\bar z=1$, using the norm-one principal-power law. The character law gives $\chi(\mathfrak a)^k=(\prod_\tau \tau(z))^{-1}$. At an inert orbit the product here has norm one, since consecutive slots have opposite orders. It is a nonzero algebraic number, so $\chi(\mathfrak a)$ is also nonzero and algebraic, and taking the $k$-th root gives norm one. All the ideal-character factors therefore leave the determinant ratio's norm unchanged. The extra factor $p^D$ cancels that ratio's norm exactly.

The proof uses the site's finite-order character law, the local determinant-order comparison, and the existence of a norm-one principal power for the determinant ideals. The idele argument above proves the principal-power assertion with an integral unit factor; the ideal-character argument uses the corresponding ideal assertion.

### Lean correspondence

- [`GlobalTheory.TwV.Xc.scal_of_pos_pair`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ThetaSeriesScalarBoundedOfPosPair.lean#L22) proves the scalar estimate.
- [`KG.expG` and `KG.scalG`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/InertKernelTheory/ScalG.lean#L19) define the exponent and scalar.
- [`lambdaCharacter_norm_eq_p_pow_of_pos`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/NormLambdaCharacterNormOneIdeleEqPPow.lean#L19) proves the step character norm formula, using [the principal-power argument](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsPowNormOneIdeleEqPrincipalMulIntegralUnit.lean#L107).
- [`norm_lamC_type_normOne`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/NormLamCTypeNormOne.lean#L58) computes the norm for a principal element.
- [`chi_alg_unit_inert`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ChiAlgUnitInert.lean#L21) proves algebraicity and the ideal-character unit norm. The finite-order step used on the integral subgroup is [`mt_finite_order`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/MtFiniteOrder.lean#L14).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
