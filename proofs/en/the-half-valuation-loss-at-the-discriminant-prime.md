# The half-valuation loss at the discriminant prime

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Use the polynomial $P$ and the notation of [the paired minors](why-high-mixed-derivatives-vanish-on-paired-minors.md). Let $p$ be prime, normalize $v_p(p)=1$, and let $\mathrm{Th}$ be a formal power series in all the $Z^\pm_{t,a,b}$ over $\mathbb C_p$. For a multi-index $\alpha$ write $\alpha!=\prod_v\alpha_v!$, and $J_\alpha(F)=\alpha![Z^\alpha]F$ for the corresponding derivative at the origin. Assume the discriminant-prime shape `ShapeD`:
$$
\mathrm{Th}(Z)=\exp\!\left(-S\sum_{t\in H} u_t\sum_{a,b} Z_{t,a,b}^-Z_{t,a,b}^+\right)G(Z),
\quad |S|_p\le p^{1/2},\quad |u_t|_p\le1,\quad |J_\alpha(G)|_p\le1\text{ for all }\alpha .
$$
Here integrality is required for the derivatives of $G$, with the factorial included. The entry of the map under study is the coefficient of any fixed auxiliary monomial $X^\beta$ in $P(X,\partial_Z)\mathrm{Th}|_{Z=0}$. The claim is that the valuation of each such coefficient is at least
$$
-\frac12\sum_{t\in H}\left(d_t^--w_t^-+\min(w_t^-,w_t^+)\right).
$$

**Expansion at the origin.** Write $P=\sum_{\beta,\eta}P_{\beta,\eta}X^\beta Z^\eta$. The Gaussian factors into one exponential for each paired entry $(t,a,b)$. Its $\kappa$-jet vanishes unless the two exponent lists agree entrywise, say $\kappa^-_{t,a,b}=\kappa^+_{t,a,b}=k_{t,a,b}$. In that case the jet is
$\prod_{t,a,b} k_{t,a,b}!(-S u_t)^{k_{t,a,b}}$, since the coefficient of the paired power divides by one factorial and the derivative multiplies by two. For fixed $\beta$, apply the product rule to $J_\eta(\mathrm{Th})$ and group terms by the derivative $\lambda$ landing on $G$ and the total $n_t=\sum_{a,b}k_{t,a,b}$ of pairs at each place. The entry is a finite sum of terms
$$
 J_\lambda(G)\prod_t(-S u_t)^{n_t}\,A_{\beta,\lambda,n},
$$
where $A_{\beta,\lambda,n}$ is the integer obtained by summing
$P_{\beta,\eta}\binom{\eta}{\lambda}\prod_{t,a,b}k_{t,a,b}!$
over the balanced differences $\eta-\lambda=(k,k)$ with these totals.

**Cancellation before taking norms.** Expand $\prod_t\Delta_t^{n_t}P$ using the multinomial theorem for the commuting partial derivatives. The sequence with multiplicities $k$ has coefficient $\prod_t n_t!/\prod_{t,a,b}k_{t,a,b}!$, and its differentiated monomial contributes $\eta!/\lambda!$. For a balanced difference $\eta-\lambda=(k,k)$ this quotient is $\binom{\eta}{\lambda}\prod_{t,a,b}(k_{t,a,b}!)^2$. It follows that
$$
[X^\beta Z^\lambda]\left(\prod_t\Delta_t^{n_t}P\right)
=\left(\prod_t n_t!\right) A_{\beta,\lambda,n}.
$$
If any $n_t$ exceeds the bound in the paired-minor lemma then the differentiated polynomial is zero, since the placewise operators commute. The factor of factorials is nonzero over $\mathbb Z$, so $A_{\beta,\lambda,n}=0$. For each remaining term $J_\lambda(G)$ and the integer $A_{\beta,\lambda,n}$ have norm at most one. Its norm is at most $p^{\frac12\sum_t n_t}$, which is at most $p^{\frac12\sum_t(d_t^--w_t^-+\min(w_t^-,w_t^+))}$. The ultrametric inequality gives the same bound for the entire entry. This proves the valuation claim even when some entries vanish.

**The project's loss.** At a level-free coefficient place above the discriminant prime, let $\nu_t^\pm$ be the project's diagrams at $(\mathrm{false},t)$ and $(\mathrm{true},t)$ for word $u$ and transition $i\to i+1$, $i<m$. Their rows of index $r<N_i$ are the specified numbers $\mathrm{nuRow}(D,u,i+1,\tau,r)$ and all other rows vanish. Thus $d_t^-$ is the sum of the minus row lengths. With $w_{t,1}^-$ the length of row $1$, the local constant `ctD` is
$$
C_t=
\begin{cases}
d_t^--w_t^-+w_{t,1}^-+w_t^+,&t\in D.\mathrm{host}.\mathrm{TT},\\
d_t^-,&t\notin D.\mathrm{host}.\mathrm{TT}.
\end{cases}
$$
The first case bounds the contraction count since $w_{t,1}^-\ge0$ and $\min(w_t^-,w_t^+)\le w_t^+$; the second uses $\min(w_t^-,w_t^+)\le w_t^-$. Hence $-\sum_t C_t/2$ is a valid valuation lower bound on every entry. This is `EntriesAtDiscriminant` once the shape is supplied for every indexed kernel.

**Lean correspondence.** The derivative and loss conditions are [`applyAt0`, `KvalGe` and `EntAtD`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/EntAtD.lean#L36). The Gaussian coefficients, derivative bridge, and cancellation are [`pExpCoeff`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/PartialDerivativeMinors/ExpCoeff.lean#L148), [`pBridge`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/PartialDerivativeMinors/Bridge.lean#L426) and [`vanish_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/PartialDerivativeMinors/Vanish.lean#L25). The norm step is [`core_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/PartialDerivativeMinors/CoreTermLe.lean#L48), and [`cPr_le_ctD`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/PartialDerivativeMinors/CardCellsEqSumRowLen.lean#L29) compares the two losses using the diagram rows. [`jet_bound_ramified_prime`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/OrbitalBoundsConclusion/EntAtD.lean#L10) assembles the proof. The [actual kernel Gaussian](the-normalized-kernel-has-a-common-ramified-gaussian.md) supplies the shape input to this note.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
