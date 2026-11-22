# Two theta lifts share one twist and have disjoint added characters

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Let $E/F$ be a CM number field with maximal real subfield $F$, with $E/F$ unramified at every finite place. Assume $[F:\mathbb Q]$ is even and $E$ contains $x$ with $x^2=-D$ for a positive integer $D$. At every finite place $w$ of $E$ above a nonsplit place $v$ of $F$, assume $v\nmid2$, $\#k_v>3$, and the different of $F/\mathbb Q$ is not contained in the prime ideal of $v$. These are the field conditions of `TwoUpOK`. Take an even integer $n\ge1$, a definite unitary automorphic representation $U$ of rank $n$ with dominant weights $\lambda_\tau$ at each complex embedding $\tau:E\to\mathbb C$, and a finite split place $w_0$ of $E/F$. [Field conditions for even-rank ascent](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/AllCoreOf.lean#L12)

Assume the stable-range theta lifting, the existence of compatible Hermitian and skew-Hermitian spaces, and the two character dictionaries stated below. Also use the split local theta comparison stated in the proof. Then there are a positive odd integer $t$, a common algebraic Hecke character $\kappa$ of $E$ of infinity type $m$, and definite unitary automorphic representations $U_0,U_1$ of rank $n+t$. For each $j=0,1$, let $\lambda'_{j,\tau}$ be the weights of $U_j$ and let $(\psi_{j,i},p_{j,i})$ for $0\le i<t$ be algebraic Hecke characters with their integral infinity exponents. They have the following properties.

