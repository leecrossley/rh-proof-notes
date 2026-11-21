# The smoothed explicit formula retaining zeros near one

[Chinese proof](../zh/%E5%B9%B3%E6%BB%91%E6%98%BE%E5%BC%8F%E5%85%AC%E5%BC%8F%E6%80%8E%E6%A0%B7%E5%8F%AA%E7%95%99%E4%B8%8B%E9%9D%A0%E8%BF%91%E4%B8%80%E7%9A%84%E9%9B%B6%E7%82%B9.md)

For a character $\chi$ modulo $M$, write $S_\chi(y)=\sum_{n\le y}\Lambda(n)\chi(n)(y/n-1)$. Let $F_\chi=L(s,\chi)$ for nonprincipal $\chi$ and $F_\chi=(s-1)L(s,\chi_0)$ for the principal character, continued holomorphically at $1$. Then $F_\chi(1)\ne0$.

**Proposition.** For each $0<\kappa\le1/20$ there is $C>0$ such that the following holds for each integer $M\ge3$, character $\chi\bmod M$, and $T\ge2$. There exist a finite set $Z$ of zeros of $F_\chi$ with multiplicities $m_\rho\ge1$, and a constant $K_\chi$, all independent of $y$. The set contains only zeros with $\Re\rho>1-\kappa,\ |\Im\rho|\le T+1$ and includes all zeros with $\Re\rho\ge1-\kappa/2,\ |\Im\rho|\le T$. For each real $t$,
$$
\sum_{\rho\in Z,\ |\Im\rho-t|\le1}m_\rho\le C\log(M(|t|+2)).
$$
For $y\ge2$,
$$
\left|\frac{S_\chi(y)}y-K_\chi-\mathbf1_{\chi=\chi_0}(\log y-1)
+\sum_{\rho\in Z}\frac{m_\rho y^{\rho-1}}{\rho(\rho-1)}\right|
\le C\left((MT)^C y^{-\kappa/2}+\frac{\log y\,\log^2(MT)}T\right).
\tag{1}
$$
Here $K_\chi=-F'_\chi(1)/F_\chi(1)$. This is the formula used before taking differences in the [larger-modulus range](relative-prime-number-theorem-two-ranges.md#the-larger-modulus-range).

## Local bounds and the choice of contour

At $z_0=101/100+it$, use an outer radius $2/5$. The relative maximum modulus $|F_\chi(z)/F_\chi(z_0)|$ is at most $B\ll M(|t|+3)^2$. Indeed for $\Re z\ge1/2$ periodic sums give $|L(z,\chi)|\ll M(1+|z|)$ for nonprincipal $\chi$. For the principal character use
$$
\zeta(z)=\frac z{z-1}-z\int_1^\infty \{u\}u^{-z-1}\,du.
$$
Thus $|(z-1)\zeta(z)|\ll(1+|z|)^2$, and the extra Euler factors cost at most $2^{\omega(M)}\le M$. At the center, the inverse Euler product is at most $\zeta(101/100)$ in modulus and the principal factor $|z_0-1|\ge1/100$.

