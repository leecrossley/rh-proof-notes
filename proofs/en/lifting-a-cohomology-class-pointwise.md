# A cohomology lift can satisfy the identity pointwise

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E4%B8%8A%E5%90%8C%E8%B0%83%E7%9A%84%E6%8F%90%E5%8D%87%E5%8F%AF%E4%BB%A5%E9%80%90%E7%BE%A4%E5%85%83%E7%B4%A0%E5%8F%96%E7%AD%89.md)

**Proposition.** Let $D$ act linearly on modules $P,Q$ over a commutative ring $\mathcal O$, with equivariant surjection $p:P\to Q$. Let $F_P\subseteq H^1(D,P)$ and $F_Q\subseteq H^1(D,Q)$ be the chosen finite cohomology conditions. Suppose $\ell^{e'} F_Q\subseteq p_*(F_P)$ for a prime $\ell$ and integer $e'\ge0$. Every cocycle $\kappa:D\to Q$ with $[\kappa]\in F_Q$ then has a cocycle lift $b:D\to P$ with $[b]\in F_P$ and $p(b(g))=\ell^{e'}\kappa(g)$ for every $g$. With continuous cochains the adjustment below is continuous if the coboundaries are continuous.

Choose a representative $b_0$ of a lift of $\ell^{e'}[\kappa]$ in $F_P$. The cocycle $p(b_0(g))-\ell^{e'}\kappa(g)$ equals $gv-v$ for some $v\in Q$. Choose $w\in P$ with $p(w)=v$. Then $b(g)=b_0(g)-(gw-w)$ has the same class and satisfies the asserted identity by equivariance.

In the normalized block ring $A$, at column $l$ the first map is $Ae_1\to L$, $a\mapsto av_1$, to the zero-block lattice. Lift each finite basis cocycle $\kappa_{la}$; the resulting $K_{la}$ has $K_{la}(g)v_1=\ell^{e'_l}\kappa_{la}(g)$ at every $g\in D_l$. The second map is $AE\to\Delta\mathcal O$ with trivial target action. Lift $\Delta u_l$ where $u_l$ vanishes on inertia and equals $1$ at a chosen decomposition-group element. Then $K^*_{l0}(g)\in AE$ acts on block one by $\ell^{e'_l}\Delta u_l(g)$, giving the unit required in the [column kernel bound](column-relations-bound-the-kernel-in-three-blocks.md) and the unramified column condition. Both functions may be set to zero outside $D_l$. The class is preserved by the adjustment, so the [outside-point comparison](column-dimension-detects-outside-representations.md) can still apply the finite conditions.

## Lean correspondence

- `liftCoc` adjusts the representing cocycle. `colK` and `colk` use it for the two left ideals. [Pointwise lift](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/SplitLocalLifts/SplitLocalLiftProofs/LocLift.lean#L13) · [Column lifts](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/SplitLocalLifts/SplitLocalLiftProofs/LocLift.lean#L38)
- `liftO_of_liftF` and `liftCol_eve_Dd` and `liftCol_evE_Dd` supply the hypotheses from `LiftAt`. [Finite classes](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/AdmissibleDesigns/FiniteClassesLocalEq.lean#L178) · [Application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/AdmissibleDesigns/FiniteClassesLocalEq.lean#L798)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
