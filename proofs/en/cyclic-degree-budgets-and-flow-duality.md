# Cyclic degree budgets and flow duality

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

The same local term appears in two forms in the proof. One describes how much degree can be moved between entries of a Frobenius orbit. The other chooses weights for a coefficient estimate. The equality of the two forms lets the local valuation estimate use weights without giving up the sharp degree bound.

## The degree problem

Let $p\ge2$ be an integer, $d\ge1$, $S=\mathbb Z/d\mathbb Z$, and $I=\{i:1\le i<d,\ i\text{ odd}\}$. Take $D_s\ge0$ for all $s\in S$. For $x_{s,i}\ge0$ define its load and value by
$$
B_s(x)=\sum_{i\in I}p^i x_{s,i}+\sum_{i\in I}x_{s-i,i},
\qquad
V(x)=\sum_{s\in S}\sum_{i\in I}x_{s,i}.
$$
The variable $x_{s,i}$ consumes $p^i$ units of degree budget at $s$ and one at $s+i$ per unit of value. Put
$$
V_*=\max_{x\ge0,\ B_s(x)\le D_s}V(x),
\qquad
\gamma=\frac p{p^2-1},
\qquad
F(D)=\gamma\sum_sD_s-V_*.
$$
Then
$$
V_*=\min_\sigma\sum_sD_s\sigma_s,\qquad
F(D)=\max_\sigma\sum_sD_s(\gamma-\sigma_s),
$$
with both extrema over $0\le\sigma_s\le1$ and $p^i\sigma_s+\sigma_{s+i}\ge1$ for every $s\in S$ and $i\in I$. If $d$ is even, every such $\sigma$ satisfies the same inequalities for **all positive odd** $i$. In Lean, `strong` proves the minimum formula (already for $p\ge1$), and `strongDuality` packages the maximum formula with $p\ge3$ and even $d\ge2$. The support condition in `lpFeasible` sets all other coordinates to zero, so `lpF_eq_Fnum` identifies its value with this $F(D)$. [Flow and dual definitions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/IncomingBounds/IncomingBound.lean#L12) · [Minimum formula](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/IncomingBounds/FlowDegreeBounds/MaxFlowValueAttained.lean#L377) · [Maximum formula](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/IncomingBounds/FlowDegreeBounds/MaxFlowValueAttained.lean#L430) · [Equality of the two implementations](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/Divisibility/JetPolynomialLogs/DworkPowerSeriesWeights.lean#L49)

## Proof of duality

The feasible flow set contains zero and is closed. Every $x_{s,i}$ is between zero and $D_s/p^i$, so the set is compact and $V_*$ is attained. Evaluating the dual inequality on each edge and adding gives
$$
V(x)\le\sum_{s,i}x_{s,i}(p^i\sigma_s+\sigma_{s+i})
=\sum_s\sigma_sB_s(x)
\le\sum_sD_s\sigma_s.
$$
The equality reindexes the incoming term with $s$ replaced by $s+i$. This proves weak duality. [Reindexing and weak duality](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/IncomingBounds/FlowDegreeBounds/MaxFlowValueAttained.lean#L22) · [Attainment of the primal maximum](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/IncomingBounds/FlowDegreeBounds/MaxFlowValueAttained.lean#L108)

For the reverse inequality, consider the cone of all $(A,t)\in\mathbb R^S\times\mathbb R$ for which some $x\ge0$ has $B_s(x)\le A_s$ and $t\le V(x)$. It is convex by linearity. To see it is closed, take a convergent sequence in the cone. Its capacities $A_s$ are uniformly bounded, and every corresponding witness has each coordinate at most $A_s/p^i$. Pass to a convergent subsequence of the witnesses in a fixed finite box. Continuity gives a witness at the limit.

For $\varepsilon>0$, the point $P=(D,V_*+\varepsilon)$ is outside the cone. There is a linear functional $f(A,t)=\sum_s a_s A_s+ct$ that is nonnegative on the cone and negative at $P$. For instance, let $Q$ be the nearest point of the closed cone to $P$. The derivative of squared distance along any segment from $Q$ into the cone gives $(Q-P)\cdot(Y-Q)\ge0$ there. Taking $Y=0$ and $Y=2Q$ gives $(Q-P)\cdot Q=0$, so $f(Y)=(Q-P)\cdot Y$ works. Lean uses separation of a point from a closed convex set followed by the same cone scaling.

The cone contains each coordinate vector $(e_s,0)$ and the unit-flow vector $(B(x),1)$ for $x$ supported with value one on $(s,i)$. Consequently $a_s\ge0$ and $p^i a_s+a_{s+i}+c\ge0$. Since $D_s\ge0$ and $V_*+\varepsilon>0$, negativity at $P$ forces $c<0$. Dividing by $-c$ gives nonnegative weights $\tau_s=a_s/(-c)$ satisfying the dual inequalities and $\sum_sD_s\tau_s<V_*+\varepsilon$.

Clipping every $\tau_s$ at one leaves the inequalities valid. If an endpoint is clipped, that endpoint alone now contributes at least one, since its coefficient is $1$ or $p^i\ge1$. Clipping only decreases the objective. The clipped feasible set is a closed subset of the cube $[0,1]^S$ and contains the all-ones vector. Its minimum is below $V_*+\varepsilon$ for every $\varepsilon>0$, so weak duality forces equality. Subtracting from $\gamma\sum_sD_s$ gives the formula for $F$. For even $d$, reducing any positive odd $i$ modulo $d$ preserves parity and the endpoint, and $p^i$ is at least the power for that remainder. This gives the advertised extension of the inequalities. [Closedness of the cone](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/IncomingBounds/FlowDegreeBounds/MaxFlowValueAttained.lean#L198) · [Separation and normalization](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/IncomingBounds/FlowDegreeBounds/MaxFlowValueAttained.lean#L230) · [Clipping and compactness](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/IncomingBounds/FlowDegreeBounds/MaxFlowValueAttained.lean#L338) · [Extension to all odd shifts](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/IncomingBounds/FlowDegreeBounds/MaxFlowValueAttained.lean#L399)

## An explicit value for balanced degrees

For any $d\ge1$, adding the capacity inequalities over $s$ gives $(p+1)V(x)\le\sum_sD_s$ because every $i\in I$ is at least one. Together with the zero flow this yields
$$
\frac{\sum_sD_s}{p^2-1}\le F(D)\le\frac{p\sum_sD_s}{p^2-1}.
$$
For $d\ge2$, suppose $D_a\le p D_b$ for every $a,b\in S$. Set all flows to zero except at shift $1$, and put
$$
x_{s,1}=\frac{\displaystyle\sum_{k=0}^{d-1}(-1)^k p^{-k-1}D_{s-k}}{1-(-1)^d p^{-d}} .
$$
The denominator is positive. The magnitudes in the alternating numerator decrease, by $D_{s-k-1}\le pD_{s-k}$. Pairing consecutive terms proves nonnegativity, including an unpaired positive last term when $d$ is odd. The numerator telescopes under $p x_{s,1}+x_{s-1,1}$, using $D_{s-d}=D_s$, and the result is $D_s$. Thus the upper bound on $V_*$ is attained by these shift-one flows. The lower estimate for $F$ is an equality. This is the origin of the coefficient $1/(p^2-1)$ for balanced degrees in the numerical inert-prime term. For a nontrivial orbit the project applies this calculation at each starting point and divides their sum by the orbit length. Each cyclic translation permutes the places, so $\sum_z\sum_s D_{z,s}=d(k-1)\sum_z w_j(z)$ for $D_{z,s}=(k-1)w_j(\operatorname{pos}(p,z,s))$. The special case of a fixed inert place uses the coefficient directly by definition. [General bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Divisibility/DivisibilityProofs/NumbersP.lean#L60) · [Explicit feasible flow](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Divisibility/DivisibilityProofs/NumbersP.lean#L122) · [Summed inert-prime formula](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Divisibility/DivisibilityProofs/NumbersP.lean#L249)

## How much mass can require a large dual weight?

Now let $p\ge3$, $d\ge2$ even and $\sigma$ optimal. If $x$ is an optimal flow, equality in the two weak-duality inequalities gives, separately,
$$
\sigma_s(D_s-B_s(x))=0,\qquad
x_{s,i}(p^i\sigma_s+\sigma_{s+i}-1)=0.
$$
Each summand in the duality gap is nonnegative, so all vanish. If $\sigma_s\ge2/p$, the first equality fills the budget and the second kills all outgoing flow, because $p^i\sigma_s\ge2$. Hence $D_s=\sum_i x_{s-i,i}\le\sum_i p^{-i}D_{s-i}$. Since $\sum_{i\ge1,\ i\ \mathrm{odd}}p^{-i}=\gamma$, at least one degree is at least $D_s/\gamma$. More globally, summing the incoming flow only over the heavy vertices and then allowing all incoming flow gives
$$
\sum_{\sigma_s\ge2/p}D_s
\le \sum_{s,i}x_{s-i,i}
= \sum_{s,i}x_{s,i}
\le\frac1p\sum_sD_s .
$$
The last inequality uses only the outgoing part of the capacity constraints. For nonnegative perturbations $E$, maximizing the dual formula at $D+E$ using the optimizer at $D$ gives $F(D+E)\ge F(D)-\sum_s E_s(\sigma_s-\gamma)_+$. Flow monotonicity gives $F(D+E)\le F(D)+\gamma\sum_sE_s$. The small mass of vertices with large $\sigma_s$ is what makes the perturbation cost in the valuation calculation of order $1/p$. [Complementary slackness identity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/IncomingBounds/FlowDegreeBounds/LemmaFd.lean#L31) · [Pointwise incoming bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/IncomingBounds/FlowDegreeBounds/LemmaFd.lean#L175) · [Total heavy mass](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/IncomingBounds/FlowDegreeBounds/LemmaFd.lean#L203) · [Perturbing degrees](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/IncomingBounds/FlowDegreeBounds/LemmaF.lean#L236)

The numerical optimizer is used with a cyclic label on each variable of the theta-series jet. The next step relates its inequalities to the monomials that can have a small valuation. [Prime powers in the coefficient bound](prime-powers-in-the-jet-coefficient-bound.md).

Status. Source-based reconstruction draft. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
