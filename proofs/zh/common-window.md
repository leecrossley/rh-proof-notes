# 怎样让两类估计共用一个窗口

[English](../en/common-window.md) · [进度与复核状态](../../STATUS.md)

原证明要在同一个尺度上使用扭曲素数和估计与上同调长度界。两条上游定理各有自己的适用区间。下面说明为什么能在一个长区间内固定同一对辅助素数，并让两类估计都适用。

## 1. 命题

固定导子为 $M$ 的本原狄利克雷特征 $\psi$，以及 $0<\varepsilon<1/52$、$c\ge1$，记 $a=2+8\varepsilon$。以下三种条件均用原工程中的含义。

- $P(Y;q,d)$ 表示素数对可用于长度估计。它要求 $q\equiv3\bmod8$、$d\equiv7\bmod16$，控制两者的对数大小，并要求 $q$ 和指定范围内的小奇素数都整除 $d+1$。 [`WinPair` 的定义](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/ExistsPageN.lean#L27)
- $A(Y,X;q,d)$ 要求 $P(Y;q,d)$，以及模数的互素性、区间 $[Y,X]$ 上的扭曲素数和界与指定的无零点矩形。把 $X$ 减小至 $x$，$A(Y,x;q,d)$ 仍成立，因为对 $X$ 的唯一依赖是区间上界。 [`PairGood` 及其单调性](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/PairGood.lean#L18)
- $V_C(r;e,q,d)$ 表示对 $\psi,e,q,d$ 指定的每个数域，上同调局部化核在所有素数处、所有 $1\le i<\lfloor r^C\rfloor$ 的长度是有限的，并且任意有限个素数上的总长，以 $\log\ell$ 加权，至多为 $\exp(r^\varepsilon/2)$。数域由分圆自同构上 $\psi$、模 $2^{e+2}$ 的符号条件和两个二次特征共同切出。长度是非负的，因此缩小截点或放宽上界都会保留结论。 [数域、长度和 `VAt` 的定义](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/ExistsPageN.lean#L12)

假设有以下两条输入。

1. 对每个 $J\ge1$，存在 $Y_1$，使每个 $Y\ge Y_1$ 都能选到 $q,d$ 满足 $A(Y,Y^J;q,d)$。
2. 对每个函数 $n:\mathbb R\to\mathbb N$，若对 $r\ge1$ 有 $r^a\le2^{n(r)}\le2r^a$，则有 $J\ge1$ 与 $X_0$，使每个 $X\ge X_0$ 和每对满足 $P(X^{1/J};q,d)$ 的素数都给出一个 $W$。它满足 $X^{1/J}\le W$、$W^2\le X$，且对所有 $r\in[W,W^2]$ 有 $V_{401}(r;n(r),q,d)$。

**结论。** 存在 $J\ge1$，使任给下界 $B$，都能找到 $Z\ge\max(1,B)$ 和固定的 $Y,q,d$，使每个 $x\in[Z,Z^{3/2}]$ 都有一个 $e$ 满足

$$
x^{1/J}\le Y\le x,\qquad
A(Y,x;q,d),\qquad x^a\le c\,2^e\le2x^a.
$$

同时，对前面所述每个数域，截点 $\lfloor x^{400}\rfloor$ 的加权长度至多为 $\exp(x^\varepsilon/2)$。

## 2. 证明

对 $r\ge1$ 取 $n(r)=\lceil a\log_2 r\rceil$，在其他点取 $0$。这给出输入 2 所要求的幂次不等式，因而得到 $J,X_0$。用这个 $J$ 应用输入 1，取得 $Y_1$。令 $k=c^{1/a}\ge1$，选 $X\ge X_0$ 足够大，使

$$
Y=X^{1/J}\ge\max(1,B,Y_1,k^3,k^{400}).
$$

输入 1 给出一对素数 $q,d$，其解析估计在 $[Y,X]$ 上有效。这对素数也满足输入 2 所需的 $P(Y;q,d)$，于是取得 $W$。令 $Z=kW$。因为 $W\ge k^3$，有

$$
Z^{3/2}=k^{3/2}W^{3/2}\le W^2\le X.
$$

现在固定 $x\in[Z,Z^{3/2}]$，令 $r=x/k$。有 $W\le r\le x\le W^2$，所以在 $r$ 使用长度估计，在 $x$ 使用解析估计。又由 $Y\le W\le x\le X$ 得 $x^{1/J}\le Y\le x$。素数对仍是原来那一对，$A(Y,x;q,d)$ 只需把解析区间缩短即可。

取 $e=n(r)$。因为 $k^a=c$，把 $r^a\le2^{n(r)}\le2r^a$ 乘以 $c$ 就得到 $x^a\le c\,2^e\le2x^a$。最后 $r\ge W\ge k^{400}$，于是

$$
x^{400}=k^{400}r^{400}\le r^{401}.
$$

用 $r$ 处的长度界，将截点缩为 $\lfloor x^{400}\rfloor$。这只会减少要检查的指标和总和中的非负项。因为 $r\le x$、$\varepsilon>0$，把右端从 $\exp(r^\varepsilon/2)$ 放宽到 $\exp(x^\varepsilon/2)$ 即得结论。

## 3. 对照与来源

两个存在性输入分别是 `PairEx` 与 `VWinAt \psi 401`，输出是 `WinDatum`；`UpperTheory.Top.winPairs` 证明第 2 节。项 $401$ 与 $400$ 的差正用于吸收重标度 $k$。 [选素数输入](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/PairGood.lean#L28) · [上同调输入](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/ExistsPageN.lean#L44) · [输出定义](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/TwistForm.lean#L19) · [Lean 证明](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/WinPairs.lean#L5)

公开依赖线索参见 O’Desky 的[共同窗口条目](https://andrewodesky.com/rh/s/v6-window-prime-selection.html)。它列出这两个上游输入，与本篇的源码对照可互查。
