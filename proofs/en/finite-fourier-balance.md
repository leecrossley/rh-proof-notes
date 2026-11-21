# The finite Fourier identity for the prime-power count

[Chinese proof](../zh/%E5%89%A9%E4%BD%99%E7%B1%BB%E7%B4%A0%E6%95%B0%E5%92%8C%E4%B8%8E%E4%B8%BB%E9%A1%B9%E7%9A%84%E6%81%92%E7%AD%89%E5%BC%8F.md) · [Reading and review status](../../STATUS.md)

The window argument compares a weighted count of Frobenius classes with its main term. The exact difference is a finite Fourier combination of corrected prime sums. This calculation fixes both the weights at unramified and ramified primes and the sign of the nonprincipal correction.

## Data and statement

Let $H$ be a finite abelian group, written additively. Set $A=(\mathbb Z/2\mathbb Z)^2\times H$, $\Phi=\{(0,j,h)\in A\}$, $\Phi^c=A\setminus\Phi$, and $f=|\Phi|=2|H|$. The character group $\widehat A$ is written multiplicatively, with identity $1$. Let $c(i,j,h)=(-1)^i$. For $t\in H$, let $P_t(g)=g+(1,1,t)$. Restriction gives a bijection $P_t:\Phi^c\to\Phi$.

Fix natural numbers $q_1,d$, a subgroup $I_p\le A$ and an element $F_p\in A$ for each natural number $p$. In the arithmetic application these are inertia and a representative of Frobenius. Assume there is a finite $S\subseteq\mathbb N$ containing $2,q_1$, that $d$ is prime and outside $S$, and that the following hold:

- For a prime $p\notin S\cup\{d\}$, $I_p=\{0\}$.
- For $p\in S$, $I_p\subseteq\Phi$ and $F_p\in\Phi$.
- At $d$, $I_d=\{0,(1,0,0)\}$.

This is the local hypothesis `HostFactsS`. For $\psi\in\widehat A$ and $n\ge1$ define

$$
P_\psi(n)=\prod_{p\mid n}\frac1{|I_p|}\sum_{h\in I_p}\psi(v_p(n)F_p+h).
$$

Fix an arbitrary function $\ell:\widehat A\to\mathbb C$. For $y>0$ put $U_\psi(y)=\sum_{1\le n\le y}\Lambda(n)P_\psi(n)(y/n-1)$ and define

$$
G_1(y)=U_1(y)-y\log y+(1+\gamma_E)y,\qquad
G_\psi(y)=U_\psi(y)+y\ell(\psi)\quad(\psi\ne1).
$$

Here $\Lambda$ is the von Mangoldt function and $\gamma_E$ is Euler's constant. Since $P_1(n)=1$, the trivial-character term is the usual ramp sum for $\zeta$, with its main term subtracted. In the application $\ell(\psi)=(L'/L)(1,\chi_\psi)$ for the [primitive character recovered from $P_\psi$](primitive-characters-from-inertia.md).

Take $a>0$, $t\in H$, an integer $N\ge0$, and a function $w:A\to\mathbb R$ such that $w(\rho)>0$ and $a/w(\rho)\le N$ for every $\rho\in\Phi$. Write $w_g=w(P_t(g))$ for $g\in\Phi^c$, and $z_+=\max(z,0)$. The count in `ASK` is

$$
\begin{aligned}
A_t={}&
\sum_{\substack{p\le N,\ p\text{ prime}\\p\notin\{2,q_1,d\},\ F_p\notin\Phi}}
2\log p\sum_{\substack{1\le i\le N\\iF_p\in\Phi^c}}
(a/p^i-w_{iF_p})_+\\
&+(\log d)\sum_{1\le i\le N}
\sum_{g\in(iF_d+I_d)\cap\Phi^c}(a/d^i-w_g)_+.
\end{aligned}
$$

Define its possibly complex main term, `MAIN`, by

$$
M(a,w)=a\left[\log a-1-\gamma_E+\ell(c)
-\frac1f\sum_{\rho\in\Phi}\log w(\rho)\right].
$$

**Claim.** With all the preceding hypotheses we have the complex equality

$$
A_t-M(a,w)=
\frac1f\sum_{g\in\Phi^c}\sum_{\psi\in\widehat A}
\psi(-g)\,w_gG_\psi(a/w_g). \tag{1}
$$

Lean calls the right-hand side `De` and views $A_t$ as a complex number in this equality.

## Character inversion on an inertia coset

For a prime power $p^i$ with $i\ge1$, use the definition of $P_\psi$ and interchange finite sums:

