# Matching the orbit rows to the local Fock model

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix a word $u$, a served place $w$, and one component $v$ of its local system. Let $s$ be a position in this component and $\tau$ its assigned global embedding. Write $k$ for the initial rank and $h=t+1$ for the size of each added block. At layer $0\le i<m$, write $N_i=k+ih$ and $j=i+1$. Assume the local and global ranks, weights and places are tied and the local fill condition holds. Let $U_r$ ($0\le r<k$) and $e_b$ ($0\le b<m$) be the weight coordinates at $u,\tau$. The fill condition is
$$
w_l=e_{l-1}-\kappa_l,\qquad \kappa_l=\tfrac12(k+(2l-1)h),\qquad 1\le l\le m,
$$
and the initial local coordinates satisfy $\lambda_r=U_r-\tfrac12(k-1)+r$. The tied place condition identifies the $e_{j-1}$ in this equation with the global shift $w_{\rm Sz}(j,\tau)$. [Global weights and source coordinates](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalRingCardinality/DataDIVDefs.lean#L59) · [`fock_rows_of_fills`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/FockRowsOfFills.lean#L8)

Define $A_r=U_r$ for $r<k$, and $A_r=-e_b+(t-2d)/2$ for $r=k+bh+d$ with $0\le d<h$ and $0\le b<m$. Then, in zero-based row numbering, the local row lengths agree with the global diagram:
$$
\nu^{\rm loc}_{j,s}(r)=
\begin{cases}
A_r+e_i-\bigl(N_i+N_{i+1}-1-2r\bigr)/2,&r<N_i,\\
0,&r\ge N_i.
\end{cases}
$$
For $r<k$ the local formula is $\lambda_r+w_j$. The identity $(k-1)/2+\kappa_j=(N_i+N_{i+1}-1)/2$ gives the assertion. For $k\le r<N_i$, Euclidean division gives $r=k+bh+d$ with $b<i$. The local formula is $-w_{b+1}+w_j$. Its constant shift is $\kappa_{b+1}-\kappa_j=(b-i)h$, which is also
$$
\tfrac12(t-2d)-\tfrac12(N_i+N_{i+1}-1-2r).
$$
For $N_i\le r<N_{i+1}$ the same local formula gives $-w_j+w_j=0$. All later rows are zero by definition. This accounts for every row, including the terminal cases $i=0$ and $r\ge N_{i+1}$. [`NN` and `nu`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/FormalGroupSystem.lean#L23) · [The three row ranges](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/FockRowsOfFills.lean#L18)

At a supplied orbit of length $d$, the place matching sends slot $s\in\mathbb Z/d\mathbb Z$ to the global embedding associated to $(1,\theta)$ and $s$. Each local column of height $a$ is therefore a column of the identical global diagram. Matching only its total size would leave the actual determinant factors unspecified. This row calculation is used when the [second-embedding coefficient bound](a-second-embedding-orbit-bounds-its-local-cofactors.md) is applied to the selected formal system. [Matching ranks, slots and diagrams](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/LocalModelBoundPlaceOverSecondEmbedding.lean#L73)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
