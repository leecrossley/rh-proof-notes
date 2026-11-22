# The CM class mean of the normalized period area

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $K$ be an imaginary quadratic field of discriminant $-d<-4$ and $\chi_K$ its primitive quadratic Dirichlet character. Let $\Lambda=\delta I$ for a nonzero integral ideal $I$ with $\delta^{12}=\Delta(I)$. Thus $\Delta(\Lambda)=1$. For a number field $M\subset\mathbb C$ containing $g_2(\Lambda),g_3(\Lambda)$, let $\Lambda_\rho$ be the discriminant-one lattice with the two invariants transported under $\rho:M\hookrightarrow\mathbb C$. Denote Euler's constant by $\gamma_{\!E}$. Then
$$
\frac{1}{[M:\mathbb Q]}\sum_\rho \log\operatorname{area}(\Lambda_\rho)
 =\gamma_{\!E}+\log\frac{2\pi^2}{\sqrt d}
   -\frac{L'(1,\chi_K)}{L(1,\chi_K)} .
\tag{1}
$$
The [conjugate curve proof](the-conjugate-cubic-has-a-normalized-cm-ideal-lattice.md) puts each lattice into an ideal class. Their normalized areas are the ones in the [theta-to-eta calculation](the-twelfth-theta-to-eta-ratio-has-integral-conjugates.md).

**The ideal class multiplicities.** We use the first main theorem of complex multiplication for the maximal order of $K$. The $j$-invariants of the complex tori $\mathbb C/J$, indexed by nonzero fractional ideal classes $J$ of $\mathcal O_K$, are distinct roots of a polynomial irreducible over $K$. Their splitting field over $K$ is $K(j(I))$, and its Galois group acts simply transitively on these roots. In particular $[K(j(I)):K]$ is the ideal class number. [First main theorem of CM, Theorems 21.1–21.2](https://ocw.mit.edu/courses/18-783-elliptic-curves-fall-2025/mit18_783_f25_lec21.pdf)

Adjoin $K$ to $M$ if necessary. Each embedding of $M$ extends to this compositum the same number of times. Thus this extension does not change the mean of the original function of $\rho$. Among embeddings fixing $K$, each class $j$-invariant appears equally often: every embedding of $K(j(I))$ over $K$ has the same number of extensions to the compositum. Embeddings reversing $K$ are obtained from those fixing $K$ by ordinary complex conjugation. A lattice and its complex conjugate have the same area, so the same mean results over all embeddings. Two discriminant-one lattices with the same ideal class differ by a scalar with twelfth power $1$, because they are homothetic and scaling a lattice by $\omega$ multiplies its discriminant by $\omega^{-12}$. Hence the area is determined by the class. It remains to average the logarithmic area over all classes once each.

**The limit formula with constants.** For $\tau=x+iy$ in the upper half-plane and $s>1$, put
$$
 Z(\tau,s)=\sum_{(m,n)\ne(0,0)}
          \frac{y^s}{|m+n\tau|^{2s}}.
$$
The terms with $n=0$ give $2y^s\zeta(2s)$. For $n\ne0$, use the Mellin representation $u^{-s}=\pi^s\Gamma(s)^{-1}\int_0^\infty t^{s-1}e^{-\pi u t}\,dt$ on $u=(m+nx)^2+(ny)^2$, and Poisson summation on the Gaussian in $m$:
$$
 \sum_m e^{-\pi t(m+nx)^2}
 =t^{-1/2}\sum_k e^{-\pi k^2/t}e^{2\pi i k n x}.
$$
The terms with $k=0$, summed over $n\ne0$, give
$$
2 y^{1-s}\sqrt\pi\,\frac{\Gamma(s-\tfrac12)}{\Gamma(s)}\,\zeta(2s-1).
$$
At $s=1$ the factor of $2\zeta(2s-1)$ is $\pi$ and its logarithmic derivative there is $-\log y-2\log2$ by the Gamma duplication identity. The Laurent constant of $2\zeta(2s-1)$ is $2\gamma_{\!E}$. Thus the $k=0$ term equals $\pi/(s-1)+\pi(2\gamma_{\!E}-\log y-2\log2)+o(1)$.

For $n,k\ne0$ the remaining integrals and sums converge uniformly as $s\downarrow1$. Indeed for $1\le s\le3/2$, $t^{s-3/2}\le t^{-1/2}+1$, and $(ny)^2t+k^2/t\ge2|nk|y$. Split the exponential into halves and bound one half by $e^{-\pi |nk|y}$ and the other by $e^{-\pi (ny)^2t/2}$. Integration of the latter against $t^{-1/2}+1$ gives a bound $O_y(1/|n|+1/n^2)$, so the sum in $n,k\ne0$ is uniformly absolutely convergent. At $s=1$ the needed integral is
$$
 \int_0^\infty t^{-1/2}e^{-\pi((ny)^2t+k^2/t)}\,dt
 =\frac{e^{-2\pi|nk|y}}{|n|y}.
$$
For the general integral with exponent $-At-B/t$, differentiating in $B>0$ and substituting $t=B/(Au)$ gives the logarithmic derivative $-\sqrt{A/B}$. Its value at $B=0$ is $\sqrt{\pi/A}$, which proves the formula. The nonzero Fourier terms therefore contribute
$$
 4\pi\sum_{n,k\ge1}\frac{e^{-2\pi nk y}\cos(2\pi nkx)}{n}
 =-4\pi\sum_{k\ge1}\log|1-e^{2\pi i k\tau}|.
$$
Add the contribution from $n=0$, which tends to $2y\zeta(2)=\pi^2 y/3$. With the eta product, the two contributions sum to $-4\pi\log|\eta(\tau)|$. Combining everything proves
$$
 Z(\tau,s)=\frac{\pi}{s-1}
  +\pi\left(2\gamma_{\!E}-2\log2-\log\big(y|\eta(\tau)|^4\big)\right)
  +o(1).
\tag{2}
$$

**Convert the class sums.** For an ideal class $C$, choose an integral ideal $J=\omega(\mathbb Z+\tau\mathbb Z)$ in the inverse class. Every integral ideal of class $C$ has the form $(\alpha)J^{-1}$ for $\alpha\in J\setminus\{0\}$, up to multiplication of $\alpha$ by the $w_K=|\mathcal O_K^\times|$ units. Its norm is $|\alpha|^2/N(J)$. Since $|\omega|^2y=N(J)\sqrt d/2$, its partial zeta function is
$$
 \zeta_C(s)=\frac{(2/\sqrt d)^s}{w_K}Z(\tau,s).
$$
Expanding the factor $(2/\sqrt d)^s$ in (2), the coefficient of $1/(s-1)$ is the same $2\pi/(w_K\sqrt d)$ for every class, and the constant divided by that residue is
$$
 2\gamma_{\!E}-\log(2\sqrt d)-\log(y|\eta(\tau)|^4).
$$
Summing over classes gives the Dedekind zeta function $\zeta_K=\zeta L(s,\chi_K)$, by the Euler products for the split, inert and ramified prime cases. In particular $L(1,\chi_K)\ne0$, since this product has the positive residue just computed. The constant term divided by the residue in the product is $\gamma_{\!E}+L'(1,\chi_K)/L(1,\chi_K)$. Equating it with the average of the displayed constants gives
$$
 \operatorname{mean}_{C}\log(y|\eta(\tau_C)|^4)
 =\gamma_{\!E}-\log(2\sqrt d)-L'(1,\chi_K)/L(1,\chi_K).
$$
The discriminant-one representative of such a class has area $4\pi^2 y|\eta(\tau_C)|^4$. Adding $\log(4\pi^2)$ yields (1).

**Lean correspondence.** The period formula is [`mean_log_period`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/MeanLogPeriodConjugatesEqChowlaSelberg.lean#L202), which states the mean of $\log(\operatorname{area}(\Lambda_\rho)/\pi)$. The covolume version is [`mean_log_area`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DecoratedLatticeProofs/MeanLogCovolumeConjugateLatticesEq.lean#L20). The direct computation above uses the classical complex-multiplication class distribution and derives the needed Kronecker limit formula. The source obtains the same constants through its comparison with mean logarithmic norms on a family of CM elliptic curves.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
