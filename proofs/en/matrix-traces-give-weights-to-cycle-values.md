# Matrix traces give weights to cycle values

[Chinese proof](../zh/%E7%9F%A9%E9%98%B5%E7%9A%84%E8%BF%B9%E6%80%8E%E6%A0%B7%E7%BB%99%E5%91%A8%E6%9C%9F%E5%88%86%E9%85%8D%E6%9D%83.md)

## Statement

Let $L$ be a number field, $k\ge0$ even, and $q=k+1$. Let $\mathcal H_N$ be the product of real vector spaces of Hermitian $N\times N$ matrices at the infinite places, including the real places. Write $X_N$ for its positive definite part. The complex general linear groups act there by congruence and $G_N=\mathrm{GL}_N(O_L)$ acts through its embeddings. For a $q$-form $\omega$ invariant under the complex groups, let $I_{\omega,N}$ integrate it over the simplices of the real bar chains. There are functionals $\tau_{w,n}$ for each infinite place $w$ at all ranks $n$. For any given $N,\omega$ there are real $c_w$ and families $a_{j,n}$ for $2\le j\le q$ such that for each cycle $y$ at rank $N$,
$$
I_{\omega,N}(y)=\sum_w c_w\tau_{w,N}(y)+\sum_{j=2}^q a_{j,N}(y).
$$
These functionals kill boundaries and preserve cycle values on adjoining identity blocks. Repeating $d\ge1$ blocks scales $\tau_w$ by $d$ and $a_j$ by $d^j$. This is `SWtOdd` in the [rank argument](repeated-blocks-leave-one-direction-per-complex-place.md).

## Invariant tensors and closed forms

Congruence is transitive on $X_N$, with stabilizer at the identity $I$ the product of unitary groups. Invariant forms correspond to unitary-invariant real alternating tensors at $I$: transporting a tensor to another point is independent of the choice of transporting element. Write $\beta=\omega_I$. For positive $a$, $\omega_{a^2}(aY_1a,\ldots,aY_qa)=\beta(Y_1,\ldots,Y_q)$. The derivative of $a\mapsto a^2$ at $I$ is twice the identity. The inverse function theorem gives smoothness near $I$ and transitivity gives it everywhere. Differentiating at $I$ yields
$$
2(D\omega)_I(X)(Y_1,\ldots,Y_q)
=-\sum_i\beta(Y_1,\ldots,XY_i+Y_iX,\ldots,Y_q).
$$
Alternating in $X,Y_1,\ldots,Y_q$ kills each summand by symmetry in $X,Y_i$. Therefore $d\omega=0$ at $I$ and everywhere by invariance. A homogeneous bar tuple is sent to the affine simplex with vertices $g_iI$, and Stokes gives zero on boundaries.

## Counting trace factors

Choose a permutation $\sigma$ of the inputs and assign a place $w_i$ to each input. A permutation term vanishes unless places are constant along each cycle. Otherwise it is the product over cycles $(i_1\,\dots\,i_s)$ of $\operatorname{tr}(Y_{i_1,w_{i_1}}\cdots Y_{i_s,w_{i_1}})$. Take real or imaginary part and alternate. The `FFT` spanning theorem says these trace tensors span the invariant tensors over $\mathbb R$. Its proof complexifies and uses the trace pairing and double commutant to express an invariant pairing by place-labelled permutation operators.

Extend a trace tensor by congruence and integrate. Stabilization sends points to $\operatorname{diag}(h,I)$ and tangent matrices to $\operatorname{diag}(Y,0)$. At $I$ every trace factor contains at least one input, so the zero block has no contribution. Invariance gives equality of pulled-back forms everywhere and hence of simplex integrals. Repeating $d$ blocks multiplies each trace by $d$, independently in each cycle, so $j$ cycles scale by $d^j$.

A single cycle uses just one place. Reordering indices makes it the standard long cycle up to the alternation sign. For $T(Y)=\operatorname{tr}(Y_1\cdots Y_q)$, Hermitian conjugation reverses the order, so
$$
\overline{\operatorname{Alt}T}=(-1)^{q(q-1)/2}\operatorname{Alt}T.
$$
Either its real part or its imaginary part vanishes. The sum of the two parts thus spans all single-cycle tensors at that place, and its integral gives $\tau_{w,n}$. In the `FFT` expansion of the particular $\omega$, group single cycles by place and all other terms by their number of cycles. Use those coefficients for these same trace patterns at every rank. This gives the families and the asserted formula.

## Lean correspondence

- [`SWtOdd`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/SBStarOdd.lean#L9) and [`swtOdd` with integration identities](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/OddWeightCycles/AevApply.lean#L67) give the formula and scaling.
- [`tmC`, `tmR` and `AT`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/PermutationSigns/PadMHerm.lean#L22), [`FFT`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/PermutationSigns/PStab.lean#L10) and [`fft_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/PermutationSigns/FFTAsm.lean#L94) give the tensors and spanning.
- [`wOneOdd`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/OddWeightCycles/Weights.lean) handles the long cycle. [Closedness and Stokes](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/SmoothCompositionIdentity/MatOne.lean#L42) give the boundary calculation.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
