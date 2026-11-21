# Retaining the step size in a contour shift for smoothed prime sums

[Chinese proof](../zh/%E5%B9%B3%E6%BB%91%E7%B4%A0%E6%95%B0%E5%92%8C%E7%9A%84%E5%B7%AE%E5%88%86%E5%9C%A8%E7%A7%BB%E7%BA%BF%E6%97%B6%E6%80%8E%E6%A0%B7%E4%BF%9D%E7%95%99%E6%AD%A5%E9%95%BF.md) · [Reading and review status](../../STATUS.md)

For a Dirichlet character $\chi$ write

$$
A_\chi(y)=\sum_{1\le n\le y}\Lambda(n)\chi(n)(y/n-1),
\qquad D_\chi(s)=-L'(s,\chi)/L(s,\chi).
$$

**Claim.** Fix $0<\delta\le1/800$. Some $K\ge0$ works for every nonprincipal character $\chi$ modulo an integer $q\ge1$, $Q\ge\max(2,q)$, $z\ge1$ and $0<\eta\le1$, under the hypothesis that $L(w,\chi)\ne0$ throughout $\operatorname{Re}w>1-1/400$, $|\operatorname{Im}w|\le Q$. With $\sigma=1-1/400+\delta$,

$$
|A_\chi(z(1+\eta))-A_\chi(z)-z\eta D_\chi(1)|
\le K\log Q\bigl((\log Q)\eta z^\sigma+z^2/Q\bigr). \tag{1}
$$

The rectangle is `ZeroFreeBox Q χ`. The modulus need not be the conductor. The [tail proof](zero-free-rectangle-tail.md) divides by the step size, so the factor $\eta$ on the left vertical line matters.

## Bound the logarithmic derivative inside the rectangle

We show $|D_\chi(s)|\ll_\delta\log Q$ when $\operatorname{Re}s\ge\sigma$ and $|\operatorname{Im}s|\le Q-1$. For $\operatorname{Re}s\ge11/10$ the absolutely convergent series $\sum_{n\ge1}\Lambda(n)\chi(n)n^{-s}$ is uniformly bounded.

Otherwise write $t=\operatorname{Im}s$ and centre a disk at $a=21/20+it$ with radius $11/20$. Then $|s-a|\le(11/20)/6$. The character is nonprincipal, so $L(w,\chi)$ is entire, and the disk lies in $\operatorname{Re}w\ge1/2$. The [growth bound](../zh/%E6%80%8E%E6%A0%B7%E7%94%A8%E6%9C%89%E9%99%90%E5%B7%AE%E5%88%86%E6%8E%A7%E5%88%B6L%E5%87%BD%E6%95%B0%E7%9A%84%E5%A2%9E%E9%95%BF.md) gives $|L(w,\chi)|\ll q^4(|t|+2)^4$ there. The absolutely convergent reciprocal Euler product at $a$ gives $|1/L(a,\chi)|\le\zeta(21/20)\le21$. Apply the [local zero and remainder estimate](../zh/%E5%9C%86%E7%9B%98%E9%87%8C%E7%9A%84%E9%9B%B6%E7%82%B9%E6%80%8E%E6%A0%B7%E6%8E%A7%E5%88%B6%E5%AF%B9%E6%95%B0%E5%AF%BC%E6%95%B0.md) with the normalized inner radius $1/6$ and the zero radius $1/3$. The number of zeros counted with multiplicity within $(11/20)/3$ of $a$, and the remainder after subtracting their simple fractions from the log derivative at $s$, are both $O(\log(q(|t|+2)))=O(\log Q)$.

For each such zero $\rho$, $|\operatorname{Im}\rho|\le|t|+(11/20)/3<Q$. The zero-free hypothesis implies $\operatorname{Re}\rho\le1-1/400$, so $|s-\rho|\ge\delta$. The sum of the zero fractions is therefore $O_\delta(\log Q)$, proving the bound. Lean uses another growth bound in the given disk, with the same radii and separation from zeros.

## Mellin inversion for the ramp

For $y\ge1$ put $F_y(w)=D_\chi(w)y^w/[w(w-1)]$. Then

