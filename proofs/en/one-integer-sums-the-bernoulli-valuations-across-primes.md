# One integer sums the Bernoulli valuations across primes

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E6%89%80%E6%9C%89%E7%B4%A0%E6%95%B0%E7%9A%84Bernoulli%E8%B5%8B%E5%80%BC%E8%83%BD%E7%94%A8%E5%90%8C%E4%B8%80%E4%B8%AA%E6%95%B4%E6%95%B0%E7%9B%B8%E5%8A%A0.md)

Let \(N>0\), \(k\ge1\), \(G=(\mathbb Z/N\mathbb Z)^\times\), and \(\mathcal P\) a family of subgroups such that for every \(J\in\mathcal P\), \(-1\in J\) exactly when \(k\) is even. For any characteristic-zero field \(A\) containing a primitive root of order the exponent of \(G\), let \(\mathcal X_A\) be the Dirichlet characters modulo \(N\) valued in \(A\) whose kernels on \(G\) are in \(\mathcal P\). For the primitive character \(\chi^*\) of conductor \(f_\chi\) inducing \(\chi\), put
$$
A_k(\chi)=N\left(\prod_{p\le k+1}p\right)B_{k,\chi^*;f_\chi},\qquad U=16N^{k+1}k!,
$$
where \(B_{k,\psi;f}=f^{k-1}\sum_{b=1}^f\psi(b)B_k(b/f)\). There is a single nonzero \(D\in\mathbb Z\) with \(D=\prod_{\chi\in\mathcal X_A}A_k(\chi)\) in each \(A\), and \(\log|D|\le|\mathcal X_\mathbb C|\log U\). At each prime \(\ell\), for every subfamily \(T_\ell\subseteq\mathcal X_{\overline{\mathbb Q}_\ell}\),
$$
\sum_{\chi\in T_\ell}-\log|A_k(\chi)|_\ell\le v_\ell(D)\log\ell .
$$
The right sides over any finite set of primes sum to at most \(\log|D|\).

**Proof.** Let \(h\) be the exponent of \(G\); compute the product in \(\mathbb Q(\mu_h)\). Each Galois automorphism of this field permutes the characters by acting on their values, preserving the kernels and the primitive inducing data by reduction of moduli. Since Bernoulli polynomials have rational coefficients, it permutes the factors. Thus the product is rational. Embedding \(\mathbb Q(\mu_h)\) in \(A\) bijects its \(h\)-th roots and so the characters and their kernel conditions, giving the same rational value everywhere.

With \(P_k=\prod_{p\le k+1}p\), von Staudt–Clausen and the Bernoulli polynomial expansion give \(f_\chi P_k f_\chi^{k-1}B_k(b/f_\chi)\in\mathbb Z\): \(P_k\) clears the Bernoulli denominators and \(f_\chi\) clears the leading term. Since \(f_\chi\mid N\) and character values on units are algebraic integers, all factors are integral, hence the rational product is an integer. The kernels give parity \(\chi(-1)=(-1)^k\). Nonvanishing of the primitive Bernoulli value follows from [the special value and functional equation](floor-coefficients-recover-a-generalized-bernoulli-valuation.md). For \(k\ge2\) the Euler product supplies \(L(k,\chi^{*-1})\ne0\); for \(k=1\) the character is odd and nonprincipal and one uses Dirichlet's nonvanishing at \(1\) in the integer-point formula. The empty family gives \(D=1\).

In \(\mathbb C\), the [Bernoulli Fourier bound](bernoulli-values-make-the-annihilator-determinant-nonzero.md) gives \(|B_{k,\chi^*;f_\chi}|\le4f_\chi^k k!/(2\pi)^k\); it also holds at \(k=1\) from \(|B_1(x)|\le1/2\). The product of primes up to \(m\) is at most \(4^m\) by induction: for even \(m\ge4\) there is no new prime; for \(m=2j+1\), every prime \(j+1<p\le2j+1\) divides \(\binom{2j+1}{j}\le2^{2j}\), since the binomial row has two equal terms of that size. Multiply by the bound through \(j+1\); \(m\le2\) is immediate. Hence
$$
|A_k(\chi)|\le 4^{k+1}N\,4N^kk!/(2\pi)^k\le U .
$$
Multiply and take logs. Finally a root of a monic integral polynomial has \(\ell\)-adic norm at most one, as otherwise the leading term strictly dominates. Thus all \(-\log|A_k(\chi)|_\ell\) are nonnegative. Enlarge the subfamily to all characters and use the product to get \(-\log|D|_\ell=v_\ell(D)\log\ell\). Sum over primes using integer factorization. The subfamilies can vary with \(\ell\), as they do in the [negative-sign bound](negative-sign-cohomology-bound.md).

`b_ratprod` gives the rational product, `b_primmem` integrality, `b_denupper` the absolute bound, `b_prodint` the common integer and `prodVal` the sum over primes. [Rationality](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/Ratprod.lean#L7) · [Integrality](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/Primmem.lean#L17) · [Size](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/Denupper.lean#L28) · [Integer product](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/Prodint.lean#L12) · [Sum of valuations](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/ProdVal.lean#L10)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
