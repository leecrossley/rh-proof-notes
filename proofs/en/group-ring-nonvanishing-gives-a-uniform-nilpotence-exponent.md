# Group-ring nonvanishing gives a uniform nilpotence exponent

[Chinese proof](../zh/%E7%BE%A4%E7%8E%AF%E9%9D%9E%E6%B6%88%E5%A4%B1%E6%80%8E%E6%A0%B7%E7%BB%99%E5%87%BA%E7%BB%9F%E4%B8%80%E7%9A%84%E5%B9%82%E9%9B%B6%E6%8C%87%E6%95%B0.md)

## Statement

Let $\ell$ be prime, $(f,\ell)=1$, and $c>1$ odd prime to $f\ell$. Write $e=2$ at two and $e=1$ otherwise. There exist $N,n_0$ with $n_0\ge2$ such that for every $n\ge n_0$, $G=(\mathbb Z/f\ell^n\mathbb Z)^\times$ contains $\gamma=1+f\ell^e$ with $[G:\langle\gamma\rangle]=\varphi(f\ell^e)$ and
$$
([\gamma]-1)^N\in(\theta_H,1+[-1],\ell)
\quad\text{in }\mathbb Z[G],
$$
where $\theta_H$ is the [half Stickelberger element](sinnott-finite-differences-imply-nonvanishing.md). This is `memZ`. For a character $\chi$ and homomorphism $\pi$, write $\operatorname{tw}(\chi,\pi)$ for the group-ring map $[g]\mapsto\chi(g)[\pi(g)]$.

## The cyclic part

In characteristic $\ell$, let $G,Q$ be abelian, $p:G\to G$ and $\pi:G\to Q$, with $\gamma^{\ell^b}=1$, $p(G)\subseteq\langle\gamma\rangle$, $\pi p=\pi$ and $\pi(\gamma)^{\ell^K}=1$. Put $T=[\gamma]-1$. Then $T^{\ell^b}=0$. For $\theta\in k[G]$ with $\operatorname{tw}(\chi,\pi)\theta\ne0$, the element $H=\operatorname{tw}(\chi,p)\theta$ is a polynomial in $T$. Write $H=T^j u(T)$ with $u(0)\ne0$, hence $u(T)$ a unit by nilpotence. Under the map induced by $\pi$, $H$ stays nonzero but $T^{\ell^K}$ vanishes. Thus $j<\ell^K$ and $H$ divides $T^{\ell^K}$.

## The complementary group factors

Now let $k$ be algebraically closed and $G$ finite, with $J\in G$, $p(J)=1$, and $(g p(g)^{-1})^{\ell^a m}=1$ for fixed $a,m$ with $(m,\ell)=1$. Suppose all characters with $\chi(J)=-1$ satisfy the nonvanishing above. In $A=k[G]/(\theta,1+[J])$ write $r$ for reduction, and let $d(g)=(g p(g)^{-1})^{\ell^a}$ with image $D$. This finite abelian image has exponent dividing $m$ and order prime to $\ell$. For each character $\psi$ of $D$, let $e_\psi=|D|^{-1}\sum_{d\in D}\psi(d)^{-1}r([d])$. Then $r([d])e_\psi=\psi(d)e_\psi$ by reindexing, and $\sum_\psi e_\psi=1$ by character orthogonality over the algebraically closed field.

For $e_\psi\ne0$, take the character $\chi$ with $\chi(g)^{\ell^a}=\psi(d(g))$ using inverse Frobenius. Since $p(J)=1$ and $r([J])=-1$, $\chi(J)^{\ell^a}=(-1)^{\ell^a}$ by evaluation on $e_\psi$, giving $\chi(J)=-1$. Also $r([g])^{\ell^a}e_\psi=\chi(g)^{\ell^a}r([p(g)])^{\ell^a}e_\psi$. Applied to the terms of $\theta$ by Frobenius additivity, this gives $r(H)^{\ell^a}e_\psi=r(\theta)^{\ell^a}e_\psi=0$. Raise the divisibility from the previous section to the same power and multiply by $e_\psi$. Thus $r(T)^{\ell^{K+a}}e_\psi=0$. Summing gives $T^{\ell^{K+a}}\in(\theta,1+[J])$.

## Cyclotomic application and integer coefficients

By the Chinese remainder theorem $G$ is the product of the units modulo $f$, the reduction of $W$ from the nonvanishing proof, and the principal units modulo $\ell^n$ congruent to one mod $\ell^e$. For odd $\ell$, $W$ lifts the nonzero residues uniquely by simple-root lifting for $X^{\ell-1}-1$, and at two $\{\pm1\}$ gives the units modulo four. The binomial valuation $v_\ell((1+f\ell^e)^{\ell^j}-1)=e+j$ follows because each $\ell$th power increases the valuation exactly one. Hence $\gamma$ generates the principal factor and is one modulo $f$. Let $p$ project to that factor and $J=-1$. The complementary factor has size $\varphi(f\ell^e)=\ell^a m$, so the preceding exponent assumption holds.

Choose $n_0$ from nonvanishing and use its quotient map $\pi_{n_0}$, which ignores the other factors and satisfies $\pi p=\pi$. The order of $\pi(\gamma)$ divides $\ell^{n_0}$. With $k=\overline{\mathbb F_\ell}$, $\theta$ the reduction of $\theta_H$, and $K=n_0$, the result gives exponent $N=\ell^{n_0+a}$. To descend the relation's coefficients, choose an $\mathbb F_\ell$-linear functional $k\to\mathbb F_\ell$ sending one to one. Acting coefficientwise commutes with multiplication by the two generators defined over $\mathbb F_\ell$, so both multiplying coefficients can be taken over $\mathbb F_\ell$. Lift them to $\mathbb Z[G]$ and the remaining difference is divisible by $\ell$. This proves the claimed ideal membership uniformly.

## Lean correspondence

- [`phiDvd`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/PhiDvd.lean#L54), [`sepChar`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/SepChar.lean#L5) and [`algK`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/AlgK.lean#L8) give the divisibility and character reductions.
- [`gamGen`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/GamGen.lean#L65), [`deltaBij`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/DeltaBij.lean#L40) and [`struct`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/Struct.lean#L27) give the group decomposition. [`descZ`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/DescZRetr.lean#L43) and [`memZ`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/FerreroWashingtonIndex/ToKOf.lean#L13) descend and assemble.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
