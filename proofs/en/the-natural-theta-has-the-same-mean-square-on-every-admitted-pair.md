# The natural theta has the same mean square on every admitted pair

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix the [curve-ideal data and form](the-host-period-lattices-are-self-dual-and-commensurable.md), the host base which gives the [standard theta](a-fourfold-average-generates-the-standard-theta-line.md), and even nonnegative source and target ranks $a,b$. Let $L,L'$ be a full self-dual pair over $\mathcal O_E$ in those ranks, and use its complex period lattice $\Lambda_{L,L'}$. Let $\chi$ be a character on norm-one fractional ideals of $E$, multiplicative on those ideals and satisfying the principal-unitary rule
$$
\chi((z))=\prod_\tau \sigma_\tau(z)^{-1}\qquad (z\bar z=1).
$$
Let $e_{\mathrm{nat},\chi}(L,L')$ be the natural theta of the [determinant-character construction](the-determinant-character-cancels-in-the-normalized-theta-moves.md). This is the standard rectangular theta, moved to $(L,L')$ by first changing the source and then the target using the normalized finite averages, and multiplied by the determinant character factor there.

For a period lattice $\Lambda_*$ and an entire theta $F$ for it, put
$$
\mathcal N_{\Lambda_*}(F)
 =\frac{1}{\operatorname{vol}(\mathcal F)}
  \int_{\mathcal F}|F(z)|^2 e^{-\pi H(z,z)}\,dz,
