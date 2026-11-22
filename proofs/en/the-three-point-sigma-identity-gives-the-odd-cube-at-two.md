# The three-point sigma identity gives the odd cube at two

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $W$ be an integral Weierstrass model of a smooth elliptic curve over a characteristic-zero ultrametric field $K$, with integral ring $R$. Use $t=-x/y$ at the identity, the integral group law $F$, inverse $t\mapsto\ominus t$, and normalized formal logarithm $\ell$. Write $\oplus,\ominus$ for addition and subtraction in this law. The expansion of the $x$-coordinate is $x(t)=e(t)/t^2$ with $e\in1+tR[[t]]$. In additive coordinates we have $\wp(\ell(t))=x(t)+b_2/12$ and $\wp'(\ell(t))=2y(t)+a_1x(t)+a_3$. For any $s_2\in K$ define the zero-constant phase $\phi$ by
$$
t\exp(-\phi(t))=\exp(-s_2\ell(t)^2/2)\sigma(\ell(t)).
$$
The claim is that the third difference
$$
C_\phi(x,y,z)=\phi(x\oplus y\oplus z)-\phi(x\oplus y)-\phi(x\oplus z)-\phi(y\oplus z)+\phi(x)+\phi(y)+\phi(z)
$$
has integral exponential with constant $1$. The claim includes residue characteristic $2$, with no condition on the integrality of $s_2/2$. It is the additive-defect input to [the corresponding result at the half-period](the-half-period-phase-has-an-integral-third-difference-at-two.md).

Use the sigma addition identity and the three-point Frobenius–Stickelberger formula. In additive coordinates $U,V,W_0$, the latter is
$$
\det\!\begin{pmatrix}
1&\wp(U)&\wp'(U)\\
1&\wp(V)&\wp'(V)\\
1&\wp(W_0)&\wp'(W_0)
\end{pmatrix}
=-2\frac{\sigma(U+V+W_0)\sigma(U-V)\sigma(U-W_0)\sigma(V-W_0)}
{\sigma(U)^3\sigma(V)^3\sigma(W_0)^3}.
$$
The sign here uses $U-W_0$ in the product. One external source is equation (35) of [Buchstaber, Gaiur and Rubtsov](https://doi.org/10.4213/im9691e). The analytic sigma identities give formal identities by expansion at zero and clearing the Laurent denominators. In the general characteristic-zero setting the normalized expansions are obtained over the rational function field of the Weierstrass parameters, where the identities follow from the complex ones. Their coefficients are polynomials in the parameters over $\mathbb Q$, by the recurrence for $\wp$, the equation $(\log(\sigma(Z)/Z))''=Z^{-2}-\wp(Z)$, and the formal logarithm, so the cleared identities specialize to $W$.

Replacing $\sigma$ by $\exp(-s_2 Z^2/2)\sigma$ preserves both ratios. The sums of the squares in their numerators equal the weighted sum of the squares in the denominators. Define the two-point expression
$$
P_2(x,y)=\phi(x\oplus y)+\phi(x\ominus y)-2\phi(x)-2\phi(y).
$$
The sigma addition identity becomes
$$
(x\oplus y)(x\ominus y)\exp(-P_2(x,y))=x^2e(y)-y^2e(x).
$$
The right side vanishes at $y=x$ and at $y=\ominus x$, the second by evenness of the additive $\wp$. An integral series vanishing at $y=h(x)$ is divisible by $y-h(x)$ over $R$, by translating $y$ by $h(x)$. These two factors divide successively, because $x-(\ominus x)$ is nonzero in the characteristic-zero series ring. They are associates of $x\ominus y$ and $x\oplus y$ by the same substitution and comparison of linear terms. Thus the quotient on the right is integral and has constant $1$, as follows from its degree-two part.

Now write $P_3=\phi(x\oplus y\oplus z)+\phi(x\ominus y)+\phi(x\ominus z)+\phi(y\ominus z)-3(\phi(x)+\phi(y)+\phi(z))$. Multiply the determinant identity by $x^3y^3z^3$, with $U=\ell(x)$, $V=\ell(y)$, $W_0=\ell(z)$. In its determinant subtract $b_2/12$ times the first column from the second, and $a_1$ times the resulting second column and $a_3$ times the first from the third. The third column is then twice the column of $y$-coordinates. Cancelling the common $2$ in the identity gives
$$
-\det [\, t_i^3,\ t_i e(t_i),\ -e(t_i)\,]_{i=1}^3
=(x\oplus y\oplus z)(x\ominus y)(x\ominus z)(y\ominus z)\exp(-P_3),
\qquad(t_1,t_2,t_3)=(x,y,z).
$$
The determinant has integral coefficients and vanishes on the three diagonals. Divide successively by $x-y,x-z,y-z$. At each diagonal the already removed factors specialize to nonzero series, so the remaining quotient still vanishes there. The determinant also vanishes at $z=\ominus(x\oplus y)$, by the formal chord law, or by the cleared sigma identity over $K$. At that specialization the three linear differences are nonzero series. Divide the remaining quotient integrally by $z-\ominus(x\oplus y)$, an associate of $x\oplus y\oplus z$. Each linear difference is an associate of the corresponding formal difference. The resulting quotient is integral and its constant is $1$: the leading determinant of the rows $[t_i^3,t_i,-1]$ is $-(x+y+z)(x-y)(x-z)(y-z)$. Hence $\exp(-P_3)$ is an integral unit. All division by $2$ above takes place in an exact identity over $K$ with an explicit common factor.

Finally $C_\phi=P_3-P_2(x,y)-P_2(x,z)-P_2(y,z)$. Its exponential is a product of the integral units just proved and their inverses. If $B(x,y)=\phi(x\oplus y)-\phi(x)-\phi(y)$, then $C_\phi=B(x\oplus y,z)-B(x,z)-B(y,z)$. Consequently $B$ is additive in the first slot modulo integral exponentials, and its symmetry gives additivity in the second.

**Lean correspondence.** The integral determinant factors are in [`cube_mem'`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/WeierstrassTwoTorsion/WeierstrassSubstitution/DifferenceLinearCoeff.lean#L203), the pair identity in [`ParO_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/FrobeniusFibreCurves/LogarithmicSubstitution/InVarAddInVarNeZero.lean#L305), and the Frobenius–Stickelberger identity is proved formally in [`FrobStickLog_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/FrobeniusFibreCurves/LogarithmicSubstitution/RealAdelicInertTransportTypeFormsEqAlt.lean#L318). The three-point comparison and subtraction are [`ParThree_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/FrobeniusFibreCurves/LogarithmicSubstitution/ConstantCoeffLawWithInverseThree.lean#L454) and [`cube_relation_from_parallelograms`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/FrobeniusFibreCurves/LogarithmicSubstitution/FirstLevelOfThreeVarParallelogram.lean#L29).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
