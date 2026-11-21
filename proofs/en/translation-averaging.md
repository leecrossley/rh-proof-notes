# How translation averaging gives the pointwise prime-sum bound

[Chinese proof](../zh/%E5%B9%B3%E7%A7%BB%E5%B9%B3%E5%9D%87%E5%A6%82%E4%BD%95%E7%BB%99%E5%87%BA%E7%B4%A0%E6%95%B0%E5%92%8C%E7%9A%84%E9%80%90%E7%82%B9%E4%BC%B0%E8%AE%A1.md) · [Reading and review status](../../STATUS.md)

The [finite Fourier identity](finite-fourier-balance.md) expresses a count discrepancy as a character sum. Suppose that for every translation in a subgroup the discrepancy is at most the same specified error. Averaging then retains only the characters trivial on that subgroup. The argument below controls the effect of moving all their arguments to a common point, and tracks the exponent of the error after rescaling.

## Data and conclusion

Use the notation of the [finite Fourier identity](finite-fourier-balance.md), including the local hypothesis `HostFactsS`. Thus $H$ is finite abelian, $A=(\mathbb Z/2\mathbb Z)^2\times H$, $\Phi=\{(0,j,h)\in A\}$ and $f=|\Phi|=2|H|$. The local data $D,S$ and the correction function $\ell:\widehat A\to\mathbb C$ give the ramp errors $G_\psi(y)$. Denote the count, main term and Fourier expression by $A_t(D,N,a,w)$, $M(a,w)$ and $\Delta(D,\ell,a,t,w)$, respectively.

Fix a subgroup $H_0\le H$ and let $\Psi$ be the set of characters trivial on $\{(0,0,h):h\in H_0\}$. Choose $K_p\subseteq\Psi$. For $\psi\in K_p$ put $c_\psi=1$ when its restriction to the $H$ factor is trivial and $c_\psi=c$ otherwise. Set

$$
G_m(x)=\sum_{\psi\in K_p} c_\psi\operatorname{Re}G_\psi(x),
\qquad
\Sigma(x)=\sum_{\psi\in\Psi\setminus K_p}|G_\psi(x)|.
$$

Let $N,m$ be natural numbers, $T,T_2\subseteq H$ finite, $a:H\to\mathbb R$, and $w_{u,j}:A\to\mathbb R$ for $u\in H$ and $1\le j\le m$. Write $n=|H|$, $n_T=|T|$ and $n_2=|T_2|$. For real $b,b',k,a_E,\eta,X',\tau$ define

$$
\begin{aligned}
\mathrm{gap}(u)&=\sum_{t\in T}\sum_{j=1}^m
   \bigl(A_t(D,N,a(t),w_{u,j})-\operatorname{Re}M(a(t),w_{u,j})\bigr),\\
B_E&=n_Ta_E(1+m^2/k)
  +m\left[2nmbx^\varepsilon+
    \frac{n_2kbx^\varepsilon}{n^2x^{-\varepsilon}}\right].
\end{aligned}
$$

**Theorem.** Fix real $C,\varepsilon,C_E,K_0,c,M_0$ with $C\ge0$, $\varepsilon>0$ and $|c|\le1$. There exists a real threshold $x_1$ such that for each real $x\ge x_1$ and all the above data satisfying the following five conditions,

$$
G_m(x)\le x^{1/2+(C+3)\varepsilon}+\Sigma(x).
$$

1. We have $T_2\subseteq H_0$, $b>0$, $a_E\ge0$, $k>0$, and
   $$
   a_E\le2xb,\quad n_T\ge nx^{-\varepsilon/8}/2,\quad n_2/n\ge x^{-\varepsilon},
   \quad x^{1/2-\varepsilon}\le m\le x^{1/2+\varepsilon/2},
   \quad xm\le k\le n^2x^{1/2-\varepsilon}.
   $$
