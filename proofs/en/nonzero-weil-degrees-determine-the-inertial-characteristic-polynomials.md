# Nonzero Weil degrees determine the inertial characteristic polynomials

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let \(K\) be a number field, \(w\) a finite place, and \(W_K\) the local Weil group at a fixed prolongation of \(w\) to an algebraic closure. Its degree homomorphism \(d\colon W_K\to\mathbb Z\) sends a chosen Frobenius lift \(F\) to \(1\). Its kernel is the inertia group. Let \(\rho_1,\rho_2\) be the Weil actions of two complex Weil–Deligne parameters at this place. Suppose their characteristic polynomials agree on every \(g\in W_K\) with \(d(g)\ne0\). Then they agree for every \(g\), including \(g\) in inertia. The statement concerns the Weil actions. In applications where both monodromy operators vanish, this comparison also identifies the Frobenius-semisimple parameter classes. [Lean theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/CharPolEqOfDegNeZero.lean#L52)

## Proof

The hypothesis applied to \(F\) gives equality of dimensions and traces at \(F\). Take \(t\) in inertia. For \(i>0\), the element \(tF^i\) has degree \(i\). With
\[
A_j=\rho_j(F),\qquad S_j=\rho_j(t),\qquad
P(X)=\det(XI-A_1)\det(XI-A_2)=\sum_{i=0}^{D}c_iX^i,
\]
this implies
\[
\operatorname{tr}(S_1A_1^i)=\operatorname{tr}(S_2A_2^i)\qquad(i>0).
\]
Both matrices \(A_j\) are invertible, so \(c_0\ne0\). Cayley–Hamilton gives \(P(A_j)=0\) for each \(j\). Multiply on the left by \(S_j\) and take traces. Subtracting the resulting two identities cancels every positive-power term and yields
\[
c_0\bigl(\operatorname{tr}S_1-\operatorname{tr}S_2\bigr)=0.
\]
Thus the two traces agree on inertia as well as on elements of nonzero degree.

In particular, for any \(g\in W_K\) and positive integer \(i\), the two traces agree at \(g^i\). They are the power sums of the eigenvalues of \(\rho_j(g)\), counted with multiplicity. In characteristic zero, the common dimension and the power sums up through that dimension determine the characteristic polynomial. Indeed, for the elementary symmetric coefficients \(e_m\) of the eigenvalues and the power sums \(p_i\), Newton's recurrence is \(m e_m=\sum_{i=1}^m(-1)^{i-1}e_{m-i}p_i\), with \(e_0=1\). This proves the assertion. [Cayley–Hamilton step](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/CharPolEqOfDegNeZero.lean#L12) · [Weil-group step](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/CharPolEqOfDegNeZero.lean#L52)

The toral comparison uses this argument because the auxiliary spherical lift is selected separately for each element of nonzero degree. The proof recovers the omitted inertia polynomials algebraically. [Application away from the coefficient prime](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SphericalGaloisCompatibility/ToralDeRham/ToralGalois2.lean#L23)


Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
