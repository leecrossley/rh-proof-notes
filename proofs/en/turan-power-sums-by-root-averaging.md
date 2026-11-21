# Turán power sums by rational functions and roots of unity

[Chinese proof](../zh/%E6%9C%89%E7%90%86%E5%87%BD%E6%95%B0%E5%92%8C%E5%8D%95%E4%BD%8D%E6%A0%B9%E6%80%8E%E6%A0%B7%E7%BB%99%E5%87%BATur%C3%A1n%E7%9A%84%E8%BF%9E%E7%BB%AD%E5%B9%82%E5%92%8C%E7%95%8C.md)

**Proposition.** Let $n\ge1$ and $m\ge0$ be integers. If $|z_i|\le1$ for $z_1,\ldots,z_n\in\mathbb C$ and at least one has modulus $1$, some integer $m+1\le k\le m+n$ satisfies
$$
\left|\sum_{i=1}^n z_i^k\right|\ge \left(\frac{n}{1600(m+n)}\right)^n.
\tag{1}
$$
This is the power-sum input in the [screening zero-repulsion argument](lossy-zero-repulsion-by-turan.md).

## Choosing the radius

For any list of $n$ real numbers $t_i$, center $b\in\mathbb R$, and $r>0$, there exists $|\rho-b|\le r$ with $\prod_i|\rho-t_i|\ge(r/25)^n$. Induct on $n$, starting with the empty product. Of the three disjoint open intervals of radius $2r/5$ centered at $b-4r/5,b,b+4r/5$, one contains $s\le n/3$ entries with repetitions. If its center is $b'$, use induction at radius $r/5$ about $b'$ for the $s<n$ entries within it. The other distances are at least $r/5$, so the total product is at least $(r/125)^s(r/5)^{n-s}=(r/25)^n5^{n-2s}\ge(r/25)^n$. The chosen $\rho$ remains within $r$ of $b$.

Apply this with $t_i=|z_i|$, $r=n/[6(m+n)]$, $b=1-2r$. Then $1-3r\le\rho\le1-r$ and $P=\prod_i|\rho-|z_i||\ge(r/25)^n>0$. Set $q_0=\lfloor(m+n)/n\rfloor$. Since $m+1\le q_0n\le m+n$ and $3q_0 r\le1/2$, Bernoulli's inequality gives $\rho^{q_0}\ge1/2$ and $\rho^{m+1}\ge2^{-n}$. Hence $\rho^{m+1}P\ge[n/(300(m+n))]^n$.

## A uniform bound from the consecutive coefficients

Put $p_k=\sum_i z_i^k$ and $B=[n/(1600(m+n))]^n$. Suppose all $n$ consecutive sums in (1) have modulus less than $B$. Write
$$
H(w)=\sum_i\frac{(z_iw)^{m+1}}{1-z_iw},\qquad Q(w)=\prod_i(1-z_iw)=\sum_{a=0}^n q_a w^a.
$$
We have $\sum_a|q_a|\le2^n$. The expression $QH/w^{m+1}$ is a polynomial of degree at most $n-1$. By expanding the geometric series on $|w|<1$, its coefficient of $w^b$ is $\sum_{a=0}^b q_a p_{m+1+b-a}$. Thus on $|w|=1/\rho$, $|QH|\le |w|^{m+1}n|w|^n2^nB$. The reverse triangle inequality gives $|Q(w)|\ge\rho^{-n}P$. We conclude that
$$
|H(w)|\le \frac{n2^n B}{\rho^{m+1}P}\le n(3/8)^n<1
\quad (|w|=1/\rho).
\tag{2}
$$

## The root-of-unity average

Set $u_i=z_i/\rho$, so no $|u_i|=1$ and at least one $|u_i|>1$. For integer $N>m+1$, put $\omega=e^{2\pi i/N}$. On the circle use
$$
\frac{(u_i\omega^j)^{m+1}}{1-u_i\omega^j}
=\frac{\sum_{\ell=0}^{N-1}(u_i\omega^j)^{m+1+\ell}}{1-u_i^N}.
$$
Averaging $j=0,\ldots,N-1$ retains the one exponent divisible by $N$, namely $N$. Thus the mean of $H(\omega^j/\rho)$ is $\sum_i u_i^N/(1-u_i^N)$. As $N\to\infty$, each summand tends to zero for $|u_i|<1$ and to $-1$ for $|u_i|>1$. The limiting absolute value is at least $1$, contradicting the uniform bound in (2). This proves (1).

## Lean correspondence

- `exists_far_from_points` and `prodDist` provide the radius, and `Tbound` and `tp_sum_norm` yield the bound on the rational function. [Radius](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/ExistsFarFromPoints.lean#L92) · [Rational function](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/HDSucc.lean#L28) · [Coefficient norm](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/TpCoeffNorm.lean#L54)
- `avgLimit` gives the root average, `turan2Main` closes the contradiction and `turan_power_sum_bound` sets the constants for screening. [Limit](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/RootNorm.lean#L112) · [Conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/Turan2Main.lean#L29) · [Screening input](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/TuranPowerSumBound.lean#L12)

The Chinese note records replay in Lean 4.33.1 of the radius choice, rational-function step, averaging step, two Turán statements, and the screening corollary. Their recorded axiom lists contain only `propext`, `Classical.choice` and `Quot.sound`. The proposition imposes only the stated conditions on the finite list of complex numbers.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