$$
A_\chi(y)=\frac1{2\pi}\int_{\mathbb R}F_y(2+it)\,dt. \tag{2}
$$

In fact, for $\operatorname{Re}w>1$ the [ramp integral](pole-data.md#integration-against-the-ramp) gives

$$
\int_0^\infty A_\chi(y)y^{-w-1}\,dy
=\sum_{n\ge1}\Lambda(n)\chi(n)\int_n^\infty (y/n-1)y^{-w-1}\,dy
=\frac{D_\chi(w)}{w(w-1)} .
$$

The sum and integral can be interchanged by the same calculation with coefficients in absolute value and $w$ replaced by $\operatorname{Re}w$. Set $v=\log y$. At $w=2+it$ this formula is the Fourier transform with kernel $e^{-itv}$ of $e^{-2v}A_\chi(e^v)$. The latter function is continuous, since new summands start at zero, and integrable by the absolute integral estimate. Its transform is integrable because $D_\chi(2+it)$ is bounded and the denominator grows quadratically. Fourier inversion proves (2).

## Take the difference on the left side of the contour

Take $T=Q/2\le Q-1$. In the closed rectangle $\sigma\le\operatorname{Re}w\le2$, $|\operatorname{Im}w|\le T$, $D_\chi$ is holomorphic. The only possible pole of $F_y$ there is at $1$, with residue $yD_\chi(1)$. The pole of the denominator at $0$ is outside. By the residue theorem and (2), $A_\chi(y)-yD_\chi(1)$ is the signed sum of the integral on the left edge, the two horizontal integrals and the tails $|t|>T$ on the right, with the normalization $1/(2\pi)$ and the horizontal direction factors of modulus one.

Use this formula at $y=z(1+\eta)$ and at $y=z$. For both, $z\le y\le2z$. On the right tail $|F_y(2+it)|\ll z^2/t^2$, so each tail is $O(z^2/T)$. On a horizontal edge we have $|w|,|w-1|\ge T$, $|y^w|\le(2z)^2$, and $|D_\chi(w)|\ll_\delta\log Q$. Its length is at most two, giving $O_\delta(z^2\log Q/T^2)$ per edge. Thus the combined contribution of those terms in the difference is $O_\delta(z^2\log Q/Q)$.

On the left edge take the difference of the kernels before bounding it. The identity

$$
(1+\eta)^w-1=w\int_0^{\log(1+\eta)}e^{vw}\,dv
$$

gives $|(1+\eta)^w-1|\le2\eta|w|$, since $0<\sigma<1$ and $0<\eta\le1$. Therefore

$$
|F_{z(1+\eta)}(w)-F_z(w)|
\le |D_\chi(w)|\,\frac{2\eta z^\sigma}{|w-1|}.
$$

Besides producing $\eta$, this cancels the factor $w$ in the denominator. As $1-\sigma\ge1/800$,
$\int_{-T}^{T}dt/|\sigma+it-1|\ll\log Q$. To see this split at $|t|=1/800$, using $800$ inside and $1/|t|$ outside. The left-edge difference is $O_\delta(\eta z^\sigma\log^2 Q)$. Combining the contributions yields (1).

## Lean references and review

- [`tail_box_negLD`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/TailBox.lean#L35) uses [`landau_lemma_lfunction_zeros`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/ExceptionalZeroBounds/LandauLemmaLfunctionZeros.lean#L9) and the rectangle to bound the logarithmic derivative.
- The inversion and transform are in [`PerronChi.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/ExceptionalZeroBounds/PerronChi.lean#L236), with the rectangle formula in [`RectShiftChi.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/ExceptionalZeroBounds/RectShiftChi.lean#L114). [`tail_shift_identity`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/TailContourA.lean#L20) specializes to the empty set of zeros.
- [`tail_kernel_cpow`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/TailKernel.lean#L27) retains the step size, [`tc_left_int`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/TailContourB.lean#L157) controls the integral, and [`tail_contour`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/TailContour.lean#L14) combines the edges.

English translation draft. The rectangle is a hypothesis of this proof.
