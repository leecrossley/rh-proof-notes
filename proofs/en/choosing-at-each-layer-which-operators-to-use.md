# Choosing at each layer which operators to use

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix the local formal-group system at a prime $p$, with $m$ layers and lattice $L_j$ at layer $j$. Let $K_j$ be the linear map from layer $j$ to $j+1$, and $H_j=K_{j-1}\cdots K_0$, with $H_0=1$. Let $y_v$ be the commuting operators on the initial space, each preserving $L_0$. Assume the local operator package supplies operators $Z_{v,j}$ on layer $j+1$ and exponents $P_0(v,j+1)\in\mathbb Z$ such that
$$
Z_{v,j} H_{j+1}=p^{P_0(v,j+1)}H_{j+1}y_v
$$
on the span of $L_0$. Assume also the following one-layer bound on $Z_{B,j}K_j L_j$ for any set $B$ of distinct components, with $Z_{B,j}$ their ordered product. Its valuation floor is the sum of $G(v,j+1)$ on $B$, for any $G$ bounded above by the system's operator gain, plus the supplied ordinary cofactor floor $G_0(v,j+1)$ off $B$, minus the layer normalization $d_j$. In the source this bound is `ZL_bound`, with inputs `FormB`, `EntCondition` and the constraints on the coefficients of $Z_{v,j}$ in `Conclusion4`. [The operator package](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/FormalGroupSystem.lean#L671) · [`ZL_bound`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/AofUpdate.lean#L172) · [`main_ind`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/YEPEComm.lean#L131)

For a subset $J$ of components, write $Y_J=\prod_{v\in J}y_v$. In layer $j$, choose any $B_j\subseteq J$. Since the $y_v$ commute,
$$
Y_J^{j+1}=Y_{B_j}Y_J^jY_{J\setminus B_j}.
$$
The last factor takes an integral input to another integral input. Apply the induction hypothesis to $H_jY_J^j$ at that input. Applying $K_j$ and $Z_{B_j,j}$ then adds the one-layer bound. Moving $Y_{B_j}$ to the output of $H_{j+1}$ costs $\sum_{v\in B_j}P_0(v,j+1)$ in valuation, by the displayed commutation. For $j=0$ the starting bound is zero. This proves that the valuation of $H_mY_J^m L_0$ is at least
$$
\sum_{j=0}^{m-1}
\left(\sum_{v\in B_j}\bigl(G(v,j+1)-P_0(v,j+1)\bigr)+
\sum_{v\notin B_j}G_0(v,j+1)-d_j\right).
$$
The induction uses only a lower bound on valuation of the scaled element each time, so rounding each inductive exponent up can only improve the result. [Transporting the operator product](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/YEPEComm.lean#L110) · [The induction at a layer](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/YEPEComm.lean#L145)

Now fix $Q$ of eligible components and costs $P_1\ge P_0$ on $Q$. For a generating term of `Iprod` with used set $J\subseteq Q$, use
$$
B_j=\{v\in J: G(v,j+1)-P_1(v,j+1)\ge G_0(v,j+1)\}.
$$
For $v\in J$ this attains at least $\max(G-P_1,G_0)$ at each layer. For $v\in Q\setminus J$, only $G_0$ is attained. The shortfall over all layers is $\sum_j\max(G-P_1-G_0,0)$ for that component. By definition the generating input has been scaled by the uniformizer to power $\sum_{v\in Q\setminus J}\lceil eS(v)\rceil$, where $1/e$ is its valuation, and $S(v)$ dominates this exact shortfall. This yields the full target in [the local product theorem](selected-local-operators-and-ordinary-cofactors-give-a-product-bound.md) for each generator. The scaled terminal lattice is a submodule and the chain is linear, so the bound extends to the span. In the source's extra degenerate case $e=0$, the formal exponent $e\,s$ vanishes for every $s$, there are no components, and ordinary lattice preservation of the chain gives the conclusion directly. [The missing-component inequality](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/LiftBoundOfIntegrality.lean#L24) · [`lift_bound_of_integrality`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/LiftBoundOfIntegrality.lean#L103) · [Degenerate exponent branch](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/PrvAndKernelCommutationUpToUnitsOfRests.lean#L45)

The [one-layer bound](the-zero-hecke-term-pays-for-its-own-valuation-loss.md) derives the estimate on $Z_{B,j}K_j$ from component coefficients. The [alternating-polynomial calculation](a-symmetric-polynomial-inverse-removes-the-added-hecke-parameters.md) derives the commutation with $H_{j+1}$ from the one-layer Hecke relation.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
