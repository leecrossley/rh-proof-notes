# Idèle norm shifts give disjoint theta characters

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Suppose $E/F$ is a CM number field with $F$ its maximal real subfield, unramified at every finite place. Fix a complex embedding $\tau_v$ above each real place $v$ of $F$ and a split finite place $w_0$ of $E$. Let $n\ge0$ be even, $t\ge1$ be odd, and $b\in\mathbb Z$. There are two pairs of unitary Hecke characters $(\chi_{X,j},\chi_{W,j})$, $j=0,1$, restricting to $\eta_{E/F}^n$ and $\eta_{E/F}^{n+t}$ on the ideles of $F$. Write $m_{X,j}(v)$ and $m_{W,j}(v)$ for their angular exponents at $\tau_v$. There are also an algebraic Hecke character $\kappa$ of infinity type $m$ and algebraic characters $\psi_{j,i}$ of types $p_{j,i}$ for $0\le i<t$, such that $m_{W,j}(v)\le b$ for every $v,j$ and
$$
\begin{aligned}
2m(\tau_v)&=m_{W,j}(v)-m_{X,j}(v)+t,&
2m(\bar\tau_v)&=m_{X,j}(v)-m_{W,j}(v)+t,\\
2p_{j,i}(\tau_v)&=m_{X,j}(v)+2i-(n+2t-2),&
2p_{j,i}(\bar\tau_v)&=-m_{X,j}(v)+2i-(n+2t-2).
\end{aligned}
$$
No $\psi_{0,i}$ equals any $\psi_{1,i'}$, and $\kappa$ and all $\psi_{0,i}$ are unramified at $w_0$. At any finite $w$ at which $\kappa$ and every $\psi_{j,i}$ are unramified, $\chi_{X,j}$ and $\chi_{W,j}$ are unramified and the uniformizer values satisfy
$$
\kappa(w)=\frac{\chi_{W,j}(w)}{\chi_{X,j}(w)}q_w^{-t/2},
\qquad
\psi_{j,i}(w)=\chi_{X,j}(w)q_w^{(n+2t-2)/2-i},\qquad q_w=\#k_w.
$$
These properties constitute `ChrPairs`. The character $\eta_{E/F}$ is the quadratic norm character of $E/F$. The prescribed infinity type uses the positive exponents of the character on archimedean ideles, so the corresponding Galois jump has the opposite sign. [Character dictionary and the pair statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/SplitLineSubtraction/TwoUpOKOf.lean#L14)

## An angular character and its two-parameter family

Take a unitary Hecke character $\mu$ of $E$ with restriction $\eta_{E/F}$, unramified at $w_0$, and archimedean character
$$
(z_v)_v\longmapsto \prod_v (z_v/|z_v|)^{-1}
$$
at the chosen embeddings. The [adelic construction](prescribing-a-unitary-hecke-characters-angular-exponents.md) gives it with these prescribed exponents. The source reads $\mu$ as a character $\chi$ of the relative ideles using their natural identification with the ideles of $E$. This preserves the finite local characters and the angular exponents. [Prescribing the exponents at the chosen embeddings](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/IdeleNormCharacters/ConjDivNorm.lean#L30) · [Reading the local characters and the norm shifts](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/IdeleNormCharacters/ChrExPf.lean#L75)

Let $|\cdot|_{\mathbb A_E}$ be the idèle norm, so on a uniformizer idèle at $w$ it gives $q_w^{-1}$ and at the complex places it gives $\prod_v|z_v|^2$. For $k\ge0$ and $s\in\mathbb Z$ write
$$
\Psi(k,s)=\mu^k|\cdot|_{\mathbb A_E}^{s/2}.
$$
The norm is trivial on $E^\times$ by the product formula. At any finite $w$, $\Psi(k,s)$ is unramified exactly when $\chi^k$ is, and its uniformizer value is $\chi(w)^k q_w^{-s/2}$. At infinity its factor at $v$ is $(z_v/|z_v|)^{-k}|z_v|^s$. If $s+k$ is even, this equals $z_v^{(s-k)/2}\bar z_v^{(s+k)/2}$. Thus $\Psi(k,s)$ is algebraic of these two exponents. The unitary character $\chi^k$ has angular exponent $-k$ and restricts to $\eta_{E/F}^k$, which depends only on the parity of $k$. [Definition of the two-parameter family](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/IdeleNormCharacters/ChrExPf.lean#L11) · [Local and archimedean formulas](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/IdeleNormCharacters/ChrExPf.lean#L73)

Equality of two characters $\Psi(k,s)$ and $\Psi(k',s')$ implies $k=k'$. Restrict to the circle at a single complex place, with all other idèle coordinates one. The norm factor drops out and the two restrictions are $z^{-k}$ and $z^{-k'}$. If $k\ne k'$ then $z=\exp(\pi\mathbf i/(k-k'))$ makes their ratio $-1$. The Lean proof of this step extends equality on principal infinite components by density to all tuples of complex numbers, and then varies one coordinate in this way. The Hecke characters themselves already agree on the archimedean ideles under the hypothesis. [Distinguishing the angular exponents](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/IdeleNormCharacters/ExpInj.lean#L62)

## Making the two pairs

Choose a positive odd $K$ with $-K\le b$, for example $K=2|b|+1$. For $j=0,1$ and $0\le i<t$ set
$$
\chi_{X,j}=\chi^{2j},\qquad
\chi_{W,j}=\chi^{K+2j},\qquad
\kappa=\Psi(K,t),\qquad
\psi_{j,i}=\Psi(2j,\,2i-(n+2t-2)).
$$
The first two powers have the same parity as $n$ and $n+t$, respectively. The target exponent is $-K-2j\le b$. The norm twists are algebraic because $K,t$ are odd and $n+2t-2$ is even. The exponent formulas follow by substitution in the two exponents of $\Psi(k,s)$, with $m_{X,j}=-2j$ and $m_{W,j}=-K-2j$. Distinctness across the lists follows from $2j=0$ versus $2j=2$. The required unramifiedness at $w_0$ follows from the same property for $\mu$. [Choice of exponents and parity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/IdeleNormCharacters/ChrPairsPf.lean#L26)

At a place $w$ with the stated unramifiedness, $\chi^K$ is unramified because $\kappa$ is, and $\chi^{2j}$ is unramified because $\psi_{j,0}$ is. The index $0$ exists since $t$ is odd. Their product is $\chi^{K+2j}$, so both source and target characters are unramified. Their values satisfy $\chi_{W,j}(w)/\chi_{X,j}(w)=\chi(w)^K$, which gives the formula for $\kappa(w)$. The formula for $\psi_{j,i}(w)$ is the norm factor with $s=2i-(n+2t-2)$. The same $\kappa$ works in both dictionaries. [The common twist at the finite places](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/IdeleNormCharacters/ChrPairsPf.lean#L78) · [Instantiation of the construction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/IdeleNormCharacters/ChrPairsHolds.lean#L15)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
