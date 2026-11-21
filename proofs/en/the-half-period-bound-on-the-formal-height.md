# The half-period bound on the formal height

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Let $p\ge5$ be prime, let $\Lambda$ be a complex lattice and $\iota:\mathbb C\to\mathbb C_p$ a field isomorphism. Assume $g_2=\iota(g_2(\Lambda))$ and $g_3=\iota(g_3(\Lambda))$ are integral and $g_2^3-27g_3^2$ has norm one. We use the short Weierstrass law $F_E$ in the parameter $t$, with logarithm $\ell$. The multiplication series $M_p=\ell^{-1}(p\ell)$ has integral coefficients and some coefficient of degree at most $p^2$ of norm one. This is the hypothesis needed to start the [two Frobenius descents](the-cm-endomorphism-forces-two-frobenius-descents.md). We give the product argument of `level_le`. It also applies to homothetic models, by first rescaling the complex lattice as in [the CM norm proof](extending-the-cm-norm-law-to-all-unramified-units.md). [Height bound by the isogeny product and a half-period](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/UnramifiedIntegrals/FgLevel.lean#L54)

## The squared product for multiplication by an integer

For this part write $W=\wp_\Lambda$, and define the complex sigma function
$$
S(z)=z\prod_{\lambda\in\Lambda\setminus\{0\}}(1-z/\lambda)
  \exp(z/\lambda+z^2/(2\lambda^2)),\qquad
S_*(z)=S(z)\exp(-s_2z^2/2).
$$
The product converges normally on compact sets, since its factors differ from $1$ by $O(|\lambda|^{-3})$ uniformly on such sets for large $|\lambda|$. The same lattice sum bound as in [the isogeny distribution proof](the-lattice-isogeny-and-its-weight-two-constant.md) applies. Its zeros are simple and precisely the lattice, and $S_*$ is odd, by pairing opposite lattice elements. The logarithmic derivative of $S_*$ is $\zeta_\Lambda(z)-s_2 z$, by differentiating the locally convergent sums of logarithms away from the zeros. Its second logarithmic derivative is therefore $-W-s_2$. This also identifies its Taylor series at zero with $z\exp(J(z)-s_2z^2/2)$ by the constant and linear normalization of the logarithm of $S_*/z$.

Let $n$ be a positive odd integer, and $I$ a set of representatives of all nonzero classes in $n^{-1}\Lambda/\Lambda$, so $|I|=n^2-1$. We have
$$
S_*(nz)^2=n^2 S_*(z)^{2n^2}\prod_{P\in I}(W(z)-W(P)).
\tag{1}
$$
Near zero this is the squared product argument of [the curve norm proof](the-curve-norm-law-from-a-prime-to-p-isogeny.md#the-sigma-product-and-its-constant), using the distribution relation and $\alpha=\alpha'=n$, so the coordinate sum is zero. That algebraic calculation of the squared identity does not require the coordinates to be integral. Both sides are meromorphic functions on the plane and agree near zero, hence everywhere as meromorphic functions. [Formal squared product and its integral factor](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/UnramifiedIntegrals/FgIsoU.lean#L53)

Under $\iota$, write $x_P=\iota(W(P))$ and $e(t)=t^2x(t)$ as in the short-model chart. Let $f$ be the curve exponent with $S_*(\ell(t))=t\exp(-f(t))$ in the formal identity at zero, with the coefficients mapped by $\iota$. The parallelogram for $f$ has integral exponential as proved in [the formal sigma note](from-formal-sigma-addition-to-the-curve-biextension.md). For integral $[n]t=\ell^{-1}(n\ell(t))$, substitute $[n]t,t$ in the parallelogram to get
$$
f([n+1]t)+f([n-1]t)\sim 2f([n]t)+2f(t).
$$
Induction from $n=0,1$ gives $f([n]t)\sim n^2 f(t)$. Thus
$$
U(t)=\exp\bigl(2(f([p]t)-p^2 f(t))\bigr)
$$
is integral with constant term $1$. Taking the formal equality (1) for $n=p$, mapping its coefficients, and substituting $z=\ell(t)$ gives
$$
M_p(t)^2=t^2 U(t) G(t),\qquad
G(t)=p^2\prod_{P\in I}\bigl(e(t)-x_Pt^2\bigr).
\tag{2}
$$
Consequently $G$ is integral, by dividing $M_p^2$ by $t^2$ and the integral unit $U$.

## The product evaluated at a half-period

Take a basis period $\omega$ and $A=\omega/2$, a nonidentity half-period. In the decomposition of the zeta quasi-period, $\eta(w)=s_2 w+b\bar w$. The log derivative of $S_*(z+\omega)/S_*(z)$ is $b\overline{\omega}$. Evaluating the resulting shift law at $z=-\omega/2$ and using oddness gives
$$
S_*(z+\omega)=-\exp(b\overline{\omega}(z+\omega/2))S_*(z).
$$
By iteration, the shift by $m\omega$ has sign $(-1)^m$ and exponent $b m\overline{\omega}(z+m\omega/2)$. Here the ratio at the half-period is defined since the sigma zeros are precisely $\Lambda$.

Put $k=3W(A)^2-g_2(\Lambda)/4$. The two-variable sigma addition formula from the formal proof also holds meromorphically in the complex variables, since the local Taylor identities agree. Take $u=A+z,v=A$. It gives
$$
\frac{S_*(\omega+z)S_*(z)}{S_*(A+z)^2S_*(A)^2}=W(A)-W(A+z).
$$
Now $W'(A)=0$ by evenness and periodicity. The coefficient of $z^2$ on the right is $-W''(A)/2=-k$. On the left it is $-\exp(b|\omega|^2/2)/S_*(A)^4$ by the shift and $S_*'(0)=1$. Hence $k S_*(A)^4=\exp(b|\omega|^2/2)$. For odd $n=2m+1$, apply the shift by $m\omega$ at $z=A$, square the result, and use $2m(m+1)=(n^2-1)/2$. This gives
$$
\frac{S_*(nA)^2}{S_*(A)^{2n^2}}=k^{(n^2-1)/2}.
$$
By (1), the same ratio is $n^2\prod_{P\in I}(W(A)-W(P))$. This identity at $n=p$ is the point at which the bound on $G$ becomes sharp. [The isogeny product at a nonidentity half-period](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/UnramifiedIntegrals/FgAnTwo.lean#L104)

The half-period point on the local curve is a nonzero $2$-torsion point, so $a=\iota(W(A))$ is integral by the prime-to-$p$ torsion argument. It has $y=0$ and $a$ is a root of the cubic. Because the discriminant is a unit, $3a^2-g_2/4=\iota(k)$ is a unit. Taking norms of the half-period product therefore yields
$$
1=\lVert p\rVert^2\prod_{P\in I}\lVert a-x_P\rVert
\le\lVert p\rVert^2\prod_{P\in I}\max(1,\lVert x_P\rVert).
\tag{3}
$$
Only coefficients and scalar identities are mapped by $\iota$; the norm in (3) is on $\mathbb C_p$.

## The first maximal coefficient in the product

Each series $e(t)-x_Pt^2$ has coefficient norms bounded by $C_P=\max(1,\lVert x_P\rVert)$, and it first attains that bound at degree zero if $\lVert x_P\rVert\le1$, otherwise at degree two. The latter follows from integrality of $e$ and the strict larger norm of $x_P$. In a finite product of such series, the first degree at which the product reaches the product of the bounds is the sum of those first degrees. At that degree there is exactly one term achieving the bound, obtained by taking the first maximal coefficient in every factor. Each other term must use at least one earlier coefficient in some factor and thus has strictly smaller norm. Earlier degrees also have smaller norm. Applying this to $G$, it has a coefficient of norm $\lVert p\rVert^2\prod_P C_P$ by degree $2|I|$. Integrality of $G$ makes this norm at most $1$, and (3) makes it at least $1$. It is therefore $1$.

Multiplication by $U$ in (2), whose constant term is $1$ and whose other coefficients are integral, preserves the first degree of a coefficient of norm one, by the same argument. Thus $M_p^2$ has a unit coefficient at degree at most $2+2|I|=2p^2$. If all coefficients of $M_p$ through degree $p^2$ had norm strictly less than one, every product contributing to a coefficient of $M_p^2$ through degree $2p^2$ would contain one of them, and the finite sum would have norm strictly less than one. This contradiction proves the height bound. [First coefficient of maximal norm in the finite product](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/UnramifiedIntegrals/FgGauss.lean#L113)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
