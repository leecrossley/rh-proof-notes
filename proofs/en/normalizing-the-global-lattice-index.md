# Normalizing the global lattice index over a DVR

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E6%8A%8A%E7%A6%BB%E6%95%A3%E8%B5%8B%E5%80%BC%E7%8E%AF%E7%9A%84%E9%95%BF%E5%BA%A6%E5%90%88%E6%88%90%E6%95%B4%E4%BD%93%E6%A0%BC%E6%8C%87%E6%95%B0.md)

Fix a host field $E$, local index $i$ of prime $\ell$, and good Hecke point $\pi\in Z$. Let $\mathcal O$ be the corresponding DVR with $\ell$ nonzero and noninvertible, $K$ its fraction field, and $e=\operatorname{length}_{\mathcal O}(\mathcal O/\ell\mathcal O)>0$. For finite-length $M$, put $L_\ell(M)=\operatorname{length}_{\mathcal O}(M)/e$. Write $X$ for the parameter set and $\mathbb T\subseteq\mathcal O^X$ for the integral Hecke function ring, containing the constants. The congruence ideal and normalized index are
$$
\mathfrak c_\pi=\{f(\pi): f\in\mathbb T,\ f|_{X\setminus Z}=0\},\qquad
v_\pi=L_\ell(\mathcal O/\mathfrak c_\pi).
$$
The constants make $\mathfrak c_\pi$ an ideal.

**Proposition.** Let $R,C$ be disjoint finite sets of row and column places above $\ell$ and $Q$ a finite set of specified places with units $\zeta_v\ne1$. Let $r\ge0,t\ge1$, $n_V=r+t$, $d_w=[E_w:\mathbb Q_\ell]$, and $c_B\ge0$ an integer. At rows assume finite lengths $A_w\le e\,\operatorname{lenRow}(w)$ with rational bounds $\operatorname{lenRow}(w)$. At columns let $j_w,e'_w\ge0$ be the rank and lifting exponents and assume invariant length $B_w\le\operatorname{length}_{\mathcal O}(W^{G_{E_w}})<\infty$, where $W=K^r/\mathcal O^r$ with the good-point zero-block action `WpO`. Let $S<\infty$ be the length of the strictly constrained Selmer submodule of $H^1(E,W)$, and $\mathrm{Sha}_k<\infty$ the $\mathbb Z_\ell$-length of the specified localization kernel of twist $-k$ for $1\le k<t$. Let $H_0$ be the finite maximum of the column invariant lengths for $(K/\mathcal O)(\chi_\ell^{-k})$ at $w\in C,1\le k<t$, with empty maximum zero. Assume the denominator valuation is $D=e\,v_\Delta$ with $v_\Delta=\sum_{1\le k<t}(s_0+v_\ell(k))$. Finally assume the integer length bound
$$
\begin{aligned}
\operatorname{length}_{\mathcal O}(\mathcal O/\mathfrak c_\pi)\le{}&
\sum_{w\in R}A_w+\sum_{w\in C}[ee'_w+j_w(ee'_w+D)+2D+B_w]\\
&+S+e\sum_{1\le k<t}\mathrm{Sha}_k+e\,v_\ell(h_E)
+t e c_B\sum_{w\in R}(d_w+2)\\
&+4(r+t)(|C|+1)D+t|C|H_0+t\sum_{v\in Q}\operatorname{ord}_{\mathcal O}(\zeta_v-1),
\end{aligned}
\tag{1}
$$
allowing infinite lengths. Then $\mathcal O/\mathfrak c_\pi$ has finite length and with $s_\pi=S/e$, $h_0=H_0/e$,
$$
\begin{aligned}
v_\pi\le{}&
\sum_{w\in R}\operatorname{lenRow}(w)
+\sum_{w\in C}[e'_w+j_w(e'_w+v_\Delta)+2v_\Delta+L_\ell(W^{G_{E_w}})]\\
&+s_\pi+\sum_{1\le k<t}\mathrm{Sha}_k+v_\ell(h_E)
+t c_B\sum_{w\in R}(d_w+2)\\
&+4n_V(|C|+1)v_\Delta+t|C|h_0
+t\sum_{v\in Q}L_\ell(\mathcal O/(\zeta_v-1)).
\end{aligned}
\tag{2}
$$

Every term on the right of (1) is finite, including each valuation since $\zeta_v\ne1$. Thus the left is finite. This permits passing to ordinary integer lengths before dividing by positive $e$. In Lean the conversion of extended natural lengths to naturals sends infinity to zero, so the finiteness is needed first. The uniformizer filtration shows $\operatorname{length}(\mathcal O/(a))=\operatorname{ord}_{\mathcal O}(a)$ for $a\ne0$, giving the last term of (2). Replace $A_w/e$ and $B_w/e$ by their given upper bounds, and divide the remaining terms by $e$. Since $e$ is independent of the places, $H_0/e$ is the maximum of the normalized column lengths. This proves (2). The row and column sums can be combined on $R\cup C$ because the sets are disjoint. Their separate parametrizations in Lean are injective and preserve each sum.

The project instantiates (1) using the [three block estimates](lattice-index-from-column-relations-and-cohomology.md) with $\ell$ distinct from the two specified generating primes, and the normalized block-ring identification of the congruence ideal. In the zero block the coordinate permutation comparing its matrix entries to `WpO` is equivariant and injective into $W$, giving the invariant length bound. Finiteness is proved for [the zero block](finite-quotient-invariants-from-no-fixed-vectors.md) and [the higher twists](cyclotomic-inertia-annihilates-higher-block-invariants.md). The conditions `TameGeneratorConditions` ensure $\zeta_v\ne1$ at sites of the last term.

## Lean correspondence

- `ccIdeal`, `ccAt` and `lenUnit` define the ideal, its local evaluation and the length normalization. [Definitions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/DataN.lean#L25) · [Global theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/DecompositionData.lean#L323)
- `SelmerLengthInequality` states (1), `selmer_length_inequality` normalizes it, and `theorem_of_display_inequality` combines them. `invariants_display_match` gives the zero-block comparison and `theorem_of_display_and_g2` adds finiteness. [Inequality](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/AdmissibleDesigns/HigherColumnInvariantsBound.lean#L512) · [Normalization](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/AdmissibleDesigns/HigherColumnInvariantsBound.lean#L371) · [Application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/AdmissibleDesigns/HigherColumnInvariantsBound.lean#L529)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