The [local disk theorem](../zh/%E5%9C%86%E7%9B%98%E9%87%8C%E7%9A%84%E9%9B%B6%E7%82%B9%E6%80%8E%E6%A0%B7%E6%8E%A7%E5%88%B6%E5%AF%B9%E6%95%B0%E5%AF%BC%E6%95%B0.md) bounds the total multiplicity within radius $2/15$ by $O(\log B)$ and gives, for each nonzero point $s$ of $F_\chi$ within radius $1/15$,
$$
\frac{F_\chi'(s)}{F_\chi(s)}=\sum_{|\rho-z_0|\le2/15}\frac{m_\rho}{s-\rho}+O(\log B).
\tag{2}
$$
The phrase “nonzero point” means $F_\chi(s)\ne0$. Zeros with $\Re\rho\ge9/10$ satisfy $|\Re\rho-101/100|\le11/100$ by nonvanishing for $\Re s\ge1$. Cover a unit-height window with centers spaced by at most $1/7$. Each such zero lies within a disk of radius $2/15$ because its height differs from some center by at most $1/14$. Summing the disk counts gives $O(\log(M(|t|+2)))$ per window and $O((T+1)\log(M(T+2)))$ in $\Re\rho\ge9/10,\ |\Im\rho|\le T+3$.

Let $N$ count the distinct zeros in that rectangle. In any interval of length $h$ there is a point at distance at least $h/(2(N+1))$ from all of $N$ prescribed reals: take the $N+1$ equally spaced subinterval midpoints, each prescribed number excluding at most one. Apply this to the real parts and absolute imaginary parts to choose
$$
\sigma_1\in[1-\kappa,1-3\kappa/4],\qquad T'\in[T,T+1].
$$
The left line and horizontals avoid all relevant local zeros by at least $\Delta=\kappa/(8(N+1))$, with $\Delta^{-1}\ll_\kappa (T+1)\log(M(T+2))$. A local zero outside the rectangle counted above is already farther away, either in real part on the left line or in height on a horizontal. On a horizontal with $\Re s\ge 19/20$, a zero with real part below $9/10$ is also farther away by its real part.

At edge points with $19/20\le\Re s\le107/100$, apply (2) with $t=\Im s$, since $|s-z_0|\le3/50<1/15$. For $D_\chi=-L'/L$ this gives
$$
|D_\chi(s)|\ll \frac{\log(M(|t|+2))}{\Delta}
+\frac{\mathbf1_{\chi=\chi_0}}{|s-1|}.
\tag{3}
$$
On remaining portions to the right, absolute convergence at $107/100$ gives a constant bound. Take $Z$ to be all zeros with $\Re\rho>\sigma_1$, $|\Im\rho|<T'$ and their actual multiplicities. The contour parameters give the required inclusions, and the unit-window bound applies to this subset.

## Residues and errors

On $c=1+1/\log y$ the integral of $D_\chi(s)y^s/[s(s-1)]$, divided by $2\pi i$, equals $S_\chi(y)$ by [ramp Mellin inversion](contour-shift-step-size.md). Truncate at $\pm T'$ and shift to $\sigma_1$. Each $\rho\in Z$ gives residue $-m_\rho y^\rho/[\rho(\rho-1)]$. At $1$ use
$$
D_\chi(s)=\frac{\mathbf1_{\chi=\chi_0}}{s-1}-\frac{F_\chi'(s)}{F_\chi(s)}.
$$
The analytic term gives residue $K_\chi y$. For the principal character the double pole contributes the derivative of $y^s/s$ at $1$, namely $y(\log y-1)$. The kernel pole at $0$ lies outside.

Divide the errors by $y$. On the original tail, $|D_\chi(c+it)|\ll\log y$, $y^c=ey$ and $|s(s-1)|\ge t^2$, giving $O(\log y/T)$. On the horizontals, (3), $|s(s-1)|\ge T'^2$, and bounded edge length give $O_\kappa(\log^2(MT)/T)$. On the left, $|s(s-1)|\ge\sigma_1(1-\sigma_1)\gg\kappa$ and the pole term in (3) is at most $4/(3\kappa)$. The error is $O_\kappa((T+1)^2\log^2(MT)y^{\sigma_1-1})$, which fits the first term on the right of (1). All residues and errors now give (1). In particular the same $Z$ is available at both endpoints of a subsequent difference.

## Lean correspondence

- `ex_local`, `ex_box` and `ex_choose` give the disk formula, the unit-window count and the contour choice. [Disk](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTExplLocL.lean#L86) · [Count](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTExplBox.lean#L115) · [Choice](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTExplPick.lean#L43)
- `ex_negLD_bound` gives (3), `ex_rect_Fchi` computes the residues, `exm_core` bounds the integrals and `smoothed_explicit_formula` assembles (1). [Log derivative](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTExplNeg.lean#L27) · [Residues](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTExplRectF.lean#L154) · [Integrals](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTExplMainB.lean#L31) · [Conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTExplMain.lean#L15)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
