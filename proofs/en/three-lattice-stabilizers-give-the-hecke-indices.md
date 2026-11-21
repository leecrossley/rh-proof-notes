# Three lattice stabilizers give the Hecke indices

[Chinese proof](../zh/%E4%B8%89%E4%B8%AA%E6%A0%BC%E7%9A%84%E7%A8%B3%E5%AE%9A%E7%BE%A4%E6%80%8E%E6%A0%B7%E7%BB%99%E5%87%BAHecke%E7%9A%84%E6%9C%89%E9%99%90%E6%8C%87%E6%95%B0.md)

## Statement

Let $L$ be a number field, $R=O_L$, $\pi$ a prime element, $q=|R/(\pi)|\ge25$, and $N\ge3$. Let $D_r$ be diagonal with the first $r$ entries $\pi$ and others $1$, and $K_r=D_r^{-1}\mathrm{SL}_N(R)D_r$ for $r=0,1,2$. Put $E_{rs}=K_r\cap K_s$ and $B=K_0\cap K_1\cap K_2$. Then $B$ has finite index in each $K_r$, $[E_{02}:B],[E_{01}:B]\ge25$, and the complements of $E_{01},E_{12},E_{12}$ in $K_0,K_1,K_2$, respectively, are each at most one double coset. These are `Arith` and `Tri`. If $L$ is totally imaginary, $\langle K_0,K_1\rangle$ is dense in $\prod_{w\mid\infty}\mathrm{SL}_N(\mathbb C)$, as in `Dens`.

## Indices and double cosets

In $K_r$ use coordinates $\gamma=D_rgD_r^{-1}$. Membership in $K_s$ means the conjugate by $D_sD_r^{-1}$ remains integral, since it keeps determinant one. Check only the entries divided by $\pi$. Over $\mathbb F=R/(\pi)$, in $K_0$ this makes $E_{01}$ the stabilizer of $\mathbb F e_0$ and $E_{02}$ the stabilizer of $\langle e_0,e_1\rangle$. In $K_1$ coordinates $E_{12}$ stabilizes $\mathbb F e_1$. In $K_2$ coordinates $E_{12}$ stabilizes the hyperplane $x_1=0$. Reduction of $\mathrm{SL}_N(R)$ onto $\mathrm{SL}_N(\mathbb F)$ is surjective by elementary matrices, and the principal congruence subgroup in each coordinate system lies in $B$, giving finite index.

Special linear matrices act transitively on ordered pairs of distinct lines by choosing bases and adjusting one vector's scale for determinant one. By duality they also act transitively on distinct hyperplane pairs. Thus a line or hyperplane stabilizer acts transitively on the other lines or hyperplanes, giving the three double coset conclusions. In $K_0$ coordinates $B$ fixes both the given line and plane. The plane stabilizer acts transitively on its lines, so $[E_{02}:B]=q+1$. The line stabilizer acts transitively on planes containing it by considering lines in the quotient by that line, so $[E_{01}:B]=(q^{N-1}-1)/(q-1)$. Each count is at least $q+1$.

## Density

Write $U_{ij}(a)=I+aE_{ij}$ for $i\ne j$. The generated group contains $U_{ij}(a)$ for $a\in R$ from $K_0$ and $U_{0j}(a/\pi)$ from $K_1$. The three-index identity $[U_{ik}(b),U_{kj}(c)]=U_{ij}(bc)$ gives all $U_{ij}(a/\pi^m)$ by induction. For $i,j\ne0$, use intermediate index $0$ and denominators $\pi^m,\pi$. For $i=0$ use a third index with denominators $\pi,\pi^m$. For $j=0$ use the just-established off-zero pair at denominator $\pi^{m+1}$ and $U_{k0}(1)$.

The ring $R$ is a full lattice $\Lambda$ in the product of complex places. The union of $\pi^{-m}\Lambda$ is dense. Otherwise a nonzero real additive character trivial on its closure exists by the structure of closed subgroups of a real vector space. Its functional would belong to every dual lattice of $\pi^{-m}\Lambda$. Under trace duality the intersection is $\bigcap_m\pi^m\mathfrak D^{-1}=0$ for the inverse different, by valuation at $(\pi)$. This contradiction proves density of the parameters. The group closure therefore contains every elementary transvection at each complex place independently, and these generate the whole product.

## Lean correspondence

- [`dg`, `Kg`, `Arith` and `Dens`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/Arith.lean) and [`Tri`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/AEConst.lean#L54) state the input.
- [`arith_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/PArith.lean#L721) uses the explicit congruence and index calculations.
- [`mem_sup` and `dens_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/IntegralTransvectionMemSlIntegersConjugateZero.lean#L101), [density of parameters](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/PDensG.lean) and [density for matrix groups](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/PDensM.lean) prove the second assertion.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
