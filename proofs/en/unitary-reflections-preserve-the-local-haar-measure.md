# Unitary reflections preserve the local Haar measure

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Let $E/F$ be a CM extension with conjugation $z\mapsto\bar z$. Fix a nondegenerate Hermitian form $h$ over $E$, conjugate linear in its first variable. For a finite place $v$ of $F$ put $B=E\otimes_F F_v$, with the extended conjugation, and let $G$ be the group of $B$-linear automorphisms preserving the extended form. Then the modular character $\Delta_G:G\to\mathbb R_{>0}$ is identically one. In particular left Haar measure is invariant under inner conjugation. This gives the comparison of indices of two conjugate compact open lattice stabilizers in the [column level calculation](the-column-level-index-factors-into-finite-field-indices.md).

We prove the algebraic part for a finite product $B$ of characteristic-zero fields with an involution. The data used are an orthogonal basis $v_1,\ldots,v_k$ with $h(v_i,v_i)$ units, an invertible element $\delta$ with $\bar\delta=-\delta$, and a semilinear involution $C$ satisfying $h(Cx,Cy)=\overline{h(x,y)}$. At $v$ these data are obtained from $E$. In fact, over $E$, if $h(z,z)=0$ for every $z$, applying this to $x+y$ and $x+\delta y$ gives $h(x,y)+\overline{h(x,y)}=0$ and $h(x,y)-\overline{h(x,y)}=0$. This would give the zero form. A vector of nonzero norm splits off its orthogonal complement, so induction gives the basis. The diagonal entries in this basis are fixed by conjugation, and $C$ is coordinate conjugation in it. The element $\delta$ can be any nonzero difference of an element of $E$ and its conjugate. All these data extend to $B$, since the nonzero field elements used in the construction map to units. The algebra $B$ is a product of local fields because $E/F$ is separable.

## Choosing a norm-one scalar

For every fixed unit $q=\bar q$ and every $b\in B$, we can choose a unit $u$ such that
$$
u\bar u=1,\qquad q-\bar u b\in B^\times,\qquad 2q-\bar u b-u\bar b\in B^\times.
\tag{1}
$$
Choose $u=(t+\delta)/(t-\delta)$ for an integer $t$, avoiding zeros of the two denominators in every field factor. After clearing denominators the two further unit conditions are nonvanishing of
$$
(q-b)t+\delta(q+b)
\quad\text{and}\quad
(2q-b-\bar b)t^2+2\delta(b-\bar b)t-\delta^2(2q+b+\bar b).
$$
In each field factor the first polynomial is nonzero since $q,\delta$ are units and $2\ne0$. The leading and constant coefficients of the second cannot both vanish since this would give $4q=0$. Excluding their finitely many roots in all the factors gives (1). Conjugating the defining quotient gives $\bar u=u^{-1}$.

## A reflection and its character

For $d\in B^k,c\in B$ set
$$
R_{d,c}(x)=x-c\,h(d,x)d .
$$
If $c+\bar c=c\bar c h(d,d)$, multiplying the two rank-one corrections gives $R_{d,c}R_{d,\bar c}=1$, and expanding $h(R_{d,c}x,R_{d,c}y)$ gives $h(x,y)$. Thus it is a unitary map with inverse $R_{d,\bar c}$. In particular, if $h(v,v)=h(w,w)=q$ and $q-h(w,v)$ is a unit, take $d=v-w$ and $c=(q-h(w,v))^{-1}$. The required relation follows from
$$
h(d,d)=h(d,v)+\overline{h(d,v)} .
$$
This reflection sends $v$ to $w$.

Let $\chi:G\to\mathbb R_{>0}$ be a homomorphism with $\chi(CgC)=\chi(g)$ for all $g$. We show that $\chi(R_{d,c})=1$ whenever $h(d,d)$ is a unit. Write $d'=Cd$, so $h(d',d')=h(d,d)=q$. Choose $u$ by (1) for $b=h(d',d)$. Since $h(ud',d)=\bar u b$, the preceding construction gives a unitary $\rho$ sending $d$ to $ud'$. For any $c'$, conjugation by $\rho$ sends $R_{d,c'}$ to $R_{ud',c'}=R_{d',c'}$. The last equality uses $u\bar u=1$. Conjugation by $C$ sends $R_{d,c}$ to $R_{d',\bar c}$, so
$$
\chi(R_{d,c}^{-1})=\chi(R_{d,\bar c})
=\chi(R_{d',\bar c})=\chi(R_{d,c}).
$$
A positive real number equal to its inverse is $1$.

## Fixing one basis vector at a time

Suppose $g\in G$ fixes a subset of the orthogonal basis vectors and $v=v_i$ is outside that subset. Put $q=h(v,v)$ and $b=h(gv,v)$. Choose $u$ as in (1). The reflection with $d=v$ and $c=(1-u)/q$ sends $v$ to $uv$ and fixes each already fixed basis vector by orthogonality. Its character is $1$. Compose $g$ on the right with this reflection to get $g_1$; then $w=g_1v=ugv$. We have $h(w,w)=q$ and $q-h(w,v)=q-\bar u b$ a unit. The reflection sending $v$ to $w$ has direction $v-w$ of norm $2q-\bar u b-u\bar b$, which is a unit by (1), so its character is also $1$. Its direction is orthogonal to all the already fixed basis vectors, since both $v$ and $g_1v$ are. Composing $g_1$ on the left with the inverse of this reflection gives an element fixing the enlarged subset, with the same character as $g$. After all basis vectors are fixed the resulting element is the identity. Hence $\chi(g)=1$.

For the local unitary group use $\chi=\Delta_G$. The map $g\mapsto CgC$ is a continuous involutive automorphism. The pushforward of left Haar measure by it is another left Haar measure, hence a positive scalar multiple of the original. It intertwines right translation by $g$ with right translation by $CgC$. Comparing their Haar scaling factors gives $\Delta_G(g)=\Delta_G(CgC)$. The reflection calculation proves unimodularity.

## Lean correspondence

- [`reflMat`, `refl` and `exists_refl`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FlagMeasures/AdelicUnitaryHaarBiInvariant.lean#L87) calculate the rank-one correction. [`char_refl`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FlagMeasures/AdelicUnitaryHaarBiInvariant.lean#L141) proves the character is one on the reflections of unit norm, and [`char_eq_one`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FlagMeasures/AdelicUnitaryHaarBiInvariant.lean#L181) performs the induction on basis vectors.
- [`eventually_isUnit` and `generic_of_semilocal`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FlagMeasures/AdelicUnitaryHaarBiInvariant.lean#L259) give the choice (1). [`exists_framed`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FlagMeasures/AdelicUnitaryHaarBiInvariant.lean#L338) gives the orthogonal coordinates and semilinear involution from a Hermitian form over the host field.
- [`modular_involution`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FlagMeasures/AdelicUnitaryHaarBiInvariant.lean#L449) proves the Haar scaling identity, and [`exists_involution`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FlagMeasures/AdelicUnitaryHaarBiInvariant.lean#L492) constructs the continuous group automorphism. [`modular_eq_one`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DivisorProofs/ExistsIsHeckeOpFullDualLab.lean#L107) applies these facts after completion.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
