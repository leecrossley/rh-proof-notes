# Recovering the standard phase from the actual orbit series

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Use the field, $p>2$, $\sigma$, height-two logarithm $\ell$, even length $d$, biextension $b_0$, trace-dual lists, root of unity of order $p^d-1$ and mean $\bar b$ from [biextension averaging](why-root-of-unity-averaging-preserves-the-biextension.md). Embed the coefficient field isometrically in $K$. For $N_0,N_1\ge0$, let $\Theta$ be a series over $K$ in the coordinates $Z_{s,a,b}$ with $s\bmod d$, $1\le a\le N_0$ and $1\le b\le N_1$. Suppose that there are a unit of norm $1$, $\eta\in K$, and an integral series $U$ such that, with $\mathcal L_{s,a,b}(Y)=\sum_{j\ge0}p^{-j}Y_{s-2j,a,b}^{p^{2j}}$,
$$
\Theta(\eta\mathcal L(Y))=U(Y)\exp\!\left(-\sum_{a,b}\bar b(\mathcal L_{a,b}(Y))\right).
\tag{1}
$$
The orbit expansion provides exactly (1). We recover the standard phase presentation of $\Theta(\eta Z)$ with an integral factor and explain the passage from this series to the bound on coefficients of the orbit's determinant polynomial.

## Integral inverse substitution through the trace frame

Work at one matrix entry $(a,b)$, suppressed in the notation. Introduce $d/2$ pairs $x_i,y_i$, and let
$$
L_s(x,y)=
\begin{cases}
\sum_i \sigma^s(\omega_i)\ell(x_i),&s\text{ even},\\
\sum_i \sigma^s(\omega_i^*)\ell(y_i),&s\text{ odd}.
\end{cases}
$$
Define $q(Z)$ to be the tuple with entries $\ell^{-1}(E_{\omega_i^*}(Z))$ and $\ell^{-1}(O_{\omega_i}(Z))$, using the even and odd forms of the averaging proof. The product identities for the trace matrices give $L(q(Z))=Z$ and $q(L(x,y))=(x,y)$. For example at even $s$ the coefficient at $Z_t$ of $L_s(q(Z))$ is $\sum_i\sigma^s(\omega_i)\sigma^t(\omega_i^*)=\delta_{st}$ for even $t$, and there are no odd terms.

