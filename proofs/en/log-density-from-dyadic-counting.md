# The fixed-modulus log-density bound from dyadic counting

[Chinese proof](../zh/%E7%AD%9B%E9%80%89%E7%94%A8%E7%9A%84%E9%9B%B6%E7%82%B9%E5%AF%86%E5%BA%A6%E6%80%8E%E6%A0%B7%E4%BB%8E%E4%BA%8C%E5%80%8D%E5%8C%BA%E9%97%B4%E8%AE%A1%E6%95%B0%E5%BE%97%E5%88%B0.md)

**Proposition.** There is an absolute $C>0$ such that for every integer $M\ge3$, $T\ge2$, and $\sigma\ge1/2$, the following holds. Let $S$ be a finite set of pairs $(\chi,\rho)$ with $\chi\bmod M$, $L(\rho,\chi)=0$, $\Re\rho\ge\sigma$, and $|\Im\rho|\le T$. Exclude the principal pole at $1$. Suppose distinct points for the same character differ by at least $1$ in height. Then
$$
|S|\le C(MT)^{24(1-\sigma)}\log^{10}(MT).
\tag{1}
$$
This is the `LogDensityM` input used in the [weighted zero sum](weighted-zero-sum-with-logarithmic-losses.md).

## Large values on one block

For positive integers $Y,N$, put $a_{Y,N}(n)=\sum_{d\mid n,\ d\le Y,\ n/d\le N}\mu(d)$ and $B_{Y,N,U}(\chi,s)=\sum_{U<n\le2U}a_{Y,N}(n)\chi(n)n^{-s}$ for integer $U\ge1$. We have $|a_{Y,N}(n)|\le d(n)$. Counting ordered divisor pairs gives
$$
\sum_{n\le V}d(n)^2=\sum_{d,e\le V}\left\lfloor\frac V{\operatorname{lcm}(d,e)}\right\rfloor\le V(1+\log V)^3.
$$
For the inequality write $d=gu$, $e=gv$ with $g=\gcd(d,e)$, so the denominator is $guv$. Extending each of the three sums to all positive integers at most $V$ gives three harmonic factors. Thus for $b_n=a_{Y,N}(n)n^{-\sigma}$ on the block,
$$
A=\sum_{U<n\le 2U}|b_n|^2\le2U^{1-2\sigma}(1+\log(2U))^3.
\tag{2}
$$

For $p=(\chi,\rho)$ write $v_{p,n}=\chi(n)n^{-(\rho-\sigma)}$ on the block and $G_{p,p'}=\sum_n v_{p,n}\bar v_{p',n}$. We claim the absolute row sum is $O(U\log(2T+1)+|S|MT)$. The diagonal has modulus at most $U$. In the other entries the exponent is $w=\rho-\sigma+\overline{\rho'-\sigma}$, with $0\le\Re w\le1$ and $|\Im w|\le2T$. If the characters differ, their product with one conjugated is nonprincipal and sums to zero over a period. Its partial sums are $O(M)$ and partial summation using $|(x^{-w})'|\le |w|/U$ bounds the entry by $O((M+1)(1+|w|))$. If the characters coincide, subtract the period mean $\varphi(M)/M$ and bound the zero-mean part in the same way. The mean part is a multiple of $\int_U^{2U}x^{-w}dx$ with error $O(1+|w|)$ by summing the integrated derivative over unit intervals. The integral has modulus at most $4U/|\Im w|$ from its antiderivative. For fixed $p$, on either side of its height there is at most one same-character point at distance in $[j,j+1)$ for each $j\ge1$. This bounds the reciprocal sum by $O(\log(2T+1))$ and proves the row estimate.

Suppose $S'\subseteq S$ and $|B_p|=|\sum_n b_n v_{p,n}|\ge\theta>0$ for $p\in S'$. Apply Cauchy–Schwarz to $\sum_p|B_p|^2=\sum_n b_n\sum_p\bar B_p v_{p,n}$. The square of the second norm is a Gram quadratic form, bounded above by $\sum_p|B_p|^2$ times the largest absolute row sum, using $|B_p B_{p'}|\le(|B_p|^2+|B_{p'}|^2)/2$. It follows that $\theta^2|S'|\le C A(U\log(2T+1)+|S'|MT)$. If $C A MT\le\theta^2/2$, absorb the last term and use (2):
$$
|S'|\ll \theta^{-2}U^{2-2\sigma}(1+\log(2U))^3\log(2T+1).
\tag{3}
$$
The same bound holds for the principal-character points measured using the constant character modulo $1$, since the same-character row calculation then uses period mean $1$.

## Finding the blocks at zeros

