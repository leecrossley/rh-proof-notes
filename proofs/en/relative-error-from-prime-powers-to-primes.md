# Transferring relative error from prime powers to prime counts

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E6%8A%8A%E9%80%9A%E7%94%A8%E7%9A%84%E7%B4%A0%E6%95%B0%E5%B9%82%E7%9B%B8%E5%AF%B9%E8%AF%AF%E5%B7%AE%E4%BC%A0%E7%BB%99%E7%B4%A0%E6%95%B0%E4%B8%AA%E6%95%B0.md)

For a predicate $P$ on positive integers define $\psi_P(u)=\sum_{n\le u,\ P(n)}\Lambda(n)$ and $\pi_P(u)=\#\{p\le u:p\text{ prime},\ P(p)\}$. Let $\operatorname{Li}(y)=\int_2^y dt/\log t$ for $y>1$. Set $J(u)=u-\theta u^\beta/\beta$ and $H(u)=\operatorname{Li}(u)-\theta\operatorname{Li}(u^\beta)$. The second terms are omitted for $\theta=0$. The project calls $H$ the main term `Emain`.

**Proposition.** Given $c_2,c_3,C,c_{\rm S}>0$, there exist $c_2',c_3',C'>0$ as follows. Let $B\ge3$, $1\le\phi\le B$, $\beta\in\mathbb R$, and $\theta\in\mathbb Z$. Assume $\theta=0$, or $\theta=\pm1$ with $7/8\le\beta$ and $1-\beta\ge c_{\rm S}/B^3$. Put $\mathcal E_c(v)=e^{-c\log v/\log B}+e^{-\sqrt{c\log v}}$. If
$$
|\phi\psi_P(u)-J(u)|\le C\mathcal E_{c_3}(u)J(u)\quad(u\ge B^{c_2}),
\tag{1}
$$
then $|\phi\pi_P(X)-H(X)|\le C'\mathcal E_{c_3'}(X)H(X)$ for every $X\ge B^{c_2'}$.

## Removing the higher prime powers

When $\theta=0$ take $\beta=7/8$, which leaves both main terms unchanged. With $c_*=\min(c_{\rm S},1)$ and $\delta=c_*/B^3$, both cases have $7/8\le\beta<1$ and $1-\beta\ge\delta$. Consider $Y=s^8$, $X=s^{16}$ with $\delta s\ge64B$, and suppose the error in (1) on $[Y,X]$ is bounded by $rJ(u)$ with $r\ge0$.

On this interval $\delta u\le J(u)\le3u$. For the lower bound when $\theta=1$, put $d=1-\beta$. We have $u/u^\beta\ge1+4d$ since $\log u\ge4$. Also $\beta^2\ge3/4$ and $\beta^2\ge1-2d$ give $(1+4d)\beta^2\ge1$. Thus $u^\beta/\beta\le\beta u$ and $J(u)\ge du\ge\delta u$. The other cases and upper bound follow from $u^\beta\le u$, $1/\beta\le2$.

Let $\vartheta_P(u)=\sum_{p\le u,\ P(p)}\log p$. The nonnegative difference $\psi_P-\vartheta_P$ is bounded by $2\sqrt u\log u$, since the higher powers come from primes $p\le\sqrt u$ with weight at most $\log u$ per prime. As $\log u\le4u^{1/4}$ and $\delta u^{1/4}\ge\delta s^2\ge64Bs$,
$$
\phi|\psi_P(u)-\vartheta_P(u)|\le8Bu^{3/4}\le\delta u/s\le J(u)/s.
$$
Thus the relative error for $\phi\vartheta_P$ is at most $r+1/s$.

## Partial summation and the initial endpoint

Abel summation gives
$$
\pi_P(X)-\pi_P(Y)=
\vartheta_P(X)/\log X-\vartheta_P(Y)/\log Y
+\int_Y^X\vartheta_P(t)\frac{dt}{t\log^2 t}.
$$
Since $H'(t)=J'(t)/\log t$, the same formula for $H(X)-H(Y)$ uses $J$ in place of $\vartheta_P$. Subtracting the formulas gives
$$
|\phi(\pi_P(X)-\pi_P(Y))-(H(X)-H(Y))|
\le(r+1/s)(H(X)-H(Y)+2J(Y)/\log Y).
\tag{2}
$$
We have $|H(Y)|\le3Y$ by $2\le Y^\beta\le Y$ and $\operatorname{Li}(v)\le(3/2)v$ for $v\ge2$. Also $J(Y)/\log Y\le Y$. At the upper endpoint, $J(X)/\log X\ge\delta s^{16}/(16\log s)\ge8s^{14}$ using $\delta s\ge64B\ge128$ and $\log s\le s$. The integral in the formula for $H$ is nonnegative, giving $H(X)\ge8s^{14}-4Y\ge4s^{10}$. Thus the right side in (2) is at most $3(r+1/s)H(X)$. The omitted endpoint costs $|\phi\pi_P(Y)-H(Y)|\le(B+3)Y\le H(X)/s$ since $B+3\le s$. In total the error is at most $(3r+4/s)H(X)$.

## Applying the interval estimate

Take $c_2'=16(c_2+4+64/c_*)$, $c_3'=\min(c_3/2,1/16)$ and $C'=3C+4$. For $X\ge B^{c_2'}$, $s=X^{1/16}$ satisfies $\delta s\ge64B$ and $Y=s^8\ge B^{c_2}$. On $[Y,X]$, $\log u\ge(\log X)/2$, so $\mathcal E_{c_3}(u)\le\mathcal E_{c_3'}(X)$. Also $1/s\le\mathcal E_{c_3'}(X)$. Apply the interval estimate with $r=C\mathcal E_{c_3'}(X)$.

**Progression corollary.** There exist $0<h\le1/8$ and $c_2',c_3',C',c_{\rm S}>0$ that work for every integer $M\ge3$. There is at most one exceptional pair modulo $M$ in the sense of `IsExc h`, with $1-\beta\ge c_{\rm S}/(M^2\log M)$ when present. For each unit $b\bmod M$ and $\theta,\beta$ satisfying `ExcData h M b θ β`, the conclusion holds for $P(n)=(n\equiv b\bmod M)$, $B=M$, and $\phi=\varphi(M)$. Indeed choose $h$ in the range of both the [exceptional-pair theorem](exceptional-zero-change-of-modulus.md) and the [relative prime-power estimate](relative-prime-power-error-in-progressions.md). They give the gap and (1), and $\log M\le M$ yields the required weaker gap $c_{\rm S}/M^3$. This is the statement `PrimesRel`.

## Lean correspondence

- `integral_main`, `abel`, `psi_sub_wt`, `main_bounds` and `step` handle the interval argument, which `pi_rel_of_psi_rel` applies. [Summation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/PrimeCountRelativeErrorOfPsiRelativeError.lean#L95) · [Interval](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/PrimeCountRelativeErrorOfPsiRelativeError.lean#L215) · [Conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/PrimeCountRelativeErrorOfPsiRelativeError.lean#L309)
- `GlobalTheory.Lin.primesRel_holds` gives the corollary, using `chebyshevPsiProgression_relative_error` for the hypothesis (1). [Progression corollary](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/PrimesInProgressionsRelativeError.lean#L22) · [Forwarding theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/PrimesInProgressionsRelativeErrorStatement.lean#L8)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
