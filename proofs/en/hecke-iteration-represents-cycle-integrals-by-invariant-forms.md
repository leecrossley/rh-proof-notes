# Hecke iteration represents cycle integrals by invariant forms

[Chinese proof](../zh/Hecke%E8%BF%AD%E4%BB%A3%E6%80%8E%E6%A0%B7%E6%8A%8A%E5%91%A8%E6%9C%9F%E7%A7%AF%E5%88%86%E5%BD%92%E5%88%B0%E4%B8%8D%E5%8F%98%E5%BD%A2%E5%BC%8F.md)

## Statement

Let $L$ be totally imaginary and $k\ge0$ with $k+1<r_2(L)$. Above every $N_0$ there is $N\ge N_0$ such that every homogeneous $(k+1)$-cocycle $c$ of $G_N=\mathrm{GL}_N(O_L)$ with trivial real coefficients has the same values on cycles as a form $\omega_b$ invariant under $G_\infty=\prod_{w\mid\infty}\mathrm{GL}_N(\mathbb C)$. The forms are on the product $X_N$ of positive definite Hermitian cones, and their values integrate over the affine simplices with vertices $g_i I$. This is `SSurj` in the [rational rank bound](repeated-blocks-leave-one-direction-per-complex-place.md).

## Smoothing and averaging

Write $F_\omega(x)$ for the tensor at $I$ obtained by pulling back $\omega_{xI}$ along the tangent action of $x$. Let $\mathcal D$ be a finite Haar measure fundamental domain for $SL_N(O_L)$ acting on the product of the complex special linear groups, and $x_y$ the image of $y\in\mathcal D$ in $G_\infty$. Choose a prime element $\pi$ with absolute norm at least $25$. Take $N\ge3$ above the uniform Hecke detection threshold and large enough for the height moment. Specifically `SPU` chooses the uniform partition-of-unity exponent $a$, and `SMom` allows $\int_{\mathcal D}\mathrm{ht}(x_y)^{2a(k+1)}d\mu(y)<\infty$. None of these rank choices depends on $c$.

The [equivariant partition](a-partition-of-unity-from-the-thick-part.md) and [smoothing](a-partition-of-unity-smooths-group-cocycles.md) produce a continuous form with closed integration cochain, giving the same cycle values as $c$. It is initially invariant for the arithmetic group and central directions with common absolute value. [Center averaging](averaging-along-unit-directions-gives-center-invariance.md) produces full center invariance while keeping the values. The height changes on the compact set of shifts by at most a fixed factor by `SHt`. These inputs give the form $\omega'$ with $\|F_{\omega'}(x)\|\le K\mathrm{ht}(x)^{a(k+1)}$. The [height moment](siegel-set-volume-controls-height-moments.md) makes the tensor square integrable and hence integrable on the finite measure domain.

The [tensor averaging result `SMean`](averaging-tensors-on-a-fundamental-domain.md) gives a fully invariant $\omega_b$ with
$$
F_{\omega_b}(x)=\mu(\mathcal D)^{-1}\int_{\mathcal D}F_{\omega'}(x_y)d\mu(y).
$$
The source uses inverse zero if the measure is zero. Put $\eta=\omega'-\omega_b$. Each tensor evaluation $f_u(x)=F_\eta(x)(u_1,\ldots,u_{k+1})$ is continuous, arithmetic and center invariant, in $L^2(\mathcal D)$ with mean zero by linearity. The integration cochain of $\omega_b$ is closed by `SInv`, hence so is that of $\eta$.

## From contraction to cycle vanishing

The [normalized Hecke operator $T$ at $\pi$](the-hecke-average-contracts-mean-zero-functions.md) preserves this function space and has $L^2$ norm at most $3/5$ there, by `SGap` for $N\ge3$ and residue size at least $25$. Set $\eta_r=T^r\eta$ using the finite form average. Evaluating a pulled-back tensor commutes with this average, as do integration and the cochain differential. On tuples $u$ from a fixed basis, finite dimensionality gives $\|A\|^2\le K_1\sum_u |A(u)|^2$. Thus
$$
\int_{\mathcal D}\|F_{\eta_r}(x_y)\|^2d\mu(y)
\le K_1(3/5)^{2r}\sum_u\|f_u\|_2^2.
$$
The [period bound `SLoc`](an-l2-bound-for-a-fixed-period.md) controls the absolute integral on any fixed cycle $z$ by $C_z$ times the $L^2$ norm of the pulled-back tensor, for continuous arithmetic and center invariant forms with closed integration cochain. Hence $|I_{\eta_r,N}(z)|\le C'_z(3/5)^r$ with $C'_z$ independent of $r$.

The [period detection theorem `SHecke`](hecke-periods-cannot-decay-at-three-fifths.md) says that at the chosen rank and degree, an arithmetic-invariant closed cochain on homogeneous tuples in $\mathrm{GL}_N(L)$ with this decay on every cycle has all original cycle values zero. Apply it to the integral cochain of $\eta$. Then $\omega_b$ gives all the values of $\omega'$, and thus of $c$.

## Lean correspondence

- [`SSurj`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/SBStar.lean#L20) and [Hecke, smoothing, center and mean inputs](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/SBridgeAlt.lean) specify the theorem. [`JoinReconstruction.key`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/IteratedHeckeBounds/LemForm.lean) assembles it.
- [Mean subtraction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/IteratedHeckeBounds/LemLz.lean) and [norm and period bounds](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/IteratedHeckeBounds/LemBound.lean) yield the decay estimate.
- [`sHecke_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/SHeckeOf.lean), [`sGap_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/SGapOf.lean), and [`sLoc_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/CompactLocalSets/SLocOf.lean) are the theorem entry points.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
