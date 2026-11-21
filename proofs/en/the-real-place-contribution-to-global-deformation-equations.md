# The real-place contribution to global deformation equations

[Chinese proof](../zh/%E5%85%A8%E5%B1%80%E5%8F%98%E5%BD%A2%E7%9A%84%E6%96%B9%E7%A8%8B%E6%95%B0%E4%B8%BA%E4%BB%80%E4%B9%88%E6%AF%94%E5%8F%98%E9%87%8F%E5%A4%9A%E4%B8%80%E4%B8%AA%E5%AE%9E%E5%A4%84%E8%B4%A1%E7%8C%AE.md)

Let $\ell$ be odd, $k$ a finite field of characteristic $\ell$, and $V$ a finite-dimensional $k$-space with continuous action $\rho$ of $G=G_{\mathbb Q,S}$ for $S$ a finite set of rational primes containing $\ell$. Use absolute decomposition maps $G_v\to G$ for $v\in S$. For $q\in S\setminus\{\ell\}$, let $N_q\triangleleft G_q$ be closed in inertia $I_q$, acting trivially on $V$, with $[I_q:N_q]$ prime to $\ell$. Let $T$ be the continuous cocycles on $G$ zero on $G_\ell$ and all $N_q$ (`H1c`). Let $E$ (`Ob`) be arrays $(u,(b_v))$ of a global two-cocycle and local one-cochains with $\operatorname{res}_v u=db_v$, modulo arrays
$$
(d h,\ \operatorname{res}_\ell h-dy,\ (\operatorname{res}_q h-z_q)_{q\ne\ell}),
$$
with $h$ a global one-cochain, $y\in V$ and $z_q$ a local one-cocycle zero on $N_q$. Assume some $g\in G_{\mathbb Q}$ acts trivially on $V$ and has residual cyclotomic character $-1$. With the usual cohomological finiteness, Euler characteristics and Poitou–Tate duality, both spaces are finite dimensional and
$$
\dim_k E=\dim_k T+\dim V^{\rho(c)=1}
$$
for complex conjugation $c$. [Array definitions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CommutativeAlgebra/FramedTwoCoboundaries.lean) · [`frame_count`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CommutativeAlgebra/FrameCount.lean#L268)

**One- and two-cocycles.** Write $h^i,h_v^i$ for global and local cohomology dimensions. Let $L_q^1$ be the kernel of restriction to $N_q$ in $H^1(G_q,V)$, and $U_1=H^1(G_\ell,V)\oplus\bigoplus_{q\ne\ell}H^1(G_q,V)/L_q^1$. Set $S_1=\ker(H^1(G,V)\to U_1)$. Every representative of a class in $L_q^1$ is zero on $N_q$ because the action there is trivial. A representative for $S_1$ can be made zero on $G_\ell$ by subtracting a global coboundary, retaining the other conditions. The kernel of $T\to S_1$ is the coboundaries of vectors fixed by $G_\ell$, modulo global fixed vectors. Thus $\dim T=h_\ell^0-h^0+\dim S_1$.

Let $\operatorname{res}_2$ be the restriction from global $H^2$ to the product of all local $H^2$. Sending an array to $[u]$ maps onto $\ker\operatorname{res}_2$ by the definition of local primitives. For an array with $u=dh$, subtract the $h$-relation to arrange $u=0$. The remaining local cocycles modulo the local relations give $U_1$, further modulo restrictions of global cocycles, since a relation preserving $u=0$ has $dh=0$. Thus
$$
0\to U_1/\operatorname{im}\operatorname{res}_1\to E\to\ker\operatorname{res}_2\to0.
$$
This proves finiteness and yields $\dim E=h_\ell^1+\sum_{q\ne\ell}(h_q^1-\dim L_q^1)-h^1+\dim S_1+h^2-\operatorname{rank}\operatorname{res}_2$.

**Euler calculation.** The chosen $g$ acts by $-1$ on $V^*(1)$, so that dual has zero global invariants. The last part of Poitou–Tate gives $\operatorname{res}_2$ surjective; the real place has zero positive cohomology at odd $\ell$. Since $I_q/N_q$ has invertible order, averaging makes its higher cohomology zero, and inflation identifies $L_q^1$ with $H^1(\widehat{\mathbb Z},V^{I_q})$. This is the cokernel of $\mathrm{Frob}-1$, of the same dimension $h_q^0$ as its kernel. A Frobenius value can be realized at a finite cyclic quotient by taking a period killing both the action and the cumulative cyclic sum. Now $h_q^0-h_q^1+h_q^2=0$ away from $\ell$ cancels these contributions. At $\ell$ the characteristic is $-\dim V$, whereas globally $h^0-h^1+h^2=-\dim V+\dim V^{c=1}$. Substitution gives $\dim E=h_\ell^0-h^0+\dim S_1+\dim V^{c=1}$, proving the claim. [`box_count`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeGroups/BoxCount.lean#L51)

**Rank-three specialization.** Complex conjugation swaps the two blocks of the rank-six realization, whose Lie algebra has blocks $X,-JX^{\mathsf T}J$. Its fixed matrices satisfy $X=-JX^{\mathsf T}J$, hence have form
$$
\begin{pmatrix}x&y&0\\ z&0&-y\\0&-z&-x\end{pmatrix}.
$$
The weights are $0,1,-1$ respectively, giving excess $\mathbf1_{\{|j|\le1\}}$ in each degree. To obtain the required $g$, `GD` supplies $h$ fixing $\mu_\ell$ and killing the character away from $\ell$ with $\eta(h)=-1$. It also kills the $\ell$-component, because the kernel of unit reduction from an $\ell$-power to $\ell$ is an $\ell$-group and the character has prime-to-$\ell$ order. Hence $\bar\Psi(h)=1$. Take $g=ch$: both sign and matrix are residual identity, while $\bar\varepsilon_\ell(g)=-1$, so every weight of the adjoint action is trivial there. [Fixed space](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeGroups/FinrankKerAdRepComplexConjSubOneEqBoxDef.lean#L94) · [Duality element](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeGroups/ExistsGaloisCyclotomicNegOneTrivialOnEtaPsi.lean#L43)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
