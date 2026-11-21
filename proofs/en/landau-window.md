# The Landau window lemma

[中文](../zh/landau-window.md) · [Reading and review status](../../STATUS.md)

## 1. Statement

Fix $0<\theta<1$ and $\delta>0$. Let $g:\mathbb R\to\mathbb R$ be measurable with $|g(u)|\le C_0e^{2u}$ for $u\ge0$ and some $C_0\ge0$. Suppose $\Phi(s)=\int_0^\infty g(u)e^{-su}\,du$ for $\operatorname{Re}s>2$. Assume $\Phi$ is holomorphic in the right half-plane off a set $Z$ of isolated poles. More precisely, each point of the right half-plane has a punctured neighborhood disjoint from $Z$. At each $\rho\in Z$ the expansion is

$$
\Phi(s)=\frac{c_\rho}{s-\rho}+h_\rho(s),
$$

with $h_\rho$ holomorphic near $\rho$, $c_\rho\ne0$, and $c_\rho>0$ if $\rho$ is real.

Assume that for every $\eta>0$ and every lower bound $U_0$ there is $U\ge U_0$ and a real function $R$ with $R\ge0$ and $g\le R$ on $[U,(1+\delta)U]$. The weighted restriction $R(u)e^{-\theta u}$ is integrable there and its integral is at most $e^{\eta U}$. Then all $\rho\in Z$ satisfy $\operatorname{Re}\rho\le\theta$.

## 2. The tails of a derivative kernel

For $k\ge0$ put $A_k(s)=(-1)^k\Phi^{(k)}(s)/k!$. In $\operatorname{Re}s>2$ it is the integral of $g(u)u^ke^{-su}/k!$. Differentiation under the integral follows by domination by a polynomial times $e^{-\epsilon u}$ on a sufficiently small neighborhood. Also the transform is bounded on every half-plane $\operatorname{Re}s\ge\sigma_0>2$ by $C_0/(\sigma_0-2)$. Hence no pole has real part greater than $2$.

For $U\ge1$, put $V=(1+\delta)U$. Let $T$ be the integral of $u^ke^{-(\sigma-2)u}/k!$ over $(0,\infty)\setminus[U,V]$. For $0<\ell<\sigma-2$, multiply the integrand by $e^{\ell(u-V)}$ on the upper tail and $e^{\ell(U-u)}$ on the lower tail. Each multiplier is at least one. Extending both integrals to the positive half-line gives

$$
T\le \frac{e^{-\ell V}}{a_+^{k+1}}
     +\frac{e^{\ell U}}{a_-^{k+1}},
\qquad
a_\pm=\sigma-2\mp\ell.
$$

This uses $\int_0^\infty u^k e^{-a u}\,du/k!=a^{-k-1}$ for $a>0$, obtained by integration by parts. Choose

$$
\ell=2+6/\delta,\quad M=\ell(1+\delta),\quad
\sigma=M(\ell+2),\quad k=\lceil(1+\delta/2)\sigma U\rceil.
$$

Now $k\ge U$ and $\sigma-2>\ell$. In the upper term of $\sigma^k T$, use $\log(\sigma/a_+)\le1/(M-1)$ and $(1+\delta/2)\sigma=M(M-1)$. Its exponential factor is at most $\exp(-MU+k/(M-1))\le e$. For the lower term, use $\log(\sigma/a_-)\le-(\ell-2)/a_-$, $(1+\delta/2)(\ell-2)=\ell+1$ and $\ell a_-\le(\ell+1)\sigma$. Its exponential factor is at most $\exp(\ell U-k(\ell-2)/a_-)\le1$. Thus $T\le C_1/\sigma^k$, with $C_1=e/a_++1/a_-$ independent of $U$.

## 3. Keeping the one-sided bound

Set $E=\sigma-\theta$. Take a window supplied by the hypothesis with $U\ge\max(1,U_0)$, and choose $k$ as above. Write $w(u)=u^ke^{-\sigma u}/k!$. Since $g$ is real, for each $\gamma\in\mathbb R$,

$$
|A_k(\sigma+i\gamma)|+\operatorname{Re}A_k(\sigma)
 \le \int_0^\infty (|g(u)|+g(u))w(u)\,du.
