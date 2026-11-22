# A unit CM multiplier gives integral torsion coordinates

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $K_0=\mathbb Q(\sqrt{-d})$ with $d>0$ squarefree and $d\equiv3\bmod4$, and let an elliptic period lattice $\mathcal L$ be stable under its ring of integers. Fix an odd prime $p\nmid d$ and transport the curve via $\iota:\mathbb C\cong\mathbb C_p$ to an integral short Weierstrass model of unit discriminant. Write $R=\mathcal O_{\mathbb C_p}$. Let $\alpha\in\mathcal O_{K_0}$ have $|\iota(\alpha)|=1$. If a point $P\ne O$ of the curve is killed by $\alpha$, then both its affine coordinates belong to $R$. The degree $D=\alpha\bar\alpha$ of the isogeny can be divisible by $p$. This is the torsion input of the derivative estimate at a split prime.

If $p\nmid D$, the kernel is killed by the prime-to-$p$ integer $D$. Indeed multiplication by $\bar\alpha$ after $\alpha$ acts by $D$. Apply [the integral coordinates for prime-to-$p$ torsion](why-prime-to-p-torsion-has-integral-unramified-coordinates.md).

For the remaining case, write $\ell$ for the normalized formal logarithm, $v(T)=\ell^{-1}(\iota(\alpha)\ell(T))$, and use the sigma phase $\phi$ such that $\iota(S)(\ell(T))=T\exp(-\phi(T))$. Here $\iota(S)$ means its Taylor series with transported coefficients. The curve-endomorphism norm law used in Lean gives
$$
v(T)\in TR[[T]],\qquad
\exp\bigl(\phi(v(T))-D\phi(T)\bigr)\in1+TR[[T]].
\tag{1}
$$
In this law the completed CM ring is described by the two embeddings into $\mathbb C_p$, with conjugation exchanging the coordinates. At a prime away from $d$ the completion modulo $p$ is a quadratic field or the product of two copies of $\mathbb F_p$. In either ring for odd $p$, every element is a sum of two units: in each field choose an element different from both zero and the required sum. In the product choose independently in each factor. For a global CM element the pairs with both coordinates units are the multipliers of degree prime to $p$; these are dense in the units of the completed ring. The coefficient maps for the endomorphism and the exponential congruence are continuous in the two scalar entries. Hence the [prime-to-$p$ isogeny norm law](the-curve-norm-law-from-a-prime-to-p-isogeny.md) yields (1) for units of the completed CM ring. Formal addition now gives integral endomorphisms for sums of two units.

To extend the phase congruence, write $C(P,Q)=\phi(P\oplus Q)-\phi(P)-\phi(Q)$ and use the [sigma parallelogram](from-formal-sigma-addition-to-the-curve-biextension.md) for additivity of $C$ in both coordinates modulo integral exponentials. That congruence respects multiples by $\mathbb Z_p$ by taking limits of integer multiples, and $C$ is $\mathbb Z_p$-linear for the formal CM action of those scalars by the same continuity. For a unit $u$, polarizing the norm congruence gives $C([u]P,[u]Q)\sim N(u) C(P,Q)$. Substitute $[u^{-1}]Q$ to obtain $C([u]P,Q)\sim C(P,[\bar u]Q)$. For two units $u,v$ the cross term $C([u]P,[v]P)$ is therefore equivalent to both $C(P,[\bar u v]P)$ and $C(P,[u\bar v]P)$, by symmetry. Adding the two representations gives
$$
2 C([u]P,[v]P)\sim \operatorname{Tr}(\bar u v)\, C(P,P)
 \sim 2\operatorname{Tr}(\bar u v)\,\phi(P).
$$
The last equivalence uses $C(P,P)=\phi([2]P)-2\phi(P)\sim2\phi(P)$, since $2$ is a unit. Division by $2$ preserves the congruence over $R$: an integral unit with constant $1$ has an integral square root of constant $1$ by coefficient recursion. Expanding the phase at $[u+v]P=[u]P\oplus[v]P$ now gives the norm rule with $N(u+v)=N(u)+N(v)+\operatorname{Tr}(\bar u v)$. This proves (1) for the desired multiplier. [The two-unit extension of the phase and adjoint laws](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/SecondCoefficientNorms/BinomialSeriesCoefficients/UnitaryInverseIdentity.lean#L424)

Let $x_S(T)$ be the formal $x$-coordinate and $A(T)=T^2 x_S(T)\in1+TR[[T]]$. The lattice isogeny identity for the full kernel of $\alpha$ has the same form as the norm-law identity for an isogeny of degree prime to $p$. With $x_Q$ the $x$-coordinates of all nonzero kernel points,
$$
\prod_{\substack{Q\in\ker\alpha\\Q\ne O}}\bigl(A(T)-x_Q T^2\bigr)
=\left(\frac{v(T)}{\iota(\alpha)\,T}\right)^2
   \exp\bigl(-2(\phi(v(T))-D\phi(T))\bigr).
\tag{2}
$$
The product includes both signs of each pair of nonzero kernel points when they are distinct. The identity follows by substituting the formal parameter into the [complex isogeny formula](the-lattice-isogeny-and-its-weight-two-constant.md), then cancelling the common powers of $T$ and the sigma exponential. The exponent in (2) uses the full degree $D$. We may form it before knowing that the kernel coordinates are integral. By (1) and $|\iota(\alpha)|=1$, the right side is integral.

If any $x_Q$ had norm greater than one, divide its factor in (2) by $x_Q$. That divided factor is integral with reduction $-T^2$, since $A(T)$ is integral. Leave the factors with integral $x_Q$ unchanged, and each of those has constant coefficient $1$. The reduced product of all these integral factors is nonzero, because the residue formal series ring is a domain. On the other hand the product on the left of (2) was integral, and the scalar dividing it is the product of the nonintegral $x_Q$'s, of norm greater than one. The reduction of the divided product must therefore vanish. This contradiction gives $x_Q\in R$ for every $Q$. The curve equation with integral coefficients now implies $y_Q^2\in R$, hence $y_Q\in R$. This proves the assertion even when multiplication by the degree is insufficient for the prime-to-$p$ torsion argument.

## Lean correspondence

- [`unit_kernel_integral_coords`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/AlgebraicTheory/AlgebraicTheoryProofs/UnitKer.lean#L523) distinguishes the two cases of the degree.
- [`calcGen`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/AlgebraicTheory/AlgebraicTheoryProofs/UnitKer.lean#L312) gives (1), invoking [`curveEndoUnitBall`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/SecondCoefficientNorms/CurveJetsUnitBall.lean#L6).
- [`main_case`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/AlgebraicTheory/AlgebraicTheoryProofs/UnitKer.lean#L402) substitutes the isogeny formula. [`prod_int`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/AlgebraicTheory/AlgebraicTheoryProofs/UnitKer.lean#L46) makes (2) integral, and [`gauss_roots`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/AlgebraicTheory/AlgebraicTheoryProofs/UnitKer.lean#L117) is the reduction argument.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
