# Small-prime errors at two and three share a scale

[Chinese proof](../zh/%E4%BA%8C%E5%92%8C%E4%B8%89%E5%A4%84%E7%9A%84%E5%B1%80%E9%83%A8%E8%AF%AF%E5%B7%AE%E6%80%8E%E6%A0%B7%E7%BB%9F%E4%B8%80%E5%88%B0%E5%90%8C%E4%B8%80%E4%B8%AA%E5%B0%BA%E5%BA%A6.md)

## Statement

In a `FamP eps` family put $x>1$, $L=x^\varepsilon$, $b=e^L$. Fix a row with $1\le m\le f\le t$, $V\le2t$. For prime $\ell$ let $N=\mathrm{condN}$, and let $\mathrm{QS}$ be the tower conductor. Assume $x\ge3$, $C_0\ge1$, $n,t\le x^{C_0}$, $v_\ell(N)=v_\ell(\mathrm{QS})$, and $1\le\mathrm{QS}\le n^2$. Let $H=b+\mathrm{Sc}+\eta_{\rm size}+t+2$ with $\mathrm{Sc},\eta_{\rm size},t\le b$, $s=\max(1,v_\ell(N))$, and $\Lambda=s+\log_\ell(2H)+1$. For $A,B\ge0$ take $C_m=18AC_0+2B(3C_0+9)+5C_0+1$. Then
$$
A fmHs+B f^2t^2V\Lambda\le C_m fm b\log x+C_m x^{C_m}L^2 .
$$
This is `Num.cost_le'`, with $A=6000,B=30000$ from the [split-prime estimates](explicit-split-estimate-constants-at-two-and-three.md).

## Proof and uniformity

Since $\ell^{v_\ell(\mathrm{QS})}\le\mathrm{QS}\le x^{2C_0}$ and $\log\ell>2/3$, $v_\ell(\mathrm{QS})\le3C_0\log x$. The same bound covers $1$ since $x\ge3$. Also $H\le6b$, giving $A fmHs\le18AC_0 fm b\log x$. Next $\log(2H)\le\log(12b)<L+3$ and $\log\ell>1/2$, giving $\log_\ell(2H)\le2L+6$. With $\log x\le x$ and $L\ge1$, obtain $\Lambda\le(3C_0+9)xL$. Since $f\le t$ and $V\le2t$,
$$
B f^2t^2V\Lambda\le2B(3C_0+9)x^{5C_0+1}L.
$$
The definition of $C_m$ is at least both coefficients and the polynomial exponent. With $x,L\ge1$, adding the two bounds proves the claim.

The family parameter lemma chooses a common $C_0$ and threshold on every row. At two the required conductor valuation is that of $\mathrm{QS}$, and at three it is also that of $\mathrm{QS}$ since $N=\mathrm{QS}\,q\,d$ with $q,d\ne3$ in this branch. Both local errors can therefore be replaced by the displayed function. If the branches have different constants, take their maximum and the larger threshold, using monotonicity of the cost in its nonnegative constant. Substituting the given $A,B$ with a common $C_0$ gives $C_m=288005C_0+540001$. Preserve the cohomology, class-number valuation and residual terms to get `BoundAtTwoThreeFamilyFonAlt` for the [rowwise estimate](rowwise-local-estimates-give-linkn-for-the-original-family.md).

## Lean correspondence

- [`hB_bounds` and `level_le'`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ResidueCharacters/NumCost.lean#L13) give the sizes. [`cost_le'`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ResidueCharacters/NumCost.lean#L55) combines the costs.
- [`mid_of_rowOn_alt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/FamilyBoundAtTwoThreeOfLocalBounds.lean#L11) applies the bound to a family. [`boundAtTwoThree_of_local_bounds_at_two_three`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/At23OfAll.lean#L19) combines the two primes.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
