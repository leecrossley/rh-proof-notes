# A Jacobi expansion evaluates the scalar theta mean square

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $\Lambda=\omega(\mathbb Z+\tau\mathbb Z)$ be a complex lattice with $\omega\ne0$, $\tau$ in the upper half-plane and $y=\operatorname{Im}\tau$. Let $t$ be a nonzero half-period class, so $2t\in\Lambda$, $t\notin\Lambda$. Write $f_t$ for the normalized translate of the [modified sigma](the-modified-sigma-has-the-canonical-period-multiplier.md) by $t$, and use the probability-normalized mean square $\mathcal N_\Lambda(f_t)$ with Gaussian $e^{-\pi|z|^2/\operatorname{area}(\Lambda)}$. For $a,b\in\{0,1\}$ put
$$
\Theta_{ab}(w,\tau)=
 \sum_{n\in\mathbb Z}\exp\!\left(
   \pi i(n+a/2)^2\tau+2\pi i(n+a/2)(w+b/2)\right).
$$
There is a unique $(a,b)\ne(1,1)$ with
$$
 t/\omega\equiv (1-b)/2+(1-a)\tau/2\pmod{\mathbb Z+\tau\mathbb Z}.
\tag{1}
$$
Then $\Theta_{ab}(0,\tau)\ne0$, and
$$
\mathcal N_\Lambda(f_t)=\frac{1}{\sqrt{2y}\,|\Theta_{ab}(0,\tau)|^2}.
\tag{2}
$$
For the host CM lattice, one can choose the period basis with $1/2\le y\le\sqrt d/2$. There is an absolute $C_0\ge1$ with $|\Theta_{ab}(0,\tau)|\le C_0$ for all these bases, independent of the lattice and the characteristic.

**The scalar theta with the given periods.** The series defining $\Theta_{ab}$ converges locally uniformly in $w$ by the Gaussian decay from $y>0$, so is entire. For shifts by $1$ and $\tau$ its factors are
$$
 \Theta_{ab}(w+1,\tau)=(-1)^a\Theta_{ab}(w,\tau),\qquad
 \Theta_{ab}(w+\tau,\tau)=(-1)^b e^{-\pi i\tau-2\pi i w}\Theta_{ab}(w,\tau).
$$
The first is termwise and the second is obtained by replacing $n$ by $n+1$. The function is nonzero because its Fourier coefficients on a real unit interval, after removing the factor $e^{\pi i a w}$, are nonzero. Its logarithmic derivative is unchanged under translation by $1$ and shifted by $-2\pi i$ under translation by $\tau$. The integral of this logarithmic derivative around a fundamental parallelogram with no zeros on its boundary is therefore $2\pi i$. By the argument principle there is one zero in a period cell, counted with multiplicity.

For the odd characteristic $(1,1)$, replacing $n$ by $-n-1$ shows that the series is odd, so its zero is at $0$. For every $(a,b)$, shift $w$ in the odd theta by $t/\omega$ given by (1). Completing the square in the summation exponent and reindexing identifies it with $\Theta_{ab}(w,\tau)$ times a nonvanishing exponential and a nonzero constant. Concretely, the added $(1-a)\tau/2$ changes the summation offset $1/2$ to $1/2+(1-a)/2$, congruent to $a/2\bmod1$, and the added $(1-b)/2$ changes $1/2$ in the $w$-offset to the same class as $b/2\bmod1$. Hence the unique zero of $\Theta_{ab}$ is the class of the negative shift, which here equals the shift. For nonzero $t$ the characteristic is even and the value at zero is nonzero.

In the variable $w=z/\omega$, the function
$$
F(w)=e^{\pi w^2/(2y)}\frac{\Theta_{ab}(w,\tau)}{\Theta_{ab}(0,\tau)}
$$
has the Hermitian translation multipliers for the form $w\bar v/y$. For $v=1$ the extra sign is $(-1)^a$; for $v=\tau$ it is $(-1)^b$, using $\tau-\bar\tau=2iy$ to combine the exponential terms. The half-period translate $f_t$ has these same signs: the sign at $1$ and at $\tau$ is the unshifted sign $-1$ times $e^{\pi i B(v,2t/\omega)}$, with $B(w,v)=\operatorname{Im}(w\bar v)/y$. Writing $2t/\omega\equiv r+s\tau\bmod 2(\mathbb Z+\tau\mathbb Z)$, equation (1) gives $r\equiv1-b,\ s\equiv1-a$, and the two sign factors follow. The Gaussian law for all periods follows from the two generators. The scalar theta space with these signs is one-dimensional by the [one-pole argument](a-fourfold-average-generates-the-standard-theta-line.md). Both functions equal $1$ at zero, so $f_t(\omega w)=F(w)$.

**The Gaussian integral.** The density of $F$ is $|\Theta_{ab}(w,\tau)/\Theta_{ab}(0,\tau)|^2 e^{-2\pi(\operatorname{Im}w)^2/y}$. In the normalized cell write $w=s+u\tau$, with $0\le s,u<1$; the Haar probability measure is $ds\,du$. Integrating in $s$ removes all products of distinct Fourier modes because their frequencies differ by nonzero integers. The remaining density integral, before dividing by $|\Theta_{ab}(0,\tau)|^2$, is
$$
 \int_0^1\sum_{n\in\mathbb Z} e^{-2\pi y(n+a/2+u)^2}\,du
 =\int_{\mathbb R}e^{-2\pi y v^2}\,dv
 =\frac{1}{\sqrt{2y}} .
$$
Termwise integration in $s$ follows from uniform convergence on the compact cell closure. The change to the real integral uses nonnegative summands and the consecutive intervals of integration. This proves (2).

**Uniform bounds for the CM period basis.** Let $\Lambda$ be a host CM lattice stable under $\vartheta=(1+i\sqrt d)/2$. Choose a shortest nonzero period $\omega$, which is primitive and hence extends to an oriented integral basis of $\Lambda$. Subtract an integer multiple of $\omega$ from the second basis vector to arrange $|\operatorname{Re}\tau|\le1/2$. Its length is at least $|\omega|$, so $|\tau|\ge1$ and $y\ge\sqrt3/2$. Stability gives $\vartheta \omega=A\omega+B\omega\tau$ with $A,B\in\mathbb Z$. Taking imaginary parts after dividing by $\omega$ gives $By=\sqrt d/2$, so $B\ge1$ and $y\le\sqrt d/2$. At $y\ge1/2$ the absolute value of the theta constant is at most
$$
 C_0=\max_{a=0,1}\ \sum_{n\in\mathbb Z} e^{-\pi(n+a/2)^2/2}.
$$
This is finite and at least $1$.

**Lean correspondence.** The characteristic and its defining sum are [`thetaChar`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/BlockTheory/GlobalSignature/JacobiThetaHalfCharacteristic.lean#L13) and [`thetaChar_eq_tsum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/BlockTheory/GlobalSignature/JacobiThetaHalfCharacteristic.lean#L28). The source identifies the theta through its odd characteristic, evaluates the normalized translate and finds the unique even characteristic in [`meanSquare_normalizedThetaTwoTorsion`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MeanSquareNormalizedThetaTwoTorsion.lean#L103), [`existsUnique_char`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MeanSquareNormalizedThetaTwoTorsion.lean#L182) and [`normTheta0`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MeanSquareNormalizedThetaTwoTorsion.lean#L206). The later scalar mean bound uses the uniform constant and the two bounds on $y$ in [the positive-part estimate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DecoratedLatticeProofs/ThetaZeroMeanLogNormConjugatesOfWeber.lean#L105).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
