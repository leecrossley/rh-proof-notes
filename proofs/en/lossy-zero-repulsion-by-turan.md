# Zero repulsion with logarithmic losses from Turán's theorem

[Chinese proof](../zh/Tur%C3%A1n%E5%B9%82%E5%92%8C%E6%80%8E%E6%A0%B7%E6%8E%A8%E5%87%BA%E5%B8%A6%E5%AF%B9%E6%95%B0%E6%8D%9F%E5%A4%B1%E7%9A%84%E9%9B%B6%E7%82%B9%E6%8E%92%E6%96%A5.md)

**Proposition.** There are absolute $c_0,c_1,c_2>0$ with the following property. Let $M\ge3$ be an integer, $T\ge2$, and $L=\log(MT)$. Let $\chi_1$ be a nonprincipal real character modulo $M$ with a real zero $1-c_1/L<\beta<1$. Let $\rho$ be a zero for a character $\chi\bmod M$ with $\Re\rho\ge1-c_0$, $|\Im\rho|\le T$, and $(\chi,\rho)\ne(\chi_1,\beta)$, excluding the principal pole. Then
$$
(1-\Re\rho)L\ge c_2\log\frac{c_1}{(1-\beta)L^3}.
\tag{1}
$$
The project statement `DeuringHeilbronnMB` allows an existential natural exponent on $L$. The proof takes $3$, which feeds into the [weighted zero sum](weighted-zero-sum-with-logarithmic-losses.md).

## Local reciprocal powers and their first moment

Put $\lambda=1-\beta$, $t=\Im\rho$, and $\ell=\log(3M)$. For $0<h\le2/25$, write $s_0=1+h$, $s_1=1+h+it$, and use the normalized series
$$
D_j(\psi;s)=\frac{1}{(j-1)!}\sum_{n\ge1}\Lambda(n)\psi(n)(\log n)^{j-1}n^{-s},
\qquad A_j=D_j(\chi_0;s_0)+D_j(\chi_1;s_0).
$$
Here $j\ge1$. Since $1+\chi_1(n)\ge0$ on the units and all terms vanish on the nonunits, $A_j$ is nonnegative. Absolute convergence and $|\chi(n)n^{-it}|\le1$ give $|D_j(\chi;s_1)+D_j(\chi\chi_1;s_1)|\le A_j$. In particular the four terms together have nonnegative real part.

The local estimate `DHLocal` uses all zeros $w$ within radius $4/25$ of $z_0=26/25+iv$, for the character $\psi$ modulo $M$, counted with multiplicities $m_w$. The total multiplicity is $O(\log(M(|v|+2)))$, and for $\Re s>1$ and $|s-z_0|\le1/25$,
$$
D_j(\psi;s)=\frac{\mathbf1_{\psi=\chi_0}}{(s-1)^j}-\sum_w m_w(s-w)^{-j}
+O\bigl(\log(M(|v|+2))25^{j-1}\bigr).
\tag{2}
$$
For this, apply the [local disk theorem](local-log-derivative-from-disk-zeros.md) at outer radius $12/25$, to $f=L(s,\psi)$ or to $f=(s-1)L(s,\chi_0)$. The latter has nonzero value $\prod_{p\mid M}(1-1/p)$ at $1$. At $z_0$, the inverse $L$-value has modulus at most $\zeta(26/25)\le26$ by the Euler product, and $|z_0-1|\ge1/25$. On the outer disk $\Re s>1/2$, so periodic sums bound $L$ for a nonprincipal character, and the pole-removed zeta bound times $\prod_{p\mid M}(1-p^{-s})$ bounds $f$ for the principal character. The finite product has modulus at most $2^{\omega(M)}\le M$. Hence the log of the relative growth is $O(\log(M(|v|+2)))$. The bounded log-derivative remainder after subtracting the zero fractions is holomorphic on radius $(12/25)/6=2/25$. At points within $1/25$ of the center, the Cauchy derivative estimate with radii tending up to $1/25$ gives the factor $25^{j-1}$ for the normalized order $j-1$. Differentiating the pole and zero fractions gives (2).

Choose $c_1\le1/20$, $c_0\le2/25$. At $v=0$ the $\chi_1$ list contains $\beta$ and can lose one copy against the principal pole. At $v=t$, if the pair $\chi,\chi\chi_1$ contains the principal character its companion is $\chi_1$. Cancel one copy if the disk contains $\beta$. A matched pair has error at most $j\lambda h^{-j-1}$ by integrating the derivative of $(s-x)^{-j}$ from $\beta$ to $1$. If the raised pair has a pole but no copy, then $26/25-\beta\le9/100$ and the disk radius $4/25$ imply $|t|>1/8$. The pole costs at most $8^j$, which fits the local error.

Let $w_i$ be the list of $s_1$ minus the remaining zeros from these last two character lists, counted with multiplicity. Each has $\Re w_i\ge h$. There is a target entry $h+1-\Re\rho$: the zero $\rho$ lies in the prescribed disk and the pair exclusion protects it from deletion. The raised-pair estimate and (2) give
$$
\left|\sum_i w_i^{-j}\right|\le A_j+2j\lambda h^{-j-1}+25^j C_F L
\qquad(j\ge1)
\tag{3}
$$
for an absolute $C_F>0$. For $j=1$ use the real part of all four series, their nonnegative sum, and the nonnegative real parts of the zero reciprocals. Dropping the unraised zero list gives
$$
\Re\sum_i w_i^{-1}\le2\lambda h^{-2}+25 C_F L.
\tag{4}
$$

## The positive series input

