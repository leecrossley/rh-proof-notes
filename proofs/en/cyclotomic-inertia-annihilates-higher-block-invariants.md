# A cyclotomic inertia element bounds higher-block invariants

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E5%88%86%E5%9C%86%E6%83%AF%E6%80%A7%E5%85%83%E8%83%BD%E6%B6%88%E5%8E%BB%E9%AB%98%E6%AC%A1%E5%9D%97%E7%9A%84%E4%B8%8D%E5%8F%98%E9%87%8F.md)

**Proposition.** Let $\ell$ be prime, $F=\mathbb Q_\ell$, $\Omega$ an algebraic closure, $F^{\rm nr}$ the maximal unramified extension in it, and $\chi_\ell$ the $\ell$-adic cyclotomic character. Assume $s\ge1$ and that a finite extension $L/F$ in $\Omega$ satisfies $L\subseteq F^{\rm nr}(\mu_{\ell^s})$. Let $\mathcal O$ be a DVR finite over $\mathbb Z_\ell$ with injective coefficient map, and $K=\operatorname{Frac}(\mathcal O)$. For every integer $a\ge1$ let $G_L$ act on $K/\mathcal O$ by $\chi_\ell^{-a}$. Then the invariant submodule is annihilated by
$$
c_a=(1+\ell^s)^a-1\ne0
$$
and has length at most $\operatorname{ord}_{\mathcal O}(c_a)$.

For $n\ge1$, $\Phi_{\ell^n}(1+X)$ is monic with constant term $\ell$ and reduces to $X^{\ell^{n-1}(\ell-1)}$ modulo $\ell$, by the geometric-sum expression for $\Phi_{\ell^n}$. Thus it is Eisenstein over every finite unramified extension of $F$. It remains irreducible over $F^{\rm nr}$ since the coefficients of any factorization would lie in a finite such extension. Consequently exponentiation by $1+\ell^s\bmod\ell^n$ on the roots defines an automorphism of $F^{\rm nr}(\mu_{\ell^n})$ over $F^{\rm nr}$. These compatible automorphisms define one on the union, which extends to $\Omega$. The resulting $g$ fixes $F^{\rm nr}$ and $\mu_{\ell^s}$, hence fixes $L$ and its maximal unramified extension $LF^{\rm nr}$. Thus $g$ is in the inertia group of $L$ and $\chi_\ell(g)=1+\ell^s$. The same construction works with any $1+\ell^s z$ for $z\in\mathbb Z_\ell$.

For a fixed class $x$ one has $(1+\ell^s)^{-a}x=x$, hence $c_ax=0$. The integer $c_a$ is nonzero since $a\ge1$. The submodule it annihilates is $c_a^{-1}\mathcal O/\mathcal O\simeq\mathcal O/c_a\mathcal O$, whose length is its valuation. This proves the proposition.

In the higher-block column estimate let $C$ be the finite set of column places, $t\ge1$, and let $H_{w,a}$ be the length of the invariants of $(K/\mathcal O)(\chi_\ell^{-a})$ under $G_{E_w}$ for $w\in C$, $1\le a<t$. The host-field hypothesis supplies the cyclotomic containment locally, so the proposition makes each length finite. Let $H_{\max}$ be their maximum, or zero if there are none. The normalized block isomorphism identifies the twisted $k$th module, $2\le k\le t$, with $(K/\mathcal O)(\chi_\ell^{-(k-1)})$. Its column coboundary map $x\mapsto(g\mapsto gx-x)$ has exactly the corresponding invariants as kernel. Thus all the higher-block column terms are bounded in total by $t|C|H_{\max}$. The zero block uses the [general quotient argument](finite-quotient-invariants-from-no-fixed-vectors.md).

## Lean correspondence

- `GlobalTheory.Cyc.exists_inertia_cycZ_eq`, `GlobalTheory.EpsInertia.fix_roots`, and `epsAll` supply the element and its passage to the global decomposition group. [Inertia](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsInertiaCycZEq.lean#L27) · [Passage to the host](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CycZBridge.lean#L50)
- `length_lt_top_of_killed` and `finiteLength_invariants_negTwist_KmodO` give finite length. `ShaT.blkTw_of_def` and `kernel_length_higher_columns` transfer it to the column. [Finite length](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/FiniteLengthInvariantsNegTwistKmodO.lean) · [Block isomorphism](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/AdmissibleDesigns/H1MapMemLcH1.lean#L179) · [Column](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/AdmissibleDesigns/KernelLengthHigherColumns.lean#L156)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
