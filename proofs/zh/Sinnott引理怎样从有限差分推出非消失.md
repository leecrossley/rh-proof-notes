# Sinnott 引理怎样从有限差分推出非消失

**命题一（[`sinnott`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/Sinnott.lean#L10)）。** 设 $\ell$ 为素数，$I$ 为有限非空集，$\eta_i\in\mathbb Z_\ell^\times$（$i\in I$），且在 $i\ne j$ 时，整数关系 $a\eta_i=b\eta_j$ 蕴涵 $a=0$。给定正整数 $N$，存在 $n_0$，使对任意 $n\ge n_0$、任意交换环 $k$、任意 $P:\mathbb N\to k$ 和 $\alpha:\mathbb Z/\ell^n\mathbb Z\to k$，若

$$
\alpha(y)-\alpha(y-N)=\sum_{\substack{0\le s<N\\s\equiv y\bmod\ell^n}}P(s),
 \qquad
 \sum_{i\in I}\alpha(\overline{\eta_i}^{-1}y)=0
 \quad\text{对每个 }y,
 \tag{1}
$$

则 $P(s)=0$ 对所有 $0\le s<N$ 成立。上横线表示模 $\ell^n$ 的降约。

## 一、把有限差分写成群环里的乘法

对加法群 $A$，记 $k[A]$ 的基元为 $[a]$，满足 $[a][b]=[a+b]$。在 $A=\mathbb Z/\ell^n\mathbb Z$ 中设

$$
F_i=\sum_{y\in A}\alpha(y)[\overline{\eta_i}y],\qquad
 B_i=\sum_{s=0}^{N-1}P(s)[s\overline{\eta_i}].
$$

对照第一个 (1) 式的系数，有 $B_i=(1-[N\overline{\eta_i}])F_i$。第二个 (1) 式就是 $\sum_i F_i=0$。因此

$$
\sum_{i\in I} B_i\prod_{j\ne i}(1-[N\overline{\eta_j}])=0.
$$

这是下列有限支撑表达式降模 $\ell^n$ 的结果。

$$
E=\sum_{i\in I}
   \left(\sum_{s=0}^{N-1}P(s)[s\eta_i]\right)
   \prod_{j\ne i}(1-[N\eta_j])\in k[\mathbb Z_\ell].
 \tag{2}
$$

所有可能的指数都属于有限集 $\{s\eta_i+\sum_{j\in J}N\eta_j: i\in I,\ 0\le s<N,\ J\subseteq I\}$，这个集合由 $I,N,\eta$ 决定。两个不同的 $\ell$ 进整数最终在模 $\ell^n$ 下不同，故在这整个有限集上，充分高的降模映射是单射。取这样的 $n_0$，(2) 的每个系数都可从降模结果中单独读出，遂有 $E=0$。

## 二、在群环中保留一个方向

固定 $i_0\in I$，将 (2) 送到 $k[\mathbb Z_\ell/\mathbb Z N\eta_{i_0}]$。记 $\eta_i'$ 为商群中的像。除 $i=i_0$ 外，每项都含 $1-[N\eta_{i_0}']=0$。因此