$$
K(p^i,g)=\frac1f\sum_{\psi\in\widehat A}\psi(-g)P_\psi(p^i)
=\frac1{f|I_p|}\sum_{h\in I_p}\sum_{\psi\in\widehat A}\psi(iF_p+h-g).
$$

The inner sum at $z=iF_p+h-g$ is $|A|=2f$ if $z=0$. For $z\ne0$, choose a character $\psi_0$ with $\psi_0(z)\ne1$. Multiplication by $\psi_0$ permutes $\widehat A$ and multiplies the sum by $\psi_0(z)$, so the sum is zero. Thus

$$
K(p^i,g)=\frac2{|I_p|}\mathbf 1_{g\in iF_p+I_p}. \tag{2}
$$

In particular the coefficient is twice a singleton indicator at an unramified prime and is one per member of the coset at $d$.

## The count equals the uncorrected ramp sum

Set

$$
F=\frac1f\sum_{g\in\Phi^c}\sum_{\psi\in\widehat A}\psi(-g)
\sum_{1\le n\le N}\Lambda(n)P_\psi(n)(a/n-w_g)_+.
$$

Since $\Lambda$ is supported on prime powers, (2) gives

$$
F=\sum_{p^i\le N}(\log p)\sum_{g\in\Phi^c}K(p^i,g)(a/p^i-w_g)_+,
$$

where $p$ ranges over primes and $i\ge1$. For $p^i>N$ every ramp above is zero because $a/w_g\le N$. Therefore for $p\le N$ we may sum over $1\le i\le N$. If $d>N$, the terms at $d$ also vanish.

For $p\in S$ the coset $iF_p+I_p$ lies within the subgroup $\Phi$, so its intersection with $\Phi^c$ is empty. These primes are also excluded from the first part of $A_t$ by the condition on $F_p$. For $p\notin S\cup\{d\}$ the coset is a singleton, with factor $2\log p$ whenever $iF_p\in\Phi^c$. If $F_p\in\Phi$ all its multiples lie there. Since $S$ contains $2,q_1$, the surviving terms are exactly the first part of $A_t$. At $d$ the inertia size is two, so each member of $(iF_d+I_d)\cap\Phi^c$ contributes one copy with factor $\log d$. This is the second part of $A_t$. Hence $F=A_t$.

On the other hand $(a/n-w_g)_+=w_g(a/(nw_g)-1)_+$, and $N$ already covers all nonzero terms. The inner sum in $F$ is consequently $w_g U_\psi(a/w_g)$. By the definitions of $G_\psi$, this equals $w_gG_\psi(a/w_g)$ plus

$$
\begin{cases}
a(\log a-\log w_g-1-\gamma_E),&\psi=1,\\
-a\ell(\psi),&\psi\ne1.
\end{cases} \tag{3}
$$

## Summing the main terms

For a character nontrivial on $\Phi$, translation by a suitable $h\in\Phi$ shows that $\sum_{g\in\Phi^c}\psi(-g)=0$. A character trivial on $\Phi$ factors through the group $A/\Phi$ of order two and is either $1$ or $c$. The sums over $\Phi^c$ for these two characters are $f$ and $-f$, respectively. Thus among the nontrivial characters the corrections in (3) contribute only $a\ell(c)$ to $F$. The trivial character contributes

$$
a\left[\log a-1-\gamma_E-\frac1f\sum_{g\in\Phi^c}\log w_g\right].
$$

The bijection $P_t$ converts the final sum to $\sum_{\rho\in\Phi}\log w(\rho)$. Thus the total correction in (3) is $M(a,w)$, proving (1).

The next stage takes real parts of (1), sums several choices of $a,t,w$, and averages over translations. The sum of the discrepancies on the left is `gapA`. It is this discrepancy that must be bounded by the arithmetic estimates.

## Lean references and review

- The group, local data, partner weights and counts are defined in [`PartnersToFactorsAt.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThickAverageLoss/PartnersToFactorsAt.lean), [`FirstPrimeNeSecondPrime.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/FirstPrimeNeSecondPrime.lean), and [`Deduction.CH.HostFactsS`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/SplitInertia.lean#L14).
- Formula (2) is [`orthogonality_ramified`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ChainSlopeWindows/StronglyIrreducible.lean#L311). The treatment of the three prime cases and the finite expansion use `lsplit`, `lunram`, `ld` and `askExp` in [`ChBalance.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/ChBalance.lean).
- The coset sum is [`colour_sum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ChainSlopeWindows/StronglyIrreducible.lean#L171). Equation (1) is [`Deduction.ch_balance`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/ChBalance.lean#L200). Its next use is [`CharacterBalanceMoves.core`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/ChCore.lean#L283).

English translation draft. The identity precedes the analytic and arithmetic bounds, which enter when the discrepancies are averaged.
