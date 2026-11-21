# Testing integral power series at cyclotomic roots

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E5%9C%A8%E5%88%86%E5%9C%86%E6%A0%B9%E5%A4%84%E6%A3%80%E6%9F%A5%E6%95%B4%E5%B9%82%E7%BA%A7%E6%95%B0%E7%9A%84%E6%95%B4%E9%99%A4%E6%80%A7.md)

Let \(\ell\) be prime, \(s\ge1\), and \(L/\mathbb Q_\ell\) a finite extension containing all \(\ell^s\)-th roots of unity. Let \(O=\mathcal O_L\) with maximal ideal \((\varpi)\), and set
$$
X=(1+U)^{\ell^{s-1}}-1,\qquad Q=\sum_{j=0}^{\ell-1}(1+U)^{j\ell^{s-1}}.
$$
For an \(\ell^s\)-th root \(\zeta\), write \(E_\zeta(g)\in L[[t]]\) for the expansion of \(g\in O[[U]]\) at \(U=\zeta\exp(t)-1\). For \(m\ge0\), \(Q^m\mid g\) in \(O[[U]]\) if and only if \(t^m\mid E_\zeta(g)\) at every primitive \(\ell^s\)-th root. The same assertion holds for \(X^m\) with the set of all \(\ell^{s-1}\)-th roots. For either set, any chosen root \(\zeta_0\) and any \(f\in L[[t]]\), there exist \(b\in O[U]\), \(c\in L^\times\) with \(cE_{\zeta_0}(b)\equiv f\bmod t^m\) and \(E_\zeta(b)\equiv0\bmod t^m\) at every other root in the set.

**Proof.** As \(\zeta\) has \(\ell\)-power order, \(a=\zeta-1\in(\varpi)\). The degree-\(j\) Taylor coefficient of \(g(a+Y)\) is
$$
\sum_{n\ge j} g_n\binom nj a^{n-j},
$$
a convergent sum in \(O\). Then substitute \(Y=\zeta(\exp t-1)\). This substitution preserves order and gives an isomorphism \(L[[Y]]/(Y^m)\simeq L[[t]]/(t^m)\), since its linear coefficient is \(\zeta\ne0\).

For \(m>0\), let \(P=Q^m\) or \(P=X^m\), with \(d=\deg P\). Each polynomial is monic and reduces to \(U^d\) modulo \(\varpi\). The map \((h,r)\mapsto U^dh+r\) from \(O[[U]]\oplus O[U]_{<d}\) to \(O[[U]]\) is an isomorphism by separating coefficients below degree \(d\). Replacing \(U^d\) by \(P\) changes the map by an operator taking values in \(\varpi O[[U]]\). Composing with the coefficient-splitting inverse gives the identity plus a \(\varpi\)-divisible operator. Its inverse is the convergent geometric series in the negative of that operator, since the modules are complete for powers of \(\varpi\). Thus \(g=Ph+r\) with \(h,r\) integral and \(\deg r<d\).

The roots of \(Q\) are \(\zeta-1\) for primitive \(\ell^s\)-th roots; those of \(X\) are \(\zeta-1\) for \(\ell^{s-1}\)-th roots. Both sets consist of simple roots in characteristic zero. If \(g\) vanishes to order at least \(m\) at the chosen roots, then so does \(r\). Over \(L[U]\) the factors \((U-a)^m\) there are pairwise coprime and all divide \(r\). Their product has degree \(d\); hence \(r=0\). The reverse implication follows by evaluating \(Ph\), and \(m=0\) is automatic.

For interpolation, pull \(f\bmod t^m\) back to a prescribed class modulo \((U-(\zeta_0-1))^m\) using the truncated substitution. The polynomial Chinese remainder theorem gives \(b_0\in L[U]\) with this class and zero classes at all other selected roots. Clear the finitely many denominators by \(d_0\in O\setminus\{0\}\), taking \(b=d_0b_0\), \(c=d_0^{-1}\).

The tests are `Q_test` and `X_test`, and single-root interpolation is `lev_dense_van`. The proof applies the tests componentwise in `weierstrass_dense`. [Test at primitive roots](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachWeierstrassTestAndDensity.lean#L172) · [Test at lower roots](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachWeierstrassTestAndDensity.lean#L188) · [Interpolation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachWeierstrassTestAndDensity.lean#L219) · [Components](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachWeierstrassTestAndDensity.lean#L284) · [Expansion at a root](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLevelExpansionAtRootOfUnity.lean#L210)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
