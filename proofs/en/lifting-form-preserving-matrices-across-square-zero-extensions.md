# Lifting form-preserving matrices across square-zero extensions

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E5%9C%A8%E5%B9%B3%E6%96%B9%E4%B8%BA%E9%9B%B6%E7%9A%84%E6%89%A9%E5%BC%A0%E4%B8%8A%E6%8F%90%E8%B5%B7%E4%BF%9D%E5%BD%A2%E7%9F%A9%E9%98%B5.md)

## Statement

Let $A,A'$ be complete Noetherian local $O$-algebras with the residue field of $O$. Suppose $A$ has a finite weighted formal presentation with coordinates in the maximal ideal and a weight-component-closed ideal. Let $p:A\twoheadrightarrow A'$ have kernel $V$ killed by $\mathfrak m_A$. Use the form, blocks, free weight group $X$, reference lift and $2\in O^\times$ of the [obstruction argument](second-obstructions-bound-the-number-of-deformation-relations.md).

1. A continuous family of $A'$-valued block-diagonal isometries reducing to the identity, with each entry admitting a preimage of its specified weight $w_a-w_b$, admits a continuous isometry lift with those entry weights.
2. If the kernel of $p$ is also weight-component-closed, a local homomorphism lift $r'$ over $A'$ with entries admitting the specified weights lifts to a homogeneous homomorphism over $A$ satisfying the same local condition $L$. The condition has the closedness, invariance, small-extension lifting and tangent properties in the relation bound.

The first assertion lifts matrices for the global multiplication and frames, and the second lifts a local homomorphism at each condition.

## Continuous homogeneous preimages

Maximal ideal powers are weight-component-closed in the formal presentation. Taking a weight part is therefore continuous on $A$ and is a projection with closed image $A_j$. The decreasing subspaces $\mathfrak m_A^n\cap V$ stabilize, and their intersection is zero by separatedness. For large $n$, $p$ identifies $\mathfrak m_A^n$ with $\mathfrak m_{A'}^n$. Similarly $(A_j+\mathfrak m_A^n)\cap V$ stabilizes at $A_j\cap V$ since $A_j$ is closed. For such $n$, an $x\in p(A_j)\cap\mathfrak m_{A'}^n$ has its unique deep lift in $A_j$ by subtracting an arbitrary homogeneous lift. For a continuous function valued in $p(A_j)$, choose homogeneous representatives by residue modulo $\mathfrak m_{A'}^n$, then use the unique deep lift for the remaining difference. The first choice is locally constant and the second continuous because it carries each deeper power back into the corresponding power of $\mathfrak m_A$.

## Correcting the form

Lift each within-block entry to obtain $h_0$. Its form error is $E=h_0^{\mathsf T}Jh_0-J$ with entries in $V$. Set $Z=-\frac12J^{-1}E$. The common symmetry sign of $E$ and $J$ gives $JZ=Z^{\mathsf T}J=-\frac12E$. Since $J^{-1}$ and $E$ are supported on paired blocks, $Z$ is block diagonal. Also $h_0\equiv1\bmod\mathfrak m_A$ and $\mathfrak m_A V=0$, so
$$
(h_0+Z)^{\mathsf T}J(h_0+Z)-J=E+JZ+Z^{\mathsf T}J=0.
$$
If paired coordinates have weight sum $c$, the error entry $E_{ab}$ has weight $c-w_a-w_b$. Nonzero $J^{-1}_{ia}$ require $w_i+w_a=c$, so $Z_{ib}$ has weight $w_i-w_b$. Thus $h_0+Z$ has the required weights and continuity.

## Preserving the local homomorphism

Use the small-extension property to take a lift $r_1$ satisfying $L$. Independently take continuous homogeneous entry lifts $y_{ab}(g)$ of $r'$. Their differences from the entries of $r_1$ are locally constant in $V$, which is detected modulo a sufficiently deep maximal ideal power. Choose a homogeneous basis $v_i$ of $V$ of weights $h_i$, possible because the kernel is finite dimensional and its defining ideal is closed under weight components.

Set $S=A[[T_1,\ldots,T_b]]$ and $t(j)=\prod_i(1+T_i)^{j_i}$. Write $i:A\hookrightarrow S$ for constants, and $\kappa:A\to S$ for inverse weight substitution, sending a homogeneous $x$ of weight $h$ to $t(-h)i(x)$. Apply $\kappa$ to $r_1$ and conjugate by the torus $t$. At an entry of prescribed weight $d=w_a-w_b$, the $y_{ab}$ term becomes $i(y_{ab})$ and a difference term $c_i v_i$ becomes $t(d-h_i)i(c_i v_i)$. Thus all entries lie in
$$
A^\ast=i(A)\oplus\bigoplus_{u\in E_0}t(u)i(V),\qquad
E_0=\{w_a-w_b-h_i\}\setminus\{0\}.
$$
The directness is Laurent monomial independence. The added terms have pairwise zero products since $V^2=0$, so this is a finite square-zero extension of $A$ with a ring projection killing them.

After base change and conjugation, the matrices over $S$ satisfy the homomorphism and form equations and retain $L$. They satisfy the same equations over $A^\ast$ by injectivity, using the defining ideal of $L$ for that condition. Continuity over $A^\ast$ follows from the continuous constant term and locally constant differences. Project to $A$. Only the prescribed-weight terms remain, and the group law, form and $L$ still hold.

When the local source group is initially equipped only with a topology on its underlying set, one may generate a group topology by cosets of kernels of locally constant homomorphisms. These cosets are open in the original topology, and the locally constant homomorphisms are unchanged. Thus continuity modulo each maximal ideal power is preserved in this formulation.

## Lean correspondence

- [`part_closed`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CommutativeAlgebra/PartClosed.lean) and [`cont_section`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CommutativeAlgebra/ContSection.lean#L55) give continuous homogeneous preimages.
- [`fix_point` and `hh_section`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CommutativeAlgebra/HhSection.lean#L81) correct the form. The script retains within-block correction entries and checks this preserves $JZ$.
- [`square_zero_extension_ring`, `split_data` and `loc_graded`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CommutativeAlgebra/LocGraded.lean#L53) give the extension and projection. [`loc_graded_top`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CommutativeAlgebra/LocGradedTop.lean#L94) handles the topological-space formulation used in `obs_class`.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
