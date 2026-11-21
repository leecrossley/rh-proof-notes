# Summing the local lengths within the window

[Chinese proof](../zh/%E6%8A%8A%E5%90%84%E7%B1%BB%E7%B4%A0%E6%95%B0%E7%9A%84%E5%B1%80%E9%83%A8%E9%95%BF%E5%BA%A6%E5%8A%A0%E8%B5%B7%E6%9D%A5%E4%B8%BA%E4%BB%80%E4%B9%88%E4%BB%8D%E5%9C%A8%E7%AA%97%E5%8F%A3%E5%86%85.md)

## Statement

Fix row $D$, its size data and compatible parameter choice $P$. Put $x>1$, $\varepsilon>0$, $L=x^\varepsilon$, $b=e^L$, and let $f,m\ge1$ be the degree and layer parameters. Assume `admitted` for a real $C$: whenever `ShaFinOdd` holds, a table satisfies the seventeen `AdmT` conditions, including the point-to-local-length, rank, numerical and parameter bounds. Also assume `Large`:
$$
\begin{gathered}
x\ge100,\quad 8x\le e^{x^{\varepsilon/3}},\quad 4\le b,\quad
x^{C+2}e^{x^{\varepsilon/3}}\le b,\quad 48C\le\sqrt{x},\\
(C+3)^2(1+\log x)^2\le L,\quad
x^{20(C+2)}e^{20x^{\varepsilon/4}}\le e^{x^{\varepsilon/3}},\quad
10^8(C+1)^3\le x.
\end{gathered}
$$
For any such row with `ShaFinOdd`, layer $1\le j\le m$, and summable $V(\ell)=\log\ell\sum_{1\le e<t}\mathrm{shaLen}(\ell,e)$ over primes, with other terms zero, one has
$$
\eta_{\rm sum}(j)\le d_j\left[
2000(|C|+1)^3\big(fm\,b L^2+(\log x)^2N_c\big)+\sum_\ell V(\ell)\right].
\tag{1}
$$
Here $\eta_{\rm sum}$ adds weighted local lengths, $d_j$ is the reference rank, and $N_c\ge0$ a lattice budget. The tables come from the [rowwise comparison](rowwise-local-estimates-give-linkn-for-the-original-family.md).

## Grouping by rational prime

One parameter condition gives $0<P.\mathrm{CLw}\le C$. Let $S$ be the finite set of residue characteristics of active places and $\eta_\ell$ their contribution above $\ell$. The table yields
$$
\eta_\ell\le d_j\log\ell\left(\nu_\ell+2/\ell^2+\lambda_C(\ell)
+\mathrm{VV}(\ell)+v_\ell(h_E)+v_\ell(A)\right).
\tag{2}
$$
Here $h_E,A$ are the class number and the finite group order, $\mathrm{VV}(\ell)=\sum_{1\le e<t}\mathrm{shaLen}(\ell,e)$, and the baseline costs $\nu_\ell\ge0$ obey $\sum_{\ell\in S}\nu_\ell\log\ell\le\nu_{\rm budget}$. At generator primes the bound is already rank-normalized. At the other primes use the pointwise valuation comparison and good-point multiplicities, whose sum is bounded by local rank, identified with $d_j$. Summing the normalized ramification and residue-degree weights above $\ell$ gives at most $\log\ell$.

The inverse-square term has total at most six by $\sum_{n\ge2}(\log n)/n^2\le2$. Factorization bounds the two valuation sums by $\log h_E,\log A$. Nonnegativity and summability bound the cohomology terms by $\sum_\ell V(\ell)$. Thus for $B_0=6+\nu_{\rm budget}+\log h_E+\log A$,
$$
\eta_{\rm sum}(j)\le d_j\left(B_0+\sum_{\ell\in S}\log\ell\,\lambda_C(\ell)+\sum_\ell V(\ell)\right).
\tag{3}
$$

## The local cost sums

