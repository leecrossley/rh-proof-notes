# Bernoulli values make the annihilator determinant nonzero

[Chinese proof](../zh/Bernoulli%E5%80%BC%E6%80%8E%E6%A0%B7%E4%BF%9D%E8%AF%81%E6%B6%88%E5%8E%BB%E8%A1%8C%E5%88%97%E5%BC%8F%E9%9D%9E%E9%9B%B6.md)

Let $M>0$, $\Gamma$ finite abelian, $\phi:(\mathbb Z/M\mathbb Z)^\times\to\Gamma$ a homomorphism with $c=\phi(-1)\ne1$, and $a,k\ge2$ with $(a,M)=1$. Let $\epsilon=(-1)^k$, $h=|\Gamma|/2$, and define
$$
E_k(b)=\frac{M^{k-1}}k B_k([b]_M/M),\quad
\Theta=-\sum_bE_k(b)[\phi(b)^{-1}],\quad
Y=(1-a^k[\phi(a)^{-1}])\Theta,
$$
summing over units and using standard residues. If $\Delta(Y)$ is the multiplication determinant on $\mathbb Q[\Gamma]/([c]-\epsilon)$, then for $D=Mk(k+1)!$, $U=2a^kM^kk!$,
$$
D^h\Delta(Y)\in\mathbb Z\setminus\{0\},\qquad
|D^h\Delta(Y)|\le(DU)^h .
$$

**Proof.** The quotient has a basis from one element of each pair $g,cg$. There are $h$ complex characters $\chi$ with $\chi(c)=\epsilon$: for $+1$ use the quotient group, and for $-1$ use a translate by a character separating $c$ from $1$. The evaluation rows on the chosen basis are nonzero and pairwise orthogonal, since their inner product is half the full group sum of $\chi\bar\chi'$, with the same value on both elements of a pair. These give a dual basis diagonalizing multiplication, with determinant $\prod_{\chi(c)=\epsilon}\chi(Y)$. [Character count](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/StickelbergerCharacterEval/Chcard.lean#L29) · [Determinant product](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/StickelbergerCharacterEval/Detprod.lean#L8)

Let $\psi(b)=\chi(\phi(b)^{-1})$ on units and zero otherwise. Then $\chi(Y)=(1-a^k\psi(a))(-B_{k,\psi;M}/k)$, where $B_{k,\psi;M}=M^{k-1}\sum_{0\le b<M}\psi(b)B_k(b/M)$. The first factor is nonzero since $a^k>1$ and $|\psi(a)|=1$. With conductor $f$ and primitive character $\psi^*$, the [modulus-change formula](floor-coefficients-recover-a-generalized-bernoulli-valuation.md) gives
$$
B_{k,\psi;M}=B_{k,\psi^*;f}\prod_{p\mid M,\ p\nmid f}(1-\psi^*(p)p^{k-1}).
$$
Grouping by $f$ gives the primitive Bernoulli sum by the distribution identity; exclusion of multiples of primes is inclusion–exclusion, where the terms for multiples of $d$ contribute $d^{k-1}\psi^*(d)B_{k,\psi^*;f}$. Each Euler factor is nonzero since the subtracted term has modulus $p^{k-1}>1$. The primitive part is nonzero by $\psi^*(-1)=(-1)^k$, the $1-k$ special value and functional equation in the linked proof, and the Euler product at $k\ge2$.

On $0\le x\le1$ the Bernoulli Fourier expansion is $B_k(x)=-k!/(2\pi i)^k\sum_{n\ne0}e^{2\pi inx}/n^k$. Integration by parts using $B_j'=jB_{j-1}$, equality at endpoints for $j\ge2$, and $B_1(1)-B_1(0)=1$ gives its nonconstant coefficients. The constant coefficient is zero by integrating $B_k=B_{k+1}'/(k+1)$. Absolute uniform convergence and uniqueness of Fourier coefficients give the formula including endpoints. Since $\sum_{n\ge1}n^{-k}\le2$, $|B_k(x)|\le4k!/(2\pi)^k\le k!$. Therefore $|B_{k,\psi;M}|\le M^kk!$, and $|1-a^k\psi(a)|\le2a^k$ gives $|\chi(Y)|\le U$. [Evaluation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/StickelbergerCharacterEval/GroupRingCharEvalStickelbergerYNeZeroOfParity.lean#L8) · [Nonzero](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/StickelbergerCharacterEval/GroupRingCharEvalStickelbergerYNeZeroOfParity.lean#L14) · [Norm bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/StickelbergerCharacterEval/NormCharEvalHigherStickelbergerLe.lean#L7) · [Bernoulli nonzero](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/BNzC.lean#L10) · [Bernoulli size](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/BUpper.lean#L7)

By von Staudt–Clausen and the values in degrees zero, one and odd $j>1$, $(k+1)!B_j(0)$ is integral for $0\le j\le k$. The Bernoulli polynomial expansion gives $DE_k(b)=(k+1)!\sum_{j=0}^k\binom kj B_j(0)M^j[b]_M^{k-j}\in\mathbb Z$. Thus $DY$ acts by an integral matrix on the coset basis over $\mathbb Z$. Its determinant is $D^h\Delta(Y)$, which is nonzero and bounded as claimed by the product formula. This is used to [extract the prime-power factor](extracting-a-prime-power-from-a-group-ring-annihilator.md). [Denominators](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/StickelbergerCharacterEval/ExistsIntHigherStickelbergerDenomSmul.lean#L25) · [Bernoulli denominator](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/Denint.lean#L8) · [Integer determinant](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/StickelbergerCharacterEval/Detint.lean#L9)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