Set $X=\lceil MT\rceil$, $Y=X^3$, $J=8(\lfloor\log_2 X\rfloor+1)$, and $N=2^J$, so $X^8\le N\le(2X)^8$ and $J\ll\log X$. Work first with $\sigma\ge3/4$.

For a nonprincipal zero $\rho$, the [partial-summation estimate](mobius-truncation-detecting-zeros.md#nonprincipal-characters) bounds the sum $\sum_{n\le N}\chi(n)n^{-\rho}$ by $2(M+1)(1+|\rho|/\Re\rho)N^{-\Re\rho}$. Multiply by $\sum_{d\le Y}\mu(d)\chi(d)d^{-\rho}$, of modulus at most $Y$. Since $1+|\rho|/\Re\rho\le3T$ and $N^{-3/4}\le X^{-6}$, the product has modulus at most $8/X^2\le1/2$. Since $Y\le N$, the coefficients below or at $Y$ are the full divisor sums of $\mu$, so the product is $1+\sum_{Y<n\le YN}a_{Y,N}(n)\chi(n)n^{-\rho}$. At least one of the $J$ blocks $U=Y2^j$ must have modulus at least $1/(2J)$.

For a principal zero with $\Re\rho>0$, the extra Euler factors are nonzero, so $\zeta(\rho)=0$. Write $P(K)=\sum_{n\le K}n^{-\rho}$ and $z=2^{1-\rho}$. The initial $2N$ terms of the alternating series are $P(2N)-zP(N)$. Its full sum is $(1-z)\zeta(\rho)=0$, by continuation from the absolutely convergent region using the locally uniform alternating series in $\Re s>0$. Its coefficients have bounded partial sums. By partial summation after multiplication by the truncated Möbius series we obtain
$$
\left|(P(2N)-zP(N))\sum_{d\le Y}\mu(d)d^{-\rho}\right|
\le4(1+|\rho|/\Re\rho)N^{-\Re\rho}Y\le12/X^2.
$$
Writing the two truncated products as $1+E_1$ and $1+E_2$, we have $|1-z|\le12/X^2+|E_2|+2|E_1|$ since $|z|\le2$. The [principal zero-free region](three-four-one-zero-free-region.md#principal-zeros) gives $1-\Re\rho\ge c_*/(2\log X)$ for an absolute $c_*>0$. Thus $|1-z|\ge |z|-1\ge(1-\Re\rho)/2\ge c_*/(4\log X)$. For sufficiently large $X$, $12/X^2\le c_*/(8\log X)$. One of $E_1,E_2$ has modulus at least $c_*/(24\log X)$. Partition the corresponding remainder $(Y,YN]$ or $(Y,2YN]$ into at most $J+1$ dyadic blocks to find one of modulus at least $c_*/[24(J+1)\log X]$.

## Summing the block counts

For each block $X^3\le U$ and $2U\le 2YN\le X^{12}$ when $X\ge512$. For $\sigma\ge3/4$, (2) gives $AMT\ll X^{-1/2}\log^3 X$. Thus for large enough $X$, the smallness condition for (3) holds for both thresholds, of orders $(\log X)^{-1}$ and $(\log X)^{-2}$. Since $X\le2MT$ and $3/4\le\sigma\le1$, $U^{2-2\sigma}\le64(MT)^{24(1-\sigma)}$. Equation (3) gives a log exponent $6$ for each nonprincipal block and $8$ for each principal block. There are $O(\log X)$ blocks in the union of the possibilities, yielding the claimed log exponent $10$, with the calculation giving $9$ before the final relaxation.

For $\sigma<3/4$ use the separation to count at most $M(2T+1)\le3MT$, bounded by the right side of (1). For $X$ below the absolute threshold, the same trivial count is absorbed by enlarging the constant. If $\sigma>1$ the set is empty. This completes (1).

## Lean correspondence

- `divisor_square_bound`, `coefficient_block_bound`, `off_diagonal_bound`, `dyadic_block_count`, and `duality_inequality` give the block estimate. [Coefficients](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDensDiv.lean#L102) · [Counting](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDensBlock.lean#L164) · [Duality](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/CountZDual.lean#L9)
- `zero_detection_second` treats nonprincipal characters. `eta_partial_sums`, `principal_zeta_bound`, and `zero_detection_first` treat the principal case. `mollifier_identity` computes the truncated product. [Nonprincipal](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/ZeroDetectionSecond.lean#L16) · [Alternating sum](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDensLs.lean#L133) · [Principal](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/OneSubTwoCpowLower.lean#L59) · [Product](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/CountZMoll.lean#L79)
- `zero_count_first` and `zero_count_second` are combined with `trivial_bound` in `log_density_bound`. [Principal count](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/ZeroCountFirst.lean#L90) · [Nonprincipal count](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/SecondBlockCount.lean#L87) · [Conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDens.lean#L19)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
