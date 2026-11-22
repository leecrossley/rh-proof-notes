# An invariant trace extends a representation across index two

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Let $G$ be a topological group, $K$ an algebraically closed topological field of characteristic zero, and $\eta:G\to\{1,-1\}$ a character with open kernel $H$. Let $r:H\to\mathrm{GL}_n(K)$ be continuous and semisimple, with $n\ge0$. Suppose its trace is invariant under $G$-conjugation on $H$:
$$
\operatorname{tr}r(ghg^{-1})=\operatorname{tr}r(h)
\qquad(g\in G,\ h\in H).
$$
Then $r$ extends to a continuous semisimple representation of $G$ in the same basis. This is `GlobalTheory.IndexTwoExt.main`. [Exact extension theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsExtensionRepIndexTwoOfTraceInvariant.lean#L193)

## Correcting the conjugating matrix

If $H=G$ take $r$ itself. Otherwise choose $t\in G\setminus H$ and put $c(h)=tht^{-1}$. The representations $r$ and $r\circ c$ are semisimple with equal traces, hence isomorphic by the [semisimple character criterion](a-cross-multiplied-polynomial-identity-splits-off-character-lines.md#finding-an-invariant-line). Choose $P$ with $r(c(h))=P r(h)P^{-1}$ for every $h$. The extension requires the action of $t$ to square to $r(t^2)$. The matrix $P$ satisfies the conjugacy requirement, and $P$ commutes with $r(t^2)$ since $c(t^2)=t^2$. Applying the conjugacy requirement twice gives
$$
P^2r(h)P^{-2}=r(t^2)r(h)r(t^2)^{-1}.
$$
Consequently $M=P^{-2}r(t^2)$ commutes with $P$ and with every $r(h)$. It is invertible. [Intertwiner and its defect](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsExtensionRepIndexTwoOfTraceInvariant.lean#L221)

There is a polynomial $f\in K[X]$ with $f(M)^2=M$. To see this, for each nonzero eigenvalue $z$ of $M$ choose a square root $\beta_z$. Modulo $(X-z)^s$, where $s$ is the multiplicity in the characteristic polynomial, take
$$
 f_z(X)=\beta_z\sum_{j=0}^{s-1}\binom{1/2}{j}\left(\frac{X-z}{z}\right)^j .
$$
Its square is $X$ modulo $(X-z)^s$, by the formal binomial identity truncated at degree $s-1$. The Chinese remainder theorem gives a polynomial with each of these residues. The characteristic polynomial divides $f(X)^2-X$, so evaluating by Cayley–Hamilton proves the assertion. The source obtains the same polynomial square root by lifting from one linear factor at a time. As a polynomial in $M$, $D=f(M)$ commutes with both $P$ and $r(H)$. It is invertible since its square is. Thus $B=PD$ still satisfies $Br(h)B^{-1}=r(c(h))$, and $B^2=P^2D^2=r(t^2)$. [Polynomial square root preserving commutation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsExtensionRepIndexTwoOfTraceInvariant.lean#L108) · [Corrected intertwiner](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsExtensionRepIndexTwoOfTraceInvariant.lean#L264)

## Constructing and checking the extension

Define $\rho(h)=r(h)$ and $\rho(ht)=r(h)B$ for $h\in H$. These formulas cover the two cosets. The relations $Br(h)=r(c(h))B$ and $B^2=r(t^2)$ are exactly those needed to multiply two expressions in coset form. In particular $(h_1t)(h_2t)=h_1c(h_2)t^2$ maps to the product of their matrices. Hence $\rho$ is a representation. It is continuous on both open cosets since the action on $H$ is continuous and multiplication by $t$ and $B$ are homeomorphisms. [Multiplication in the two cosets](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsExtensionRepIndexTwoOfTraceInvariant.lean#L282)

Finally, let $W$ be any $\rho(G)$-invariant subspace. Semisimplicity on $H$ gives an $H$-equivariant projection $p$ onto $W$. The operator
$$
q=\tfrac12(p+BpB^{-1})
$$
is a projection onto $W$ because each summand has image in $W$ and restricts to the identity there. It commutes with $r(H)$ by normality of $H$ and with $B$ because $B^2=r(t^2)$ commutes with $p$. Its kernel is therefore a $G$-invariant complement. This proves semisimplicity of the extension. [Averaging the projection across the two cosets](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsExtensionRepIndexTwoOfTraceInvariant.lean#L12)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
