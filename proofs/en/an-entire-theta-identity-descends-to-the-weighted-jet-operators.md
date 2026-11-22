# An entire theta identity descends to the weighted jet operators

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $K$ be the project's coefficient field, $\sigma:K\hookrightarrow\mathbb C$ its chosen embedding and $I$ the finite set of complex blocks in an adjacent-rank step. Fix ranks $a,b$, dominant source and target weights $\lambda_\tau,\lambda'_\tau$ at each $\tau\in I$, and nonnegative determinant powers $n_\tau$. Let $V_\lambda,V_{\lambda'}$ be the corresponding polynomial weight spaces over $K$. For a derivative multi-index $m=(m_{\tau,\beta,\alpha})$ on $\prod_{\tau\in I}\mathbb C^{b\times a}$, put
$$
d_\tau(m)=\sum_{\beta,\alpha}m_{\tau,\beta,\alpha},
\qquad
D_\tau=\sum_{j=1}^a(\lambda_{\tau,j}-\operatorname{detShift}(\lambda_\tau)+n_\tau).
$$
Here $\operatorname{detShift}(\lambda_\tau)$ is the last weight in positive rank, and the sum is zero in rank zero. Let $c_\tau\in\mathbb C$ be the fixed derivative scaling in each block. Define $J(G)_m=(\prod_\tau c_\tau^{d_\tau(m)})\,\partial^mG(0)$. The derivative is the iterated coordinate derivative, which is the Taylor coefficient multiplied by the multi-index factorial for an entire $G$.

For each $k=1,2$, let $I_k$ be finite, $\xi_{k,t}\in K$, $F_{k,t}$ entire for $t\in I_k$, and $u_k\in\mathbb C$. Assume that, whenever $d_\tau(m)=D_\tau$ for every $\tau$, each normalized derivative $u_kJ(F_{k,t})_m$ lies in $\sigma(K)$. Let $J_{k,t}(m)\in K$ denote its unique preimage at such an index, with arbitrary entries at the other indices. If $r\in K$ and
$$
\sum_{t\in I_1}\sigma(\xi_{1,t})u_1F_{1,t}(z)
=\sigma(r)\sum_{t\in I_2}\sigma(\xi_{2,t})u_2F_{2,t}(z)
\quad\text{for every }z,
$$
then the induced maps $V_\lambda\to V_{\lambda'}$ satisfy
$$
\sum_{t\in I_1}\xi_{1,t}\operatorname{JetOp}(J_{1,t})
=r\sum_{t\in I_2}\xi_{2,t}\operatorname{JetOp}(J_{2,t}).
$$

### Which derivatives can appear

In $\operatorname{JetOp}(J)$, first multiply $F\in V_\lambda$ by the source determinant in block $\tau$ to the power $n_\tau$. Then substitute, for each source matrix entry, the corresponding entry of a product using a target-frame matrix and a matrix of formal derivative variables. In block $\tau$ a term in this substitution contains one derivative variable and one target-frame variable in that same block. An entry outside the admitted frame range is sent to zero. The substitution sends each coefficient of a derivative monomial with multi-index $m$ to itself times $J(m)$, and the resulting polynomial is projected to $V_{\lambda'}$ by the fixed linear retraction.

The polynomial $F$ is homogeneous in block $\tau$ of degree $\sum_j(\lambda_{\tau,j}-\operatorname{detShift}(\lambda_\tau))$. On a generator, this is obtained by summing its prescribed column degrees in that block. All products of block generators, and hence their linear span, have the same block degree. The determinant multiplier adds $a n_\tau$. To track the substitution, give the target-frame variables weight zero and the derivative variables in block $\tau$ weight one. Variables from every other block have weight zero for this calculation. The substitution preserves the resulting weighted degree, so every surviving monomial has $d_\tau(m)=D_\tau$. This works for each block separately. It proves that entries outside these degrees never affect the operator.

### Descent

Apply the linear functional $J(-)_m$ to the identity of entire functions. All sums are finite, so it can be applied to individual summands. For $m$ in the prescribed degrees this gives
$$
\sigma\!\left(\sum_{t\in I_1}\xi_{1,t}J_{1,t}(m)\right)
=\sigma\!\left(r\sum_{t\in I_2}\xi_{2,t}J_{2,t}(m)\right).
$$
Injectivity of $\sigma$ gives the identity of entries in $K$. Linearity of the substitution-and-evaluation operator in the derivative table commutes with the sums and the scalar $r$. The block-degree calculation then gives equality of maps. In the application to theta movement, the hypotheses about the preimages of the normalized derivatives are the two `JetsIn` assumptions. This argument uses them at the specified degrees.

### Lean correspondence

- [`subD_hom`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SubDSharpInDeg.lean#L62) tracks the weight of each substitution. The source block degree and determinant addition are [`VV_hom`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SubDSharpInDeg.lean#L75) and [`sharp_hom`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SubDSharpInDeg.lean#L86).
- [`jetOp_sum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/JetOpIdentityOfEntire.lean#L39) proves linearity in the table. [`jetOp_congr`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/JetOpIdentityOfEntire.lean#L58) uses equality on the required degrees.
- [`derivAt0`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/ThDistC.lean#L56) and [`jetC`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/ThDistC.lean#L60) define the derivative and scaling. [`jetOp_identity_of_entire`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/JetOpIdentityOfEntire.lean#L104) combines differentiation, descent and the degree restriction.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
