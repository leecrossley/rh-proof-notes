# A unit difference bounds the relaxation at a ramified place

[Chinese proof](../zh/%E6%8C%87%E5%AE%9A%E7%B4%A0%E5%A4%84%E7%9A%84%E5%8D%95%E4%BD%8D%E5%B7%AE%E6%80%8E%E6%A0%B7%E7%95%8C%E5%AE%9A%E5%B1%80%E9%83%A8%E6%94%BE%E5%AE%BD%E4%BB%A3%E4%BB%B7.md)

**Proposition.** Let $A$ be a ring with central coefficients $T'$, $r:G\to A^\times$, $\chi:G\to(T')^\times$, and $u(g)=\chi(g)^{-1}r(g)$. Let $M$ be a left $A$-module with a commuting action of a commutative ring $\mathcal O$. For $E\in A$, set $y(g)=(u(g)-1)E$ and let $Y$ be the left ideal these elements generate. Each $A$-linear map $f:Y\to M$ gives a cocycle $z_f(g)=f(y(g))$.

Let $I\subseteq D\subseteq G$ be the inertia subgroup and ambient local group. Suppose $\gamma\in I$, $\zeta\in T'$ and $\zeta_{\mathcal O}\in\mathcal O$ satisfy $(r(\gamma)-1)(r(\gamma)-\zeta)=0$ and $\chi(\gamma)=\zeta$. For every $g\in I$ suppose a nonnegative integer $n(g)$ is given with $r(g)=r(\gamma)^{n(g)}$ and $\chi(g)=\chi(\gamma)^{n(g)}$. Assume $u$ acts trivially on $M$ over $I$ and $r(\gamma)$ acts as the scalar $\zeta_{\mathcal O}$. Set $F=\ker(H^1(D,M)\to H^1(I,M))$. Then there is a submodule $B\supseteq F$ containing every $[z_f|_D]$ with
$$
\operatorname{length}(B/F)\le \operatorname{length}M[\zeta_{\mathcal O}-1].
\tag{1}
$$

Since $\zeta$ is a unit, $(r(\gamma)-1)y(\gamma)=\zeta^{-1}(r(\gamma)-1)(r(\gamma)-\zeta)E=0$. Thus $(\zeta_{\mathcal O}-1)z_f(\gamma)=0$. Over $I$, the cocycle is additive and its value at $\gamma^n$ is $nz_f(\gamma)$. The given powers imply $y(g)=y(\gamma^{n(g)})$, so $z_f(g)=n(g)z_f(\gamma)$.

With trivial action, $H^1(I,M)$ has zero coboundaries. Take $B$ to be the inverse image under restriction of the submodule of cocycles satisfying the last two constraints on $z_f|_I$. Evaluation after restriction at $\gamma$ maps $B$ to $M[\zeta_{\mathcal O}-1]$. The kernel is exactly $F$, because the single value determines the whole restricted cocycle. This proves (1). For $M=K/\mathcal O$ over a DVR and $\zeta_{\mathcal O}\ne1$, multiplication by $\zeta_{\mathcal O}-1$ identifies the torsion with $\mathcal O/(\zeta_{\mathcal O}-1)$, of length $\operatorname{ord}_{\mathcal O}(\zeta_{\mathcal O}-1)$. Each one-dimensional positive block uses this at every specified place in $Q$.

## Lean correspondence

- `StatQAlg` and `StatQPlace` state the conditions. `qAlg` and `qPlace` give (1), and `bridgeChiC` and `bridgeChiOne` apply it to the two kinds of positive blocks. [Statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/CoprimeLiftBounds/Statement.lean#L202) · [Algebra](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/CoprimeLiftBounds/CoprimeLiftProofs/SmulYGenEqZero.lean#L54) · [Length](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/CoprimeLiftBounds/CoprimeLiftProofs/YGenCongr.lean#L23) · [Application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/CoprimeLiftBounds/CoprimeLiftProofs/Bridge.lean#L45)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