2. We have $\eta\ge0$, $X'>0$, $b'>0$, $b'X'\le xb$, $\tau\ge0$, and $|a(t)/b-x|\le1$ for all $t\in T$. For $u\in H_0$ and $1\le j\le m$, the thick points are the points $(0,1,s+u)$ with $s\in T_2$. Require $w_{u,j}(\rho)>0$ throughout $\Phi$, with $b\le w_{u,j}(\rho)\le b+\eta+1$ at the thick points and $w_{u,j}(\rho)\le2b'$ elsewhere. For every $t\in T$ and $\rho\in\Phi$, require $a(t)/w_{u,j}(\rho)\le N$.
3. For all $\psi\in\widehat A$ and $y\ge X'/3$, $|G_\psi(y)|\le y\tau$. Also $2f(x+1)\tau\le1/x$ and $6f(x+1)(\eta+1)\le b/x$.
4. We have $1\in K_p\subseteq\Psi$, $|\Psi|\le M_0$, and $\psi(1,0,0)=1$ for every $\psi\in K_p$. Write $\chi_\psi(t)=\psi(0,0,t)$. For each $\psi\in K_p$ with nontrivial $\chi_\psi$,
   $$
   \left|\sum_{t\in T}\chi_\psi(t)-cn_T\right|
   \le M_0 x^{-1+\varepsilon}n_T.
   $$
   For $\psi\in K_p\setminus\{1\}$ require $|\ell(\psi)|\le K_0$, and for $\psi\in\Psi\setminus K_p$ require $|\ell(\psi)|\le C_E\log x$.
5. For every $u\in H_0$, $\mathrm{gap}(u)\le E=x^{C\varepsilon}B_E$.

The conditions on weights, small-weight arguments and retained characters use `SizesA`, `ThinScales`, `CostWindows` and `CharsA`. The parameter $\tau$ is a bound on the small-weight error per unit argument.

## Replace thick weights by a single weight

We take $x\ge3$. Write $y_t=a(t)/b$, so $x-1\le y_t\le x+1$ and $a(t)>0$. The Fourier identity replaces the difference in each summand of $\mathrm{gap}$ by $\operatorname{Re}\Delta$. Its terms have the form $wG_\psi(a(t)/w)$, where $g\in\Phi^c$, $\psi\in\widehat A$ and $w=w_{u,j}(P_t(g))$. For each $t,j,u$ we compare this with a sum only over thick points, using the common weight $b$ there.

For any local data $D$, correction function $\ell$, character $\psi$, and positive $A_*,w,w'$, the weight bound used here is

$$
\big|wG_\psi(A_*/w)-w'G_\psi(A_*/w')\big|
\le 3A_*\frac{|w-w'|}{\min(w,w')}. \tag{1}
$$

To see this, the ramp $(A_*/n-w)_+$ changes by at most $|w-w'|$ and contributes only for $n\le A_*/\min(w,w')$. Use $|P_\psi(n)|\le1$ and the elementary estimate $\sum_{1\le n\le Y}\Lambda(n)\le3Y$ for $Y\ge0$. The correction $A_*\ell(\psi)$ cancels for nontrivial $\psi$. For $\psi=1$ and $w\le w'$, the two differences in the ramp sum and the main term are both nonnegative and at most $3A_*(w'-w)/w$. For the main term this follows from $\log(w'/w)\le(w'-w)/w$. The absolute value of their difference is bounded by the same quantity. Interchanging $w,w'$ covers the other order.

At a thick point, (1) shows that replacing $w$ by $b$ changes the term by at most $3(x+1)(\eta+1)$. At a non-thick point, $w\le2b'$ implies

$$
a(t)/w\ge(x-1)b/(2b')\ge xb/(3b')\ge X'/3.
$$

Discarding the term therefore costs at most $w\cdot(a(t)/w)\tau\le (x+1)b\tau$. There are $f$ values of $g$ and $2f$ characters. Each coefficient $\psi(-g)$ has modulus one, and the normalization is $1/f$. The total error in the real part of one Fourier expression is at most

$$
2f\bigl(3(x+1)(\eta+1)+(x+1)b\tau\bigr)\le 2b/x
$$

by condition 3.

## Average over the subgroup

Let $e(h)=(1,0,h)$. The partner map $P_t$ takes $e(s+u-t)$ to the thick point $(0,1,s+u)$. The resulting common-weight expression is independent of $j$ and equals

