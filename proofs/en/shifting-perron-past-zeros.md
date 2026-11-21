# Shifting the Perron contour past zeros

[Chinese proof](../zh/%E7%A7%BB%E5%8A%A8Perron%E7%A7%AF%E5%88%86%E6%97%B6%E6%80%8E%E6%A0%B7%E9%81%BF%E5%BC%80%E9%9B%B6%E7%82%B9.md)

Let $\chi$ be primitive modulo $q\ge1$, $2\le T\le u$, and $c=1+1/\log u$. Define $Z(Y)$ to be the zeros of $L(s,\chi)$ with $0<\Re\rho<1$ and $|\Im\rho|<Y$, and write $m_\rho$ for multiplicity.

**Proposition.** There is an absolute $C>0$ such that for each such input one can choose $T'\in[T,T+1]$ with
$$
\left|\frac1{2\pi}\int_{-T'}^{T'}-\frac{L'}{L}(c+it,\chi)\frac{u^{c+it}}{c+it}\,dt
-\mathbf1_{q=1}u+\sum_{\rho\in Z(T')}m_\rho\frac{u^\rho}{\rho}\right|
\le C\left(\frac{u\log^2(quT)}{T}+\log(qu)+
\sum_{\rho\in Z(1)}\frac{m_\rho}{|\rho|}\right).
\tag{1}
$$

## Choosing one height for both edges

The [strip formula](local-log-derivative-from-disk-zeros.md) bounds both the total multiplicity within $7/2$ of $2+iv$ and the error in the log derivative after subtracting the corresponding fractions by $O(\log(q(|v|+2)))$. Its evaluation range here is $-1\le\Re s\le2$, $\Im s=v$, excluding zeros and the pole. The zeta pole correction is bounded when $|v|\ge2$.

For $t\in[T,T+1]$, a zero in the disk at $2+it$ with $-1\le\Re w<1$ lies in at least one of the disks at the endpoints $2+iT$ and $2+i(T+1)$. If the height lies outside $[T,T+1]$, the nearer endpoint only reduces the distance. Otherwise its height differs from the nearer endpoint by at most $1/2$, while its real part differs by at most $3$, and $\sqrt{9+1/4}<7/2$. Apply the same argument to $-t$ with endpoints $-T,-T-1$. Collect the heights from the positive endpoint disks and the negative heights of zeros from the negative endpoint disks into one set of $J\ll\log(qT)$ real numbers. Removing the open neighborhoods of radius $d=1/(2(J+1))$ of these numbers costs total length less than $1$. Choose $T'$ in the remaining part of $[T,T+1]$.

For $-1/2\le\Re s\le2$ on either horizontal edge, each local zero $w$ with $\Re w\ge-1$ is at distance at least $d$ by the choice of height. If $\Re w<-1$, the real parts are at distance at least $1/2$. Applying the disk count and derivative formula gives $|L'/L(s,\chi)|\ll\log^2(qT)$ and shows the edges are zero-free. For $2\le\Re s\le c$ use the absolutely convergent series at real part $2$.

## The left edge and the origin

On $\Re w\le0$, primitive $L$-functions can have only the simple trivial zeros at integers. In the functional equation the reflected point $1-w$ has real part at least $1$, where the $L$-function is nonzero and the Gamma factor has no zero or pole. The left zeros therefore arise from the simple zeros of $1/\Gamma((w+a)/2)$, with parity $a\in\{0,1\}$. At $q=1,w=0$ use $\zeta(0)=-1/2$ separately because the completed zeta function has a pole. Hence every point of the line $\Re s=-1/2$ is at distance at least $1/2$ from each zero. The strip formula gives $|L'/L(-1/2+it,\chi)|\ll\log(q(|t|+2))$, including the bounded zeta pole term.

Write $L'/L(s,\chi)=m/s+h(s)$ near zero with $h$ holomorphic and $m\in\{0,1\}$. Approach $0$ through positive reals in the disk formula at center $2$ after subtracting $m/s$. The other finitely many zero terms converge to $m_w/(-w)$. Nonzero trivial zeros have $|w|\ge1$, and zeros at $|\Im w|\ge1$ do too. Their total multiplicity is $O(\log(2q))$, while the remaining zeros belong to $Z(1)$. Thus
$$
|h(0)|\ll\log(2q)+\sum_{\rho\in Z(1)}m_\rho/|\rho|.
\tag{2}
$$

## The residue sum

Shift $G(s)=-(L'/L)(s,\chi)u^s/s$ on the rectangle with real edges $-1/2,c$ and heights $\pm T'$. The right edge is zero-free by the Euler product, and the other edges have just been treated. Nontrivial zeros inside are exactly $Z(T')$, contributing residues $-m_\rho u^\rho/\rho$. The pole at $1$ for $q=1$ contributes $u$. At $0$ the expansion $u^s=1+s\log u+O(s^2)$ gives
$$
G(s)=-m/s^2-(m\log u+h(0))/s+O(1).
$$
So (2) bounds the extra residue after adding $\log u$. The horizontal integrals together are $O((u/T)\log^2(quT))$, by bounded edge lengths, $|s|\ge T$ and $|u^s|\le eu$. On the left, $|u^s|=u^{-1/2}$ and the integral of $(1/4+t^2)^{-1/2}$ over $|t|\le T'$ is $O(\log(2T'+1))$. The resulting error $O(u^{-1/2}\log(q(T'+2))\log(2T'+1))$ fits the same bound since $u/T\ge1$. Taking the right edge upwards, the residue theorem gives (1).

## Lean correspondence

- `GlobalTheory.GoodHeight.exists_far`, `local_formula` and `exists_height` construct the choice of $T'$. The trivial-zero statement is `GlobalTheory.LFunction_zero_of_re_nonpos`. [Height choice](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsBoundRight.lean#L150) · [Trivial zeros](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/CompletedLFunctionNeZeroOfReNonpos.lean)
- `logDeriv_LFunction_near_zero` gives (2), and `GlobalTheory.ExplicitRect.residue_identity` and `GlobalTheory.PerronShift.perron_shift` give the residue identity and (1). The Chinese note records local Lean verification of the upstream strip formula. [Origin](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LogDerivLFunctionNearZero.lean#L104) · [Residues](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/AnalyticAtDslope.lean#L189) · [Shift](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/PerronIntegralShiftPrimitiveLFunction.lean#L227)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
