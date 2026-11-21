# Weight differences annihilate cyclotomic coinvariant torsion

[Chinese proof](../zh/%E5%88%86%E5%9C%86%E7%94%9F%E6%88%90%E5%85%83%E7%9A%84%E4%BD%99%E4%B8%8D%E5%8F%98%E9%87%8F%E4%B8%BA%E4%BB%80%E4%B9%88%E7%94%B1%E6%9D%83%E5%B7%AE%E4%B9%98%E7%A7%AF%E6%B6%88%E5%8E%BB.md)

## Statement

Let $\ell$ be prime, $C=\mathbb C_\ell$, $\chi$ cyclotomic, and $K/\mathbb Q_\ell$ finite with maximal unramified subfield $K_0$. Let $K_m=K_0(\mu_{\ell^m})$, $K_\infty=K_0(\mu_{\ell^\infty})$, and $G_m,H_\infty$ their absolute subgroups. Require $m\ge1$, or $m\ge2$ if $\ell=2$. Let $\widehat{\mathcal O}_\infty$ be the closure of the integers of $K_\infty$ in $C$, and take $g\in G_m$ with $v_\ell(\chi(g)-1)=m$. For $r\ge0$ assume a continuous $U:G_m\to\mathrm{GL}_r(\mathcal O_{K_m})$, trivial on $H_\infty$, with $\|U(g)-I\|<\ell^{-1/(\ell-1)}$ in maximum entry norm. Write $A_i(\sigma)y=\chi(\sigma)^iU(\sigma)\sigma(y)$. Assume a $C$-basis of $C^r$ with vectors $e_a$ fixed by $A_{u_a}$ for $u_a$ in a finite integer set $J$. These are `Frame` and `HTBasis`.

For $i\in\mathbb Z$, $w,w'\in\widehat{\mathcal O}_\infty^r$, and $k\ge0$, suppose $(A_i(g)-1)w'=\ell^k w$. Then $(A_i(g)-1)y=\ell^Nw$ for some integral $y$, where
$$
N=\max\left(1,\sum_{u\in J\setminus\{i\}}(m+v_\ell(u-i))\right).
\tag{1}
$$

## The higher-layer part

The [integral trace decomposition and Tate operator](trace-decomposition-and-the-cyclotomic-tate-operator.md) give $\widehat{\mathcal O}_\infty=\mathcal O_{K_m}\oplus X_m$, where $X_m$ is the closure of the additive span of $\zeta\mathcal O_{K_{j-1}}$ for $j>m$ and primitive $\ell^j$th roots. The two summands are stable under $g$ and integral scalars from $K_m$. For $\pi_\ell=\zeta_\ell-1$ there is an integral $\mathcal O_{K_m}$-linear $S:X_m\to X_m$ with $S(g-1)=(g-1)S=\pi_\ell I$.

We have $|\chi(g)^i-1|\le\ell^{-m}<|\pi_\ell|$ by a geometric sum and inversion for negative $i$. Thus $\chi(g)^iU(g)=I+\pi_\ell B$ with integral $B$ and $\|B\|<1$. Write $B=\alpha B'$ using a largest entry $\alpha$ and integral $B'$, or take both zero. Put $E=B'gS$. It preserves the unit ball and commutes with $\alpha$ since $g$ fixes $K_m$. Then $(A_i(g)-1)S=\pi_\ell(I+\alpha E)$. For $w_x\in X_m^r$, the convergent series $\sum_{n\ge0}(-\alpha)^n S E^n w_x$ solves the equation with right side $\pi_\ell w_x$ by telescoping. Also if $(A_i(g)-1)y=0$, apply $S$ to get $y=-\alpha S B'g y$. Iteration makes its norm at most $|\alpha|^n$ for every $n$, so $y=0$. This argument applies at every twist. Since $\ell^N/\pi_\ell$ is integral, it gives the requested high-layer solution.

## The fixed-layer polynomial

Scale a Hodge–Tate basis vector by an $\ell$-power to make it integral. On $H_\infty$ both matrix and cyclotomic twists are trivial. Tate's fixed-field theorem puts it in $\widehat{\mathcal O}_\infty^r$. Its $X_m$ component is fixed under $A_{u_a}(g)$, hence zero by injectivity there. So $U(g)e_a=\chi(g)^{-u_a}e_a$ since $g$ fixes the coefficients in $K_m$. Undo scaling. It follows that $P(X)=\prod_{u\in J}(X-\chi(g)^{-u})$ annihilates $U(g)$.

Project the input equation to the integral fixed layer, with components $w_0,w_0'$. Set $a=\chi(g)^{-i}$ and $P_i(X)=\prod_{u\in J\setminus\{i\}}(X-\chi(g)^{-u})$. Then $(U(g)-aI)w'_0=a\ell^k w_0$, and $P_i(U(g))(U(g)-aI)=0$ by $P$. Applying $P_i(U(g))$ and canceling $a\ell^k$ gives $P_i(U(g))w_0=0$. With $\beta=P_i(a)$, divide $P_i(X)-\beta$ by $X-a$ over the integer ring to get $Q(X)$. Substituting gives $(U(g)-aI)(-Q(U(g))w_0)=\beta w_0$. The [binomial valuation argument](cyclotomic-invariant-length-is-bounded-by-a-weight-valuation.md), also for $1+\ell^m c$ with unit $c$, gives valuation $m+v_\ell(u-i)$ of each factor of $\beta$. Thus $\beta\ne0$ and $\ell^N/\beta$ is integral. Multiply the solution vector by $a\ell^N/\beta$ and use $A_i(g)-1=\chi(g)^i(U(g)-aI)$ on the fixed layer. Add the two solutions to obtain (1).

## Lean correspondence

- [`tors_int`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TorsionCoinvariantsTwistedCyclotomicGenerator.lean#L14) gives the polynomial comparison and [`torsion_coinvariants`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TorsionCoinvariantsTwistedCyclotomicGenerator.lean#L175) combines both layers.
- [Integral trace decomposition](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TateDecompositionCompletedCyclotomicIntegersStatement.lean#L7), [`exists_tate_operator`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsTateOperatorLevelComplement.lean#L444), [`perturbation`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CyclotomicTowerGeneratorMatrixPerturbation.lean#L302) and [`eigen_of_norm_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/AevalProdEqZeroHodgeTateCyclotomicFrame.lean#L59) give the layer splitting, inverse and eigenvalues.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