$$
U(u,t)=\frac b f\sum_{s\in T_2}\sum_{\psi\in\widehat A}
\psi(-e(s+u-t))G_\psi(y_t).
$$

The comparison gives $\operatorname{Re}U(u,t)\le\operatorname{Re}\Delta+2b/x$ for each $j$. Sum in $j,t$ and use condition 5 to get $m\sum_{t\in T}\operatorname{Re}U(u,t)\le E+2n_Tmb/x$ for each $u\in H_0$. Since the first coordinate has order two,

$$
-e(s+u-t)=e(t)+(0,0,-s)+(0,0,-u).
$$

Summing the last factor of the character over $u\in H_0$ gives $|H_0|$ for $\psi\in\Psi$ and zero otherwise, by orthogonality. The remaining factor from $s$ is one because $T_2\subseteq H_0$. Thus, with $\delta_2=n_2/n$,

$$
\frac1{|H_0|}\sum_{u\in H_0}U(u,t)
=\frac{b\delta_2}{2}\sum_{\psi\in\Psi}\psi(e(t))G_\psi(y_t).
$$

The normalization $f=2n$ accounts for the factor $1/2$. The averaged discrepancy inequality is now

$$
\frac{mb\delta_2}{2}\sum_{t\in T}\sum_{\psi\in\Psi}
\operatorname{Re}\!\left[\psi(e(t))G_\psi(y_t)\right]
\le E+2n_Tmb/x. \tag{2}
$$

## Move every argument to $x$

The argument-change lemma supplies an absolute $C_d\ge0$ such that for arbitrary local data, correction function and $y,z\ge1$,

$$
\begin{aligned}
|G_1(y)-G_1(z)|&\le C_d|y-z|,\\
|G_\psi(y)-G_\psi(z)|&\le |y-z|\bigl(\log\max(y,z)+C_d+|\ell(\psi)|\bigr)
\quad(\psi\ne1).
\end{aligned} \tag{3}
$$

The nontrivial case follows by bounding the ramp derivative with $\sum_{n\le Y}\Lambda(n)/n\le\log Y+O(1)$, using $|P_\psi(n)|\le1$. In the trivial case the derivative of the corrected ramp has the same bound after subtraction of the logarithmic main term. The [proof of the two variation estimates](ramp-variation.md) gives the details.

Let $r=|M_0|x^{-1+\varepsilon}$. Let $R$ bound all three quantities

$$
\begin{gathered}
C_d,\\
\log(x+1)+C_d+|K_0|+rx\bigl(\log x+C_d+|K_0|\bigr),\\
\log(x+1)+C_d+|C_E|\log x.
\end{gathered}
$$

For the trivial character, (3) moves each term from $y_t$ to $x$ at cost at most $C_d$, since $|y_t-x|\le1$. The sum is at least $n_T(G_1(x)-R)$.

For a retained nontrivial character, $\psi(e(t))=\chi_\psi(t)$ by the condition on the first coordinate. Using (3) costs at most $n_T(\log(x+1)+C_d+|K_0|)$. To replace $\sum_{t\in T}\chi_\psi(t)$ with $n_Tc_\psi$, the additional change in magnitude is at most $n_Tr|G_\psi(x)|$ by condition 4, with zero change for trivial $\chi_\psi$. Since $G_\psi(1)=\ell(\psi)$, (3) gives $|G_\psi(x)|\le x(\log x+C_d+|K_0|)$. The resulting real sum is at least $n_T(c_\psi\operatorname{Re}G_\psi(x)-R)$.

Each discarded character is nontrivial. For each $t$ use $\operatorname{Re}z\ge-|z|$ and (3) to get a lower bound $-|G_\psi(x)|-R$. Summing the three cases gives the lower bound $n_T(G_m(x)-\Sigma(x)-|\Psi|R)$ for the double sum in (2).

## Normalize the four error terms

For $x\ge3$ we have $\log x\le4x^{1/4}$ and $\log(x+1)\le5x^{1/4}$. Since $rx=|M_0|x^\varepsilon$, we may take $R=A_1x^{1/4+\varepsilon}$, where

