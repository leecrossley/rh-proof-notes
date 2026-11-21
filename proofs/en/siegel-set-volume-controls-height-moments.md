# Siegel set volume controls height moments

[Chinese proof](../zh/Siegel%E9%9B%86%E5%90%88%E9%87%8C%E7%9A%84%E4%BD%93%E7%A7%AF%E6%80%8E%E6%A0%B7%E6%8E%A7%E5%88%B6%E9%AB%98%E5%BA%A6%E7%9F%A9.md)

## Statement

Let $L$ be totally imaginary, $A\ge0$ an integer, $N\ge A+2$, and $\Gamma=\mathrm{SL}_N(O_L)$ in $S=\prod_w\mathrm{SL}_N(\mathbb C)$. There is a finite Haar measure fundamental domain $D$ with $\int_D\mathrm{ht}(x)^A\,d\mu(x)<\infty$ for the [height by lattice minima](height-from-a-lattice-and-its-inverse-transpose-form.md). This is the range in `SMom` for the squared norms in [Hecke iteration](hecke-iteration-represents-cycle-integrals-by-invariant-forms.md).

## Siegel boxes and their volume

For $\sum_i s_i=0$, take $a(s)=\operatorname{diag}(e^{s_i})$ at every place and write $W(s)=\sum_{i=0}^{N-2}|s_i-s_{i+1}|$, $\Phi(s)=\sum_{i<j}(s_i-s_j)$. A Siegel set consists of $p a(s)k$ with $p$ in a compact set of upper triangular matrices with bounded entries and diagonal moduli bounded below, with product of diagonal moduli across places one for each column. Here $k$ is special unitary in each factor and $s_{i+1}\le s_i+T$. Restrict $s_i\in[m_i,m_i+1]$ for integer $m_i$ to get the compact sets $X_m$.

Fix any allowed $s^{(0)}$ in a box. In one complex place choose upper unitriangular $u$ whose entries $i<j$ are Gaussian integers of modulus at most $2e^{s_i^{(0)}-s_j^{(0)}}$. In other places set $u=1$. A disk contains at least a constant times its radius squared many lattice points, using an inscribed square with the zero point for small radii. There are at least $C_1 e^{2\Phi(s^{(0)})}$ choices. The translates $uX_m$ lie inside $a(s^{(0)})$ times a fixed compact set. Indeed conjugation of $u$ by $a(-s^{(0)})$ bounds its entries, and conjugation of $p$ bounds upper entries since $e^{s_j^{(0)}-s_i^{(0)}}\le e^{(j-i)T}$. The remaining $a(s-s^{(0)})k$ is uniformly compact.

If two translates meet then
$$
u^{-1}u'=p\,a(s)(kk'^{-1})a(-s')p'^{-1}.
$$
At the chosen place this makes $kk'^{-1}$ upper triangular and unitary, hence diagonal. Since $s,s'$ lie in the same box, the right side is uniformly bounded. The entries of $u^{-1}u'$ are Gaussian integers, so there are uniformly finitely many possible overlaps. Integrating the total multiplicity of the left translates, whose measures equal $\mu(X_m)$, gives $\mu(X_m)\le C e^{-2\Phi(s^{(0)})}$.

## Bounding the height and summing the boxes

For a fixed rational translate $c$, meaning $c_w=z_w w(g)$ for scalars $z_w$ and $g\in\mathrm{GL}_N(L)$, one has $\mathrm{ht}(c p a(s) k)\le C_c e^{2W(s)}$. To bound the first minimum, clear denominators in $g^{-1}$ by an integer and choose the last nonzero coordinate of $g^{-1}y$. At that coordinate $p^{-1}$ only scales it by its diagonal unit, bounded below in modulus. The corresponding cleared algebraic integer has modulus at least one somewhere. After applying $a(-s)$ and the unitary factor, the bound is a constant times $e^{-2\max s_i}$. For the transpose use the first nonzero coordinate of $g^\mathsf T y$ since $p^\mathsf T$ is lower triangular. The bound is a constant times $e^{2\min s_i}$. Taking the reciprocal product gives the estimate since $\max s_i-\min s_i\le W(s)$.

With $h_i=s_i-s_{i+1}\ge-T$,
$$
\Phi(s)=\sum_{i=0}^{N-2}(i+1)(N-i-1)h_i\ge(N-1)W(s)-C_T .
$$
The positive terms have coefficients at least $N-1$ and the negative terms are bounded. Also $\sum_i|s_i|\le NW(s)$ by sum zero and the total variation bound. For $B<2(N-1)$ this gives $BW(s)-2\Phi(s)\le C'-\epsilon\sum_i|s_i|$ with $\epsilon>0$. On each box, combine the volume bound with the height supremum. The bounded differences of $s$ in that box change $W$ by only a fixed constant, and $\sum_i|s_i|\ge\sum_i|m_i|-N$. Hence each term is bounded by a constant times $e^{-\epsilon\sum_i|m_i|}$. These sum by a product of geometric series. Take $B=2A<2(N-1)$.

## Passing to a fundamental domain

Reduction theory `SRed` supplies finitely many rational translates and a common compact $P$ and bound $T$ such that every $\Gamma$-orbit meets their union of Siegel sets. The source passes from general to special linear reduction by the finite quotient of units modulo $N$th powers. Unfolding the integral over the union counts each point of a fundamental domain at least once. For the nonnegative invariant function $\mathrm{ht}^A$ the integral is therefore bounded by the finite sum of Siegel set integrals. The same argument for one gives the finite volume.

## Lean correspondence

- [`Sieg`, `W`, `SHtB`, `SIntB` and `SRed`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/MomentEntryBounds/InstLCSL.lean) give the conditions.
- [`pack`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/IntegralMomentReduction/MtInvUpper.lean#L62), [`sHtB`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/IntegralMomentReduction/PrimalY.lean#L125) and [`main_of_pack`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/IntegralMomentReduction/SetLIntegralLeOfMul.lean#L37) handle volume, height and summation.
- [`sRed_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/IntegralMomentReduction/SRedOf.lean), [`sMom_of_parts`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/MomentEntryBounds/SetLIntegralPreimageMulLeft.lean#L68) and [`sMom_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/IntegralMomentReduction/SMomOf.lean#L10) give the covering and domain integral.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
