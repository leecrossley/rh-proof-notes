# Odd-orbit dual weights pay for the folded theta coefficients

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix an inert prime $p\ge5$ whose projected Frobenius has odd order $d>1$, the case `IsCs`. The place set is the union of two parts $A$ and $B$, named `kindA` and `kindBC`. The shift $P$ preserves the parts and its orbits have length $d$. Fix a word and a layer $i<m$. At each place $z$ let $D_z$ be the size of its Young diagram, and $w_z$ the positive degree weight. The shape hypotheses imply, for $z\in B$,
$$
(k-1)w_z\le D_z\le(k-1)w_z+4w_z,\qquad k>1.
$$
Also $D_z\le a^2$ everywhere, $p\le X''\le a$, and the layer dimensions $N_i,N_{i+1}\le N_m$. Let $f$ be the number of places, $\gamma=p/(p^2-1)$, and $F_r=F((k-1)w)$ the [finite flow functional](cyclic-degree-budgets-and-flow-duality.md) on the orbit of $r$, using positive odd shifts less than $d$. Suppose the actual series has the [folded theta product form](folding-the-two-parities-preserves-the-weighted-jet-bound.md). We claim that its determinant jets have valuation at least
$$
\frac1d\sum_{z\in B}F_z-\frac{k-1}{p^3}\sum_{z\in B}w_z
-\frac8p\sum_{z\in B}w_z-3fN_m^2\log_p a. \tag{1}
$$

On one orbit in $B$, take an optimal dual vector $s_z$ for the demand $(k-1)w_z$, with $0\le s_z\le1$. The duality and complementary slackness arguments in the flow proof apply for odd $d$ as well, since their finite constraint set uses only odd $e<d$. In particular
$$
\sum_{z:s_z\ge2/p}w_z\le p^{-1}\sum_z w_z.
\tag{2}
$$
Indeed the corresponding vertices have no outgoing flow and must have full incoming load, so their total demand is bounded by the sum of all flows, at most $p^{-1}\sum_z (k-1)w_z$. The division is valid because $k>1$.

Set $\sigma_z=\max(s_z,p^{-3})$. For odd shifts $e<d$ the dual inequality persists by monotonicity. For odd $e\ge d$, one has $e\ge3$, so $p^e\sigma_z\ge1$ and the inequality follows with no constraint at the endpoint. Thus $\sigma$ pays for all the folded exceptional monomials. Raising the floor costs at most $(k-1)p^{-3}\sum_z w_z$ in the value at the original demand. For the change to $D_z$, the error coefficient $\gamma-\sigma_z$ is at least $-1/p$ at vertices with $s_z<2/p$, because $\gamma\ge1/p$ and $p^{-3}<2/p$. Elsewhere it is at least $-1$, since $\sigma_z\le1$. The perturbation is at most $4w_z$, so (2) bounds the additional loss by $4p^{-1}\sum_z w_z+4p^{-1}\sum_z w_z$. Therefore
$$
\sum_zD_z(\gamma-\sigma_z)\ge F_r-\left((k-1)p^{-3}+8p^{-1}\right)\sum_z w_z
$$
on each orbit of $B$.

On $A$ choose the constant $\sigma=1/(p+1)$. It meets the inequality for every odd positive shift since $(p^e+1)/(p+1)\ge1$. Its contribution is nonnegative since $\gamma-\sigma=\rho=1/(p^2-1)$. Combine these choices over the orbits. The resulting sum on $B$ uses each $F_r$ once. Since $F_z$ is invariant under change of origin in its orbit and the orbit size is $d$, this sum equals $d^{-1}\sum_{z\in B}F_z$.

Every monomial of the product of minors uses $D_z$ entries at place $z$, counting multiplicities. In a monomial of its theta variables all individual exponents are therefore at most $a^2$. Apply the folded coefficient theorem with $H=a^2$ and $fN_iN_{i+1}$ variables. Its first term is exactly $\sum_zD_z(\gamma-\sigma_z)$. The error $fN_iN_{i+1}(\log_p(a^2)+1)$ is at most $3fN_m^2\log_p a$, since $\log_p a\ge1$. Each coefficient of the differentiated product of minors is an integer linear combination of those jets, hence inherits the bound by the ultrametric inequality. This gives (1).

For the numerical comparison, $F_{\mathrm{inert}}=d^{-1}\sum_{z\in A\cup B}F_z$. In the odd case the prescribed penalty `EatI` includes $\max(0,d^{-1}\sum_A F_z)$, so $F_{\mathrm{inert}}$ less this term is at most $d^{-1}\sum_B F_z$. The penalty `EatX` supplies the term $(k-1)p^{-3}\sum_Bw_z$ and a logarithmic term $c_6 fN_m^2\log_p a$. The other nonnegative losses in `EatI` include $c_6p^{-1}\sum_B w_z$. The hypotheses give $c_6\ge12$, so these losses cover the subtracted $8$ and $3$ terms of (1). There are no designated top places in $B$ for this prime class. Hence $F_{\mathrm{inert}}-\mathrm{EatI}$ is bounded above by (1), which proves the required lower valuation bound with the prescribed global error.

**Lean correspondence.** The floor and perturbation estimate is [`exists_nonneg_dual_fnum_sub_le_of_demand_near_mul`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/OrbitLabellings/ExistsNonnegDualFnumSubLeOfDemandNearMul.lean#L9). The weights on the two parts, orbit reindexing and determinant conclusion are [`orbit`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/OrbitLabellings/KvalGeThetaOfShape.lean#L48), [`radii`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/OrbitLabellings/KvalGeThetaOfShape.lean#L97), and [`kvalGe_theta_of_shape`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/OrbitLabellings/KvalGeThetaOfShape.lean#L155). The error comparison is [`fInert_sub_eatI_le_orbit_average_sub_errors`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/OrbitLabellings/FInertSubEatILeOrbitAverageSubErrors.lean#L7).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
