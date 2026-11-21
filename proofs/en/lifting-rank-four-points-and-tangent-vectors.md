# Lifting rank-four points and tangent vectors to the matrix algebra

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E6%8A%8A%E7%A7%A9%E5%9B%9B%E7%9A%84%E7%82%B9%E5%92%8C%E5%88%87%E5%90%91%E9%87%8F%E6%8F%90%E5%8D%87%E5%88%B0%E7%9F%A9%E9%98%B5%E4%BB%A3%E6%95%B0.md)

## Statement

Fix [admissible rank-four data $D$](constructing-rank-four-base-data-for-cases-ii-and-iii.md), its [deformation model](rank-four-cotangent-length-counts-only-nonisomorphic-representations.md), a finite $\ell$-adic integer ring $O$, and $K=\overline{\mathbb Q}_\ell$. The model grades the matrix coefficient algebra $B$ by $\mathbb Z^2$, with weights adding under multiplication. The graded equation algebra $A=\bigoplus_j A_j$ maps onto $B_{0,*}=\bigoplus_j B_{0,j}$ with homogeneous kernel $I$. Assume `Fin0`, the finiteness of the weight-$(0,0)$ coefficient algebra over $O$.

Every $x:A\to K$ killing $I$ lifts to a point of $B$. After a two-parameter torus rescaling, the lift arises from the actual local deformation ring. Suppose $x$ is a two-sided point and the associated actual representation satisfies the hypotheses of [rank-four rigidity](rank-four-cotangent-length-counts-only-nonisomorphic-representations.md). Then every derivation $\delta:A\to K$ at $x$ killing $I$ has the form $\delta(f)=bjx(f)$ for $f\in A_j$ and some $b\in K$. Thus the tangent space to the equations at $x$ has dimension at most one.

## Lifting and rescaling a point

Put $C=A/I=B_{0,*}$. Projection to first weight zero is a $C$-linear retraction $B\to C$. Base change along $x:C\to K$ gives a $K$-linear map from $B\otimes_{C,x}K$ to $K$ taking $1$ to $1$. The fiber is nonzero and is finitely generated over $K$ by the finiteness assumptions of the graded model. The weak Nullstellensatz gives a maximal ideal with residue field $K$, hence a lift $B\to K$ of $x$.

For the rescaling, write $b_i$ for the coordinates of the lifted point and $w_i\in\mathbb Z^2$ for their weights. For $b_i\ne0$, put $v_i=v_\ell(b_i)$. A positive-degree monomial of weight zero belongs to the maximal ideal of the formal local ring. Its value belongs to the image of the finite weight-zero $O$-algebra. Some power of the monomial lies in $\mathfrak m_O$ times this finite algebra. Consequently its nonzero value has positive valuation.

We need $\mathbf y\in\mathbb Q^2$ such that $v_i+w_i\cdot\mathbf y>0$ for every nonzero coordinate. If this strict system were inconsistent, Fourier–Motzkin elimination would give nonnegative rational numbers $c_i$, at least one positive, with $\sum_i c_iw_i=0$ and $\sum_i c_iv_i\le0$. Indeed each elimination step combines an upper and a lower bound with nonnegative coefficients, and an inconsistent final constant inequality yields the certificate. Clearing denominators would give a positive-degree weight-zero monomial of nonpositive valuation. Hence the system has a solution, and strictness lets us choose a rational solution. Choose two scalars in $K$ with those valuations to perform the rescaling. Now every coordinate belongs to the maximal ideal of a finite coefficient ring. Evaluate formal power series there by [formal substitution](moving-a-graded-point-back-to-the-local-deformation-ring.md). Compatibility on the graded subalgebra follows by the same fixed-weight monomial argument, now with two weights.

## Lifting the derivation

For a two-sided point, `twoIrr` [gives full matrix span](cross-block-links-force-rank-four-irreducibility.md). Choose matrix coefficients $u,v$ nonzero at the lifted point, in positions $(0,1)$ and $(1,0)$ of weights $(1,0)$ and $(-1,0)$, respectively. Their product belongs to $B_{0,0}$ and $x(uv)\ne0$. After inverting $uv$, the element $u$ is invertible. Multiplication by $u^{-a}$ puts every element of first weight $a$ in first weight zero. The direct grading therefore identifies
$$
B[(uv)^{-1}] \simeq C[(uv)^{-1}][u,u^{-1}].
$$
The dual-number point $x+\epsilon\delta$ on $C$ extends across $(uv)^{-1}$ because $x(uv)\ne0$. Assign $u$ the nonzero constant value it took at the lifted point. This gives a dual-number point on $B$.

Rescale its constant part as above, acting on the whole dual-number point by weight. The constant coordinates are now in the maximal ideal. The $\epsilon$-part is square-zero, so the same formal substitution for dual numbers extends the point to the actual local ring. By rigidity the resulting first-order matrix change is $[X,r]$ for $X$ in the symplectic Lie algebra. The local normalization conditions enter in `rigidDiag`, which realizes this change as the derivative of the two-parameter diagonal torus. At torus parameters $1+\epsilon a,1+\epsilon b$, the action on degree $(d,j)$ is $1+\epsilon(da+jb)$. The matrix coefficients determine the point by `ptExt`. Restricting to $C$, where $d=0$, and undoing the nonzero rescaling gives $\delta(f)=bjx(f)$ for $f\in A_j$. All derivations are thus in the span of this one weight derivative.

## Lean correspondence

- [`ptLift` and `ext_of_proj`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/PtLift.lean#L124) give the fiber argument. [`m2`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/FgMapMk.lean#L24) passes weight-zero finiteness to the equation algebra.
- [`ptScale`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/PtScale.lean#L45) uses [`points_finite`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CommutativeAlgebra/PointsFinite.lean#L310). [`carver`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CommutativeAlgebra/Carver.lean#L135) supplies the valuation parameters by elimination.
- [`exists_lift_of_derivation_on_ideal`, `derivation_kills_ideal_lifts` and `m4`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/ExistsLiftOfDerivationOnIdeal.lean#L130) handle the dual-number lift and tangent bound. `twoIrr` and `rigidDiag` enter as upstream results.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
