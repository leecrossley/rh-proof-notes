# A thin-scale weighted prime-sum estimate from a zero-free region

[Chinese proof](../zh/%E6%97%A0%E9%9B%B6%E7%82%B9%E5%8C%BA%E5%9F%9F%E6%80%8E%E6%A0%B7%E7%BB%99%E5%87%BA%E8%96%84%E5%B0%BA%E5%BA%A6%E7%9A%84%E5%8A%A0%E6%9D%83%E7%B4%A0%E6%95%B0%E5%92%8C%E7%95%8C.md)

Let $\mathcal X$ be a family of primitive Dirichlet characters closed under inversion, with $\log N\le\lambda$ for each modulus $N$ in the family and $\lambda\ge1$. Assume every zero with $0<\Re\rho<1$ of a character in the family satisfies
$$
1-\Re\rho\ge a/(\lambda+\log(|\Im\rho|+3))
\tag{1}
$$
for one $a>0$. Let $A_\chi(y)=\sum_{n\le y}\Lambda(n)\chi(n)(y/n-1)$ and $\psi_{0,\chi}(u)=\sum_{n\le u}\Lambda(n)\chi(n)-\mathbf1_{\chi=\chi_0}u$. The project function `gChi χ y` means $A_\chi(y)+yL'(1,\chi)/L(1,\chi)$ for nonprincipal $\chi$, and $A_\chi(y)-y\log y+(1+\gamma)y$ for the trivial character of modulus $1$.

**Proposition.** For every $\epsilon,a>0$ there exist $c>0$ and $x_0>1$. For $x\ge x_0$, assume that $1\le\lambda\le8x^{\epsilon/5}(\log x)^2$ and that $\mathcal X$ satisfies (1) and the stated conductor bound. Then all $\chi\in\mathcal X$ and $y\ge e^{x^{\epsilon/3}}/3$ satisfy
$$
|g_\chi(y)|\le ye^{-c x^{\epsilon/8}}.
\tag{2}
$$
This is `ThinE` for the application $\mathcal X=\mathcal X_D$ and $\lambda=\max(1,\log N_E)$. The [exceptional-zero exclusion](no-exceptional-zero-for-thin-scale-family.md) supplies (1) from `BoxE` and the odd-part bound. The box hypothesis `PropTwoSixBoxHypothesis` supplies $\log N_E\le2x^{\epsilon/5}(\log x)^2$.

## A reciprocal bound in the explicit formula

Let $Z_\chi(T)$ consist of the zeros with $0<\Re\rho<1$, $|\Im\rho|<T$, with multiplicities $m_\chi(\rho)$. The functional equation reflects $\rho$ to a zero $1-\rho$ for $\chi^{-1}$, so (1) gives $\Re\rho\ge a/(\lambda+\log5)\ge a/(3\lambda)$ for $|\Im\rho|\le2$. The `adm11` input, obtained from the [disk count](high-log-derivatives-from-nearby-zeros.md), is that for every primitive character $\chi\bmod N$ and real $v$, zeros at $0<\Re\rho<1$, $|\Im\rho-v|\le1$ are finite and have total multiplicity at most $C_{11}\log(N(|v|+2))$. The low zeros therefore have total multiplicity $O(\lambda)$ and each costs at most $3\lambda/a$ in the reciprocal sum. For $2<|\Im\rho|<T$, group by the sign and $j=\lfloor|\Im\rho|\rfloor$. In each group $1/|\rho|\le1/j$, with multiplicity $O(\log(N(T+2)))$. The harmonic sum over $j$ gives
$$
\sum_{\rho\in Z_\chi(T)}m_\chi(\rho)/|\rho|\le C_2(\lambda+\log T)^2
\qquad(T\ge1).
\tag{3}
$$

