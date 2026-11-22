# Constructing the point model by a torsion quotient

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix a layer of rank $n$ with the arithmetic group and level laws of the true chain and a [splitting of the decorated points](splitting-a-point-into-its-word-prime-data-and-off-prime-data.md). For each class label $b$, write $D_b$ for the set of arithmetic points and $H_b$ for the arithmetic frame group. Its matrix homomorphism $\gamma_b$ surjects onto the unitary group $U_n(E)$, and its level character $\chi_b$ takes values in $\mu(K)$, the group of roots of unity of the coefficient field. Its action on the selected local pairs is through just $\gamma_b$. Assume the stabilizer condition that an element of $H_b$ fixing an arithmetic point and having matrix $1$ is the identity. These are the properties of the layer and of `Split` used below.

We construct the point set with the larger action of $G=U_n(E)\times\mu(K)$. Each orbit of arithmetic points in a fixed label gives exactly one orbit of this action, and the corresponding stabilizers have equal orders. The construction realizes the selected local pairs and gives the torsion identifications used to [extend the kernel to all points](extending-the-coefficient-kernel-to-all-complex-points.md).

### The off-prime quotient

For each $b$, write $d\sim_{\rm off}d'$ when the points have the same retained off-prime data in the splitting. On $\mu(K)\times D_b$ define the relation
$$
(s,d)\sim(t,d')\quad\Longleftrightarrow\quad
\exists h\in H_b,\ \gamma_b(h)=1,\ s=t\chi_b(h),\ hd\sim_{\rm off}d'.
$$
It is reflexive by the identity. Inversion gives symmetry since the off-prime relation is equivariant, and multiplication of the two witnessing group elements gives transitivity. Let $Z_b$ be the quotient and set $Z=\coprod_b Z_b$. Put
$$
\mathcal P=Z\times \prod_{P\in\mathcal T}\mathcal P_P,
$$
where $\mathcal P_P$ consists of full $\mathcal O_{E,P}$ lattices in $E^n$ with nonzero residue functionals. This is a local valuation-ring model in the field $E$ itself. Its eventual value space is over $\mathbb C$. For an arithmetic point $d$ define
$$
[b,s,d]_{\rm pt}=\bigl((b,[(s,d)]),(\text{local pair of }d\text{ at }P)_P\bigr).
$$
The splitting realizes any prescribed tuple of local pairs with the same off-prime data as a chosen representative $d$ of a class in $Z_b$. Thus every point in $\mathcal P$ has the displayed form.

Equality of two off-prime components gives equality of their labels and a witnessing element $h$ in the relation. That element acts trivially on each selected local pair because $\gamma_b(h)=1$. For equality of the full points it follows that $hd$ and $d'$ also have the same local pairs. The uniqueness in the splitting then gives $hd=d'$. Conversely such an equality and $\gamma_b(h)=1$, $s=t\chi_b(h)$ give equality of the full points. This is precisely the stronger identification needed in the kernel descent.

### The action and its stabilizers

Given $(\gamma,s)\in G$, choose $h\in H_b$ with $\gamma_b(h)=\gamma$. Define the action on any point expression by
$$
(\gamma,s)[b,t,d]_{\rm pt}=[b,st\chi_b(h)^{-1},hd]_{\rm pt}.
$$
To check both choices at once, suppose the original point is also $[b,t',d']_{\rm pt}$ and use a lift $h'$ instead. The equality of the original points supplies $a$ with $\gamma_b(a)=1$, $d'=ad$, $t=t'\chi_b(a)$. The element $h'a h^{-1}$ has matrix component $1$, sends $hd$ to $h'd'$, and has character $\chi_b(h')\chi_b(a)\chi_b(h)^{-1}$. This is exactly the quotient correction between $st\chi_b(h)^{-1}$ and $st'\chi_b(h')^{-1}$. Thus the result is independent of both choices. The identity acts trivially, and a product acts by the product of the chosen lifts, with the scalar corrections multiplying. This proves the group law. The off-prime action depends only on the off-prime component, by the same calculation with $ad\sim_{\rm off}d'$ in place of equality.

Use the map $d\mapsto[b,1,d]_{\rm pt}$ from arithmetic points. The homomorphism $h\mapsto(\gamma_b(h),\chi_b(h))$ intertwines the actions because the character of the lift cancels in the action formula. Every full point is obtained from an arithmetic point by the central element $(1,s)$. For any $b$, every element of $G$ is an image of an arithmetic frame element times a central torsion element, by the surjectivity of $\gamma_b$. The action at the selected local pairs is by the rational matrix, and the torsion factor acts trivially there. On the complex value space the corresponding action is substitution of the inverse matrix on frames and multiplication by the embedded scalar. Thus a central torsion element acts on values exactly by that scalar.

Every point is in the orbit of the image of an arithmetic representative, by first choosing a point expression and then using the arithmetic orbit description in $D_b$. Conversely suppose $(\gamma,s)[b,1,d]_{\rm pt}=[b,1,d']_{\rm pt}$. A lift $h$ of $\gamma$ gives $[b,s\chi_b(h)^{-1},hd]_{\rm pt}=[b,1,d']_{\rm pt}$. The full equality criterion yields $a$ of matrix $1$ with $a h d=d'$ and $\chi_b(a)=s\chi_b(h)^{-1}$. Then $a h$ realizes the move in $H_b$ and has image $(\gamma,s)$. This proves correspondence of orbits and surjectivity on stabilizers. Injectivity on stabilizers is the assumed faithfulness there of the matrix component. The stabilizer orders therefore agree.

### Lean correspondence

- [`rel` and `ZZ`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsLevelPrimePointModelRealisation.lean#L117) define the off-prime quotient. [`mk` and `mk_fst_iff`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsLevelPrimePointModelRealisation.lean#L138) give the point expression and the first-component criterion. [`mk_eq_iff` and `mk_surj`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsLevelPrimePointModelRealisation.lean#L165) establish equality and surjectivity.
- [`sm`, `sm_mk` and `actPT`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsLevelPrimePointModelRealisation.lean#L189) give the action and independence of lifts. [`smul_fst` and `smul_snd`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsLevelPrimePointModelRealisation.lean#L253) check the two components.
- [`rep_surj`, `rep_inj` and `card_stab`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsLevelPrimePointModelRealisation.lean#L272) compare arithmetic and point orbits. [`model` and `real`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsLevelPrimePointModelRealisation.lean#L421) assemble this data with the residue reductions and invariant value pairing into the full point model.

Status. Source-based reconstruction draft. The proof above reconstructs the point set, its group action and the arithmetic realization. The residue-move readout and invariant inner product are further inputs to the full model. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
