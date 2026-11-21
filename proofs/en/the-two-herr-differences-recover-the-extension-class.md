# The two Herr differences recover the extension class

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88Herr%E5%AF%B9%E7%9A%84%E4%B8%A4%E4%B8%AA%E7%AE%97%E5%AD%90%E5%B7%AE%E7%BB%99%E5%87%BA%E5%90%8C%E4%B8%80%E4%B8%AA%E6%89%A9%E5%BC%A0%E7%B1%BB.md)

Use the groups, generator, étale modules and comparison in [integral Herr cohomology](herr-cocycles-and-integral-galois-cohomology.md). Let \(0\to T\xrightarrow{\iota}T'\xrightarrow{q}O\to0\) be exact in continuous lattices, with trivial action on \(O\). Take \(e\in D(O)\) fixed by Frobenius and the cyclotomic action, with \(J_O(e)=1\otimes e_0\), \(e_0\in O^\times\). Let \(a\in O\) and \(x\in D(T')^\Delta\) with \(D(q)x=ae\). Define \(y,z\) by
$$
D(\iota)y=(\varphi-1)x,\qquad D(\iota)z=(\gamma-1)x.
$$
Then \(y,z\) are a Herr pair in \(D(T)^\Delta\) and \({\rm cl}_T(y,z)=a\kappa\), where \(\kappa\) is the connecting class of \(e_0\). For the class \(\kappa_1\) of \(1\), this is \(ae_0\kappa_1\).

**Proof.** Both differences in the display map to zero under \(D(q)\), so [étale exactness](etale-exactness-descends-from-the-period-ring.md) gives unique preimages. They are \(\Delta\)-fixed and satisfy the Herr cocycle identity by commuting the operators and using injectivity of \(D(\iota)\).

Lift \(e_0\) to \(t\in T'\), giving \(c(\sigma)=\iota^{-1}(\sigma t-t)\). The vector \(J_{T'}(x)-1\otimes at\) maps to zero in \(P(O)\). The tensor sequence on periods is exact, since the original short exact sequence splits over \(O\). Write the difference as \(P(\iota)b\). Then \((\varphi-1)b=J_T(y)\) because Frobenius fixes \(1\otimes at\). If \(\sigma\) lifts \(\Delta\), it fixes \(x\), so \(-(\sigma-1)b=1\otimes ac(\sigma)\). If \(\sigma\) lifts \(\gamma\), the defining equation for \(z\) gives \(J_T(z)-(\sigma-1)b=1\otimes ac(\sigma)\). These are the Herr representative formulas, and agreement on these lifts gives agreement everywhere by continuity. Thus the class is \(a\kappa\).

If \(e'\) is another Frobenius- and cyclotomic-fixed generator of the rank-one Wach lattice of \(O\), then \(e'=u e\) for a unit of the coefficient ring. Frobenius's fixed vectors in the period module give \(J_O(e')=1\otimes e_0'\), \(e_0'\in O\). The comparison of the generators makes \(e_0'\) a unit in the period ring and hence in \(O\): a nonunit in \(O\) lies in its uniformizer ideal, whose image is in the Jacobson radical since a uniformizer power is a unit times \(\ell\). The factor \(e_0'/e_0\) is therefore a unit and can be removed by rescaling the lift.

`dict_K` compares the representative, `unitVector` supplies the two compatible generators, and `herr_extension_class_formula` gives the formula at either group. `coreExtΔ_of` applies the unit rescaling and tame averaging in lifting to the Wach lattice. [Representative](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/MemFixingSubgroupMaxUnramifiedOfMemLocalGalois.lean#L451) · [Unit generator](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/UnitVectorOfUnitFor.lean#L51) · [Formula](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/HerrExtensionClassFormula.lean#L15) · [Wach application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/ExtensionInvariantClause.lean#L144)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