$$

On the window, $|g|+g=2\max(g,0)\le2R$. The exponential series gives $w(u)\le e^{-\theta u}/E^k$. Outside the window the bound is $2C_0T$. Since $0<E<\sigma$, for one constant $C=2+2C_0C_1$ we get

$$
|A_k(\sigma+i\gamma)|+\operatorname{Re}A_k(\sigma)
  \le C e^{\eta U}/E^k. \tag{1}
$$

A contradiction will follow if a pole forces an inequality of the form

$$
c/d^k\le M_*/b^k+C e^{\eta U}/E^k,\qquad
c>0,\quad M_*\ge0,\quad 0<d<b\le E, \tag{2}
$$

with $c,M_*,d,b$ fixed independently of the window. Indeed choose $\eta=\tfrac12\log(b/d)>0$. After dividing (2) by its left side and using $k\ge U$, its right side is at most $(M_*+C)e^{-\eta U}/c$. This is less than one for all sufficiently large $U$.

## 4. A pole forces derivative growth

Assume some $\rho_0$ has $\operatorname{Re}\rho_0>\theta$. Let $D$ be the minimum of $E$ and the distances from $\sigma$ to poles in the closed disk of radius $E$ centered at $\sigma$. The disk lies in the right half-plane and contains finitely many poles, by compactness and the punctured-neighborhood condition. Thus $D>0$ and the open disk of radius $D$ about $\sigma$ is pole-free.

On a circle of radius $b$, the Cauchy estimate bounds the normalized $k$-th coefficient of a holomorphic function by $M_*/b^k$, where $M_*$ is its maximum modulus on the circle. In a disk with only one pole $\rho$, subtract $c_\rho/(s-\rho)$ first. Its removed contribution to $A_k(z)$ at the center is $c_\rho/(z-\rho)^{k+1}$.

**First case.** Some pole $\rho_1$ has $\sigma-\operatorname{Re}\rho_1<D$. Start with $z_0=\sigma+i\operatorname{Im}\rho_1$ and move it slightly along the vertical line. We can keep $|z-\rho_1|<D$ and arrange that the nearest pole is unique. Only the finitely many poles in a slightly larger disk about $z_0$ can compete. For two such poles with different imaginary parts, equality of squared distances excludes at most one height. With equal imaginary parts the distances differ, because both real parts lie strictly to the left of $\sigma$. Avoiding the finitely many excluded heights suffices.

Let $\rho$ be the nearest pole, $d=|z-\rho|$ and choose $d<b<D$ small enough that the closed disk of radius $b$ about $z$ contains only $\rho$. The one-pole estimate gives $|A_k(z)|\ge |c_\rho|/d^{k+1}-M_1/b^k$, and the disk about $\sigma$ gives $\operatorname{Re}A_k(\sigma)\ge-M_2/b^k$. Substitution into (1) gives (2) with $c=|c_\rho|/d$.

**Second case.** All poles have $\sigma-\operatorname{Re}\rho\ge D$. The pole $\rho_0$ gives $D\le\sigma-\operatorname{Re}\rho_0<E$. Thus some pole is at distance $D$ from $\sigma$. Its horizontal distance is already at least $D$, so it is the real pole $\beta=\sigma-D$, the only pole at that distance. Choose $D<b<E$ with no other pole in the corresponding closed disk. Its residue $c_\beta$ is positive. Subtracting the pole term and applying Cauchy's estimate gives $\operatorname{Re}A_k(\sigma)\ge c_\beta/D^{k+1}-M_1/b^k$. Taking $\gamma=0$ in (1), whose left side is at least $\operatorname{Re}A_k(\sigma)$, gives (2) with $d=D$ and $c=c_\beta/D$.

Both cases contradict (2). This proves the statement.

## Lean and application

The theorem is `Deduction.landau_window`. The weighted prime-sum application gets the pole hypotheses from `Deduction.poleData`, then obtains the logarithmic window by setting $u=\log y$. [Lean window lemma](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/landauWindow.lean#L83) · [Pole data](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/poleData.lean#L248) · [Application to RH](from-windows-to-rh.md)
