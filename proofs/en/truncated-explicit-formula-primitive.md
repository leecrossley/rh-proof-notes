# The truncated explicit formula for a primitive character

[Chinese proof](../zh/%E6%9C%AC%E5%8E%9F%E7%89%B9%E5%BE%81%E7%9A%84%E6%88%AA%E6%96%AD%E6%98%BE%E5%BC%8F%E5%85%AC%E5%BC%8F%E6%80%8E%E6%A0%B7%E5%90%88%E6%88%90.md)

Let $\chi$ be primitive modulo $q\ge1$, and let $\Psi_\chi(u)=\sum_{n\le u}\Lambda(n)\chi(n)$. Write $W(Y)=\{\rho:L(\rho,\chi)=0,\ 0<\Re\rho<1,\ |\Im\rho|\le Y\}$, with multiplicity $m_\rho$. The project quantity `psi0 χ u` is $\Psi_\chi(u)-\mathbf1_{\chi=\chi_0}u$. The sums `zsum χ 0 Y f` and `zsumR χ 0 Y f` sum $m_\rho f(\rho)$ over $W(Y)$, for complex and real $f$ respectively.

**Proposition.** There is an absolute $C>0$ such that for every $q,\chi$ as above and real $2\le T\le u$, the set $W(T)$ is finite and
$$
\left|\Psi_\chi(u)-\mathbf1_{\chi=\chi_0}u+
\sum_{\rho\in W(T)} m_\rho u^\rho/\rho\right|
\le C\left(\frac{u\log^2(quT)}T+\log(qu)+
\sum_{\rho\in W(1)}m_\rho/|\rho|\right).
\tag{1}
$$

The [local disk estimate](local-log-derivative-from-disk-zeros.md) bounds the total multiplicity in $0<\Re\rho<1,\ |\Im\rho-v|\le1$ by $O(\log(q(|v|+2)))$. Covering a bounded height range by finitely many such windows gives the finiteness of $W(Y)$. Write $Z(Y)$ for the window with strict height bound $|\Im\rho|<Y$. For $T\le T'\le T+1$, the difference $Z(T')\setminus Z(T)$ lies in the unit windows at $\pm T$ and has $|u^\rho/\rho|\le u/T$. Thus
$$
\left|\sum_{\rho\in Z(T')}m_\rho u^\rho/\rho-\sum_{\rho\in Z(T)}m_\rho u^\rho/\rho\right|
\ll (u/T)\log(q(T+2)).
\tag{2}
$$

The [Perron shift](shifting-perron-past-zeros.md) supplies $T'\in[T,T+1]$ and the residue formula with $Z(T')$ and $Z(1)$ for the integral on $\Re s=1+1/\log u$. Since $2\le T'\le T+1\le2u$, [truncated Perron inversion](truncated-perron-prime-powers.md) replaces that integral by $\Psi_\chi(u)$ at cost $O((u/T')\log^2u+\log u)$. A primitive character is principal exactly at modulus $1$, so the main term in the shift is $\mathbf1_{\chi=\chi_0}u$. By (2) we can use $Z(T)$ in the resulting bound, with the same error as in (1) using $Z(1)$.

Finally choose $T''\in(T,T+1)$ smaller than or equal to every height $|\Im\rho|>T$ in $W(T+1)$. This is possible because those heights form a finite set. Then $Z(T'')=W(T)$. Apply (2) with $T''$ to the open-window formula, and bound the reciprocal sum for $Z(1)$ by that for $W(1)$. This proves (1), including zeros at height exactly $T$.

## Lean correspondence

- `GlobalTheory.ZeroBand.zeros_band` gives (2), and `truncated_explicit_formula` combines the integral bounds for the open window. [Band](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/FiniteBox.lean#L96) · [Open window](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/TruncatedExplicitFormula.lean#L11)
- `exists_open_eq_closed` chooses $T''$, and `explicit_formula_closed` proves (1). The right-half formula uses the forwarding theorem `GlobalTheory.T.norm_psi0_add_zsum_le`. [Choice](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExplicitFormulaClosed.lean#L16) · [Closed formula](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExplicitFormulaClosed.lean#L44) · [Forwarding statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExplicitFormulaClosedStatement.lean#L12)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
