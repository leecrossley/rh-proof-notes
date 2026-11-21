# The lattice isogeny and its weight-two constant

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Setting and statement

Let $\Lambda=\mathbb Z\omega_1+\mathbb Z\omega_2$ be a lattice in $\mathbb C$, with $\omega_1,\omega_2$ linearly independent over $\mathbb R$. Take a nonzero $\alpha\in\mathbb C$ satisfying $\alpha\Lambda\subseteq\Lambda$. Let $I$ be a set of representatives of the nonzero classes in $\alpha^{-1}\Lambda/\Lambda$. Put $N=1+|I|$. Let $\wp_\Lambda$ be the Weierstrass function and $\zeta_\Lambda$ the Weierstrass zeta function. For a period $\omega\in\Lambda$ put $\eta(\omega)=\zeta_\Lambda(z+\omega)-\zeta_\Lambda(z)$, which is constant in $z$ away from the poles. Extend $\eta$ real-linearly to $\mathbb C$. There are unique scalars $s_2,b\in\mathbb C$ such that $\eta(w)=s_2 w+b\overline w$. This defines the coefficient $s_2=s_2(\Lambda)$ used in the curve exponent. In Lean the two coefficients are obtained from the values at $\omega_1,\omega_2$. [The zeta function, its quasi-periods and s2](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/EisensteinTranslationProducts/SemiChar.lean#L8)

Then $N=|\alpha|^2$ and
$$
\begin{aligned}
\alpha^2\wp_\Lambda(\alpha z)
&=\wp_\Lambda(z)+\sum_{P\in I}\bigl(\wp_\Lambda(z+P)-\wp_\Lambda(P)\bigr),\\
\sum_{P\in I}\wp_\Lambda(P)&=(\alpha^2-N)s_2(\Lambda).
\end{aligned}
\tag{1}
$$
The first identity holds wherever $\alpha z\notin\Lambda$ and as an equality of meromorphic functions. These are `IsogenyP` and `QuasiPeriodConstIsogeny`. The sum over $I$ uses one representative per nonzero kernel class, so it is independent of that choice by periodicity.

## Periodicity and the pole comparison

The expansions
$$
\wp_\Lambda(z)=z^{-2}+\sum_{\lambda\in\Lambda\setminus\{0\}}
 \bigl((z-\lambda)^{-2}-\lambda^{-2}\bigr),\qquad
\zeta_\Lambda(z)=z^{-1}+\sum_{\lambda\in\Lambda\setminus\{0\}}
 \bigl((z-\lambda)^{-1}+\lambda^{-1}+z\lambda^{-2}\bigr)
$$
converge normally on compact sets away from the lattice. Indeed their tails are bounded there by a constant times $|\lambda|^{-3}$. A fixed annular band $n\le|\lambda|<n+1$ contains $O(n+1)$ lattice points, by placing disjoint disks of radius less than half the shortest nonzero lattice length about the points. The resulting series of bounds is summable. This also justifies termwise differentiation, giving $\zeta_\Lambda'=-\wp_\Lambda$ and $\wp_\Lambda'=-2\sum_{\lambda\in\Lambda}(z-\lambda)^{-3}$. The latter sum is absolutely convergent, so $\wp_\Lambda'$ is periodic. The shift difference of $\wp_\Lambda$ by either basis period is constant. It vanishes at minus the half-period, by the evenness of $\wp_\Lambda$. Those half-periods are outside the lattice, so this proves periodicity for both generators and therefore for every $\omega\in\Lambda$. Consequently the shift difference of $\zeta_\Lambda$ is constant, its value at that minus half-period is $2\zeta_\Lambda(\omega_i/2)$ by oddness, and the shifts add on $\Lambda$. This is the extension $\eta$ just defined. [Quasi-period and derivative inputs to the isogeny argument](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/EisensteinTranslationProducts/AnalyticIdentityTheorems/QuasiPeriodConstIsogeny.lean#L147)

The index of $\Lambda$ in $\alpha^{-1}\Lambda$ is the index of $\alpha\Lambda$ in $\Lambda$. It is the absolute determinant of multiplication by $\alpha$ in a lattice basis, equivalently the ratio of the two covolumes. Multiplication by a complex scalar has real determinant $|\alpha|^2$, proving $N=|\alpha|^2$.

For the first line of (1), both sides are $\Lambda$-periodic. Their poles are at $\alpha^{-1}\Lambda$. In each kernel class exactly one summand on the right has a pole, since $0$ and $I$ represent all classes, and its principal part is $(z-z_0)^{-2}$. This is also the principal part of $\alpha^2\wp_\Lambda(\alpha z)$ at $z_0$. The difference is therefore entire. It is bounded on a fundamental parallelogram and hence on the plane. Liouville's theorem makes it constant. The constant term of the Laurent expansions at zero on both sides is zero: the defining subtraction in $\wp_\Lambda$ gives this for the pole at zero, and the other summands have had their values at zero subtracted. Thus the constant is zero. [Weierstrass distribution by cancellation of all poles](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/EisensteinTranslationProducts/AnalyticIdentityTheorems/IsogenyP.lean#L74)

## The quasi-period comparison

Let $C=\sum_{P\in I}\wp_\Lambda(P)$. By the first identity of (1), the derivative of
$$
\alpha\zeta_\Lambda(\alpha z)-\zeta_\Lambda(z)
-\sum_{P\in I}\zeta_\Lambda(z+P)-Cz
$$
vanishes off $\alpha^{-1}\Lambda$. That complement is connected, for example by paths detouring around the finitely many lattice points on a given compact line segment. The expression is thus constant there. Subtract its value at $z$ from its value at $z+\omega$ for a nonzero $\omega\in\Lambda$. All arguments are away from poles, and $\alpha\omega\in\Lambda$, so
$$
C\omega=\alpha\eta(\alpha\omega)-N\eta(\omega)
=(\alpha^2-N)s_2\omega+
b(\alpha\overline{\alpha}-N)\overline\omega .
$$
The second term vanishes and $\omega\ne0$, giving the second line of (1). [The cancellation of the conjugate-linear quasi-period](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/EisensteinTranslationProducts/AnalyticIdentityTheorems/QuasiPeriodConstIsogeny.lean#L126)

If $\alpha=m+n\omega_K$, where $\omega_K=(1+\sqrt{-d_K})/2$ and the lattice is stable by $\omega_K$, then $N=m^2+mn+n^2(d_K+1)/4$. The equality $\alpha^2-N=\alpha(\alpha-\overline\alpha)$ identifies the scalar condition in the [local norm proof](the-curve-norm-law-from-a-prime-to-p-isogeny.md). The group of kernel classes is killed by $N$, since it is finite of order $N$. If $p\nmid N$ and the scaled torsion coordinates are integral and unramified at $p$, (1) gives the distribution and coordinate sum for that proof after mapping coefficients of the Laurent expansions to the local field. The required formal compatibility of the translated coordinates and the passage to all unramified scalar units are separate steps. [CM isogeny identities for the lattice endomorphisms](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/EisensteinTranslationProducts/EisensteinRecursion.lean#L16)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