The [hyperbola estimate](positive-prime-power-sum-by-hyperbola.md) gives, for $h\le1$ and $\beta\ge1-1/\ell$,
$$
A_j\le C_P\lambda\ell^2(j+1)^2 h^{-j-1}
+\frac{(C_P\ell)^j}{(j-1)!}
+\frac{C_P(j+1)\ell^2}{Mh^j}
\tag{5}
$$
for an absolute $C_P>0$. Here $\ell\le2L$ makes the zero hypothesis automatic. Also the [Siegel lower gap](siegel-gap-from-positive-coefficients.md) gives $\lambda\gg M^{-1/2}$, so $\ell^2/M\ll\lambda$.

## The choice of a Turán block

Take $c_1\le c_Z/4$, where $c_Z>0$ is the absolute [region constant with uniqueness](unique-simple-exceptional-zero.md). Thus $\beta$ is in that region and $\rho$ is outside it, so $L(1-\Re\rho)\ge c_Z/2$ by $\log(M(|t|+2))\le2L$. Take $h=1-\Re\rho$ and $K=\log(c_1/(\lambda L^3))$. Suppose $hL<c_2 K$. Then $K>c_Z/(2c_2)$, made arbitrarily large by choosing $c_2$ sufficiently small. Set $u_i=h/w_i$. Then $|u_i|^2\le\Re u_i$, and one term equals $1/2$. By (4),
$$
S:=\sum_i\Re u_i\le2\lambda/h+25 C_F hL.
\tag{6}
$$
The first term is at most $4c_1/c_Z\le1$ since $\lambda L^3=c_1 e^{-K}$ and $L\ge1$.

Use the [consecutive Turán bound](turan-power-sums-by-root-averaging.md). In the notation of the general version, for $n$ points of maximum modulus $1$ it gives a power $m+1\le j\le m+An$ with sum of modulus at least $[n/(C_T(m+n))]^{An}$. We may take $A=1$, $C_T=1600$. Write
$$
R=16e^{A+1},\quad \epsilon=R^{-1},\quad \theta=(2\log R)^{-1},\quad
D=\log\max(C_T,1),\quad \kappa=\frac{\theta\epsilon^2}{A(D+1)}.
$$
Require $c_0\le1/(25R)$, $25 C_Fc_2\le\kappa$, and $2e C_P c_2R\le\theta$. Then $S\le1+\kappa K$. Retain only the $n$ entries with $|u_i|\ge\epsilon$, where $1\le n\le S/\epsilon^2$ by $|u_i|^2\le\Re u_i$. Divide by an entry of maximal modulus, at least $1/2$, and use Turán with $m=\lceil\theta K\rceil$. The resulting $j$ satisfies
$$
2^{-j}\left(\frac{n}{C_T(m+n)}\right)^{An}
\le\left|\sum_i u_i^j\right|+\epsilon^{j-2}S,
\tag{7}
$$
since each dropped term has $|u_i|^j\le\epsilon^{j-2}\Re u_i$. From $n\epsilon^2\le1+\kappa K$, we have $\theta K<j\le2\theta K+J$, with $J=1+A/\epsilon^2$, and $AnD\le AD/\epsilon^2+j$. Using $An\log(1+m/n)\le Am\le Aj$, the left side of (7) is at least $e^{-AD/\epsilon^2}(8/R)^j$.

For the right side multiply (3) and (5) by $h^j$. The $\lambda/h$ and $1/M$ terms together are $O((j+1)^2\lambda L^3)$, using $1/h\ll L$ and $\ell^2/M\ll\lambda$. The factorial bound $j!\ge(j/e)^j$ gives
$$
(C_P\ell h)^j/(j-1)!\le j(eC_P\ell h/j)^j\le j R^{-j}
$$
since $\ell h\le2c_2 K$ and $j>\theta K$. The disk error is $C_F L(25h)^j\le jR^{-(j-1)}$ from $25h\le R^{-1}$ and $25C_F hL\le\kappa K\le\theta K$. The tail in (7) is at most $R^2(1+j)R^{-j}$. Finally $j\le K/\log R+J$ implies $\lambda L^3=c_1e^{-K}\le c_1 R^{J-j}$. Thus (7) forces $8^j\le C(j+1)^2$ with $C$ independent of $c_2,M,T$ and the characters. Choosing $c_2$ sufficiently small that $\theta c_Z/(2c_2)$ exceeds every $j$ allowed by that inequality gives the contradiction and proves (1).

The three logarithms in (1) come from the $\ell^2$ on the positive series side and the $h^{-1}\ll L$ from the ordinary zero-free region.

## Lean correspondence

- `deuring_heilbronn_dominant`, `deuring_heilbronn_local` and `deuring_heilbronn_inequality` give (2)–(4). [Positive comparison](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHDom.lean#L108) · [Local expansion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHLocal.lean#L167) · [Reciprocal estimates](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHIneqF.lean#L12)
- `region_gap` supplies the ordinary gap. `exists_power_sum_lower_bound` and `ub_terms` supply the lower and upper comparisons, combined by `deuring_heilbronn_finish_turan`. [Region](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHFinish.lean#L22) · [Lower](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/ExistsPowerSumLowerBound.lean#L9) · [Upper](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/UbTerms.lean#L84) · [Combination](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/DeuringHeilbronnFinishTuran.lean#L14)
- `deuring_heilbronn_lossy` gives (1) under the real-zero hypothesis. The Chinese note reports local Lean 4.33.1 replay of the Turán inputs and of `exists_power_sum_lower_bound`. Its record for the assembled theorem is a reading of the source. [Conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHB.lean#L13)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
