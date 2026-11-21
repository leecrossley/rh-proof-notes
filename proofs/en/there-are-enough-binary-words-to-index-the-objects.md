# There are enough binary words to index the objects

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E4%BA%8C%E8%BF%9B%E5%88%B6%E5%AD%97%E8%B6%B3%E5%A4%9F%E7%BB%99%E6%89%80%E6%9C%89%E5%AF%B9%E8%B1%A1%E7%BC%96%E5%8F%B7.md)

## Statement

Fix $0<\varepsilon<1/52$ and $C_\Gamma,C_H\ge0$, and set $K_0=2(2+256C_\Gamma+C_H)+2$. Let $x\ge K_0^{1/\varepsilon}$ with positive integers $n,m,k$ satisfying $n\le2x^{2+8\varepsilon}$, $m\le2x^{1/2-\varepsilon/16}$, and $k\ge x^{9/2+10\varepsilon}$. With $f=2n$, $L=x^\varepsilon$, $\Gamma=\exp(C_\Gamma m^5 fL)$ and $M=\lceil3\Gamma^2 x^{C_H}\rceil$, one has $M>0$ and an injection of $M$ objects into binary words of length $k-2$.

## Proof

Put $X=x^{9/2+9\varepsilon}$. Multiplying the bounds gives $m^5 fL\le128 X$. Since $X\ge x>1$,
$$
\log(3\Gamma^2x^{C_H})\le2+(256C_\Gamma+C_H)X.
$$
But $k\ge K_0 X$, so $(k-2)/2$ is at least this expression by $X\ge1$. Since $\log2\ge1/2$, this proves $3\Gamma^2x^{C_H}\le2^{k-2}$. The right-hand side is an integer, so rounding gives $0<M\le2^{k-2}$. Choose $M$ distinct words from the $2^{k-2}$ available.

In `kitS` the injection is selected once for the common host data then used on all $n$ rows. Changing the row with the word index fixed preserves the bits as in `Kit.eW_code`. The rank lemma uses a slightly weaker $n\le2x^{2+8\varepsilon+\varepsilon/100}$, still giving $128X$. See the [assembly of row data](assembling-a-window-family.md).

## Lean correspondence

- [`m_pow_five_mul_f_mul_L_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MPowFiveMulFMulLLe.lean#L10) and [`exists_injective_words`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MPowFiveMulFMulLLe.lean#L40) give the capacity. [`RankVal`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/PairRowIffQdRows.lean) supplies the rank ranges.
- [`kitS`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/KitS.lean) chooses the shared injection.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
