# Integer coefficients approximate higher Stickelberger elements

[Chinese proof](../zh/%E9%AB%98%E9%98%B6Stickelberger%E5%85%83%E7%B4%A0%E6%80%8E%E6%A0%B7%E7%94%B1%E6%95%B4%E6%95%B0%E7%B3%BB%E6%95%B0%E9%80%BC%E8%BF%91.md)

Let \(\ell\mid N\) be prime, \(N>0\), \(e\ge0\), \(k=e+1\), and \(a>0\) odd and prime to \(N\). Let \(G_L=(\mathbb Z/L\mathbb Z)^\times\), \(\Gamma\) finite abelian, and \(\phi:G_N\to\Gamma\) a homomorphism. For \(m\ge0\) put \(M=N\ell^m\), and let \(\phi_M\) factor through reduction to \(G_N\). For \(L=N,M\), with standard residues \([b]_L\), define
$$
\begin{aligned}
H_{L,k}(x)&=L^{k-1}B_k(x/L)/k,\\
\Theta_L&=-\sum_{b\in G_L}H_{L,k}([b]_L)[\phi_L(b)^{-1}],&
Y_L&=(1-a^k[\phi_L(a)^{-1}])\Theta_L,\\
J_{L,a}(b)&=(a[a^{-1}b]_L-[b]_L)/L,&
C_{L,a}(b)&=(a-1)/2-J_{L,a}(b),\\
Q_M&=-\sum_{b\in G_M}[b]_M^e C_{M,a}(b)[\phi_M(b)^{-1}].
\end{aligned}
$$
Both \(J,C\) are integers by divisibility and oddness of \(a\). Then \(Y_N\) has \(\mathbb Z_\ell\)-coefficients; writing it as \(z\in\mathbb Z_\ell[\Gamma]\), for \(r\ge0\) one has
$$
Q_M\equiv z\bmod\ell^r\mathbb Z_\ell[\Gamma]\quad
\text{if } m\ge r+v_\ell(2k\prod_{p\le k+1}p)+1 .
$$

**Proof.** For \(D=\ell^m\) each lift of a unit \(t\bmod N\) has representative \([t]_N+jN\), \(0\le j<D\); all are units since no new prime divides \(M\). Their basis labels coincide. By the Bernoulli distribution identity their \(H_{M,k}\)-sum is
$$
\frac{(ND)^{k-1}}k D^{1-k}B_k([t]_N/N)=H_{N,k}([t]_N).
$$
Thus \(\Theta_M=\Theta_N\), and the correction factor is the same, so \(Y_M=Y_N\). [`yLevel`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/YLevel.lean#L76)

Let \(P_k=\prod_{p\le k+1}p\), \(D_k=2kP_k\). By the [Bernoulli denominators and expansion](floor-coefficients-recover-a-generalized-bernoulli-valuation.md),
$$
H_{M,k}(x)=x^k/(kM)-x^{k-1}/2+(M/(kP_k))w_x,\quad w_x\in\mathbb Z
$$
with last term zero for \(k=1\). Reindex the product in \(Y_M\) to make the coefficient summands \(-[H_{M,k}(x)-a^kH_{M,k}(y)]\), with \(x=[b]_M\), \(y=[a^{-1}b]_M\). Set \(j=J_{M,a}(b)\), so \(ay=x+Mj\). The difference of first terms is \((x^k-(x+Mj)^k)/(kM)\equiv-jx^{k-1}\bmod (M/k)\mathbb Z\) by the binomial formula. The second difference is \((a(x+Mj)^{k-1}-x^{k-1})/2\equiv (a-1)x^{k-1}/2\bmod (M/2)\mathbb Z\). The other terms are in \((M/(kP_k))\mathbb Z\). Combining shows \(H_{M,k}(x)-a^k H_{M,k}(y)-x^{k-1}C_{M,a}(b)\in (M/D_k)\mathbb Z\). Summing gives \(Y_M-Q_M\in(M/D_k)\mathbb Z[\Gamma]\). The threshold ensures \(v_\ell(M)\ge r+v_\ell(D_k)\), so the difference lies in \(\ell^r\mathbb Z_\ell[\Gamma]\). First take \(r=0\) to give the integral coefficient statement by \(Y_M=Y_N\), then any \(r\) to get the congruence. Thus the operators agree on any \(\ell^r\)-torsion module.

The source calls \(Y_L,C_{L,a},Q_M\) `yEl`, `Eone`, `ytEl`. `yNear` gives the single-level estimate and `congr` takes it back to the fixed level. [Coefficient definitions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/StickelbergerElements/CoefMapSingle.lean#L11) · [Termwise congruence](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/StickelbergerElements/TwistedBernoulliValueCongrPowMulFirst.lean) · [`yNear`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/YNear.lean#L10) · [`congr`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/NearLevel.lean#L24)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