$$
where $\mathcal F$ is any measurable fundamental domain and $dz$ is Lebesgue measure. This is the squared norm `normSq`, using a mean over the period cell. Write $\mathcal N_{\Lambda_c}(f_0)$ for the genus-one norm with $H(z,z)=|z|^2/\mathscr A$. Then $e_{\mathrm{nat},\chi}(L,L')$ is nonzero and
$$
\mathcal N_{\Lambda_{L,L'}}(e_{\mathrm{nat},\chi}(L,L'))
 =\mathcal N_{\Lambda_{\mathrm{std},\mathrm{std}}}(\theta_0)
 =\mathcal N_{\Lambda_c}(f_0)^{[E:K]ab}.
\tag{1}
$$
The same value holds for $U_xe_{\mathrm{nat},\chi}(L,L')$ for every $x$ of the complex matrix space. The first equality, together with the translation invariance, gives `ThetaNormIndependent` and `th22U`.

**The mean-square metric.** The Gaussian density $\rho_F(z)=|F(z)|^2 e^{-\pi H(z,z)}$ has the identity $\rho_{U_xF}(z)=\rho_F(z+x)$, by expanding $H(z+x,z+x)=H(z,z)+2\operatorname{Re}H(z,x)+H(x,x)$. On a period $y\in\Lambda_*$, $U_yF$ differs from $F$ by a sign of modulus one, so $\rho_F$ is periodic. Its integral is finite on a bounded fundamental parallelepiped. Since it descends to the torus, its integral against normalized Haar measure is independent of the fundamental domain. The same identity shows that $U_xF$ has the same mean density for every $x$: translating the torus variable does not change its Haar probability integral. If $F\ne0$, continuity and positivity on an open neighborhood of a point where it is nonzero give a positive integral.

The [pairwise averaging proof](three-theta-averages-differ-by-an-eighth-root.md) applies to any two host lattices of the fixed ranks, by their self-duality and finite relative indices and the common sign function. To see why its norm is the one above, compute its inner product using a fundamental region of the intersection $\Delta$ with total measure normalized to $1$. A theta density periodic under either lattice $\Lambda_i$ is repeated $[\Lambda_i:\Delta]$ times over that intersection region. Dividing by the intersection volume therefore gives exactly $\mathcal N_{\Lambda_i}$. On this common space the average over the finite group for the new lattice is an orthogonal projection $P_j$. If $F$ is fixed by the original group, the reverse projection acts on its new translates by killing exactly those whose translation arguments are outside the old lattice. Indeed their commutator with an old period is a nontrivial character by self-duality. The surviving fraction is $1/n$ for $n=[\Lambda_j:\Delta]$, giving $P_iP_jF=F/n$. Consequently
$$
\|P_jF\|^2=\langle F,P_jF\rangle
 =\langle F,P_iP_jF\rangle=\|F\|^2/n.
$$
The normalized intertwiner on this theta space is $\sqrt n\,P_j$, so it preserves the norm. These statements also give nonvanishing as soon as the input is nonzero.

**The scalar character has modulus one.** For the relative determinant ideal $\mathfrak a$ of two self-dual lattices, $\mathfrak a\bar{\mathfrak a}=\mathcal O_E$, by the [opposite determinant orders](the-word-prime-character-factor-is-independent-of-the-selected-side.md#conjugation-of-determinant-orders). Let $h_E$ be the class number of $E$, and write $\mathfrak a^{h_E}=(u)$ with $u\ne0$. The ideal $(u\bar u)$ is the unit ideal. Hence $\mathfrak a^{2h_E}=(u/\bar u)$. Set $z=u/\bar u$, so $z\bar z=1$. Each embedded $\sigma_\tau(z)$ then has modulus one, and the two character rules give
$$
|\chi(\mathfrak a)|^{2h_E}
 =|\chi((z))|
 =\prod_\tau|\sigma_\tau(z)|^{-1}=1.
$$
It follows that both determinant factors in $e_{\mathrm{nat},\chi}(L,L')$, with exponents $b/2$ and $-a/2$, have unit modulus. Apply the normalized intertwiner isometry to the two moves from the nonzero standard theta. The new theta is nonzero and has exactly the standard norm even after the scalar character factor. This proves the first equality of (1).

**Evaluate that standard norm.** The fourfold kernel identity is $\theta^{\boxtimes4}=\kappa (I_{sb}F_0)\circ g$, with $F_0=f_0^{\boxtimes 4f}$ and $f=[E:K]$. The isometry $g$ carries the normalized probability measure on one torus to that on its image and preserves the Gaussian. By the preceding calculation $I_{sb}$ preserves the mean square as well. For each split-prime factor $r_p$ in $\kappa$, raising it to $2h_K$ gives $\pi_p/\bar\pi_p$, of complex modulus one. Thus $|r_p|=1$ and $|\kappa|=1$. Taking the fourfold mean square, the product Gaussian and product probability measure give
$$
\mathcal N_\Gamma(\theta)^4
 =\mathcal N_{\Gamma_s}(F_0)
 =\mathcal N_{\Lambda_c}(f_0)^{4f}.
$$
Taking positive fourth roots and then multiplying the standard $\theta$ norms over $ab$ independent entries gives the second equality in (1). The product with no entries gives the norm $1$, with the same formula.

**Lean correspondence.** The mean-square definition is [`normSq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GeneralLinearActions/IsDiscriminantTwelfthRootOfIdealLattice.lean#L94). The density identity and torus translation argument are [`dens_U`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/GL3/PLinkThU.lean#L47) and [`normSq_U_of_fd`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/GL3/PLinkThU.lean#L69), applied to full host period lattices by [`theta_unitary_linkage`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/GL3/PLinkThU.lean#L739). The average isometry is [`theta_operator_isometry`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/GL3/PThIndep.lean#L13). The principal generator and absolute-value calculation are [the unitary generator of an ideal power](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/GL3/PLinkThIndep.lean#L221) and [`norm_chi_eq_one_of_normOne`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/GL3/PLinkThIndep.lean#L229). The norm of the character factor and the two-move identity are [`Base.chiFac_norm`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/KernelLocalFactors/IsAdmissibleFlagPairOfUnitriangularLeftAutomorph.lean#L662) and [`Base.eNat_normSq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/KernelLocalFactors/IsAdmissibleFlagPairOfUnitriangularLeftAutomorph.lean#L671), combined with translations in [`theta_link_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/GL3/PFamily.lean#L91). The product calculation here directly evaluates the un-conjugated standard norm from the fourth tensor identity. The family theorem also needs a separate calculation of the norms after all field embeddings.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
