# Sinnott's finite differences imply nonvanishing

[Chinese proof](../zh/Sinnott%E5%BC%95%E7%90%86%E6%80%8E%E6%A0%B7%E4%BB%8E%E6%9C%89%E9%99%90%E5%B7%AE%E5%88%86%E6%8E%A8%E5%87%BA%E9%9D%9E%E6%B6%88%E5%A4%B1.md)

## The finite-difference lemma

Let $\ell$ be prime, $I$ finite nonempty, and $\eta_i\in\mathbb Z_\ell^\times$ such that $a\eta_i=b\eta_j$ for integers $a,b$ and $i\ne j$ implies $a=0$. Given $N>0$ there is $n_0$ such that for any $n\ge n_0$, commutative ring $k$, $P:\mathbb N\to k$ and $\alpha:\mathbb Z/\ell^n\mathbb Z\to k$, the identities
$$
\alpha(y)-\alpha(y-N)=\sum_{0\le s<N,\ s\equiv y\bmod\ell^n}P(s),\qquad
\sum_i\alpha(\bar\eta_i^{-1}y)=0
$$
for all $y$ imply $P(s)=0$ for $0\le s<N$. Bars denote reduction. This is `sinnott`.

In the additive group ring of $\mathbb Z/\ell^n\mathbb Z$, write $F_i=\sum_y\alpha(y)[\bar\eta_i y]$ and $B_i=\sum_{s<N}P(s)[s\bar\eta_i]$. Comparing coefficients gives $B_i=(1-[N\bar\eta_i])F_i$ and $\sum_iF_i=0$. Multiply the latter by all the difference factors to deduce the vanishing after reduction of
$$
E=\sum_i\left(\sum_{s<N}P(s)[s\eta_i]\right)\prod_{j\ne i}(1-[N\eta_j])
$$
in the additive group ring $k[\mathbb Z_\ell]$. Its possible support is finite and fixed by $I,N,\eta$, so any sufficiently high reduction is injective on that support. Hence $E=0$.

Fix $i_0$ and pass to $\mathbb Z_\ell/\mathbb Z N\eta_{i_0}$. Only the $i_0$ term survives. Each remaining difference factor $1-[N\eta_j]$ has shift of infinite order by the hypothesis on integer relationships. Such a factor is a nonzerodivisor: a finite-support function invariant by the shift is constant on infinite orbits and thus zero. Cancel them all. The elements $s\eta_{i_0}$ for $0\le s<N$ have distinct images in this quotient, giving $P(s)=0$.

## The half Stickelberger element

Set $e=2$ at $\ell=2$ and $e=1$ otherwise. Let $W=\{w\in\mathbb Z_\ell^\times:w^{\varphi(\ell^e)}=1\}$ and $Q_m=(\mathbb Z/\ell^m\mathbb Z)^\times/\overline W$. For $\ell^m\mid M$ let $\pi_m$ reduce units and pass to this quotient. For $c>1$ odd and prime to $M$, put
$$
g(s)=\left\lfloor\frac{c\langle c^{-1}s\rangle_M}{M}\right\rfloor-\frac{c-1}{2},\qquad
\theta_H=\sum_{s\in(\mathbb Z/M\mathbb Z)^\times,\ 2\langle s\rangle_M<M}g(s)[s].
$$
Here $\langle s\rangle_M$ is the least nonnegative representative. Brackets now denote multiplicative group-ring basis elements. Fix $f$ prime to $\ell$ and $c$ also prime to $f\ell$. The assertion `nonvan` is that some $m\ge2$ works for every $n\ge m$, $M=f\ell^n$, every field $k$ of characteristic $\ell$, and every $\chi:(\mathbb Z/M\mathbb Z)^\times\to k^\times$ with $\chi(-1)=-1$. The image of $\theta_H$ under $[s]\mapsto\chi(s)[\pi_m(s)]$ is nonzero.

Choose one $w_i$ from each pair $\{w,-w\}$ of $W$. An integer relation between distinct representatives, after raising to $\varphi(\ell^e)$, would give $a=\pm b$ for nonzero coefficients and hence the same pair. Thus the finite-difference lemma applies with these $w_i$. Reduction of $W$ is injective at $m\ge2$. At two this follows from $W=\{\pm1\}$ modulo four. For odd $\ell$, an element of $W$ congruent to one mod $\ell$ must equal one by the geometric sum with $\ell-1$ terms, which is a unit.

Suppose the twisted image vanishes. Extend $\chi$ by zero to $\Psi$ on nonunits and put $\alpha(y)=\sum_{s\bmod M,\ s\equiv y\bmod\ell^m}g(s)\Psi(s)$. For nonzero $s$, changing sign makes $g(-s)=-g(s)$ since the nonintegral $c\langle c^{-1}s\rangle_M/M$ changes to $c$ minus itself. Hence $g(s)\chi(s)$ is constant on pairs $\{s,-s\}$. At a unit $y$, the coefficient of its coset in $Q_m$ collects one lower-half representative per pair. One may instead use those reducing to $w_i^{-1}y$ for the chosen $w_i$, so this coefficient is $\sum_i\alpha(w_i^{-1}y)$. For nonunits the sum is zero by definition. This is the second finite-difference hypothesis, including in characteristic two where $-1=1$.

For the first, for residues $s$,
$$
g(s)-g(s-c)=\#\{0\le j<c:j\equiv s\bmod M\}-c\mathbf1_{s=0}.
$$
If $a=\langle c^{-1}s\rangle_M>0$, the floor difference counts multiples of $M$ in $(c(a-1),ca]$, corresponding to the indicated $j$ by subtraction from $ca$. If $a=0$, the left is $\lceil c/M\rceil-c$, which is the same formula. The character $\Psi$ is periodic mod $f\ell$: the reduction kernel on units is an $\ell$-group, with only trivial image in $k^\times$, and nonunit status already follows from this smaller modulus. Set $N=cf\ell$. Telescope along $f\ell$ steps of size $c$ and multiply by $\Psi(s)=\Psi(s-N)$ to obtain
$$
g(s)\Psi(s)-g(s-N)\Psi(s-N)
=\sum_{0\le j<N,\ j\equiv s\bmod M}\Psi(j)(1-c\mathbf1_{c\mid j}).
$$
Push to modulus $\ell^m$ to get the first hypothesis with $P(j)=\Psi(j)(1-c\mathbf1_{c\mid j})$. Choose $m$ at least the finite-difference threshold for this $N$ and at least two, before choosing $n$ or $\chi$. Then $P(1)=0$ from the lemma, whereas the formula gives one. This proves nonvanishing.

## Lean correspondence

- [`sinFin`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/SinFin.lean#L5), [`sinSupp`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/SinSupp.lean#L24), [`sep`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/SepPair.lean#L18), [`sinLem`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/SinLem.lean#L18) and [`sinnott`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/Sinnott.lean#L10) give the finite identity, support separation, and cancellation.
- [`reps`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/EvenTot.lean#L24), [`twCoef`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/TwCoef.lean#L60), [`gcDiff`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/GcDiff.lean#L25), [`gcShift`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/GcShift.lean#L46), [`pushDiff`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/PushDiff.lean#L5) and [`charPer`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/CharPer.lean#L5) verify the character and difference hypotheses. [`nonvan`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/Nonvan.lean#L12) assembles them.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
