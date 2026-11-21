# Cross-block links force rank-four irreducibility

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E8%B7%A8%E5%9D%97%E4%BA%92%E9%80%9A%E4%BC%9A%E8%BF%AB%E4%BD%BF%E7%A7%A9%E5%9B%9B%E8%A1%A8%E7%A4%BA%E4%B8%8D%E5%8F%AF%E7%BA%A6.md)

## Statement

Let $K$ be a field, $G$ a group and $r:G\to\mathrm{GSp}_4(K)$ a symplectic similitude representation. Index the coordinates by $0,1,2,3$ with each $i$ paired only with $i^*=3-i$. Put $A=\{0,2\}$ and $B=\{1,3\}$. Assume $E_{ii}$ lies in $S=\operatorname{span}_K r(G)$ for each $i$. Write $i\leadsto j$ when $r(g)_{ij}\ne0$ for some $g\in G$. Suppose every mutually linked pair across blocks lies in a mutually linked class containing a third index. Then either $S=M_4(K)$, or all mutual-link classes are singletons, or the classes are $A$ and $B$ with cross-block arrows in at most one direction.

In the project, $K=\overline{\mathbb Q}_\ell$, $G=G_{\mathbb Q}$, the data satisfy `Good`, $r$ is a characteristic-zero point `EPt`, and `LocalPublishedTheorems` is assumed. `ptIn` gives the diagonal matrix units, and the [third-index lemma](a-cross-block-linked-pair-has-a-third-index.md) gives the hypothesis on links. The first conclusion is `Irr`, which implies usual irreducibility since the entire matrix algebra acts.

## Proof

The span $S$ is an algebra, since $r(g)r(h)=r(gh)$. Multiplying $r(g)$ by $E_{ii}$ on the left and $E_{jj}$ on the right shows $i\leadsto j$ implies $E_{ij}\in S$. Conversely, if all $r(g)_{ij}$ vanish, every element of $S$ vanishes in that position. Thus arrows amount to membership of matrix units, and $E_{ij}E_{jk}=E_{ik}$ makes the relation transitive. The identity gives reflexivity. For symplectic adjoint, $r(g)^*=\nu(g)r(g^{-1})$ with similitude factor $\nu(g)\ne0$. The $(j^*,i^*)$ entry of $r(g)^*$ is the $(i,j)$ entry of $r(g)$ up to sign. Therefore $i\leadsto j$ implies $j^*\leadsto i^*$.

Pass to equivalence classes under mutual linkage. The involution $i\mapsto i^*$ permutes the classes. If a class meets both blocks, the third-index hypothesis gives it at least three elements. It intersects its involution image and so equals that image. A set stable under the fixed-point-free involution has even cardinality. Thus all four indices lie in one class, giving every matrix unit in $S$. If no class meets both blocks, either all classes are singletons, or one class is a whole block. In the latter case the involution gives the other block as a class as well. Arrows in both directions between the blocks could be concatenated using within-block arrows, producing a cross-block mutual link. This gives the claimed alternatives.

## Application to two-sided points

Fix the model of $D$ and assume `Fin0`, `NoEnd` and `SoV`. The first is finiteness of the biweight-zero coefficient algebra over $O$. The second excludes full $M_2(K)$ span on the $A$ block at any admissible block-diagonal characteristic-zero point. The last is the vanishing of the characteristic-zero localized kernels used to classify diagonal-type points. Let $\xi$ be a $K$-point of the coefficient algebra whose restriction to first weight zero is nonzero on at least one positive and one negative second degree. Torus rescaling realizes it as an admissible point and preserves the arrows by multiplying each entry by a nonzero scalar.

In the singleton case, `diagCases` makes either every negative-second-weight matrix entry or every positive-second-weight entry vanish. In the indicated sign, each first-weight-zero monomial of that second degree contains a factor of the same sign. These monomials span their homogeneous pieces, contradicting two-sidedness.

In the two-block case, choose $p(a,b)=a$ or $-a$ so entries of negative $p$-weight vanish. All negative-$p$ homogeneous elements then vanish at $\xi$. Define a new point by evaluating the $p=0$ component at $\xi$. This preserves multiplication because two nonnegative degrees can add to zero only when both are zero, and a factor of negative degree makes its product vanish under $\xi$. The new point preserves within-block entries and sets all cross-block entries to zero. Rescale again to an admissible point. The indices $0,2$ are still mutually linked, giving full matrix span on the $A$ block, contrary to `NoEnd`. Only full rank-four matrix span remains.

## Lean correspondence

- [`geAlg`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/GeAlgTop.lean#L53) equates arrows and matrix units. [`tri`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/TriComb.lean#L28) proves the three cases with a finite enumeration, expressed above by equivalence classes.
- [`diagCases`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/DiagCases.lean#L8) uses the local stable flag and `SoV` to exclude one sign. [`signs`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/SpanZero.lean#L69) extends the vanishing to the graded algebra.
- [`ptLimit`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/PtLimit.lean#L167) constructs the block-diagonal point. [`twoIrr`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/TwoIrr.lean#L42) applies the two exclusions.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