Put $X=fm\,bL^2$, $U=x^{C+2}e^{x^{\varepsilon/4}}$, and write $\ell_*$ for the small-prime threshold, $J$ for generator primes, $T_0$ for designated small primes, $q,d$ for chosen ramified primes, and $E_{\mathrm{exc}}$ for exceptions. The five input estimates, each valid for any finite subset in its case, are:

- On generator primes, the sum of $C x^C\eta_{\rm size}\log\ell$ is at most $2(C+1)^2U^{18}$.
- On $T_0\cup\{3\}$, the sum of $(C fmb\log x+Cx^C L^2)\log\ell$ is at most $8CX$.
- On $\{q,d\}$, the sum of $2C fmb\log\ell$ is at most $4CX$.
- On $5\le\ell\le\ell_*$, the sum of $(\mathrm{bbB}+\mathrm{lenB}(\ell))\log\ell$ is at most $1000(C+1)^3X$.
- Above $\ell_*$ in $E_{\mathrm{exc}}$, the same sum is at most $1164000(C+1)^2U^{18}$.

Here $\mathrm{bbB}=Cfn t^2 n_V L^2$ with row rank parameters $n,t,n_V$. The definition of $\mathrm{lenB}$ splits by splitting, the specified range with large inertia degree, and the remaining case. The last sum uses at most $388U^8$ exceptions, $\ell\le3b$ giving $\log\ell\le3U$, and unweighted cost at most $1000(C+1)^2U^9$. Their product gives the reported constant. The fourth input sums by inertia degree in the short range. In defining $\lambda_C$, test generator primes first, then the designated small primes and three, then $q,d$. Above $\ell_*$ outside exceptions the term is zero. The two remaining cases use $\mathrm{bbB}+\mathrm{lenB}(\ell)$. All case bounds are nonnegative, so their sum works also for intersecting sets. Since $2\in T_0$, small primes left for the fourth case are at least five.

## Absorbing the costs

The parameter bounds give $n,t,r,x^C,L\le U$, with $\nu_{\rm budget}\le2\log n+\log t+\log r\le4U$, $\log h_E\le Cx^C$ and $\log A\le Cx^CL$. Consequently $B_0\le20(C+1)^2U^{18}$. From `Large`, $4\cdot10^6(C+1)^2\le x^2\le x^{2(C+2)}$. Multiply by $U^{18}$ and apply the two exponential comparisons to obtain $4\cdot10^6(C+1)^2U^{18}\le b$. The baseline and the generator and exception costs together are therefore at most $b\le X$. Adding $8CX$, $4CX$ and $1000(C+1)^3X$ gives at most $2000(C+1)^3X$. Substitute into (3) and enlarge $X$ by the nonnegative $(\log x)^2N_c$. The cohomology coefficient is one.

For fixed $\varepsilon>0,C$, all eight scale conditions hold eventually, by $\log x=o(x^\delta)$ for positive $\delta$ and domination of the lower powers by the higher powers in the exponential comparisons. Choose a common threshold also above the row table and family thresholds. The same $C$ then gives (1) throughout the family.

## Lean correspondence

- [`lamG`, `lamB` and `etaSum_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/MemPrimesOverOfMem.lean#L249) give the cost priority and the rational-prime sum.
- [`sum_small`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/ExportBoundOfAdmissible.lean#L18), [`sum_exc`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/ExportBoundOfAdmissible.lean#L611), [`sum_g`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/ExportBoundOfAdmissible.lean#L651), [`sum_23`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/ExportBoundOfAdmissible.lean#L733), [`sum_qd`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/ExportBoundOfAdmissible.lean#L798), and [`glob_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/ExportBoundOfAdmissible.lean#L825) give the inputs.
- [`Large`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/NEqRZeroMulXPow.lean#L418), [`big_le_b`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/ExportBoundOfAdmissible.lean#L501), [`point_bound`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/ExportBoundOfAdmissible.lean#L893), and [`export_bound_of_admissible`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/ExportBoundOfAdmissible.lean#L1023) give the exponent absorption. [`large_eventually` and `stmtU_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/ExportBoundOfAdmissible.lean#L1084) give uniformity.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
