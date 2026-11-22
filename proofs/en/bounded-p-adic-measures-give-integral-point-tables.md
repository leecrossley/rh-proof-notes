# Bounded p-adic measures give integral point tables

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $p$ be prime, $r\ge0$, $I$ any index set, and $g_i:\mathbb Z_p^r\to\mathbb C_p$ continuous for $i\in I$. Let $\mu:C(\mathbb Z_p^r,\mathbb C_p)\to\mathbb C_p$ be a $\mathbb C_p$-linear functional of operator norm at most one for the supremum norm. For any finite $I_0\subseteq I$ and $\epsilon>0$, there exist finitely many $a\in\mathbb N^r$ and weights $c_a\in\mathcal O_{\mathbb C_p}$ with
$$
\left|\mu(g_i)-\sum_a c_a g_i(a)\right|_p<\epsilon\qquad(i\in I_0).
$$
In particular the full table $(\mu(g_i))_i$ is in the integral closure of the span of the point tables $(g_i(a))_i$, in the topology of simultaneous approximation on finite subsets. If $g_i(a)$ factors through a map $a\mapsto x(a)$, the same conclusion holds with tables indexed by $x(a)$.

The functions $g_i$ for $i\in I_0$ are uniformly continuous on the compact space $\mathbb Z_p^r$. Choose $n$ such that within each residue box modulo $p^n$ their oscillations are at most $\epsilon/2$. Each box $B_a$ has a representative $a$ with coordinates in $[0,p^n-1]$. Its indicator $1_{B_a}$ is continuous because the box is both open and closed. Set $c_a=\mu(1_{B_a})$, which has norm at most one by the operator bound. The step function $\sum_a g_i(a)1_{B_a}$ differs uniformly from $g_i$ by at most $\epsilon/2$. Applying $\mu$ proves the estimate, with the same weights for the entire finite set. If several representatives map to the same $x$, sum their weights. The nonarchimedean triangle inequality keeps the new weight integral.

### The theta moment tables

For the word-prime application, take the theta and period data of one admitted pair. Let $M$ be the period lattice of homomorphisms for an admitted theta pair, and let $t$ be a translation with $nt\in M$ for some positive $n$ prime to $p$. Let $p=\pi\bar\pi$ with $\pi,\bar\pi$ coprime in the CM coefficient lattice, and assume every coefficient embedding inducing the place in question sends $\pi$ to an element of norm $<1$. The analytic moment law for the unit period $\Omega$ supplies an $N_0$ prime to $p$ and a bounded functional of the indicated form. For $y\in M$ let $v=N_0\bar\pi/\pi$. The relevant family is indexed by pairs $(y,m)$ with $m$ a jet exponent. The transported moment identity supplies continuous $g_{y,m}$ and a common scalar $\alpha$ with $|\alpha|_p=1$, such that the normalized jet of the successive translates by $t$ and $vy$ is $\alpha\mu(g_{y,m})$. On natural inputs $a$,
$$
g_{y,m}(a)=\lambda(\operatorname{brk}(vy,x(a)))\,\operatorname{ptTab}(x(a),m),\qquad
x(a)=\sum_{l=1}^r a_l\beta_l\in M .
$$
Here $\operatorname{brk}$ is the character given by the alternating period pairing, $\lambda$ is the chosen embedding of algebraic numbers into $\mathbb C_p$, and $\operatorname{ptTab}$ evaluates the monomial $m$ on the normalized adjoint matrix of $x(a)$. The normalization in each embedding $\tau$ is $u_\tau=\lambda(c_\tau)/\Omega$ for the site's differential generator $c_\tau$.

Two checks explain why this identity applies to these indices. First $pv=N_0\bar\pi^2$ is integral, so replacing any $a_l$ by $a_l+pb_l$ leaves the bracket character unchanged by the integrality of the period pairing. It therefore extends continuously by reduction modulo $p$. Second the translate $vy$ is an allowed first-level lift for the moment law: its expression $N_0\bar\pi^2y/p$ has the prescribed numerator, whose conjugate has norm $p^{-2}$ at the selected embedding. The jet identity is obtained by expanding the matrix monomial into directional derivatives and using the moment identity on those derivatives. The unit $\alpha$ is the Weil translation prefactor for $t$. The residue-box argument now gives the integral closure on the period lattice with exactly the bracket-twisted point tables in the display. Multiplication by $\alpha$ preserves the integral coefficient bound.

[The normalized pair construction](transporting-the-bounded-measure-to-the-normalized-theta-pair.md) gives the analytic moment functional with its bound and the directional identities under the stated model hypotheses. The residue-box assertion itself uses only continuity and the norm bound.

### Lean correspondence

- [`riemann_sums`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/IsLocallyConstantToZModPow.lean#L55) proves the finite simultaneous approximation.
- [`MomentsAt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/TranslateMomentsAll.lean#L23) states the analytic moment input, and [`PtMom`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/TranslateMomentsAll.lean#L84) states the resulting bracket-twisted closure.
- [`ptMom`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ContinuousToZModComp.lean#L342) constructs the functions and applies the approximation.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