$$
A_1=5+C_d+|K_0|+|M_0|(4+C_d+|K_0|)+4|C_E|.
$$

Choose a uniform threshold with $x\ge3$, $x^{1/4}\ge |M_0|A_1$ and $x^{3\varepsilon/8}\ge26$. Then $|\Psi|R\le X=x^{1/2+\varepsilon}$. Put $G=G_m(x)-\Sigma(x)$ and $Q=n_Tmb>0$. Using the lower bound in (2), and allowing the looser error $4X$ as in the Lean proof, gives

$$
Q(\delta_2/2)(G-4X)\le E+2Q/x. \tag{4}
$$

Write $Y=x^{1/2+13\varepsilon/8}$. Upon dividing $B_E$ by $Q$, its four terms satisfy

$$
\begin{aligned}
a_E/(mb)&\le 2x/m\le 2X\le 2Y,\\
a_E m/(kb)&\le 2xm/k\le 2\le2Y,\\
2nmx^\varepsilon/n_T&\le4mx^{9\varepsilon/8}\le4Y,\\
(n_2/n_T)(k/n^2)x^{2\varepsilon}&\le 2x^{1/2+9\varepsilon/8}\le 2Y.
\end{aligned}
$$

Here the first inequality in the last line uses $n_2\le n$, $n_T\ge nx^{-\varepsilon/8}/2$ and the upper bound for $k$. In the third line the exponent $13\varepsilon/8$ comes from the upper bound for $m$. Thus $E/Q\le10x^{C\varepsilon}Y$. Divide (4) by $Q$ and use $2/x\le1\le x^{C\varepsilon}Y$ to obtain $\delta_2(G-4X)\le22x^{C\varepsilon}Y$. Since $\delta_2\ge x^{-\varepsilon}$,

$$
G\le4X+22x^{1/2+(C+21/8)\varepsilon}
\le26x^{1/2+(C+21/8)\varepsilon}
\le x^{1/2+(C+3)\varepsilon}.
$$

The last step is precisely the threshold $26\le x^{3\varepsilon/8}$. This proves the theorem.

## Use in the window argument

In `core_gm` the exponent parameter is $C=e_D+e_L+3$. The discrepancy hypothesis comes from `ch_top`, which compares the count with slopes of lattices built from the same data. This gives exponent $1/2+(e_D+e_L+6)\varepsilon$ plus the discarded contribution. The [primitive-character calculation](primitive-characters-from-inertia.md) reindexes the retained sum and gives $\Sigma(x)\le4o\,x^{1/2+\varepsilon}$ for the fixed index $o$ of the layer. For sufficiently large $x$, $1+4o\le x^\varepsilon$. Under the loss bounds of that application, the combined exponent is $1/2+(e_D+e_L+7)\varepsilon$. A window estimate needs appropriate data at every point of the window. See the preceding [count discrepancy](quotient-slopes-and-count-discrepancy.md) and the subsequent [use of the window in the main theorem](main-theorem-and-window.md).

- The main statement is [`Deduction.ch_core`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/ChCore.lean#L343). The thick-point approximation is [`th_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/ChCore.lean#L75), and averaging uses [`sum_A`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/ChCore.lean#L28), [`sum_Th`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/ChCore.lean#L56), and [`CharacterBalanceMoves.core`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/ChCore.lean#L283).
- The variation inequalities are [`lipschitz_weight_all`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ChainSlopeWindows/LipschitzWeightAndMinimum.lean#L957) and [`derivative_integral_all`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ChainSlopeWindows/LipschitzWeightAndMinimum.lean#L966). The distribution estimate is [`one_char`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/ChCore.lean#L202).
- The numerical proof uses [`proposition_size_bound`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ChainSlopeWindows/LipschitzWeightAndMinimum.lean#L507). Its use for the actual character family is [`core_gm`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/PrimitiveCosets/CoreGm.lean#L12).

English translation draft. The bound on the arithmetic discrepancy is an explicit hypothesis here.