The open-window [primitive explicit formula](truncated-explicit-formula-primitive.md), `adm7`, bounds the modulus of $\psi_{0,\chi}(u)+\sum_{\rho\in Z_\chi(T)} m_\chi(\rho)u^\rho/\rho$ by
$$
C_7\left(u\log^2(NuT)/T+\log(Nu)+\sum_{\rho\in Z_\chi(1)}m_\chi(\rho)/|\rho|\right)
$$
for $2\le T\le u$. For $u\ge e$ put $v=\log u$, $s=\sqrt v$, $T=e^s$, $b=\min(a/3,1)$, $E=e^{-bv/(\lambda+s)}$, and $W=v+\lambda$. In the zero sum $\lambda+\log(|\Im\rho|+3)\le3(\lambda+s)$, so $|u^\rho|\le uE$ and (3) bounds the sum by $C_2uEW^2$. Also $T^{-1}\le E$, $uE\ge1$, $\log(NuT)\le2W$, and $\log(Nu)\le W$. Thus
$$
|\psi_{0,\chi}(u)|\ll u(\log u+\lambda)^2
\exp\left(-\frac{b\log u}{\lambda+\sqrt{\log u}}\right).
\tag{4}
$$

## Smoothing and the tail

Termwise integration gives $A_\chi(y)=y\int_1^y(\psi_{0,\chi}(u)+\mathbf1_{\chi=\chi_0}u)\,du/u^2$. Equation (4) implies $\int_1^\infty|\psi_{0,\chi}(u)|du/u^2<\infty$ since for fixed $\lambda$ and $v\ge\lambda^2$, $v/(\lambda+\sqrt v)\ge\sqrt v/2$. For real $s_0>1$, absolute convergence gives
$$
s_0\int_1^\infty\psi_{0,\chi}(u)u^{-s_0-1}\,du
=-L'(s_0,\chi)/L(s_0,\chi)-\mathbf1_{\chi=\chi_0}s_0/(s_0-1).
$$
Let $s_0\downarrow1$ by dominated convergence. The right side tends to $-L'(1,\chi)/L(1,\chi)$ in the nonprincipal case and to $-1-\gamma$ in the principal case by the Laurent expansion of $\zeta$. Thus $g_\chi(y)=-y\int_y^\infty\psi_{0,\chi}(u)\,du/u^2$.

With $V=\log y$, (4) bounds $|g_\chi(y)|/y$ by a constant times $\int_V^\infty(v+\lambda)^2e^{-bv/(\lambda+\sqrt v)}dv$. For sufficiently large $x$, $V\ge x^{33\epsilon/100}$ and $\lambda\le V^{61/100}$ since $(33/100)(61/100)>1/5$. The integral is therefore at most
$$
4e^{-(b/4)V^{39/100}}\int_0^\infty v^2e^{-(b/4)v^{39/100}}\,dv.
$$
The integral is finite by the substitution $w=v^{39/100}$. As $(33/100)(39/100)>1/8$, we can absorb the constants and take $c=b/16$ in (2) by increasing $x_0$.

## Lean correspondence

- `zero_sum_core`, `psi_thin_core` and `thin_of_zeroFree` give (3), (4) and (2). `l21a` gives the tail identity, using a fixed-modulus Siegel–Walfisz bound for convergence. Here (4) also gives convergence. [Zero sum](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/FirstClaimLemmaTwoFourOfLemmaTwoThree.lean#L2028) · [Unsmoothing](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/FirstClaimLemmaTwoFourOfLemmaTwoThree.lean#L2355) · [Tail](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/FirstClaimLemmaTwoFourOfLemmaTwoThree.lean#L368)
- `gl2b2_thinIntegral` and `nonvanishing_of_hypothesis` handle the scale parameters. The application at $(x^2,\epsilon/2)$ gives the factor $8$. `litThin` combines `adm6`, `adm7` and `adm11` and `chosenThin_of_boxesN` applies it to the chosen candidates. [Integral](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/HookFormulaTorsion/CharacterEstimateOfHypothesis.lean#L151) · [Conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LitThin.lean#L8) · [Application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/MainSup.lean#L105)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