We need a solution $T$ of $\mathcal L(T)=L$ with integral coefficients. Write $\mathcal F=\sigma^2$ followed by raising each variable to the $p^2$-th power. Each difference
$$
L_s-p^{-1}\mathcal F L_{s-2}=
\begin{cases}
\sum_i\sigma^s(\omega_i)x_i,&s\text{ even},\\
\sum_i\sigma^s(\omega_i^*)y_i,&s\text{ odd}
\end{cases}
$$
is integral. The cancellation uses $\sigma^d\omega_i=\omega_i$, $\sigma^d\omega_i^*=\omega_i^*$ and $\ell(t)-p^{-1}\ell(t^{p^2})=t$. The same cyclic difference on $\mathcal L$ gives the identity tuple. The [inverse functional equation](finding-integral-points-from-formal-logarithms.md#the-inverse-functional-equation) for the matrix of the shift by two therefore gives the desired integral $T=\mathcal L^{-1}\circ L$. In particular $\mathcal L\circ T\circ q$ is the identity.

For all matrix entries together write $B(x,y)=\sum_{a,b}\bar b(L(x_{a,b},y_{a,b}))$ and $S(x,y)=\sum_{i,a,b}b_0(x_{i,a,b},y_{i,a,b})$. Since $L_s$ satisfies the cyclic difference condition, averaging gives $B\sim\sum_{a,b}\widetilde b(L(x_{a,b},y_{a,b}))=S$, where the last equality is the inverse trace identity $q\circ L=1$. Substitute $Y=T(q(Z))$ in (1). The result is the substitution $(x,y)=q(Z)$ in
$$
U(T(x,y))\exp(-B(x,y))=\exp(-S(x,y))\,U_0(x,y),\qquad
U_0=U(T)\exp(S-B).
$$
Both factors of $U_0$ are integral. Although $q(Z)$ has a formal inverse logarithm in its definition, the integrality of $U_0$ is established before substituting $q$.

## From the presentation to the actual determinant coefficients

Suppose now $K=\mathbb C_p$ and $p>2$, with $b_0$ and the trace data as in the standard orbit. The scalar compatibility $b_0([c]x,y)\sim b_0(x,[\sigma(c)]y)$ of the averaging theorem implies the torus condition of the [normal form](two-additivity-laws-force-the-triangular-biextension.md). Indeed for $\zeta^{p^2-1}=1$, one has $\sigma(\zeta)=\zeta^p$, $\sigma^2\zeta=\zeta$ and $\ell(\zeta x)=\zeta\ell(x)$, so $[\zeta]x=\zeta x$. Along with the two additivity laws this gives the triangular phase. Choose $\varpi\in K$ with $\varpi^{p^2-1}=p$. On substituting $Z=\varpi Y$, each entry of $q$ is $\varpi\mu$ of the corresponding parity form in $Y$, with $\mu$ the inverse of $\ell(\varpi t)/\varpi$. The [rescaling proof](the-rescaled-standard-theta-has-a-cyclic-power-expansion.md) puts $\Theta(\eta\varpi Y)$ in the cyclic power class.

Fix an orbit and its diagrams, with every column height at most $N_0$. In the differential polynomial use an $N_0$-by-$N_0$ frame of independent entries $X_{s,i,a}$ at each $s$. At every column of height $h$, take the determinant of the first $h$ rows of the matrix of forms $\sum_a X_{s,i,a}Y_{s,a,b}$ at the chosen $h$ column indices. The product over all diagram columns and all $s$ is homogeneous in $Y$ of degree $D=\sum_s |\nu_s|$. Pair it with the series by sending a monomial $Y^\kappa$ to $\kappa![Y^\kappa]$ of the series, leaving the frame variables as polynomial coefficients. This is the orbit's framed jet. Evaluate the frames at independent indeterminates in the rational function field over $K$ with the Gauss norm. For a polynomial this norm is the maximum norm of its coefficients. It is multiplicative: after dividing each polynomial by a coefficient of maximum norm, the reductions are nonzero polynomials over the residue field, and their product is nonzero. This extends the norm to the fraction field. Thus a valuation lower bound for the evaluation is also a lower bound for every coefficient of the framed jet.

In this evaluation every height-one column at a top place uses the same first frame row $(X_{s,1,a})_a$; repeated choices of a column index give the corresponding power of its height-one linear form. All other columns remain minors with integral frame entries. These are the precise input $\alpha_s,C_s,D_s-\alpha_s$ of the [height-one calculation](hasse-derivatives-explain-the-height-one-orbit-gain.md). That calculation bounds the rescaled framed jet. Since it is homogeneous of degree $D$, replacing $\Theta(Z)$ by $\Theta(\eta\varpi Y)$ multiplies the pairing by $(\eta\varpi)^D$ and increases its valuation by $D/(p^2-1)$. Removing this increase gives the claimed $G_A$ of the [arithmetic comparison](the-excluded-odd-shifts-and-the-unserved-orbit-gain.md). The actual frame uses row indices that are natural numbers. Renaming $i$ from the finite frame to its corresponding natural number is injective, so no two coefficients are added in the renaming and all coefficient bounds survive.

## Lean correspondence

- [`exists_cofactor`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsIntegralOrbitSeries.lean#L208) constructs $U_0$ using the integral inverse through the trace frame. [`integral_cofactor_converse`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsIntegralOrbitSeries.lean#L343) applies it to (1) for the orbit.
- [`generic_elements_exist`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/EGaussK.lean#L16) and [`EGaussK.reduce`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/EGaussK.lean#L38) give the generic frame and identify the powers and minors used in the jet.
- [`tieFrame`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/Divisibility/JetPolynomialLogs/OneLetterJetKernel.lean#L418) identifies the determinant coefficient pairing and handles the unit $\eta$ and the injective renaming.
- [`kvalGe_gainA`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/KvalGeOrbitGainWithoutOperator.lean#L106) assembles the bound for the actual orbit series, with the exact digit loss and the exclusions from the top set.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
