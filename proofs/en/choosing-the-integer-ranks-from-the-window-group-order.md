# Choosing the integer ranks from the window group order

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E4%BB%8E%E7%AA%97%E5%8F%A3%E7%9A%84%E7%BE%A4%E9%98%B6%E9%80%89%E5%87%BA%E5%90%88%E7%94%A8%E7%9A%84%E6%95%B4%E6%95%B0%E7%A7%A9.md)

## Statement

Use a frame consisting of a finite additive abelian $A$ of order $n$, $e\ge0$, a surjection $A\to(\mathbb Z/2^{e+2}\mathbb Z)^\times/\{\pm1\}$ and $a_0\in A$ whose multiples mapping to identity are zero. Given $0<\varepsilon<1/52$, $x\ge16$, $x^{2+8\varepsilon}\le n\le2x^{2+8\varepsilon}$, and scale data with $J\ge1$, the same frame extends by $k,m$ even, $t$ odd and $r=k+m-1$, satisfying
$$
2\le m,\quad m+3\le k,\quad r+5\le t,\quad 3m<t,\quad
m\le2n\le k,\quad m^2\le k+m(t+1),
$$
and
$$
\begin{gathered}
x^{(1-\varepsilon/8)/2}\le m\le2x^{(1-\varepsilon/8)/2},\qquad
x^{9/2+10\varepsilon}\le k\le2x^{9/2+10\varepsilon},\\
r+t=8fr+4+TB,\quad f=2n,\quad T=\lceil x^{377}\rceil,\qquad
B=8\left\lceil\frac{10r}{8}\left(f+\frac{f^2(k-1)^3 x^{2\varepsilon}}m\right)\right\rceil.
\end{gathered}
$$
These are `Ranks` and `RankVal`.

## Integer choices and the upper window

For $u\ge2$, $2\lceil u/2\rceil$ is even and belongs to $[u,2u]$. Apply it to the two lower endpoints, using $x^{(1-\varepsilon/8)/2}\ge x^{1/4}\ge2$, and obtain $2\le m\le2x$, $k\ge x^4$. Since $x^2\le n\le2x^3$, this gives $m\le2n$, $2n\le4x^3\le k$, and $m+3\le2x+3\le k$. Put $t=8fr+4+TB-r$. Then $r$ is odd and $B$ divisible by eight, so $t$ is odd. Since $t\ge7r+4$ and $r\ge2m+2$, we have $t\ge r+5$, $t>3m$, and $t+1\ge m$, giving the remaining conditions. The same construction for any $T,W\in\mathbb N$ with $B=8W$ is `exists_ranks_of_frame`.

For any such `RankVal` with $x\ge2^{100}$, put $Y=x^{1/100}\ge2$. The exponent ranges give $f\le4Y^{216}$, $k\le2Y^{470}$, $m\ge Y^{49}$, $x^{2\varepsilon}\le Y^4$ and $r\le4Y^{470}$. Thus $f^2(k-1)^3x^{2\varepsilon}/m\le128Y^{1797}$, and rounding gives $B\le5288Y^{2267}$ after adding $f$. With $T\le2Y^{37700}$, the bound is
$$
t\le128Y^{686}+4+10576Y^{39967}
\le10708Y^{39967}\le Y^{40000}=x^{400},
$$
using $10708\le2^{33}$. This places $t$ within the common length window.

## Using the ranks in the host data

The additional input `HostAx` specifies $q,d$, the cyclotomic modulus $Q_Sqd$, a CM field $E$, its Galois and Artin data, CM type, and relative different factorization. The theorem `admissibleClassesTwistedChar` gives these ranks and `admitted` for the given data. For every $b$ and admitted `Choices`, if `FieldRows` and $q,d>4tr+1$ hold, there is a host with the same field data, small-prime threshold $b$, and auxiliary choices. Indeed `FieldRows` supplies an element squaring to $-q$ and its Galois action. The CM type has size $2n>0$, supplying one embedding, and `HostAx` supplies the factors of the different. Together with the prime bounds and choices these are the fields to fill. The `FieldRows` inputs include the first Artin sign given by the quadratic character modulo $q$, strict conductor conditions at each prime of $Q_S$, $Q_S\le n^2$, $[A:\langle a_0\rangle]^{64}\le2^e$, $q\ne3$, and the small-prime splitting and $4\ell\le b$ conditions for $d$.

## Lean correspondence

- [`exists_even_between`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsRanksRankValFrame.lean#L10), [`exists_ranks_of_frame`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsRanksRankValFrame.lean#L24) and [`exists_ranks_rankVal_frame`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsRanksRankValFrame.lean#L45) choose the ranks for a given frame. [`Ranks`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalRingCardinality/Params.lean) and [`RankVal`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/PairRowIffQdRows.lean) specify their bounds.
- [`eventually_rank_le_rpow_of_lt_one_div_fiftytwo`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/EventuallyRankLeRpowOfLtOneDivFiftytwo.lean#L5) gives $x^{400}$.
- [`admissibleClassesTwistedChar`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CoprimeRanks/AdmChi.lean#L13), [`FieldRows` and `Choices`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CoprimeRanks/SecondSetNoRelation.lean) and [`exists_host`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CoprimeRanks/SecondSetNoRelation.lean#L100) give the additional host assembly.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