$$
\left(\sum_{s=0}^{N-1}P(s)[s\eta_{i_0}']\right)
    \prod_{j\ne i_0}(1-[N\eta_j'])=0.
$$

对 $j\ne i_0$，$N\eta_j'$ 在商中具有无限阶。若某个正倍数为零，就有非零整数倍的 $\eta_j$ 等于一个整数倍的 $\eta_{i_0}$，违背假设。任意加法群中的无限阶元素 $t$ 都使 $1-[t]$ 在群环中可消去。若 $F=[t]F$，其系数沿每个 $\mathbb Zt$ 轨道恒定，而 $F$ 支撑有限，只能全为零。逐一消去这些因子。由于 $s\eta_{i_0}'$ 在 $0\le s<N$ 时两两不同，剩下的表达式为零逐项给出 $P(s)=0$。

## 三、用于半个 Stickelberger 元素的非消失

定义 $e=2$ 若 $\ell=2$，否则 $e=1$，并记

$$
W=\{w\in\mathbb Z_\ell^\times:w^{\varphi(\ell^e)}=1\},\qquad
 Q_m=(\mathbb Z/\ell^m\mathbb Z)^\times/\overline W.
$$

若 $\ell^m\mid M$，记 $\pi_m:(\mathbb Z/M\mathbb Z)^\times\to Q_m$ 为降约后取商。对与 $M$ 互素的正奇数 $c$，写

$$
g(s)=\left\lfloor\frac{c\, [c^{-1}s]_M}{M}\right\rfloor-\frac{c-1}{2},
 \qquad
 \theta_H=\sum_{\substack{s\in(\mathbb Z/M\mathbb Z)^\times\\2[s]_M<M}}g(s)[s],
$$

其中 $[x]_M$ 是在 $0,\ldots,M-1$ 的代表元。这次方括号 $[s]$ 表示乘法群环的基元，其乘法是 $[s][t]=[st]$。

**命题二（[`nonvan`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/Nonvan.lean#L12)）。** 给定任意素数 $\ell$、自然数 $f,c$，且 $(f,\ell)=1$，$c>1$ 为奇数，$(c,f\ell)=1$。存在 $m\ge2$，使对任意 $n\ge m$（取 $M=f\ell^n$）、任意特征 $\ell$ 的域 $k$ 及任意满足 $\chi(-1)=-1$ 的乘法特征 $\chi:(\mathbb Z/M\mathbb Z)^\times\to k^\times$，把 $\theta_H$ 降到 $k$ 后，在群环映射

$$
[s]\longmapsto \chi(s)[\pi_m(s)]
 \tag{3}
$$

下的像非零。源码记此映射为 $\mathrm{tw}(\chi,\pi_m)$。在特征二，$\chi(-1)=-1$ 的右边是 $1$，这个陈述同样适用。

从 $W$ 的每一对 $\{w,-w\}$ 里取一个代表，得非空有限集 $I$。对不同的代表 $w_i,w_j$，若 $a w_i=b w_j$ 且 $a\ne0$，取 $\varphi(\ell^e)$ 次幂得 $a^{\varphi(\ell^e)}=b^{\varphi(\ell^e)}$，故 $a=\pm b$，这将迫使两者是同一对。于是这些 $w_i$ 满足命题一的假设。$W$ 在模 $\ell^m$（$m\ge2$）的降约是单射。对 $\ell=2$，$W=\{1,-1\}$，模 $4$ 可区分。对奇素数，若 $w\equiv1\pmod\ell$ 且 $w^{\ell-1}=1$，则 $1+w+\cdots+w^{\ell-2}\equiv-1\pmod\ell$，所以 $w=1$。

假设 (3) 的像为零。把 $\chi$ 延为模 $M$ 的函数 $\Psi$，令它在非单位上为零。设

$$
\alpha(y)=\sum_{s\bmod M,\,s\equiv y\bmod\ell^m}g(s)\Psi(s).
$$

因为 $(c,M)=1$，对非零剩余类 $s$ 有 $g(-s)=-g(s)$。事实上 $c[c^{-1}s]_M/M$ 非整数，将 $s$ 取负会把此实数 $u$ 换成 $c-u$，故两下取整之和为 $c-1$。由 $\chi(-1)=-1$，$g(s)\chi(s)$ 在 $s$ 与 $-s$ 上相等。若 $y$ 为单位，在 (3) 的 $[y\overline W]$ 系数中，每对 $\{s,-s\}$ 恰取下半区间 $2[s]_M<M$ 的代表。改成每对中满足 $s\bmod\ell^m=w_i^{-1}y$ 的代表，这也是每对取一次，且权值不变。因而该系数就是 $\sum_i\alpha(w_i^{-1}y)$。若 $y$ 不是单位，这个和直接为零。于是得到第二个 (1) 式。

为得到第一个 (1) 式，先观察任意模 $M$ 的 $s$ 满足

$$
g(s)-g(s-c)=\#\{0\le j<c:j\equiv s\bmod M\}-c\,\mathbf 1_{s=0}.
 \tag{4}
$$

写 $a=[c^{-1}s]_M$。若 $a>0$，两个下取整的差数的是区间 $(c(a-1),ca]$ 中的 $M$ 的倍数。以 $ca$ 减去这些倍数，便得到 (4) 的计数。若 $a=0$，左边为 $-\lfloor c(M-1)/M\rfloor=\lceil c/M\rceil-c$，同式仍成立。

特征 $\Psi$ 的周期整除 $f\ell$。因为单位群从模 $f\ell^n$ 降到模 $f\ell$ 的核是 $\ell$ 群，而特征 $\ell$ 的域中满足 $z^{\ell^r}=1$ 的元素只有 $1$。非单位性也由模 $f\ell$ 决定。令 $N=cf\ell$，将 (4) 对 $s,s-c,\ldots,s-c(f\ell-1)$ 望远镜求和，再乘 $\Psi(s)=\Psi(s-N)$，得到

$$
g(s)\Psi(s)-g(s-N)\Psi(s-N)
 =\sum_{\substack{0\le j<N\\j\equiv s\bmod M}}
       \Psi(j)\bigl(1-c\mathbf1_{c\mid j}\bigr).
$$

将所有降到 $y$ 的 $s$ 求和，左边第二项平移后为 $\alpha(y-N)$。这给出第一个 (1) 式，其中 $P(j)=\Psi(j)(1-c\mathbf1_{c\mid j})$。事先取命题一给出的 $m$，再增至至少 $2$。它只依赖于 $\ell,f,c$。命题一现在推出 $P(1)=0$，但 $1<N,\ \Psi(1)=1,\ c\nmid1$，故 $P(1)=1$，矛盾。这就证明了非消失。

## Lean 对照

- [`sinFin`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/SinFin.lean#L5) `sinFin` 对应有限群环恒等式，[`sinSupp`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/SinSupp.lean#L24) `sinSupp` 给统一有限支撑，[`sep`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/SepPair.lean#L18) `sep` 在高层区分支撑，[`sinLem`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/SinLem.lean#L18) `sinLem` 在商群中消去移位因子。[`sinnott`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/Sinnott.lean#L10) `sinnott` 合成前两节。[SinFin 第 5 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/SinFin.lean) · [SinSupp 第 24 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/SinSupp.lean) · [SinLem 第 18 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/SinLem.lean) · [Sinnott 第 10 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/Sinnott.lean)
- [`reps`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/EvenTot.lean#L24) `reps` 选正负对的代表，[`twCoef`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/TwCoef.lean#L60) `twCoef` 改换代表读取 (3) 的系数，[`gcDiff`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/GcDiff.lean#L25)、[`gcShift`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/GcShift.lean#L46)、[`pushDiff`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/PushDiff.lean#L5) 分别证明 (4)、大步平移、再降模。[`charPer`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/CharPer.lean#L5) `charPer` 给周期性。[`nonvan`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/Nonvan.lean#L12) `nonvan` 用 $P(1)=1$ 完成反证。[代表第 24 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/EvenTot.lean) · [系数第 60 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/TwCoef.lean) · [平移第 46 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/GcShift.lean) · [非消失第 12 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/Nonvan.lean)

本篇为源码对读。统一性来自第一节的有限支撑，取 $m$ 时尚无层数 $n$ 或特征 $\chi$。所列声明的内核重放及传递公理状态未查。
