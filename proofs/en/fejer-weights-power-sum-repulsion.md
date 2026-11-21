# A power-sum repulsion inequality from Fejér weights

[Chinese proof](../zh/Fej%C3%A9r%E6%9D%83%E6%80%8E%E6%A0%B7%E4%BB%8E%E5%B9%82%E5%92%8C%E6%89%BE%E5%87%BA%E9%9D%A0%E8%BF%91%E5%8D%95%E4%BD%8D%E5%9C%86%E7%9A%84%E9%A1%B9.md)

**Proposition.** Let $I$ be finite and let $z_i\in\mathbb C$, $b_i\in\mathbb Z_{\ge0}$ for $i\in I$. Let $L\ge1$, $\delta>0$, and $0\le x\le1/2$. Suppose $\sum_i b_i\le L$ and some term of positive weight satisfies $|z_i|\ge(1+x)^{-1}$. Assume for every integer $j\ge1$ that
$$
\Re\sum_i b_i z_i^j\le 2j\delta+L2^{-j}.
\tag{1}
$$
Then $x\ge \log(1/(CL\delta))/(CL)$ with $C=2080$.

## Weighting a point on the unit circle

For integer $J\ge0$ write $a_j=1-j/(J+1)$ for $1\le j\le J$, and $P_J(w)=\sum_{j=1}^J a_j\Re(w^j)$. If $|w|\le1$ and $S_J=\sum_{j=0}^J w^j$, then $S_{J+1}=1+wS_J$ gives
$$
|S_{J+1}|^2\le |S_J|^2+1+2\sum_{j=1}^{J+1}\Re(w^j).
$$
Sum from $|S_0|^2=1$ to obtain $0\le|S_J|^2\le(J+1)(1+2P_J(w))$, hence $P_J(w)\ge-1/2$. The sum of the weights gives $P_J(1)=J/2$.

Fix a real $\vartheta$ and put $c_j=a_j(1+\cos(j\vartheta))$, so $0\le c_j\le2$. Then
$$
F(w)=\sum_{j=1}^J c_j\Re(w^j)
=P_J(w)+\tfrac12 P_J(we^{i\vartheta})+\tfrac12 P_J(we^{-i\vartheta}).
$$
Thus $F\ge-1$ on the closed unit disk. At $w=e^{i\vartheta}$ the final argument equals $1$, yielding $F(e^{i\vartheta})\ge J/4-3/4$.

## Applying the weights to the normalized sum

Choose $z_{i_1}=Re^{i\vartheta}$ of maximal modulus among positive-weight terms, so $R\ge(1+x)^{-1}>0$. All $w_i=z_i/R$ of positive weight are in the disk. Summing $b_i(F(w_i)+1)\ge0$ and retaining the term $i_1$ gives $\sum_i b_i F(w_i)\ge J/4-L$. On the other hand each $c_j R^{-j}$ is nonnegative. Applying (1) and using $R^{-1}\le1+x\le3/2$ gives
$$
c_j R^{-j}\Re\sum_i b_i z_i^j
\le 4J\delta(1+x)^J+2L(3/4)^j.
$$
Summing and using $\sum_{j\ge1}(3/4)^j=3$, we get $J/4-7L\le4J^2\delta(1+x)^J$. Take $J=\lceil64L\rceil$, so $64L\le J\le65L$ and the left side is at least $J/8$. It follows that $1\le32J\delta(1+x)^J\le2080L\delta\,e^{xJ}$. Taking logarithms gives $\log(1/(2080L\delta))\le xJ\le2080Lx$, as required. The logarithm gives a positive lower bound when $\delta L$ is small.

## Lean correspondence

- `normSq_geomSum_le_fejer`, `fejer_re_ge` and `weighted_fejer_positivity` prove the Fejér bounds. [Geometric sum](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/WeightedFejerPositivity.lean#L6) · [Weighted bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/WeightedFejerPositivity.lean#L97)
- `powerSum_weighted_ineq` applies (1) with these weights and `powerSum_repulsion` chooses $J$. [Comparison](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SumIccThreeQuartersPowLe.lean#L16) · [Conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SumIccThreeQuartersPowLe.lean#L129)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
