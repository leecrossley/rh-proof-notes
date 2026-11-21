# A hyperbola split for the nonnegative prime-power sum

[Chinese proof](../zh/%E5%8F%8C%E6%9B%B2%E7%BA%BF%E5%88%86%E5%89%B2%E6%80%8E%E6%A0%B7%E6%8E%A7%E5%88%B6%E5%B8%A6%E6%AD%A3%E7%B3%BB%E6%95%B0%E7%9A%84%E7%B4%A0%E6%95%B0%E5%B9%82%E5%92%8C.md)

**Proposition.** There is an absolute $C>0$ such that for every integer $M\ge3$, nonprincipal real character $\chi_1\bmod M$, real zero $L(\beta,\chi_1)=0$ with $1-1/\log(3M)\le\beta<1$, real $1<\sigma\le2$, and integer $k\ge0$, one has
$$
A_{k+1}:=\frac1{k!}\sum_{n\ge1}\frac{\Lambda(n)(\chi_0(n)+\chi_1(n))(\log n)^k}{n^\sigma}
\le \frac{C\lambda\ell^2(k+2)^2}{h^{k+2}}
+\frac{(C\ell)^{k+1}}{k!}+\frac{C(k+2)\ell^2}{Mh^{k+1}},
\tag{1}
$$
where $h=\sigma-1$, $\lambda=1-\beta$, $\ell=\log(3M)$ and $\chi_0$ is principal. This is `DHPrime` in the screening repulsion argument.

## A nonnegative divisor convolution

Put $r(n)=\sum_{d\mid n}\chi_1(d)$. The local sum at $p^a$ is $a+1$ if $\chi_1(p)=1$, $1$ if $\chi_1(p)=0$, and $1$ or $0$ according as $a$ is even or odd if $\chi_1(p)=-1$. Hence $r(n)\ge0$. At every prime power $p^a$ with $p\nmid M$, $1+\chi_1(p)^a\le2r(p^a)$, and the character sum on multiples of $p\mid M$ vanishes. Thus
$$
0\le\Lambda(n)(\chi_0(n)+\chi_1(n))\le2(\log n)r(n).
\tag{2}
$$

For an arbitrary nonprincipal $\chi\bmod M$, period cancellation and partial summation give
$$
\sum_{b\le U}\chi(b)/b=L(1,\chi)+O(M/U),\qquad
\left|\sum_{U<b\le V}\chi(b)(\log b)/b\right|\ll M(1+\log U)/U
$$
for $1\le U\le V$. The first uses the bounded period sums in the $1/b$ tail, which converges to $L(1,\chi)$ by continuation from $\Re s>1$. The second uses the total variation of $\log t/t$. Let $J(U)=\sum_{b\le U}\chi(b)(\log b)/b$. For integer $N\ge1$, put $U=\lfloor\sqrt N\rfloor$ and write the convolution sum over $ab\le N$ as
$$
\sum_{b\le U}\frac{\chi(b)}b H_{\lfloor N/b\rfloor}
+\sum_{a\le N}\frac1a\sum_{U<b\le N/a}\frac{\chi(b)}b ,
$$
where $H_j=\sum_{a\le j}1/a$. The second term is $O(M(1+\log N)/U)$. In the first insert $H_{\lfloor N/b\rfloor}=\log N-\log b+\gamma+O(b/N)$. Hence the convolution sum equals $(\log N+\gamma)L(1,\chi)-J(U)+O(M(1+\log N)/\sqrt N)$. Subtract at $\lfloor x\rfloor$ and $\lfloor y\rfloor$ for $1\le y\le x$. The difference of the $J$ terms has the stated tail bound at $\lfloor\sqrt{\lfloor y\rfloor}\rfloor$ and the errors have the same order, using eventual decrease of $(1+\log y)/\sqrt y$. Replacing the log difference of the floors by $\log(x/y)$ costs $O(|L(1,\chi)|/y)=O(M/y)$. For $\chi_1$ this gives
$$
\sum_{y<n\le x}r(n)/n\le |L(1,\chi_1)|\log(x/y)+C_HM(1+\log y)/\sqrt y.
\tag{3}
$$

## The factor from the real zero

For real $1-1/\ell\le x\le1$, on the circle of radius $1/(2\ell)$ about $x$ we have $\Re s\ge1-3/(2\ell)>0$ and $|s|\le2$. Split the Dirichlet series at $M$. The first terms have total modulus at most $e^{3/2}(1+\log M)$. If $A(t)=\sum_{n\le t}\chi_1(n)$, then $|A(t)|\le M$, $A(M)=0$, so the tail $s\int_M^\infty A(t)t^{-s-1}dt$ is bounded because $M^{1-\Re s}\le e^{3/2}$ and $\Re s$ has an absolute positive lower bound. Cauchy's estimate gives $|L'(x,\chi_1)|\ll\ell^2$. Integrating from $\beta$ to $1$ gives $|L(1,\chi_1)|\ll\lambda\ell^2$.

## Summing blocks with the order retained

Before dividing by $k!$, put $j=k+1$ and $v_0=\lceil8\log M\rceil$. The segment $n\le e^{v_0}$ costs $O(v_0^j)$ by the bound $0\le\chi_0+\chi_1\le2$ and $\sum_{n\le z}\Lambda(n)/n\ll\log z$ from Chebyshev's bound and partial summation. On $e^v<n\le e^{v+1}$, (2) and (3) give cost at most
$$
2w_v\bigl(|L(1,\chi_1)|+C_H M(v+1)e^{-v/2}\bigr),\qquad w_v=(v+1)^j e^{-hv}.
$$
For $t\in[v+1,v+2]$, $w_v\le e^2 t^j e^{-ht}$. Integrating over these disjoint intervals gives $\sum_{v\ge v_0}w_v\le e^2 j!h^{-j-1}$. Also $w_v\le e(j/(eh))^j\le e j! h^{-j}$ by the maximum of $t^j e^{-ht}$. The error sum then uses $\sum_{v\ge v_0}(v+1)e^{-v/2}\ll e^{-v_0/4}\le M^{-2}$. Nonnegativity carries the finite sum bounds to the infinite series. Dividing by $(j-1)!$ and applying the real-zero factor bounds the three contributions by $(C\ell)^j/(j-1)!$, $C\lambda\ell^2 j h^{-j-1}$ and $Cj/(Mh^j)$. These imply (1).

## Lean correspondence

- `cF_split`, `cF_approx` and `deuring_heilbronn_hypergeometric` give the hyperbola decomposition and (3). [Split](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHHyperA.lean#L65) · [Approximation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHHyperC.lean#L135) · [Interval](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHHyper.lean#L114)
- `dhpr_coef_le` and `lfunction_one_le_of_siegel_zero` give (2) and the real-zero factor. [Coefficient](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHPrimeA.lean#L88) · [Integral](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHPrimeA.lean#L191)
- `dhpr_wsup`, `dhpr_wsum` and `dhpr_esum` control the weights used by `dhpr_block` and `deuring_heilbronn_prime_sum`. [Weight bounds](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHPrimeB.lean#L50) · [Block](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHPrimeC.lean#L35) · [Conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHPrime.lean#L151)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
