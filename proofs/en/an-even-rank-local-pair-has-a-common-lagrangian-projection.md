# An even-rank local pair has a common lagrangian projection

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $R$ be a commutative ring with involution and fixed subring $A$ a henselian discrete valuation domain of finite residue field. Suppose $\theta-\bar\theta$ is a unit for some $\theta\in R$, and let $\pi\in A$ be a uniformizer. Let $b$ be even and $h\in\operatorname{Mat}_b(R)$ satisfy $h^*h=\pi^{2k}1$ for $k\ge0$, with $*$ denoting conjugate transpose. There are $e,f\in\operatorname{Mat}_b(R)$ with
$$
e^2=e,\qquad e^*=1-e,\qquad eh=hf.
\tag{1}
$$
The image and kernel of $e$ are isotropic because $e^*e=0$ and $(1-e)^*(1-e)=0$. Over an inert local field, (1) is the projection used to preserve two given self-dual lattices at once.

### The two local cases

By [the involution dichotomy](the-local-involution-splits-or-gives-an-unramified-quadratic-ring.md), either the ring is split with a scalar idempotent $\epsilon$ satisfying $\bar\epsilon=1-\epsilon$, or it is an unramified quadratic discrete valuation domain. In the split case take $e=f=\epsilon 1$. This is idempotent, has the required adjoint, and commutes with $h$.

In the domain case prove a stronger statement by induction on the even rank. Allow arbitrary unimodular Hermitian Gram matrices $B,B'$ with $h^*Bh=\pi^{2k}B'$, and require
$$
e^2=e,\qquad e^*B=B(1-e),\qquad eh=hf.
\tag{2}
$$
Here $e$ acts on the target of $h$, whose Gram matrix is $B$. Rank zero gives the empty matrices, so the identities hold. If $h=\pi^k h_1$ for $h_1$ invertible over $R$, choose $e$ from a hyperbolic basis of $B$, as in the dichotomy proof. The projection onto one vector in each hyperbolic pair is complementary to its adjoint for $B$. Take $f=h_1^{-1}eh_1$, which is integral, and then $eh=hf$.

### The rank-two reduction

Otherwise the [minimal-entry argument](a-minimal-entry-finds-a-common-hyperbolic-plane.md) gives two integral bases in which $B,B'$ are each the direct sum of a common hyperbolic plane and a unimodular form on a complement. In these bases
$$
B=\begin{pmatrix}J&0\\0&B_1\end{pmatrix},\quad
B'=\begin{pmatrix}J&0\\0&B'_1\end{pmatrix},\quad
h=\begin{pmatrix}D&0\\0&h_1\end{pmatrix},
\qquad
J=\begin{pmatrix}0&1\\1&0\end{pmatrix},\quad
D=\operatorname{diag}(\pi^{k-a},\pi^{k+a}).
$$
The scales satisfy $1\le a\le k$ and $h_1^*B_1h_1=\pi^{2k}B'_1$. On the plane let $e_0=f_0=\operatorname{diag}(1,0)$. Then $e_0^2=e_0,\ e_0^*J=J(1-e_0)$, and $e_0 D=D f_0$. On the complement use induction to obtain $e_1,f_1$ obeying (2) in rank $b-2$. The block diagonal matrices with blocks $(e_0,e_1)$ and $(f_0,f_1)$ satisfy every equation of (2). Return to the original target and source bases independently: the former conjugates $e$ and transforms its Gram matrix, and the latter conjugates $f$. The three equations are preserved because they are identities of maps and the target adjoint is defined by its Gram matrix. This completes the induction; taking $B=B'=1$ proves (1).

In the [local projection construction](split-and-inert-places-supply-the-local-target-projection.md#inert-places-and-their-simultaneous-frames), $h=\pi^k u$ for the relative matrix $u$ between the two self-dual lattices. Its relation with $f$ simplifies to $eu=uf$, ensuring $e$ preserves the second lattice as well as the first. Thus the local exact projection gives all three small-error matrices after rational approximation.

### Lean correspondence

- [`LocCartanPair`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/SqPair.lean#L24) states (1). [`PHyp` and `PConcl`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/LocalCartanPairs/PiNonunit.lean#L29) give the stronger formulation (2).
- [`assemble`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/LocalCartanPairs/FiniteAdeleIdempotentOfFMulSelf.lean#L34) makes the block diagonal projection. [`pgen_main`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/LocalCartanPairs/FiniteAdeleIdempotentOfFMulSelf.lean#L136) is the even-rank induction. [`locCartanPair_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/LocalCartanPairs/FiniteAdeleIdempotentOfFMulSelf.lean#L170) treats the split scalar case and specializes the induction to $B=B'=1$.
- [`local_cartan_pair`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/OrbitalBoundsConclusion/LocCartanPair.lean#L10) supplies the dichotomy, base and rank-two step, and is the local matrix theorem invoked in the global square construction.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
