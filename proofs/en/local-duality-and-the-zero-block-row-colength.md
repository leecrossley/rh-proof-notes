# Local duality turns the zero-block row cost into a colength

[Chinese proof](../zh/%E5%B1%80%E9%83%A8%E5%AF%B9%E5%81%B6%E6%80%8E%E6%A0%B7%E6%8A%8A%E9%9B%B6%E5%8F%B7%E5%9D%97%E7%9A%84%E8%A1%8C%E4%BB%A3%E4%BB%B7%E5%8F%98%E6%88%90%E4%B8%80%E4%B8%AA%E4%BD%99%E9%95%BF.md)

**Proposition.** Let $\mathcal O$ be a DVR with fraction field $K$, and let $p:C\times H\to K/\mathcal O$ be a bilinear pairing of $\mathcal O$-modules. Write $\operatorname{Ann}(J)=\{c:p(c,J)=0\}$ for $J\subseteq H$. For $I\subseteq F_s\subseteq H$,
$$
\operatorname{length}(\operatorname{Ann}(I)/\operatorname{Ann}(F_s))
\le\operatorname{length}(F_s/I).
\tag{1}
$$
A vector $c$ annihilating $I$ defines a functional on $F_s/I$ by $h+I\mapsto p(c,h)$. The kernel of this assignment is $\operatorname{Ann}(F_s)$, so the quotient injects into $\operatorname{Hom}_{\mathcal O}(F_s/I,K/\mathcal O)$. When $F_s/I$ has finite length, decompose it into cyclic modules $\mathcal O/(\varpi^n)$. Their duals are $(K/\mathcal O)[\varpi^n]$, of the same lengths. This proves (1), and the infinite-length case has infinite right side.

## Identifying the strict condition

Let $V,V'$ be $K$-spaces with subspaces $H_f,H'_f$, and $\mathcal O$-linear maps $q:V\to C$, $j:H\to V'$, where $H$ is finitely generated. Suppose $\langle\, ,\,\rangle:V\times V'\to K$ represents every $K$-linear functional on $V'$ by an element of $V$, with $H_f$ the left annihilator of $H_f'$. Suppose $p(q(a),h)=\langle a,j(h)\rangle\bmod\mathcal O$ and the left kernel of $p$ on $C$ is zero. Set $F_s=j^{-1}(H_f')$. Then $\operatorname{Ann}(F_s)=q(H_f)$.

Indeed the pairing formula proves inclusion of $q(H_f)$. For the reverse inclusion, take $x\in\operatorname{Ann}(F_s)$ and let $\psi:H\to V'/H_f'$ be induced by $j$. Then $p(x,-)$ descends to a functional on $\psi(H)$ with values in $K/\mathcal O$. The image is finitely generated and torsion-free, hence free. Lift the functional's values on an integral basis to $K$. That basis is linearly independent over $K$ by clearing denominators, so the lift extends to a $K$-linear functional on $V'/H_f'$. Pull back to $V'$ and represent by $a\in V$. It vanishes on $H_f'$, so $a\in H_f$, and the compatibility gives $p(q(a),h)=p(x,h)$ for all $h$. The left kernel condition implies $q(a)=x$.

## The row application

Here $H$ is local cohomology of the dual integral lattice and $C$ the chosen submodule on the zero-block side. The pairings are given by cup products and local invariants. The rational finite cohomology condition is orthogonal to the dual finite condition by local duality, and the comparison above identifies the strict condition on $C$. The submodule $I$ is the image of those dual finite classes admitting the specified integral lifts. The [cup-product argument](cup-product-descent-from-a-larger-module.md) shows that every produced zero-block class is orthogonal to $I$. Thus its relaxation cost is at most $A_w=\operatorname{length}(F_s/I)$ in each row.

## Lean correspondence

- `annColength` proves (1) using `matlis` for the length of the dual. `rowBK` and `rowRhoReal` give the two pairings and the strict condition. [Colength](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/LengthEqKerAddRange.lean#L127) · [Strict condition](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/CharacterSplitJumps/CharacterJumpProofs/PropLocBK.lean#L114) · [Local pairing](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/RealClassMaps/RealClassMapProofs/RowChiReal.lean#L16)
- `rowRho` and `bridgeRho` use the cup-product vanishing and the colength in the row estimate. [Row estimate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/CoprimeLiftBounds/CoprimeLiftProofs/LengthMapQuotLe.lean#L25) · [Rows](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/CoprimeLiftBounds/CoprimeLiftProofs/Bridge.lean#L14)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
