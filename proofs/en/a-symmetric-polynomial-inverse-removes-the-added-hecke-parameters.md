# A symmetric-polynomial inverse removes the added Hecke parameters

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

At a fixed served component of length $2\nu$ let $p\ne0$ in the coefficient field $K$, $q=p^\nu$, $k$ be the initial rank, $t+1$ the rank added at each layer, and $1\le r\le k$. Put $N_j=k+j(t+1)$ and let $H_j=K_{j-1}\cdots K_0$ be the linear lift through $j$ layers. Assume the rational spans of the integral spaces are preserved by the layer maps and the Hecke operators $T^-_{j,i}$. Write $E_{j,i}=q^{-i(N_j-i)} T^-_{j,i}$. The required one-layer Hecke equation is
$$
E_{j,i}K_{j-1}=u_j^i K_{j-1}\sum_{l=0}^i e_l(m_jq^t,m_jq^{t-2},\ldots,m_jq^{-t}) E_{j-1,i-l},
$$
where $u_j$ is a nonzero unit, $m_j$ is a scalar and $e_l$ is the elementary symmetric polynomial. This is `RestHecke`, a separate input for the present calculation. [The one-layer equation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/HeckeValueEstimateOfRecordValue.lean#L277) · [`Ci`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/HeckeValueEstimateOfRecordValue.lean#L195)

Let $U_j=\prod_{a=1}^j u_a$, $U_0=1$, $\widehat E_{j,i}=U_j^{-i}E_{j,i}$, and $\widehat m_j=m_j/U_{j-1}$. Dividing the equation by $U_j^i$ puts the scalar $U_{j-1}^{-l}$ in the $e_l$ term, which changes $m_j$ to $\widehat m_j$ by homogeneity. Let $X_j$ be the list of all $\widehat m_a q^{t-2b}$ for $1\le a\le j$, $0\le b\le t$. In the operator generating series in $z$ the new factor at layer $j$ is $\prod_{b=0}^t(1+\widehat m_j q^{t-2b}z)$. Successive composition with $K_{j-1}$ multiplies these scalar factors. Consequently
$$
\sum_{i\ge0}\widehat E_{j,i}H_jz^i
=\left(\prod_{x\in X_j}(1+xz)\right)H_j\sum_{i\ge0} E_{0,i}z^i.
$$
All coefficients in this identity use only finite sums. [Insertion of the cumulative units](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/HeckeValueEstimateOfRecordValue.lean#L231) · [Iterating the relation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/GaussElementarySymmetric.lean#L202)

Each inverse $(1+xz)^{-1}=\sum_{l\ge0}(-xz)^l$ exists formally. Thus the coefficient of degree $l$ in the inverse of the full scalar factor is $(-1)^lh_l(X_j)$, where $h_l$ sums all products of $l$ entries with repetitions in nondecreasing index order. Multiplying by this inverse and taking degree $r$ yields
$$
\left(\sum_{l=0}^r(-1)^l h_l(X_j)\widehat E_{j,r-l}\right)H_j=H_j E_{0,r}.
$$
This is the cancellation that the full alternating operator uses. [Elementary and complete symmetric convolution](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/GaussElementarySymmetric.lean#L170) · [`inversion_formula`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/GaussElementarySymmetric.lean#L223)

For the system's weights $\lambda_s(a)$, $w_j(s)$, define
$$
D_j(i)=\sum_{s\text{ even}}\sum_{a=1}^i\lambda_s(a)+i\sum_{s\text{ odd}}w_j(s),\qquad
A_r=\sum_{s\text{ even}}\sum_{a=1}^r\lambda_s(a)-
     \sum_{s\text{ odd}}\sum_{a=k+1-r}^k\lambda_s(a).
$$
The initial operator is $y_v=p^{A_r}T^-_{0,r}$. The alternating operator of degree $r$ is the sum above with a common scalar $p^{D_j(r)}q^{r(N_j-r)}$. To check this, use $T_{j,i}=p^{D_j(i)}T^-_{j,i}$, its unit correction $U_j^{-i}$, and the coefficient
$$
c_l=p^{D_j(r)-D_j(r-l)}q^{l(N_j-2r+l)}h_l(X_j).
$$
The constant $p^{D_j(r)}$ and the identity $r(N_j-r)-(r-l)(N_j-r+l)=l(N_j-2r+l)$ give the stated scalar. At the initial layer $E_{0,r}=q^{-r(k-r)}p^{-A_r}y_v$. Hence $Z_jH_j=p^{P_j}H_jy_v$ with
$$
P_j=D_j(r)-A_r+\nu rj(t+1).
$$
This is exactly the cost `PrZ`, since $D_j(r)-A_r$ equals $r\sum_{s\text{ odd}}w_j(s)$ plus the odd-slot sum of the final $r$ weights. It is the commutation input to [the layer induction](choosing-at-each-layer-which-operators-to-use.md). [`theorem_c_i`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/GaussElementarySymmetric.lean#L236) · [The initial exponent](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/HeckeValueEstimateOfRecordValue.lean#L65) · [The normalized exponent and cost](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/FormalGroupSystem.lean#L72)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
