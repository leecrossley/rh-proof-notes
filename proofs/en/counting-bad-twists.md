# Counting bad twists with a Dirichlet polynomial

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E7%94%A8%E7%8B%84%E5%88%A9%E5%85%8B%E9%9B%B7%E5%A4%9A%E9%A1%B9%E5%BC%8F%E6%95%B0%E5%87%BA%E5%9D%8F%E6%89%AD%E6%9B%B2.md) · [Reading and review status](../../STATUS.md)

## Statement

Fix $\sigma_0=1-1/400$. For $Q\ge3$, consider primitive Dirichlet characters of conductor at most $Q$ with at least one zero in $\operatorname{Re}s>\sigma_0$, $|\operatorname{Im}s|\le Q$. There is an absolute $C>0$ such that their number is at most $CQ^{1/4}$.

In particular, for any real $F_0$ and finite prime set $P$, suppose each $p\in P$ satisfies $p>F_0$ and has an integer $1\le a\le F_0$ with a witnessing primitive character of conductor $ap\le Q$ having a zero in the same rectangle. Then $|P|\le CQ^{1/4}$. This corollary counts the zero-detection exceptions in the [selection of auxiliary primes](prime-pair-selection.md).

The proof uses classical nonvanishing of nonprincipal Dirichlet $L$-functions in $\operatorname{Re}s\ge1$ to bound the real parts of the selected zeros by one. The unique primitive principal character, of conductor one, is counted separately by one.

## A zero is detected on one dyadic block

It suffices to take $Q$ large, in particular $Q\ge20$. Let $X=\lceil Q\rceil$, $Y=X^4$, $J=8(\lfloor\log_2 X\rfloor+1)$ and $N=2^J\ge X^8$. For each nonprincipal primitive character $\chi$ in question of conductor $f>1$, choose one zero $\rho$ and write $\sigma=\operatorname{Re}\rho$.

The character has period $f$ and sum zero on a full period. Its partial sums from the start thus have modulus at most $f$. Partial summation gives locally uniform convergence of the Dirichlet series in $\operatorname{Re}s>0$, agreeing with $L(s,\chi)$ by continuation from $\operatorname{Re}s>1$. With the partial sums starting at $N$ bounded by $2f$, it also gives

$$
\left|L(\rho,\chi)-\sum_{n\le N}\chi(n)n^{-\rho}\right|
\le2f N^{-\sigma}(1+|\rho|/\sigma).
$$

Since $L(\rho,\chi)=0$, $1+|\rho|/\sigma\le3X$ and $\sigma>15/16$, the truncated sum $P_\chi(\rho)$ has modulus at most $6X^2N^{-15/16}$. In particular $Y|P_\chi(\rho)|\le6X^{-3/2}\le1/2$.

Let $M_\chi(\rho)=\sum_{d\le Y}\mu(d)\chi(d)d^{-\rho}$ with $\mu$ the Möbius function. Then $|M_\chi(\rho)|\le Y$ and $|P_\chi(\rho)M_\chi(\rho)|\le1/2$. Expanding the product gives coefficient $a(n)=\sum_{d\mid n,\,d\le Y,\,n/d\le N}\mu(d)$. For $1\le n\le Y$ the truncations omit no divisors, so the coefficient is one at $n=1$ and zero otherwise. Thus

$$
P_\chi(\rho)M_\chi(\rho)=1+\sum_{Y<n\le YN}a(n)\chi(n)n^{-\rho}.
$$

The last sum has modulus at least $1/2$. Split it into the $J$ blocks $(U,2U]$ with $U=Y2^j$, $0\le j<J$. Some block sum $B_U(\chi,\rho)$ has modulus at least $1/(2J)$.

## Bound correlations in one block

Fix $U$ and a set $\mathcal T$ of characters detected there, with a chosen $\rho_\chi$ for each. For $U<n\le2U$, let $b(n)=a(n)n^{-\sigma_0}$ and $v_\chi(n)=\chi(n)n^{-(\rho_\chi-\sigma_0)}$. Then $B_U(\chi,\rho_\chi)=\sum_n b(n)v_\chi(n)$. The diagonal Gram entries are at most $U$ since $|v_\chi(n)|\le1$.

