# Excluding exceptional zeros in the thin-scale character family

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E8%96%84%E5%B0%BA%E5%BA%A6%E6%89%80%E7%94%A8%E7%9A%84%E7%89%B9%E5%BE%81%E6%B2%A1%E6%9C%89%E4%BE%8B%E5%A4%96%E9%9B%B6%E7%82%B9.md)

A datum `D7` has distinct primes $q,d$, a positive integer $Q_S$ coprime to $qd$, and a surjective Artin map $\mathrm{Art}:(\mathbb Z/N_E\mathbb Z)^\times\to G$ with $N_E=Q_Sqd$ and $G$ the attached Galois group. Let $B_D$ be the odd part of $Q_S$. The family $\mathcal X_D$ (`IsCharED D`) consists of primitive characters $\chi\bmod N$ agreeing on integers coprime to $N_E$ with $\psi(\mathrm{Art}(a))$ for a group character $\psi:G\to\mathbb C^\times$.

For $H>0$, `GoodFor H χ` means $\chi$ is real and primitive of modulus at most $H$, with $L(s,\chi)\ne0$ for $\Re s>1-1/400$ and $|\Im s|\le H$. For $Y>1$, $\epsilon>0$, let $X_1=e^{Y^{\epsilon/5}}$, $X_2=e^{Y^{\epsilon/5}(\log Y)^2}$. The hypothesis `BoxE D Y ε` requires `GoodFor` for real characters in $\mathcal X_D$ with $d\mid N$ at height $H=8B_D X_1X_2$, and for those with $q\mid N,\ d\nmid N$ at $H=8 B_DX_1$.

**Proposition.** For every integer $B\ge1$ there is $a>0$ such that, whenever $B_D\le B$ and `BoxE D Y ε` holds for some $Y>1,\epsilon>0$, all $\chi\in\mathcal X_D$ and their zeros with $0<\Re\rho<1$ satisfy
$$
1-\Re\rho\ge\frac{a}{\lambda_D+\log(|\Im\rho|+3)},\qquad
\lambda_D=\max(1,\log N_E).
\tag{1}
$$
This is `ZeroFreeE D a`.

The character $\psi\circ\mathrm{Art}$ on the units modulo $N_E$ extends to a Dirichlet character of that modulus. Its lift to $NN_E$ agrees with the lift of $\chi$ because the values agree on units there. The lifts preserve the inducing primitive character, so $N\mid N_E$. Taking $\psi^{-1}$ shows that $\mathcal X_D$ is closed under inversion.

A real primitive character cannot have $N=16k$. Reduction to units modulo $8k$ is surjective and has kernel of elements $1+8kt$. Every kernel element is the square of the unit $1+4kt$ modulo $16k$. Since a real character is trivial on squares, it would descend to $8k$. Thus if neither $q$ nor $d$ divides the conductor of a real member, then $N\mid Q_S$ and $N\mid8B_D$. For such conductors $N\ge3$ there are finitely many possibilities $N\le8B$, and the primitive characters are nonprincipal, analytic and nonzero at $1$. Some $[1-a_0,1]$ with $a_0>0$ depending only on $B$ is free of their real zeros. If $q$ or $d$ divides the conductor, `BoxE` excludes real zeros strictly above $1-1/400$.

The [zero-free region with uniqueness](unique-simple-exceptional-zero.md) gives a constant $c_6>0$ such that a primitive zero for $N\ge3$ in $\Re\rho\ge1-c_6/\log(\max(N,N|\Im\rho|))$ belongs to a real character and is real. For $\zeta$, $1-\Re\rho\ge c_6/\log(|\Im\rho|+3)$. Take $a=\min(c_6,a_0,1/400)$. Modulus $2$ has no primitive character and modulus $1$ follows from the zeta bound. For $N\ge3$, failure of (1) would put $\rho$ in the primitive region since $\lambda_D+\log(|\Im\rho|+3)\ge\log(\max(N,N|\Im\rho|))$. It would be real with $\Re\rho>1-a$, excluded by the two conductor cases.

In the project family `FamP ε`, one eventual constant $C_{\rm o}$ gives $o\le C_{\rm o}$, $Q_S\le C_{\rm o}n$, $n\le o\,2^e$, and $2^{e+2}\mid Q_S$, for the size $n$, order parameter $o$, and tower exponent $e$ of each datum. Hence $2^eB_D\le Q_S\le C_{\rm o}^2\,2^e$, so $B=\lceil C_{\rm o}^2\rceil$ works for the [thin-scale estimate](weighted-prime-sum-at-thin-scale.md) throughout the family.

## Lean correspondence

- `IsCharED`, `GoodFor`, `BoxE` and `NE` give the definitions. `level_dvd_condN` and `invE_holds` provide the conductor and inversion properties. [Definitions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GeneralLinearActions/FiltrationCocycleLiftCriterion.lean#L36) · [Conductor](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/FirstClaimLemmaTwoFourOfLemmaTwoThree.lean#L2439)
- `not_sixteen_dvd_of_real` and `realClassE_holds` classify the conductors. `zeroFreeE_of` gives (1) and `oddQS_le_Co` supplies uniformity. The [prime-pair selection](prime-pair-selection.md) provides `BoxE` upstream. [Classification](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/FirstClaimLemmaTwoFourOfLemmaTwoThree.lean#L2449) · [Region](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/FirstClaimLemmaTwoFourOfLemmaTwoThree.lean#L3028) · [Odd part](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/FirstClaimLemmaTwoFourOfLemmaTwoThree.lean#L3056)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
