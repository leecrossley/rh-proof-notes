# Top-row capacities and prime-power ramps

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

A determinant of a matrix of formal series is differentiated once for every cell of a Young diagram. The top row at a selected orbit slot can be much longer than the other rows. Its long degree budget gives a valuation gain, but other rows can consume part of that budget. This note proves the estimate that converts those capacity constraints into positive parts of the form $(A/p^e-C)_+$.

## Data and exact bound

Let $p\ge3$ be an integer, $d\ge2$ even, $S=\mathbb Z/d\mathbb Z$, and $T\subseteq S$. Take nonnegative integers $a_s,b_s,n_s$ with $b_s\le a_s\le n_s$. They will be the first and second row lengths and the total size of a Young diagram. Put
$$
C_s=\begin{cases}b_s&s\in T,\\a_s&s\notin T,\end{cases}
\qquad
D_s=n_s-\mathbf1_{s\in T}a_s,\qquad
\gamma=\frac p{p^2-1}.
$$
For each $s$, let $J_s$ be the least positive odd $e$ with $s+e\in T$ and set $J_s=+\infty$ if there is no such $e$. Define
$$
\begin{aligned}
G_s &= \sum_{\substack{e\ge1,\ e\ \mathrm{odd}\\ e<J_s}}(a_s/p^e-C_{s+e})_+
      +\sum_{\substack{e\ge1,\ e\ \mathrm{odd}\\ J_s<e}} a_s/p^e,\\
W_s &= \max\bigl(\{C_{s-e}:e>0\text{ odd},\ p^e\le n_{s-e}\}\cup\{0\}\bigr).
\end{aligned}
$$
Here $x_+=\max(x,0)$. These are `topTerm` and `Wcap`. Take optimal dual weights $\sigma_s$ for the degree vector $D$ as in the [cyclic degree problem](cyclic-degree-budgets-and-flow-duality.md).

Let $I$ be a finite set of variables with labels $\lambda(i)\in S$, degrees $\kappa_i\in\mathbb Z_{\ge0}$, and a specified subset of top variables. Each top variable has label in $T$. The top variables with label $s\in T$ have total degree $a_s$, and the ordinary variables at $s$ have total degree $D_s$. Each ordinary variable is assigned either no tag or a tag $(s,j)$ with $s\in T$, $j$ an odd integer and $\lambda(i)=s+j$ in $S$. Require $p^j\le a_s$ for a positive $j$ and $p^{-j}\le n_{\lambda(i)}$ for a negative $j$. For each tag $(s,j)$ the sum of $\kappa_i$ over variables with that tag is at most $C_{s+j}$.

