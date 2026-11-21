# A separable idempotent extracts a crystalline embedding frame

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E7%94%A8%E5%8F%AF%E5%88%86%E5%B9%82%E7%AD%89%E5%85%83%E6%8A%BD%E5%87%BA%E4%B8%80%E4%B8%AA%E5%B5%8C%E5%85%A5%E7%9A%84%E6%99%B6%E4%BD%93%E6%AF%94%E8%BE%83%E6%A1%86%E6%9E%B6.md)

## Statement

Let $C=\mathbb C_\ell$ and $B_d$ its maximum-norm unit ball in dimension $d$. Take a local field $K\subseteq K_m$ in a cyclotomic layer and an embedding $\tau:K\to L$ into a finite coefficient field. In a $\mathbb Z_\ell$-basis of an $O_L$-lattice, use coordinates $\mathbb Z_\ell^d\subset\mathbb Q_\ell^d$. Scalar action by $a\in L$ has matrix $A(a)$ and the $L$-linear $G_m$ action has matrix $M(\sigma)$, extended semilinearly to $C$. Suppose a period comparison gives invertible $D\in M_d(C)$ with $D,\ell D^{-1}$ integral and
$$
M(\sigma)\sigma(D)=DU(\sigma).
\tag{1}
$$
Assume `Frame` for $U$: it is continuous, integral over $K_m$, trivial over the infinite tower, and $\|U(g)-I\|<\ell^{-1/(\ell-1)}$ for the designated generator. Assume $D^{-1}A(a)D$ over $K_m$ for every $a\in O_L$. There is a Hodge–Tate basis in the original coordinates, with the comparison `EmbeddingJump.proj_eq_zero` saying that vectors surviving projection to the $\tau$ component have weights among its filtration jumps $J$.

There are $P:C^d\to C^r$ and $U'$ satisfying the same frame hypotheses and
$$
P M(\sigma)=U'(\sigma)\sigma(P),\qquad
B_r\subseteq P(B_d),\qquad \ell P(B_d)\subseteq B_r,
\tag{2}
$$
The target has a Hodge–Tate basis of weights in $J$. If $z\in\mathbb Q_\ell^d$ and $Pz\in P(B_d)$, then $z\in\mathbb Z_\ell^d$. See the [quotient invariant comparison](absence-of-weight-zero-bounds-crystalline-quotient-invariants.md).

## Projection to the chosen embedding

Choose the separability element $p=\sum_j a_j\otimes b_j\in K\otimes_{\mathbb Q_\ell}K$ with $\sum_j a_jb_j=1$ and $(v\otimes1)p=(1\otimes v)p$. For construction, take $K=\mathbb Q_\ell(\alpha)$ and write the minimal polynomial in the first variable as $(X-\alpha)g(X)$ over the second copy. Then $g(X)/g(\alpha)$ modulo that polynomial has the two properties because it equals one at $X=\alpha$ and is killed by $X-\alpha$.

Set $E=\sum_j b_j A(\tau(a_j))$. The balancing identity gives $A(\tau(v))E=vE$. Thus $E^2=E$ by the sum of products and it acts as identity on that eigenspace. The $M(\sigma)$ commute with scalars, and $\sigma$ fixes the $b_j$, so $E$ commutes with the semilinear action. Set $e=D^{-1}ED$. Its entries lie in $K_m$ by the hypothesis on conjugated scalars, extending from $O_L$ by clearing denominators. Equation (1) then makes $e$ commute with $U(\sigma)$.

## Integral factors and the frame

Let $r=\operatorname{rank}e$. Choose a largest nonzero $r$-minor $B=e_{I,J_0}$ by absolute value, taking the empty matrices at rank zero. Let $S$ insert the $J_0$ coordinates and $R=B^{-1}e_{I,*}$. By Cramer's rule and maximality, $R$ is integral, and $S$ is integral by definition. We have $RS=I$, $Re=R$, and $eSR=e$. The last identity uses the columns at $J_0$ as column-space basis, whose coordinates for any column are recovered from rows $I$.

Take $P=RD^{-1}$ and $U'(\sigma)=R U(\sigma)S$. Commutation with $e$ gives $R U(\sigma)SR=R U(\sigma)$. It follows that $U'$ is a representation, with (2) from (1). It is integral and continuous, trivial on the kernel, and $U'(g)-I=R(U(g)-I)S$ preserves the small-norm bound. The right inverse $DS$ is integral and $\ell P$ is integral, giving both inclusions. Since $PE=P$, projected Hodge–Tate vectors that survive come from surviving $E$ components. They have the required weights and still obey the fixed vector formulas by the intertwiner. Choose a basis from them.

## Recovering rational integrality

Choose $\iota:L\to C$ extending $\tau^{-1}$ on $\tau(K)$. On an $O_L$-basis of the lattice this sends coefficient coordinates to $C$ and gives a matrix $Q_0:C^d\to C^s$. It is integral because the original $\mathbb Z_\ell$ basis lies in the lattice. For rational coordinates $z$, $Q_0z$ is integral exactly when $z$ is in the original lattice, since $\iota$ preserves norms. The scalar action under $Q_0$ is through $\iota$, giving $Q_0E=Q_0$ by the separability sum. Let $Q=DeS$. Then $QP=E$, hence $Q_0=Q_0QP$. If $Pz=Px$ for $x\in B_d$, then $Q_0z=Q_0x$ is integral, so $z\in\mathbb Z_\ell^d$.

## Lean correspondence

- [`exists_sep_elem` and `sep_idem`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsTauComponentFrameOfLattice.lean#L26), [`frame_of_dec`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsTauComponentFrameOfLattice.lean#L150), and [`exists_tau_frame`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsTauComponentFrameOfLattice.lean#L253) give the embedding projection.
- [Integral factors](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsIntegralFactorOfIdempotentSubfield.lean#L97), [`frame_of_idem`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsSubBasis.lean#L85) and [`EigenCoord.exists_matrix`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/NormCoeAutLeOneIff.lean#L91) give (2) and recover integrality.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
