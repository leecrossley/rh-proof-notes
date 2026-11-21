# Preserving the relative error in a zero sum with logarithmic losses

[Chinese proof](../zh/%E9%9B%B6%E7%82%B9%E5%AF%86%E5%BA%A6%E5%B8%A6%E5%AF%B9%E6%95%B0%E6%8D%9F%E5%A4%B1%E6%97%B6%E6%80%8E%E6%A0%B7%E4%BF%9D%E4%BD%8F%E7%9B%B8%E5%AF%B9%E8%AF%AF%E5%B7%AE.md)

Fix the absolute constant $0<c_Z\le1/20$ and the exceptional choice $e_M$ from the [relative prime number theorem](relative-prime-number-theorem-two-ranges.md#the-chosen-zero-and-the-prime-power-error). In particular, a zero in $\Re s\ge1-c_Z/\log(M(|\Im s|+2))$ is unique and simple across all characters modulo $M$, and is selected as $e_M$ if it exists. Put $\eta=\min(1,(1-\beta)\log M)$ if $e_M=(\chi_1,\beta)$ and $\eta=1$ if $e_M$ is empty.

**Proposition.** There is $0<\kappa\le1/20$ such that for every real $C_1$ and $A_1\ge1$ there are $c,C,C_0>0$ with the following property. Let $M$ be positive with $8\mid M$. For each $\chi\bmod M$, let $Z_\chi$ be a finite set of zeros of $L(s,\chi)$, excluding the principal pole, all with $\Re\rho>1-\kappa$ and $|\Im\rho|\le M^{A_1}+1$. Assign natural weights $m_\chi(\rho)\ge1$, equal to $1$ whenever $L'(\rho,\chi)\ne0$. Suppose that for every real $t$ and every $\chi$,
$$
\sum_{\rho\in Z_\chi,\ |\Im\rho-t|\le1}m_\chi(\rho)\le C_1\log(M(|t|+2)).
$$
Then for every $y\ge2$ with $\log y\ge C_0\log M\log(\log M+2)$,
$$
\sum_\chi\sum_{\rho\in Z_\chi}
\bigl(m_\chi(\rho)-\mathbf1_{(\chi,\rho)=e_M}\bigr)y^{\Re\rho-1}
\le C\eta e^{-c\log y/\log M}.
\tag{1}
$$
The indicator is zero throughout if $e_M$ is empty.

## Density and repulsion inputs

The project statement `LogDensityM` supplies absolute $a\ge1$, $B\ge0$ and $C_D\ge1$. For $M\ge3$, $T\ge2$, $\sigma\ge1/2$, every finite set of pairs $(\chi,\rho)$, with $\chi$ modulo $M$, $\rho$ a zero with $\Re\rho\ge\sigma$ and $|\Im\rho|\le T$, has at most $C_D(MT)^{a(1-\sigma)}\log^B(MT)$ elements if the heights of any two distinct elements with the same character differ by at least $1$. This is a [density bound for separated pairs](log-density-from-dyadic-counting.md).

The statement `DeuringHeilbronnMB` supplies absolute $\kappa_0,c_1,c_2>0$ and an integer $N_0\ge1$ (the proof takes $3$). Let $L=\log(MT)$ for $M\ge3,T\ge2$. If $\chi_1$ is nonprincipal and real modulo $M$ and $L(\beta,\chi_1)=0$ with $1-c_1/L<\beta<1$, then every other pair $(\chi,\rho)$ of a character and a zero with $\Re\rho\ge1-\kappa_0$ and $|\Im\rho|\le T$ satisfies
$$
L(1-\Re\rho)\ge c_2\log\frac{c_1}{(1-\beta)L^{N_0}}.
\tag{2}
$$
This version uses the [Turán power-sum repulsion argument](../zh/Tur%C3%A1n%E5%B9%82%E5%92%8C%E6%80%8E%E6%A0%B7%E6%8E%A8%E5%87%BA%E5%B8%A6%E5%AF%B9%E6%95%B0%E6%8D%9F%E5%A4%B1%E7%9A%84%E9%9B%B6%E7%82%B9%E6%8E%92%E6%96%A5.md).

## From separated pairs to total multiplicity

Take $\kappa=\min(\kappa_0,1/20)$, $T=M^{A_1}+3$, $\ell=\log M$, and $L=\log(MT)$. Then $\ell\le L\le(A_1+2)\ell$. Let $V$ be the set of pairs from the $Z_\chi$ outside the $c_Z$ region. The only zero in that region, if selected, is simple and its coefficient in (1) vanishes. Dropping the subtraction for any chosen zero outside the region bounds the left side by $\sum_{(\chi,\rho)\in V} m_\chi(\rho)e^{-bu(\rho)}$, where $b=\log y/L$ and $u(\rho)=L(1-\Re\rho)\ge c_Z$.

For each $j=0,1,\ldots$, consider the layer $j<u\le j+1$. For each character and each integer $k$, choose a representative if $[k,k+1)$ contains the height of a zero in the layer. Partition the representatives by the parity of $k$. Within either parity the heights for the same character are separated by at least $1$. Use the density bound with $\sigma=\max(1/2,1-(j+1)/L)$ in both parts. The number of occupied cells is at most $2C_De^{a(j+1)}L^B$. All the zeros in each cell lie within distance $1$ in height of its representative, whose height satisfies $|\Im\rho|\le T-2$. Thus the total weight in a cell is at most $|C_1|L$. The total in layer $j$ is at most $2C_D|C_1|e^{a(j+1)}L^{B+1}$.

## Extracting the factor $\eta$

Choose $0<\tau\le1$ so that $u\ge c_2\log(1/\tau)$ throughout $V$ and $\tau\ll_{A_1}\eta L^{N_0}$. With no exception, take $\tau=1$ since $\eta=1$. If the selected $\beta$ lies outside the region, $(1-\beta)\log(2M)>c_Z$ implies $\eta\ge c_Z/2$, so again take $\tau=1$. If it lies inside but $(1-\beta)L\ge c_1$, use $\eta\ge\min(1,c_1/(A_1+2))$ and take $\tau=1$. In the remaining case (2) applies to every pair in $V$. Taking
$$
\tau=\min\left(1,\frac{(1-\beta)L^{N_0}}{c_1}\right)
$$
gives the required repulsion. Also $\tau\le\max(1,c_1^{-1})\eta L^{N_0}$ since $\ell\ge1$.

Increase $C_0$ so that $\log y\ge C_0\ell\log(\ell+2)$ implies $b\ge4(a+\log 2)$, $bc_2\ge4$, and $bc_Z/4\ge(B+1)\log L$. On layer $j$, bound the four factors of $e^{-bu}=(e^{-bu/4})^4$ using $u>j$, $u\ge c_2\log(1/\tau)$, and $u\ge c_Z$ twice. This gives
$$
e^{-bu}\le e^{-(a+\log 2)j}\tau L^{-B-1}e^{-bc_Z/4}.
$$
After multiplying by the layer weight bound and summing the resulting geometric series, we obtain $O(\tau e^{-bc_Z/4})$. Using the bound on $\tau$ gives
$$
O\left(\eta L^{N_0}\exp\left(-\frac{c_Z}{4(A_1+2)}\frac{\log y}{\ell}\right)\right).
$$
Increasing $C_0$ once more absorbs $L^{N_0}$ into half of this exponential decay. This proves (1) with the exceptional factor still present.

## Lean correspondence

- `density_norm` and `zeroSum_core` implement the normalized layers, the height cells, and the multiplicity sum. [Layer proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTZSum.lean#L240)
- `zero_sum_bound_lossy` chooses $\tau$ and absorbs the logarithmic factors. [Conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTZSumL.lean#L30)
- `DeuringHeilbronnMB` and `deuring_heilbronn_lossy` give (2). [Repulsion statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHBSt.lean#L11) · [Repulsion proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHB.lean#L13)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
