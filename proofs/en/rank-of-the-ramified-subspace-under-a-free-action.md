# Rank of the ramified subspace under a free action

[Chinese proof](../zh/%E8%87%AA%E7%94%B1%E7%BE%A4%E4%BD%9C%E7%94%A8%E6%80%8E%E6%A0%B7%E7%BB%99%E5%87%BA%E5%88%86%E6%AD%A7%E7%A9%BA%E9%97%B4%E7%9A%84%E7%A7%A9.md)

## Statement

Let $K$ be a field, $I$ a finite index set, and $H$ a finite group. Suppose $G=H^I$ acts freely on a finite set $X$. Write $[a]_v$ for the element with $a\in H$ in coordinate $v$ and the identity elsewhere. For
$$
U=\left\{F:X\to K:\sum_{a\in H}F([a]_v x)=0\text{ for all }v\in I,\ x\in X\right\},
$$
we have $(\dim_K U)h^f=|X|(h-1)^f$, where $h=|H|$ and $f=|I|$. Empty products are one. The model computes the rank of the level-zero ramified space `Mram`, the common kernel of the residue-field unit sums `Nm` on `Mu0`.

## Free coordinates on each orbit

Choosing one representative per orbit identifies $X$ with $(X/G)\times G$ by freeness. The equations can be solved independently on each orbit. On $G$ let $H'=H\setminus\{1\}$. A solution is determined by its values on $(H')^I$. At a point with an identity coordinate, the zero-sum equation expresses its value as the negative sum of values at points with one fewer identity coordinate. Induction gives uniqueness. For $b\in(H')^I$ the function
$$
P_b(g)=\prod_{v\in I}\bigl(\mathbf1_{g_v=b_v}-\mathbf1_{g_v=1}\bigr)
$$
has zero sum on every coordinate line, and restricts to the point indicator of $b$ on $(H')^I$. These functions extend arbitrary data there. Thus each orbit contributes $(h-1)^f$ free coordinates and has $h^f$ elements. [Coordinate proof and rank](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LogVandermondeBounds/LogVandermondeProofs/MulSingleMulApplySelf.lean)

## Recover translation coordinates from the action on forms

Suppose a finite abelian $G$ acts freely on a finite class set $C$, with a linear isomorphism $\Phi:M\to(\mathbb C^d)^C$ and a representation $\rho:G\to\mathrm{GL}(M)$. Assume that $\Phi(\rho(g)\phi)(c)=0$ implies $\Phi(\phi)(g c)=0$ for all $g,c,\phi$. For representatives $r_q$ of the orbits, define
$$
(E\phi)(g,q,j)=\Phi(\rho(g)\phi)(r_q)_j,\qquad 1\le j\le d.
$$
If this vanishes for all coordinates, the assumption implies that $\Phi\phi$ is zero on all $g r_q$, hence $\phi=0$. Both dimensions are $d|C|$ by freeness, so $E$ is an isomorphism. By the representation identity and commutativity, $(E(\rho(a)\phi))(g,q,j)=(E\phi)(ag,q,j)$. In these coordinates each operator acts by translation. [Orbit coordinates and intertwining](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/GL6/CoordMapInjective.lean)

## Apply the model at the auxiliary prime

For the project's columns $A:\mathrm{ColumnsAtT}\ R\ C$ at $T\ge3$, take $I=A.\mathrm{vT}$ with $f=R.f$ places above $T$. Each residue field $F_v$ has $T$ elements. A `FreeRankModel A` gives isomorphisms $F_v^\times\simeq H$, a finite free $H^I$-set $X$ and $E:\mathrm{Mu0}\simeq\mathbb C^X$ intertwining every $\rho_v(a)$ with translation in coordinate $v$. Thus $E$ sends the common kernel of $\mathrm{Nm}_v$ onto $U$. If $I\ne\varnothing$ then $h=T-1$ by any of the field unit isomorphisms. If $I=\varnothing$ the ramified space equals the full space. In both cases, with $d_M=\dim\mathrm{Mu0}$ and $d_u=\dim\mathrm{Mram}$, we get
$$
d_u=d_M\left(1-\frac1{T-1}\right)^f.
$$
For $d_M>0$ the relative rank deficit $\delta=1-d_u/d_M$ is at most $f/(T-1)\le2f/T$. This follows from $1-(1-t)^f=t\sum_{j=0}^{f-1}(1-t)^j$ at $t=1/(T-1)$. [Use of the rank deficit in the slope bound](quotient-slope-bounds.md)

In the application, `forms_level_zero_linear_equiv` supplies the class blocks. The stabilizer condition `admS` and matrices implementing the residue-field diamond actions, `DiamondElementsExist`, supply the freeness and zero-transfer properties. `free_rank_model_of_diamonds` feeds these into the orbit coordinates, and `ramified_rank_of_model` applies the resulting rank computation. [Rank from the model](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/GL6/RamifiedRankEqFinrank.lean) · [Construction from the diamond actions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/GL6/RamifiedLatticeOfRankSlopeLength.lean)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
