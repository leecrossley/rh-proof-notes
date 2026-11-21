# Vanishing for the trivial character in case Z

[Chinese proof](../zh/%E5%B9%B3%E5%87%A1%E7%89%B9%E5%BE%81%E7%9A%84Z%E7%B1%BB%E4%B8%8A%E5%90%8C%E8%B0%83%E4%B8%BA%E4%BB%80%E4%B9%88%E6%B6%88%E5%A4%B1.md)

## Statement

Let $\ell\ge5$ be prime, $O$ the integers of a finite extension of $\mathbb Q_\ell$, and $F$ its fraction field. Suppose $e\ge2$ is even and $\ell-1\mid2e$. Put $A=(F/O)(\varepsilon_\ell^{-e})$, with Galois action by multiplication by $\varepsilon_\ell(g)^{-e}$. Then
$$
\ker\left(H^1(G_{\mathbb Q},A)\longrightarrow
\prod_{v\ \mathrm{finite}} H^1(I_v,A)\times H^1(D_\ell,A)\right)=0.
$$
Choices of decomposition and inertia groups may be conjugated without changing the vanishing condition. This makes the length in [host case Z](choosing-among-seven-positive-sign-length-estimates.md) equal to zero.

## Reducing to classes killed by $\ell$

A continuous cocycle has finite image in the discrete module $A$ by compactness. Its class is therefore killed by a power of $\ell$. If the kernel is nonzero, it has a nonzero class killed by $\ell$. For its representative $z$ there is $b\in A$ with $\ell z(g)=gb-b$. Write $b=\ell b'$ by divisibility and subtract the coboundary of $b'$. Then $z$ takes values in $A[\ell]$. On $I_p$ for $p\ne\ell$ the cyclotomic action is trivial, so the local coboundary condition means $z|_{I_p}=0$.

## When $\ell-1\mid e$

Here $A[\ell]$ has trivial action. Thus $z$ is a continuous additive homomorphism giving a finite abelian quotient of exponent dividing $\ell$, unramified outside $\ell$. Kronecker–Weber and the conductor condition put this quotient in some $\mathbb Q(\mu_{\ell^j})$. The unit group modulo $\ell^j$ is cyclic of order $(\ell-1)\ell^{j-1}$, and a homomorphism to a group of exponent dividing $\ell$ kills all its $\ell$th powers. In particular the homomorphism factors through level $\ell^2$, and $z$ vanishes on $G_{\mathbb Q(\mu_{\ell^\infty})}$.

Now view $z$ as an $A$-valued cocycle on $\Gamma=\operatorname{Gal}(\mathbb Q(\mu_{\ell^\infty})/\mathbb Q)\simeq\mathbb Z_\ell^\times$. For a topological generator $\sigma$, the scalar $\varepsilon_\ell(\sigma)^{-e}-1$ is nonzero. Multiplication by this scalar on $A$ is surjective. Subtract a coboundary so that $z(\sigma)=0$. The cocycle identity gives zero at all powers of $\sigma$, and continuity gives zero on $\Gamma$.

## When $\ell-1\nmid e$

Then $e\equiv(\ell-1)/2\pmod{\ell-1}$, and evenness of $e$ gives $\ell\equiv1\pmod4$. The residual character is the Legendre character of conductor $\ell$, with fixed field $L=\mathbb Q(\sqrt{\ell})$ of discriminant $\ell$. For instance, the quadratic Gauss sum has square $\ell$ and transforms by this character.

In a chosen $I_\ell$, pick $\delta$ with $\varepsilon_\ell(\delta)^{-e}-1$ a unit, using surjectivity of the local cyclotomic character on inertia. On $D_\ell$, $z$ is the coboundary of some $b_\ell\in A$. Evaluating at $\delta$ gives $b_\ell\in A[\ell]$ because $z(\delta)$ is killed by $\ell$ and the scalar is a unit. Subtract this coboundary to set $z(\delta)=0$, keeping its values in $A[\ell]$.

The restriction to $G_L$ is a homomorphism. At each place over $\ell$ the same unit argument makes its local parameter lie in $A[\ell]$, so the restricted homomorphism vanishes on the corresponding decomposition group in $G_L$. Elsewhere it is unramified by the inertia conditions. Complex conjugation has order two and maps trivially into this $\ell$-torsion group. Class field theory therefore makes the homomorphism factor through $\mathrm{Cl}(L)$.

Minkowski gives an integral ideal of norm at most $x=\sqrt\ell$ in each class. At most $d(n)$ ideals have norm $n$, since in a quadratic field a prime-power norm $p^a$ allows at most $a+1$ allocations between primes. Hence
$$
h_L\le\sum_{n\le x}d(n)\le x(1+\log x)<x^2=\ell.
$$
The middle inequality sums $n=ab$ by $a$ and bounds the harmonic sum by an integral. Thus $z|_{G_L}=0$. Since $\delta$ represents the other coset and $z(\delta)=0$, the cocycle identity gives $z=0$.

For case Z, the odd prime outside $B_\chi$ is at least $5$ because $3\in B_\chi$. The parity condition for the trivial character gives $e$ even, and $e>0$ gives $e\ge2$. The group $V_{\ell,e}(1)$ imposes additional local conditions and lies in the zero kernel just proved.

## Lean correspondence

- [`zOne`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/TorsClass.lean#L97) uses cyclotomic control and [`kwl`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/KwlOnto.lean#L69) for conductor at most $\ell^2$.
- [`zQuad`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/ZqField.lean#L228) normalizes at $\delta$ and uses [`hQuad`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/HQuad.lean#L10) for the class number.
- [`propZ`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/PropZ.lean#L11) combines the cases. [`countZ`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/CountZ.lean#L5) applies the result.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
