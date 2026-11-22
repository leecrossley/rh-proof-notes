# How inert kernel integrality supplies the host expansion

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $D$ be the host data, with imaginary quadratic field $K=\mathbb Q(\sqrt{-d})$ and CM field $E$. Here $d$ is prime and $d\equiv3\bmod4$. The host data also fix a special prime $q$, a finite set of small primes, a test $\mathrm{psAt}(p)$, the chosen embeddings of $E$, and a fractional ideal $\mathfrak a$ used in the homomorphism lattice. Fix a nonzero integral ideal $\mathfrak c\subset\mathcal O_K$ with norm coprime to $2d$, and let $\delta^{12}$ be the discriminant of the period lattice of $\mathfrak c$. Fix a base $B$ on the resulting normalized lattice $\Lambda=\delta\,\varphi_0(\mathfrak c)$, and an admissible idelic character $\chi$ in its natural theta family. Let $p\ge5$ be prime and $\iota:\overline{\mathbb Q}\hookrightarrow\mathbb C_p$ any embedding. Assume that $p$ is in the signal class or in the class denoted `IsResidueClassZero`. Both definitions exclude the small primes, $q$ and $d$, and require $\left(\frac{-d}{p}\right)\ne1$; the signal class has $\mathrm{psAt}(p)=1$, and the other class has $\mathrm{psAt}(p)\ne1$.

The claim is `HostAt`. For this fixed $D,B,\chi,p,\iota$ there exist $c\in\mathbb C_p$ with $|c|=1$ and the curve datum $g_2,g_3,s_2,\epsilon,\sigma,F$ of the [curve-data note](assembling-the-inert-cm-curve-data.md). For every pair of self-dual Hermitian $\mathcal O_E$-lattices $M,M'$ of even ranks $N,N'$, there is a $K$-orthonormal list $b$ which is a basis for
$$
Y_{(p)}=\big(\mathfrak a\,\operatorname{Hom}_{\mathcal O_E}(M,M')\big)_{(p)}.
$$
The subscript means that we invert the rational integers prime to $p$. Orthonormality uses $h(A,B)=\operatorname{Tr}_{E/K}\sum_{ij}A_{ij}\overline{B_{ij}}$. For **every** $G$ which is a finite $p$-integral linear combination of the allowed translates at that pair, this list satisfies
$$
G\big(cB_b(L(T_i))_i\big)\exp\!\left(\sum_i\phi(T_i)\right)
\in\mathcal O_{\mathbb C_p}[[T_i]].
$$
Here $B_b$ lists all embedded matrix entries of the columns of $b$, $L(T)=\sum_{m\ge0}T^{p^{2m}}/p^m$, and $\phi=\text{`phFF`}(p,g_2,g_3,s_2,\epsilon)$. The allowed translates are coefficientwise algebraic Taylor series of the natural theta functions at pairs $p$-locally equal to $M,M'$, translated by points killed by a positive integer prime to $p$ on the matrix torus for $M,M'$. This is precisely `IsComb`, described in [the kernel-family note](one-normalization-for-the-inert-kernel-family.md).

The theorem uses the following integrality input (`IntInert`). For all $D,B,\chi,p,\iota,M,M'$ as above with $\left(\frac{-d}{p}\right)=-1$, for every such $G$, every integral discriminant-one model $W'$ of the transported lattice curve, its identity-chart series, and **every** orthonormal local basis $b$, the corrected series
$$
G\big(a' B_b(\ell_{W'}(T_i))_i\big)\prod_i A_{W'}(T_i)^{-1}
$$
has coefficients in $\mathcal O_{\mathbb C_p}$. Here $a'$ is the model's scalar on logarithmic coordinates, and $A_{W'}(t)$ is the transported modified sigma function at $a'\ell_{W'}(t)$, divided by $a't$. The ordinary Weierstrass integrality assertion in this paragraph is the input to be discharged upstream.

**Proof.** Since $p\ne d$, the Jacobi symbol cannot vanish. The two class tests exclude $1$, so it is $-1$; thus $p$ is inert and $(p)$ is a prime ideal of $\mathcal O_K$. Factor
$$
\mathfrak c=(p)^u\mathfrak c_0,\qquad (p)\nmid\mathfrak c_0,
$$
using unique factorization of ideals. The norm of $\mathfrak c_0$ is prime to $p$ as $(p)$ is the only prime above $p$; it remains coprime to $2d$. Put $\delta_0=\delta p^u$. Weight twelve under rescaling gives
$\Delta(\varphi_0(\mathfrak c_0))=p^{12u}\Delta(\varphi_0(\mathfrak c))$, and
$\delta_0\varphi_0(\mathfrak c_0)=\Lambda$. Thus the local model can be chosen using $\mathfrak c_0,\delta_0$ for the **same** complex lattice and the given embedding. The good-model construction picks a short Weierstrass model over the unramified valuation ring, its formal identity chart, and an integral isomorphism to the height-two law. This is the point at which the CM results on good reduction and the formal logarithm are used.

Apply the curve dictionary to this choice. Its invariants and sigma constant are in the maximal unramified extension, as shown by the finite torsion formula for $s_2$. The scalar $c$ has norm $1$. Taking Frobenius on the unramified field and the law $F$ of $L$ gives the curve datum, including integral short parameter and the norm identities for every unit $\alpha$ with $\sigma^2\alpha=\alpha$. The same dictionary gives one discriminant-one model $W'$ on $\Lambda$. Its integral change of parameter and the integral unit correcting the phase are the [dictionary calculation](the-curve-dictionary-transports-kernel-integrality.md).

Now fix $M,M'$. The local basis theorem gives $b$ before $G$ is chosen. Its construction starts with an orthonormal basis of the standard pair of even ranks, repeats the four-entry basis in each two-by-two block, uses equality of localized lattices, and transports by unitary matrices on the two sides. Trace of $AB^*$ is preserved by this transport. Apply `IntInert` to $W'$ and this list, for every $G$ in the quantified class. The dictionary substitution sends the resulting integral series to the required series, since its formal logarithm appears independently in every argument. This proves the claim with $c$ and the curve datum fixed before $N,N',M,M',b,G$.

**Lean correspondence.** The prime test and the theorem are [`jacobi_of_class`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/JacobiOfClass.lean#L41) and [`hostAt_inert`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/JacobiOfClass.lean#L63). The ideal reduction and the same-lattice model are [`curve_ideal_prime`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/InertKernelTheory/InertCoprimeLemmas/CurveIdealPrimeReduction.lean#L93) and [`genus_one_datum_exists_lattice`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/InertKernelTheory/InertCoprimeLemmas/GenusOneDatumExistence.lean#L211). The local orthonormal list comes from [`orthBasisExists_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/InertKernelTheory/InertCoprimeLemmas/JetsOrth.lean#L58). The integral-series input is [`IntInert`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/InertKernelTheory/StatementInt.lean#L22). The target with its order of quantifiers is [`HostAt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GaloisGeometry/ExistsConstantCoeffOne.lean#L37).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
