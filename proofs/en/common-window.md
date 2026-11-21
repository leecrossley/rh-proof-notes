# One window for two estimates

[中文](../zh/common-window.md) · [Reading and review status](../../STATUS.md)

The proof needs bounds for twisted prime sums and lengths of Galois cohomology localization kernels at the same scale. This lemma combines the two window inputs while keeping one pair of auxiliary primes throughout the resulting interval.

## 1. Statement

Fix a primitive Dirichlet character $\psi$ of conductor $M$, $0<\varepsilon<1/52$ and $c\ge1$. Set $a=2+8\varepsilon$.

- Write $P(Y;q,d)$ for the prime-pair conditions used by the cohomology estimate. They impose congruences and log-size bounds on $q,d$, and require $q$ and the indicated small odd primes to divide $d+1$. [Definition](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/ExistsPageN.lean#L27)
- Write $A(Y,X;q,d)$ for $P$ together with the coprimality condition, twisted prime-sum estimates on $[Y,X]$ and zero-free rectangles. The only dependence on $X$ is as an upper endpoint, so $A(Y,X;q,d)$ implies $A(Y,x;q,d)$ for $x\le X$. [Definition and monotonicity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/PairGood.lean#L18)
- Write $V_C(r;e,q,d)$ for the cohomology bound with cutoff $\lfloor r^C\rfloor$ and bound $\exp(r^\varepsilon/2)$. For each field specified by $\psi,e,q,d$, all localization-kernel lengths with twist index $1\le i<\lfloor r^C\rfloor$ are finite. For every finite set of rational primes, their sum, weighted by $\log\ell$ at prime $\ell$, is at most that bound. The fields are cut out by the character condition for $\psi$, the sign condition modulo $2^{e+2}$ and the two quadratic characters. This estimate persists on decreasing the cutoff or increasing the bound, since all terms are nonnegative. [Definitions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/ExistsPageN.lean#L12)

Assume the following.

1. For each $J\ge1$, there is $Y_1$ such that each $Y\ge Y_1$ admits $q,d$ satisfying $A(Y,Y^J;q,d)$.
2. For each $n:\mathbb R\to\mathbb N$ with $r^a\le2^{n(r)}\le2r^a$ for $r\ge1$, there are $J\ge1$ and $X_0$. For every $X\ge X_0$ and pair satisfying $P(X^{1/J};q,d)$, there is $W$ satisfying $X^{1/J}\le W$ and $W^2\le X$. For every $r\in[W,W^2]$ we have $V_{401}(r;n(r),q,d)$.

Then there exists $J\ge1$ such that for any lower bound $B$ one can choose $Z\ge\max(1,B)$ and a single $Y,q,d$. For every $x\in[Z,Z^{3/2}]$ there is an integer $e\ge0$ with

$$
x^{1/J}\le Y\le x,\qquad
A(Y,x;q,d),\qquad x^a\le c\,2^e\le2x^a.
$$

For every indicated field the length bound holds with cutoff $\lfloor x^{400}\rfloor$ and bound $\exp(x^\varepsilon/2)$.

## 2. Proof

For $r\ge1$ set $n(r)=\lceil a\log_2 r\rceil$, and set it to zero elsewhere. The powers satisfy the inequalities in input 2, so it gives $J$ and $X_0$. Apply input 1 with this $J$ to obtain $Y_1$. Set $k=c^{1/a}\ge1$. Choose $X\ge X_0$ large enough that

$$
Y=X^{1/J}\ge\max(1,B,Y_1,k^3,k^{400}).
$$

By input 1 choose $q,d$ for the analytic interval $[Y,Y^J]=[Y,X]$. This pair satisfies $P(Y;q,d)$, so input 2 gives the cohomology interval $[W,W^2]$. Set $Z=kW$. Since $W\ge k^3$,

$$
Z^{3/2}=k^{3/2}W^{3/2}\le W^2\le X.
$$

For $x\in[Z,Z^{3/2}]$, put $r=x/k$. Then $W\le r\le x\le W^2$. Thus the cohomology estimate is available at $r$ and the analytic estimate is available at $x$. Also $Y\le W\le x\le X$, so $x^{1/J}\le Y\le x$, and restriction of the analytic interval gives $A(Y,x;q,d)$ with the original primes.

Take $e=n(r)$. Multiplying $r^a\le2^{n(r)}\le2r^a$ by $c=k^a$ gives the desired bounds for $c\,2^e$. For the cohomology estimate, $r\ge W\ge k^{400}$ gives

$$
x^{400}=k^{400}r^{400}\le r^{401}.
$$

The smaller cutoff uses a subset of the known finite lengths and of the nonnegative summands. Also $r\le x$ gives $\exp(r^\varepsilon/2)\le\exp(x^\varepsilon/2)$. This gives the result at $x$.

## 3. Lean and reading sources

The inputs are `PairEx` and `VWinAt \psi 401`. The output is `WinDatum`. The extra unit in the input cutoff exponent absorbs the fixed rescaling. [Lean proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/WinPairs.lean#L5) · [Output definition](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/TwistForm.lean#L19) · [O’Desky’s entry on the dependency path](https://andrewodesky.com/rh/s/v6-window-prime-selection.html)