- No $\psi_{0,i}$ equals any $\psi_{1,i'}$. The character $\kappa$ and each $\psi_{0,i}$ are unramified at $w_0$.
- With $J(\lambda)=\{k-\lambda_k:0\le k<\operatorname{rank}(\lambda)\}$, one has
  $$
  J(\lambda'_{j,\tau})=(J(\lambda_\tau)+m(\tau))\sqcup\{-p_{j,i}(\tau):0\le i<t\}.
  $$
- At any split finite place $w$ where $\kappa$ and all $\psi_{j,i}$ are unramified, each Satake multiset $B$ for $U$ gives a Satake multiset $B'_j$ for $U_j$ with
  $$
  \operatorname{AlgSat}_{n+t}(B'_j)
   = \kappa(w)^{-1}\operatorname{AlgSat}_n(B)\ \sqcup\ \{\psi_{j,i}(w):0\le i<t\},
  \qquad
  \operatorname{AlgSat}_r(B)=q_w^{(r-1)/2}B.
  $$
  Here $q_w=\#k_w$, all unions are multiset sums, and an unramified character's value at $w$ is its uniformizer value in this normalization.

This is `twoUpOK_of_steps`. The two lists matter because an added character in one list can later be identified inside one odd-rank Galois representation and split off, using a polynomial identity with the other list. [The lift data and its two lists](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/SplitLineSubtraction/RowDefOfOdd.lean#L83) · [The ascent theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/TwoUpOKOfSteps.lean#L13)

## Choosing a common target rank

The Hermitian-space input `BaseNG` supplies a base $B_s$ with one complex embedding $\tau_v$ above each real place $v$ of $F$, a standard additive character of the adeles of $F$, an element $\delta$ and an integral lattice for its skew line. The base satisfies the unramified conditions on the additive character at inert places and at its specified finite exceptional set; the inert places also avoid $2$ and have residue size exceeding $3$. With the source form $I_n$ it supplies the standard positive Hermitian datum in every dimension $n$. With the target form $\delta I_d$ it supplies the standard skew-Hermitian datum in every dimension $d$. In the source these are the certified `IsHerm` and `IsSkew` models of signature parameters $(n,0)$ and $(d,0)$. The extra hypothesis that $x^2=-D$ promotes the base from `GoodNG` to `GoodK`. [Existence of both forms for one base](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/SplitLineSubtraction/TwoUpOKOf.lean#L67) · [Base conditions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/GoodLifts/OfIsGood.lean#L13) · [The additional quadratic field condition](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/HalfIndexLattices/SplitStab.lean#L15)

The theta-lift input `TLiftK` applies to this fixed source and gives a threshold $d_0$. For every $d\ge d_0$ with target of the stated skew form, it applies to any pair of Hecke characters $\chi_X,\chi_W$ of $E$ whose restrictions to the ideles of $F$ are $\eta_{E/F}^{n},\eta_{E/F}^{d}$, respectively. They must have the specified angular exponents $m_X(v),m_W(v)$ at the chosen embeddings. If
$$
d+m_W(v)\le 2(\lambda_{\tau_v})_k
\qquad\text{for every }v\text{ and }0\le k<n,
$$
the input gives a rank-$d$ automorphic lift with the archimedean formula and split local theta intertwiner used below. The order of these quantifiers lets us choose the characters *after* fixing one target rank. [Uniform threshold and the lift hypotheses](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/HalfIndexLattices/TLiftK.lean#L12) · [Weight and local intertwiner in the lift output](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/SchurStep.lean#L103)

Set $t=2(d_0+n)+1$ and $d=n+t$. Thus $t>n$, $d\ge d_0$, and $d$ is odd. There are finitely many pairs $(v,k)$, so choose an integer $b$ with $b\le(\lambda_{\tau_v})_k$ for every pair. Request the two dictionaries with upper bound $2b-d$ on $m_W(v)$. They use respective source and target characters $\chi_{X,j},\chi_{W,j}$ with the above restriction and exponent conditions. They give a common $\kappa,m$, characters $\psi_{j,i}$ with types $p_{j,i}$, the disjointness and unramifiedness in the statement, and the formulas in the following sections. By this upper bound, both dictionaries satisfy
$$
d+m_{W,j}(v)\le 2b\le 2(\lambda_{\tau_v})_k.
$$
We can therefore take the theta lift twice at the same $d$ and retain both dictionaries. [How the characters are chosen](idele-norm-shifts-give-disjoint-theta-characters.md) · [Character input with an arbitrary exponent bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/SplitLineSubtraction/TwoUpOKOf.lean#L28)

## Reading the weights at both embeddings

Fix one of the dictionaries and write $m_X,m_W$ for its exponents. At $\tau_v$, the theta lift gives a dominant weight $\lambda'$ of length $d$ governed by
$$
2\lambda'_k=
 \begin{cases}
 2\lambda_k-d-m_W+n+m_X,&0\le k<n,\\
 n+m_X,&n\le k<d .
 \end{cases}
$$
For $k<n$, it follows that $k-\lambda'_k=k-\lambda_k+(t+m_W-m_X)/2$. The last increment is $m(\tau_v)$ by the dictionary. For $k=n+i$, the padded jump is $(n-m_X)/2+i$. This is $-p_{t-1-i}(\tau_v)$, since the dictionary reads $2p_i(\tau_v)=m_X+2i-(n+2t-2)$. Reversing the padded indices leaves the multiset unchanged. [First weight identity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/SplitLineSubtraction/MapUnivAdd.lean#L20)

At the conjugate embedding $\bar\tau_v$, the weight is dual, meaning reverse the order and negate the entries. Its jumps can therefore be listed as $d-1-k+\lambda'_k$ with $k=0,\ldots,d-1$. For $k<n$, the difference from the original dual jump $n-1-k+\lambda_k$ is $(t+m_X-m_W)/2=m(\bar\tau_v)$. For $k=n+i$, the jump is $(n+m_X)/2+t-1-i=-p_i(\bar\tau_v)$, using $2p_i(\bar\tau_v)=-m_X+2i-(n+2t-2)$. Each complex embedding is exactly one of the two kinds, and the archimedean uniqueness of the original weights makes this calculation apply to the given family $\lambda_\tau$. This proves the full weight formula. [Using the assigned and conjugate embeddings](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/SplitLineSubtraction/UpOfHolds.lean#L10)

## Reading the split Satake parameters

At a split place $w$ impose the unramifiedness in the conclusion. Let $x_w=\chi_X(w)$, $y_w=\chi_W(w)$. The local dictionary implies that $\chi_X,\chi_W$ are unramified there and gives
$$
 \kappa(w)=y_w x_w^{-1}q_w^{-t/2},\qquad
 \psi_i(w)=x_w q_w^{(n+2t-2)/2-i}.
$$
The split local theta comparison used here says the following. Given the split local theta intertwiner of `IsLift`, with $d=n+t>n$, the two unramified characters and a spherical Satake multiset $B$ on the source of rank $n$, the target has multiset
$$
 B'=(x_w/y_w)B\ \sqcup\ \{x_w q_w^{(t-1)/2-i}:0\le i<t\}.
$$
It applies because a split chart for $w$ identifies the local groups with general linear groups, the two representations have compatible components in that chart, and the lift supplies the local intertwiner for those components. This Satake calculation is a further input; the pinned proof reduces it to the split local pairing. [Split chart, local lift and Satake input](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/SatakeLifts/LiftSatUPf.lean#L9) · [Local dictionary](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/SplitLineSubtraction/TwoUpOKOf.lean#L14)

Multiplying the original entries by $q_w^{(d-1)/2}$ yields $(x_w/y_w)q_w^{t/2}\operatorname{AlgSat}_n(B)=\kappa(w)^{-1}\operatorname{AlgSat}_n(B)$. Multiplying the padded entries by that power yields exactly $\psi_i(w)$. This gives the Satake formula with multiplicities. Applying the weight and Satake calculations to both lifts establishes all the asserted data. [Algebraic Satake normalization](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/SplitLineSubtraction/PSatId.lean#L23) · [Using one target rank and two dictionaries](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ThetaParseval/TwoUpOKOfSteps.lean#L22)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
