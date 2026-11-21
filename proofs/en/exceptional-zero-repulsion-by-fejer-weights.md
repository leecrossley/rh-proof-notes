# Deuring–Heilbronn repulsion from the Fejér power-sum bound

[Chinese proof](../zh/%E4%B8%80%E4%B8%AA%E4%BE%8B%E5%A4%96%E9%9B%B6%E7%82%B9%E6%80%8E%E6%A0%B7%E6%8A%8A%E5%85%B6%E4%BB%96%E9%9B%B6%E7%82%B9%E6%8E%A8%E7%A6%BB%E4%B8%80.md)

**Proposition.** There is an absolute $c>0$ such that the following holds. Let $q\ge1$, let $\chi_1,\chi$ be characters modulo $q$ with $\chi_1$ nonprincipal and $\chi_1^2=\chi_0$, and let $L(\beta,\chi_1)=L(\rho,\chi)=0$, where $\beta\in[1/2,1)$ is real and $1/2\le\Re\rho<1$. Suppose $\chi\ne\chi_1$, $\rho\ne\beta$, or $\operatorname{ord}_\beta L(s,\chi_1)\ge2$. For every real $L\ge \log(q(|\Im\rho|+2))$,
$$
1-\Re\rho\ge\frac cL\log\frac{c}{(1-\beta)L}.
\tag{1}
$$
The multiplicity alternative permits repulsion from a second copy of the exceptional zero.

## Positive Dirichlet coefficients

Put $t=\Im\rho$, and use $D_k$ from the [high log-derivative estimate](high-log-derivatives-from-nearby-zeros.md). The sum of the real parts of
$$
D_k(\chi_0;2),\quad D_k(\chi_1;2),\quad D_k(\chi;2+it),\quad D_k(\chi\chi_1;2+it)
$$
is nonnegative. Indeed nonunits contribute zero. On units the coefficient times $k!n^2/(\Lambda(n)(\log n)^k)$ when the weight is nonzero is $(1+\chi_1(n))(1+\Re(\chi(n)n^{-it}))\ge0$.

Use the high log-derivative proposition at the four indicated centers, with zero multisets $W_0,\ldots,W_3$ from the respective disks of radius $3$. Each multiset has at most $CL$ entries for a common absolute $C$. At the center $a$ for any one term with character $\psi$, take $j=k+1$ to obtain
$$
\Re D_{j-1}(\psi;a)+\Re\sum_{w\in W}(a-w)^{-j}
\le\mathbf1_{\psi=\chi_0}\Re(a-1)^{-j}+2CL\,2^{-j}.
\tag{2}
$$
On summing, nonnegativity permits dropping the $D$-sum.

## Canceling each principal pole with one copy of the real zero

Let $\delta=1-\beta>0$. For $a=2+iv$, both $A=(a-1)^{-1}$ and $B=(a-\beta)^{-1}$ have modulus at most $1$. Since $A-B=\delta AB$, the difference of powers satisfies $|A^j-B^j|\le j\delta$. Whenever a principal character is paired at the same height with $\chi_1$ and $\beta$ lies within the companion radius-$3$ disk, delete one copy of $\beta$ from the multisets on the left of (2). The corresponding pole minus that copy costs at most $j\delta$. If $\beta$ is outside the companion disk, then $|a-1|\ge |a-\beta|-\delta>3-1/2>2$, so the pole is already at most $2^{-j}$ in modulus. Either case costs at most $j\delta+2^{-j}$.

At $2$ pair $\chi_0$ with $\chi_1$. At $2+it$, if there is a principal character, its companion is $\chi_1$: the two possibilities are $\chi=\chi_0$ and $\chi=\chi_1$. The target $\rho$ lies within $3/2$ of $2+it$, so it belongs to $W_2$. If the deletion from $W_2$ were $\rho$, we would have $\chi=\chi_1$ and $\rho=\beta$, in which case the multiplicity hypothesis leaves another copy.

## The repulsion inequality

For each remaining entry $w$ take the reciprocal $(a-w)^{-1}$ with its own center and form their multiset $Y$. With $L_*=(8C+4)L\ge1$, the multiset has size at most $4CL\le L_*$, and (2) with both pole comparisons gives
$$
\Re\sum_{y\in Y}y^j\le 2j\delta+(8CL+2)2^{-j}
\le2j\delta+L_*2^{-j}.
$$
One surviving term is $(2+it-\rho)^{-1}=1/(1+x)$ with $x=1-\Re\rho\in(0,1/2]$. Apply the [Fejér power-sum inequality](fejer-weights-power-sum-repulsion.md) with $L_*,x,\delta$. It gives $x\ge\log(1/(2080L_*\delta))/(2080L_*)$. Take $c=1/(2080(8C+4))$ to obtain (1). The [relative progression estimate](relative-prime-power-error-in-progressions.md) uses (1) when $\delta L$ is small.

## Lean correspondence

- `pole_pair`, `pole_far` and `der_pos` give the comparison, the far bound and positivity. [Pole comparison](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/Repulsion.lean#L49) · [Far bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/Repulsion.lean#L70) · [Positivity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/Repulsion.lean#L107)
- `exists_list` and `exists_erase` organize the multisets. `power_step` applies `powerSum_repulsion` and `repulsion` gives (1). [Lists](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/Repulsion.lean#L164) · [Deletion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/Repulsion.lean#L204) · [Conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/Repulsion.lean#L246) · [Forwarding statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/RepulsionStatement.lean#L8)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
