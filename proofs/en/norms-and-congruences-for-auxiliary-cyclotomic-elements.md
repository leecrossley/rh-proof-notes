# Norms and congruences for auxiliary cyclotomic elements

[Chinese proof](../zh/%E8%BE%85%E5%8A%A9%E5%88%86%E5%9C%86%E5%85%83%E7%B4%A0%E7%9A%84%E8%8C%83%E6%95%B0%E4%B8%8E%E5%90%8C%E4%BD%99%E6%80%8E%E6%A0%B7%E7%9B%B8%E5%AE%B9.md)

Use $K_N,G_N,\theta_{N,b}$ and $\operatorname{IsX}_{N,b}(\mathfrak a,X)$ from the [Jacobi generator construction](jacobi-sums-generate-a-prescribed-fractional-ideal.md), extending the floor formula for any $b\ge0$. Fix $N>0$, prime $q\nmid N$, $u=q\bmod N$, $K=K_N$, $K'=K_{qN}$, $0\le b<q$, and nonzero ideal $\mathfrak a\subset\mathcal O_{qN}$ with norm $\mathfrak n$. Let $X',X$ satisfy $\operatorname{IsX}_{qN,b}(\mathfrak a,X')$, $\operatorname{IsX}_{N,b}(\mathfrak n,X)$, respectively. Then
$$
\mathrm N_{K'/K}X'=\xi\,X/\sigma_u^{-1}X,\qquad \xi^{2N}=1,\quad \xi\in K.
$$
If also $b<N$ and $\mathfrak a$ is prime to $q$, then $X'\equiv\zeta\,\sigma_u^{-1}X$ at every place above $q$, for a single $\zeta\in K'$ with $\zeta^{2qN}=1$.

**Distribution of the floors.** For the unit reduction $\pi:G_{qN}\to G_N$ and $t\in G_N$,
$$
\sum_{\pi(t')=t}\theta_{qN,b}(t')=\theta_{N,b}(t)-\theta_{N,b}(u^{-1}t).
$$
For $b=0$ this is immediate. Otherwise take all lifts $a_j=[t]_N+jN$, $0\le j<q$, with $bj=qn_j+r_j$. The $r_j$ permute $0,\dots,q-1$, so $\sum n_j=(b-1)(q-1)/2$. With $x=b[t]_N/N$, $\sum_{r=0}^{q-1}\lfloor(x+r)/q\rfloor=\lfloor x\rfloor$, by quotient and remainder. Thus the sum of the positive floor over all lifts is that constant plus $\lfloor x\rfloor$. Remove the lift $q[u^{-1}t]_N$ and subtract the analogous formula for $-t$. For the norm, conjugate ideals have norm $\mathfrak n_{\pi(t')}$, by the equivariance of residue degrees. The distribution formula gives
$$
(\mathrm N X')=\prod_t\mathfrak n_t^{\theta_{N,b}(t)-\theta_{N,b}(u^{-1}t)}
=(X/\sigma_u^{-1}X).
$$
Both elements have product with their complex conjugate $1$, since conjugation commutes with the norm and $\sigma_u^{-1}$. The uniqueness argument gives $\xi$. [`thDist`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/ThDist.lean#L140) · [`xNormDiv`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/XNormDiv.lean#L272)

**Congruence on prime and principal ideals.** First take $\mathfrak a=\mathfrak P$ of degree one over $p\nmid qN$, with residue field $\mathbb F_p$. The Jacobi characters $\chi',\chi$ in $K',K$ lift $x^D,x^{qD}$ respectively, $D=(p-1)/(qN)$, and vanish at zero. Reduction at $\mathfrak P$ is injective on $\mu_{qN}$, so $\chi'(x)^q=\chi(x)$ for $x\ne0$. Also $(\sigma_u^{-1}\chi(x))^q=\chi(x)$; these $q$-th roots reduce to the same value at all places above $q$ in characteristic $q$. Thus the characters and their complex conjugates agree after reduction and applying $\sigma_u^{-1}$ to the lower level. Substitute in the individual Jacobi sums and multiply. Their quotients $c(J')/J'$ and $\sigma_u^{-1}(c(J)/J)$ agree on reduction, since denominators divide powers of $p$ and are units at $q$. The norm ideal is $\mathfrak P\cap\mathcal O_N$ by residue degree one. The root-of-unity differences between the chosen and constructed generators produce the same $\zeta$ at all places above $q$.

For a principal ideal $(y)$ with $y$ integral and a unit everywhere above $q$, take $A=A_{qN,b}(y)$ and $B=A_{N,b}(\mathrm N y)$ from the principal formula. At a chosen $q$-place let $f(t)$ be the residue of $\sigma_{t'}^{-1}y$ for $\pi(t')=t$. It is independent of lift by total relative ramification at $q$. A Frobenius lift acting by $u$ downstairs gives $f(ut)^q=f(t)$. Grouping by the distribution formula,
$$
\bar A=\prod_t\left(\frac{f(t)}{f(ut)}\right)^{\theta_{N,b}(t)}
      =\prod_t f(ut)^{(q-1)\theta_{N,b}(t)}.
$$
This is the residue of $\sigma_u^{-1}B$, because $\sigma_{ut}^{-1}(\mathrm N y)$ has $q-1$ factors each reducing to $f(ut)$.

For general $\mathfrak a$ prime to $q$, choose a degree-one $\mathfrak P$ in its inverse class avoiding $qN$ and write $\mathfrak a\mathfrak P=(y)$. The ratios $A/X'$ and $B/X$ give generators for $\mathfrak P$ and its norm satisfying $\operatorname{IsX}$. Their congruence at all places is the prime case with one root factor $\xi_1$. Divide by the principal congruence of units to obtain the desired congruence with $\zeta=\xi_1^{-1}$. [`xCongJac`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/XCongJac.lean#L101) · [`xCongPrin`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/XCongPrin.lean#L128) · [`xCong`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/AlgStep.lean#L99)

**The auxiliary system.** For primes $\ell,r$, $F>0$, $r\equiv1\bmod F$, $0\le b<F$, fix an absolute place above $r$. For every squarefree $d$ with prime factors $p\equiv1\bmod F$, $p\ne r$, $\ell\nmid\operatorname{ord}_p(r)$, let $\mathfrak r_d$ be that place on $K_{Fd}$ and take a generator $X_d$ satisfying $\operatorname{IsX}_{Fd,b}(\mathfrak r_d,X_d)$. For $qd$ admissible, the norm of $\mathfrak r_{qd}$ is $\mathfrak r_d^{s_0(d,q)}$ with the relative residue degree. This divides $\operatorname{ord}_{Fqd}(r)$ by multiplication of residue degrees, which is prime to $\ell$ by the Chinese remainder theorem. Apply the two proved relations to $N=Fd$, $X'=X_{qd}$, $X=X_d^{s_0(d,q)}$. Here $b<N,b<q$ and the ideal avoids $q$. This gives the norm $(X_d/\Phi^{-1}X_d)^{s_0}$ and congruence to $(\Phi^{-1}X_d)^{s_0}$ up to roots in $\mu_{2Fqd}$, where $\Phi$ acts by $q$ at level $Fd$. The ideal formula gives units away from $r$, and at $d=1$ full splitting gives $v_r(\sigma_t X_1)=\theta_{F,b}(t)$ for $v_r(r)=1$. These are all the inputs of `laxEx` used to [construct the Kummer system](transferring-a-kummer-value-from-frobenius-to-inertia.md). [Relative norm](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/RelNormCyclotomicPrimeEqPowDvdOrderOf.lean#L8) · [`laxEx`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/PlaceEmb.lean#L189)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