For distinct primitive $\chi,\psi$ with conductors $f,g$, the product $\chi\bar\psi$ is nonprincipal on the units modulo $fg$. Indeed equality of the induced characters would give equality of their inducing primitive characters. Hence this product has a complete period of sum zero and prefix sums bounded by $fg$. Let $w=(\rho_\chi-\sigma_0)+\overline{(\rho_\psi-\sigma_0)}$. Then $\operatorname{Re}w>0$ and $|w|\le1+2Q$. Summing the product against $n^{-w}$ by parts on $(U,2U]$ gives at most $2fg$ from the endpoints and at most $fg|w|\log2$ from the integral, so

$$
\left|\sum_{U<n\le2U}v_\chi(n)\overline{v_\psi(n)}\right|
\le2fg(1+|w|)\le8Q^3 .
$$

For any finite family of vectors whose Gram matrix has absolute row sums at most $\Delta$, expanding the squared norm of $\sum_i c_i v_i$ and using $2|c_ic_j|\le|c_i|^2+|c_j|^2$ gives $\|\sum_i c_iv_i\|^2\le\Delta\sum_i|c_i|^2$. Both row and column sums have the same bound by conjugate symmetry. Euclidean duality gives $\sum_i|\sum_n b(n)v_i(n)|^2\le\Delta\sum_n|b(n)|^2$. Here take $\Delta=U+8Q^3|\mathcal T|$.

## Absorb the off-diagonal term

We have $|a(n)|\le \tau(n)$, the number of divisors of $n$. For any $\eta>0$, $\tau(n)\ll_\eta n^\eta$. Indeed $(k+1)\le2^k\le p^{\eta k}$ for sufficiently large primes $p$, and each of the finitely many smaller primes contributes at most its fixed $\sup_{k\ge0}(k+1)p^{-\eta k}$ after dividing by $n^\eta$. Taking $\eta=1/200$ and $\sigma_0=399/400$ gives

$$
\sum_{U<n\le2U}|b(n)|^2\le A\,U^{1+2/200-2\sigma_0}=A\,U^{-197/200}
$$

with absolute $A>0$. The Gram bound and detection give

$$
|\mathcal T|/(4J^2)\le A U^{3/200}+8AQ^3 U^{-197/200}|\mathcal T|.
$$

Since $U\ge Q^4$, the last coefficient is $O(Q^{-47/50})$. As $J=O(\log Q)$, it is at most $1/(8J^2)$ for all sufficiently large $Q$. Rearranging gives $|\mathcal T|\le8AJ^2U^{3/200}$.

Assign every detected character to one detecting block. Each $U\le Y2^J\le2^8X^{12}=O(Q^{12})$, so adding the $J$ counts and the possible trivial character gives $1+O((\log Q)^3Q^{9/50})=O(Q^{1/4})$. Bounded $Q\ge3$ adds only finitely many conductors and characters and is covered by increasing the constant.

For the corollary choose a witnessing character for every prime. If distinct $p,p'$ gave the same character, its conductor would satisfy $ap=a'p'$ and hence $p\mid a'$. This contradicts $1\le a'\le F_0<p$. The chosen map is injective.

## Lean references and review

- `mco`, `blk` and `Detect` are in [`CountZDefs.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/CountZDefs.lean). The product computation and detection use [`CountZMoll.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/CountZMoll.lean) and [`zero_detection`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/CountZDetect.lean#L43).
- The pair bounds, Gram inequality and block count are [`pair_sum_bound`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/CountZPair.lean#L98), [`pair_twist_bound`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/CountZTwist.lean#L32), [`duality_inequality`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/CountZDual.lean#L9) and [`blockCountOf_statement`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/CountZBlock.lean#L23). The square sum is [`coefficient_square_bound`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/CountZMoll.lean#L133).
- [`CountZNum.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/CountZNum.lean) and [`CountZFinal.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/CountZFinal.lean) assemble the constants. The results are [`zero_density_box`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/CountZAll.lean#L13), [`count_bad_core`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/CountBadCore.lean#L18), and [`QH.count_bad`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/CountBad.lean).

English translation draft. The proof uses elementary partial summation, the finite-dimensional duality argument and the classical nonvanishing statement above.
