# Two completeness arguments solve a Frobenius difference equation

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E7%94%A8%E4%B8%A4%E5%B1%82%E5%AE%8C%E5%A4%87%E6%80%A7%E8%A7%A3%E5%95%86%E6%A8%A1%E4%B8%8A%E7%9A%84Frobenius%E5%B7%AE%E6%96%B9%E7%A8%8B.md)

Let \(D\subset M\subset V\) be additive groups and let \(\ell\) be prime. Suppose \(M,D\) are \(\ell\)-saturated in \(V\): if \(\ell x\) belongs, so does \(x\). Let \(\Phi:V\to V\) be additive, preserving \(M,D\), and \(F_0\supset F_1\supset\cdots\) additive subgroups with \(\Phi(F_j)\subset F_{j+1}\). Assume:

1. Each \(y\in M\) has \(\Phi^n y-d\in F_0\) for some \(n\ge0\), \(d\in D\).
2. Each sequence \(f_i\in M\cap F_i\) admits \(s\in M\) with \(s-\sum_{i<k}f_i\in F_k\) for every \(k\ge0\).
3. \(\bigcap_k(D+F_k)\subset D+\ell V\).
4. Every sequence \(x_i\in M\) admits \(w\in M\) with \(w-\sum_{i<k}\ell^ix_i\in\ell^k V\) for every \(k\ge0\), and \(\bigcap_k(D+\ell^k V)=D\).

Then \(\Phi-1:M/D\to M/D\) is bijective.

**Proof.** For injectivity suppose \((\Phi-1)z\in D\). All \(\Phi^n z-z\in D\); thus assumption 1 gives \(z\in D+F_0\). If \(z-d_k\in F_k\), then \(z-[\Phi d_k-(\Phi-1)z]=\Phi(z-d_k)\in F_{k+1}\), and the bracket is in \(D\). By assumption 3, \(z=d+\ell r\), and saturation gives \(r\in M\) and \((\Phi-1)r\in D\) by multiplying the latter by \(\ell\). Reapply the step to \(r\) to obtain \(z\in D+\ell^k V\) for every \(k\); assumption 4 gives \(z\in D\).

For surjectivity take \(y\in M\) and \(e=\Phi^n y-d\in F_0\). The sequence \(\Phi^ie\in M\cap F_i\) has a sum \(s\) as in assumption 2. Its \(k\)-th partial sum satisfies \((\Phi-1)s_k=\Phi^ke-e\). Thus \((\Phi-1)s+e\in F_k\) for every \(k\), so equals \(d'+\ell r\), \(d'\in D\), by assumption 3. Put \(t=\sum_{i<n}\Phi^iy\); then \((\Phi-1)t=\Phi^ny-y\). With \(z_0=-t-s\) this gives \(y-(\Phi-1)z_0=d+d'+\ell r\). Saturation gives \(r\in M\).

Repeat the construction on each new residual \(r\). This gives \(z_i\in M,d_i\in D\) with
$$
y-(\Phi-1)\sum_{i<k}\ell^i z_i-\sum_{i<k}\ell^i d_i\in\ell^k V .
$$
Assumption 4 gives \(w\) congruent to the first partial sums modulo \(\ell^kV\), and additivity preserves these congruences under \(\Phi-1\). Hence \(y-(\Phi-1)w\in D+\ell^kV\) for every \(k\), so is in \(D\). In the application the first approximation uses powers of the cyclotomic parameter modulo \(\ell\), and \(\Phi\) is a matrix times coordinatewise Frobenius.

`sub_one_bijective_quotient_of_topNilpotent` uses `step` for the fixed class and `step1` for the geometric sum modulo \(\ell\). [Lean proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/SubOneBijectiveQuotientOfTopNilpotent.lean#L5)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
