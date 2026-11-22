# The singleton Frobenius orbit gives the conjugate-prime weight

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $p\ge5$ be inert with trivial projected Frobenius, so the place shift is the identity. Fix a level-free kernel entry of layer $i<m$ for which the singleton expansion holds. Let $A$ be the finite place set, $D_z=|\nu_z|$ the Young diagram size at $z$, and $J$ the set of matrix entries of size $N_i\times N_{i+1}$. Put $H=a^2$ and suppose $p\le a$ and $D_z\le H$ at every place. The singleton expansion asserts
$$
\Theta(\eta\mathscr L(X))=U(X)\exp\left(\sum_z B_z(\mathscr L(X)_z)\right),
\qquad
B_z(X_z)=\frac{\epsilon_z}{2}\sum_{j\in J} b_z(X_{z,j},\xi_z X_{z,j}).
$$
Here $\mathscr L_{z,j}=\sum_{h\ge0}p^{-h}X_{z,j}^{p^{2h}}$, $U$ is integral, $\eta,\xi_z$ are units, $\epsilon_z=\pm1$, and every $b_z$ satisfies the [two-parity coefficient hypotheses](prime-powers-in-the-jet-coefficient-bound.md) with length $2$. This is the expansion supplied by [the diagonal curve calculation for a singleton](identifying-the-two-parities-on-an-odd-frobenius-orbit.md). For every choice of column indices, the coefficients obtained by applying the product of minors to the kernel have valuation at least
$$
\frac{\sum_zD_z}{p^2-1}-|A|N_iN_{i+1}(\log_p H+1).
\tag{1}
$$

Use $\rho=1/(p^2-1)$ and $\gamma=p/(p^2-1)$. A possible exceptional monomial has exponent sum $p^\alpha+p^\beta$ with $\alpha+\beta$ odd, by the two-parity congruence. The sum is at least $1+p$. Raising the uniform variable weight from $\rho$ to $\gamma$ supplies at least $(p+1)(\gamma-\rho)=1$ to its weighted valuation. Thus at weight $\gamma$ every coefficient of each $b_z$ has weighted valuation at least $1/(p-1)$. The substitution of $\xi_zX$ for the second variable and the scalar $\epsilon_z/2$ preserve the bound. The exponential of the sum thus has nonnegative weighted valuation, since $v_p(j!)\le j/(p-1)$.

Substitute the formal inverse $g$ of $\mathscr L$. Each $g_{z,j}$ has weighted valuation at least $\rho$ even with variable weight $\rho$, by the recursive estimate $(p^{2h}-1)\rho\ge h$. The integral factor $U(g(X))$ therefore has weighted valuation at least zero with the larger weight $\gamma$. This proves at that weight that $\Theta(\eta X)$ has nonnegative weighted valuation. In particular $v([X^m]\Theta)\ge-\gamma\sum m_{z,j}$, since $\eta$ is a unit. For terms of the determinant operator, the total degree at each place is $D_z$, and thus $m_{z,j}\le H$. Adding the factorial valuations gains at least $(p-1)^{-1}\sum m_{z,j}-|A||J|(\log_p H+1)$. The coefficient of $\sum m_{z,j}$ is now $(p-1)^{-1}-\gamma=\rho$, which proves (1) term by term.

The Lean proof performs this estimate by applying the one-letter determinant bound separately and gluing the results. The same reasoning justifies that gluing directly. Truncate $U$ at the degree of the product of minors. The higher-degree terms remain above that degree under substitution of $g$, multiplication by the exponential, and unit rescaling, so they cannot contribute. The image of each remaining monomial times the exponential is a product over places, since $g$ acts coordinate by coordinate and the exponent is a sum of functions in disjoint variables. The determinant polynomial also factors over places. Differentiation and coefficient extraction factor on disjoint variables, so the valuations add. The coefficients of the finitely many terms from $U$ are integral, so recombining them preserves the bound. This yields the same total (1) as the combined coefficient argument.

To obtain the numerical weight, let $w_z\ge0$ be the degree weights and $W=\sum_z w_z$. The shape assumptions give $D_z\ge(k-1)w_z$ for every $z$, including at a top place after accounting for its first row. Here $f=|A|$, and $N_iN_{i+1}\le N_m^2$. With $\log_p a\ge1$, $\log_p H+1=2\log_p a+1\le3\log_p a$. For a local logarithmic loss constant $C\ge0$, the actual entry bound with loss $CfN_iN_{i+1}(\log_p H+1)$ therefore exceeds
$$
F_{\mathrm{inert}}-\mathrm{EatC}
=\rho(k-1)W-\rho W-c_{\mathrm{dig}} fN_m^2\log_p a ,
$$
because $c_{\mathrm{dig}}\ge3C$ and $\rho W\ge0$. The definition of the numerical $F_{\mathrm{inert}}$ uses the same $W$, written as a sum over the complex embeddings. The sum over the places is equal to that sum by the chosen place indexing. The application uses $C=1$ for the one-letter estimate.

**Lean correspondence.** The expansion is [`ThetaExpansionRealPlaces`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/Divisibility/OrbitPlaces.lean#L192). The single letter and the inverse substitution are bounded in [`oneLetterR_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GaussJetBounds/GaussJetProofs/AsmOne.lean#L86) and [`thmOne_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/Divisibility/JetPolynomialLogs/DworkPowerSeriesWeights.lean#L235). The gluing, total estimate and numerical comparison are [`orbitsAddAtConjugate`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/OrbitJetLogarithm/OrbitsAddAtConjugate.lean#L55), [`entC_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/Divisibility/OrbitPlaces.lean#L1142), and [`sumOrbC`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/OrbitSumCount/SizeGe.lean#L36).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
