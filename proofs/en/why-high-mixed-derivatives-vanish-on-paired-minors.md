# Why high mixed derivatives vanish on paired minors

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix integers $N_0,N_1\ge0$. At each index $t$ of a finite set $H$ there are two $N_0$-by-$N_1$ matrices $Z_t^-,Z_t^+$ of independent polynomial variables. For either sign take auxiliary row variables $X_{t,r,a}^\pm$ for row index $r\ge0$ and $1\le a\le N_0$. The linear form in column $b$ of row $r$ is
$$
\ell^\pm_{t,r,b}=\sum_{a=1}^{N_0} X_{t,r,a}^\pm Z_{t,a,b}^\pm .
$$
Take a Young diagram $\nu_t^\pm$ for each sign and place. For each of its columns of height $h$, choose $h$ distinct column indices of $Z_t^\pm$, in increasing order. Form the determinant of the $h$-by-$h$ matrix of $\ell^\pm$'s using those columns and rows $0,\ldots,h-1$. Let $P_t^\pm$ be the product of the resulting minors. The full polynomial $P=\prod_t P_t^-P_t^+$ is `Gxz`. If no admissible column choice exists, a universal assertion over such choices has empty range.

Set $\Delta_t=\sum_{a,b}\partial_{Z_{t,a,b}^-}\partial_{Z_{t,a,b}^+}$. Let $d_t^-$ be the number of cells in $\nu_t^-$ and $w_t^\pm$ the number of cells in its indicated top row. For every $n>d_t^--w_t^-+\min(w_t^-,w_t^+)$,
$$
\Delta_t^n P=0.
$$
This is the local cancellation in the discriminant-prime jet bound.

**Proof.** Suppress $t$; the factors at other places are constant for $\Delta_t$. Expand each minus determinant into products of its linear forms. Every resulting term is a product of $d^-$ factors, with $w^-$ from row $0$ and $d^--w^-$ from the other rows. For a single factor $\ell^-_{r,b}$, contracting its minus derivative with the plus derivative applies the operator
$$
D_{r,b}=\sum_a X^-_{r,a}\partial_{Z^+_{a,b}}
$$
to the plus polynomial. By the Leibniz rule, a contraction on a product of minus linear forms and a plus polynomial sums over the choices of one minus factor to remove, applying its $D_{r,b}$ to the plus polynomial. This is because all minus derivatives kill the plus polynomial and vice versa. Applying $n$ contractions therefore sums over ordered choices of $n$ distinct minus factor slots, applying the corresponding $n$ operators to $P^+$. All $D_{r,b}$'s commute, since their coefficients involve only auxiliary $X$-variables.

For $r=0$, $D_{0,b}$ differentiates the plus matrix column $b$ in the direction $X^-_0$. A simultaneous shift of any plus columns by multiples of $X^-_0$ adds to each column of a plus minor a multiple of a common vector, with entries $\sum_a X^+_{r,a}X^-_{0,a}$ in the rows of that minor. Expanding the determinant by multilinearity, terms using two such added columns vanish by alternation. Hence each plus minor has total degree at most one in all the shift parameters. Their product has total degree at most $w^+$. It is killed by every composite of more than $w^+$ operators $D_{0,b}$, including when one column index repeats. This follows by identifying each composite with the corresponding partial derivative of the shifted polynomial at zero.

If $n>d^-$, no ordered choice of $n$ distinct minus factor slots exists. For $n\le d^-$, if $n>d^--w^-+\min(w^-,w^+)$ then $w^+<w^-$ and any choice must contain more than $w^+$ row-zero slots. Commuting those derivatives together kills the plus polynomial. Thus every term in the minus determinant expansion vanishes under $\Delta_t^n$, as claimed.

**Lean correspondence.** The operators and bound are [`lapT` and `PLapZero`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/PartialDerivativeMinors/PMinorAff.lean#L91). [`minorAff_derDet`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/PartialDerivativeMinors/MinorAff.lean#L28) proves the rank-one derivative identity, [`symbol_degree_mul`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/PartialDerivativeMinors/SDegMul.lean#L24) bounds the derivative order of the product, and [`pLapForms`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/PartialDerivativeMinors/LapForms.lean#L360) carries out the ordered contractions. The conclusion for the full polynomial is [`lapZero_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/PartialDerivativeMinors/HeartPderivMinor.lean#L84).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