**Claim.** There are $\varepsilon_s\ge0$, with $\varepsilon_s\ge p^{-J_s}$ when $s\in T$ and $J_s<\infty$, giving weights
$$
\tau_i=\begin{cases}
\varepsilon_{\lambda(i)}& i\text{ top},\\
\sigma_{\lambda(i)}& i\text{ ordinary, without tag},\\
\max(\sigma_{\lambda(i)},1-p^j\varepsilon_s)& i\text{ tagged }(s,j),\ j>0,\\
\max(\sigma_{\lambda(i)},p^j)& i\text{ tagged }(s,j),\ j<0
\end{cases}
$$
such that
$$
\sum_i\kappa_i(\gamma-\tau_i)\ge \sum_{s\in T}(G_s-\gamma W_s)+F(D).
$$
This is `ThmAAssembly`, realized by `rowRadiusAssembly`. The signs of $j$ record which of the two exponents in an exceptional monomial is larger. [Definition of the row weights](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GaussJetBounds/StatementA.lean#L10) · [Statement of the assembly](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GaussJetBounds/StatementA.lean#L19) · [Row-radius assembly](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GaussJetBounds/GaussJetProofs/CapacityLeReachCapacity.lean#L278)

## Choose a weight for the long row

Fix a top label $s$ and write $A=a_s$, $J=J_s$, $C(e)=C_{s+e}$. On positive odd $e$ the geometric sum of $A/p^e$ is $A\gamma$. Subtract the summand of $G_s$ from $A/p^e$ and denote the remainder by $H_e$, extending it by zero to even $e$. Then $H_e=\min(A/p^e,C(e))$ below $J$, $H_J=A/p^J$ when $J$ is finite, and $H_e=0$ above $J$. All these remainders are nonnegative.

Let $\mathcal R$ be the finite set of positive tag levels present anywhere in the monomial. We want
$$
A\varepsilon_s+\sum_{j\in\mathcal R}C(j)(1-p^j\varepsilon_s)_+
\le\sum_e H_e=A\gamma-G_s. \tag{1}
$$
Choose the smallest positive odd $q<J$ for which $H_q=A/p^q$, if there is one. Otherwise take $q=J$ when $J<\infty$. In either case put $\varepsilon_s=p^{-q}$. For odd $j<q$ the minimality gives $C(j)=H_j$. For $j\ge q$ the positive part vanishes. Thus the sum in (1) is at most $\sum_{e<q}H_e$ and its first term is $H_q$. Since $q\le J$, this weight also has $\varepsilon_s\ge p^{-J}$ when required. If no $q$ exists, then $J=+\infty$ and $H_j=C(j)$ for every positive odd $j$. Set $\varepsilon_s=0$ and use the same bound (1). At labels outside $T$ the weights can be chosen by the same rule. This choice is `asmA_top_gen`. [Cutoff choice](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GaussJetBounds/GaussJetProofs/CapacityLeReachCapacity.lean#L81) · [Remainder of the odd geometric series](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GaussJetBounds/GaussJetProofs/CapacityLeReachCapacity.lean#L126)

## Pay for each possible modification of a row weight

With the top weights chosen and every ordinary weight initially $\sigma_{\lambda(i)}$, the sum of $\kappa_i(\gamma-\tau_i)$ before the ordinary modifications equals $\sum_{s\in T}a_s(\gamma-\varepsilon_s)+F(D)$. This uses the total degrees and the dual maximum formula.

A positive tag increases the weight by at most $(1-p^j\varepsilon_s)_+$. Group the variables by tag. At fixed $(s,j)$ their total degree is at most $C(j)$, so all positive tags at $s$ cost at most the sum in (1). Together with $a_s\varepsilon_s$, this leaves at least $G_s$ out of $a_s\gamma$. A negative tag with $j=-e$ increases the weight by at most $p^{-e}$. At fixed $(s,-e)$ its degree is at most $C_{s-e}\le W_s$, by $p^e\le n_{s-e}$. Sum over distinct negative tag levels at $s$ and then use $\sum_{e>0,\ e\ \mathrm{odd}}p^{-e}=\gamma$. The cost is at most $\gamma W_s$. Summing over the top labels yields the claimed bound. [Reachable capacities](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GaussJetBounds/GaussJetProofs/CapacityLeReachCapacity.lean#L219) · [Cost of increasing a weight](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GaussJetBounds/GaussJetProofs/CapacityLeReachCapacity.lean#L255)

## Why these weights control the small coefficients

Use the exceptional monomials from the [jet coefficient bound](prime-powers-in-the-jet-coefficient-bound.md), so their labels obey $\lambda(i)+\alpha=\lambda(j)+\beta$ and are of opposite parity. In the determinant construction there is an additional condition on tags and coefficients. Whenever a two-power monomial dividing the chosen monomial has a coefficient below the uniform threshold and exactly one of its variables is top, the ordinary variable carries the tag $(s,\alpha-\beta)$, with $s$ the top label and $\alpha,\beta$ the exponent indices at the top and ordinary variables. The frame and label construction in Lean supplies this condition. It is the condition that allows the following coefficient argument to apply.

For two ordinary variables the all-odd dual inequalities give the missing unit, as in the preceding note, since their weights are at least the corresponding dual weights. For a top variable at $s$ and an ordinary variable with tag $(s,j)$, if $j=\alpha-\beta>0$, the added weights contribute at least $p^\beta(p^j\varepsilon_s+1-p^j\varepsilon_s)=p^\beta\ge1$. If $j<0$, the ordinary variable contributes at least $p^\beta p^j=p^\alpha\ge1$. Finally, if both variables are top, order them so that $\alpha>\beta$. The odd shift $e=\alpha-\beta$ reaches the second top label, so $J_s\le e$. Thus $p^\alpha\varepsilon_s\ge p^{\alpha-e}=p^\beta\ge1$ already. These are the other three cases of `dualRadiiInequalities`.

The weighted derivative bound therefore yields a local gain of $\sum_{s\in T}(G_s-\gamma W_s)+F(D)$ up to the logarithmic factorial loss, for each monomial for which the frame and degree conditions hold. The frame proof constructs those rows and then removes the auxiliary variables to bound the actual determinant coefficients. [Construction and removal of the frame](generic-frames-for-the-determinant-jet.md) · [Four radius checks](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GaussJetBounds/GaussJetProofs/OneLetterRadiusIdentity.lean#L124) · [Where the tag condition is used](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GaussJetBounds/GaussJetProofs/TheoremAOneMonomialLogLoss.lean#L15)

At a signal prime, an odd Frobenius shift always moves a top label to the other half of the orbit, where there are no top labels. Then $J_s=+\infty$ and $G_s$ consists entirely of the positive parts in (1), one for each odd power. The next proof identifies these terms with the local summands used in the window's comparison with the prime-power count. [From orbit valuations to the prime-power count](from-orbit-valuations-to-the-prime-power-count.md).

Status. Source-based reconstruction draft. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
