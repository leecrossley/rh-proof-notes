# Finite-layer class group counts control the localization kernel

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E9%80%90%E5%B1%82%E7%9A%84%E6%89%AD%E6%9B%B2%E7%B1%BB%E7%BE%A4%E8%AE%A1%E6%95%B0%E6%8E%A7%E5%88%B6%E4%B8%80%E9%98%B6%E5%B1%80%E9%83%A8%E5%8C%96%E6%A0%B8.md)

## Statement

Let $L$ be totally imaginary, with a primitive $\ell^c$th root of unity and none of order $\ell^{c+1}$, where $\ell$ is prime, $c\ge1$, and $c\ge2$ for $\ell=2$. Take integers $e\ge1$ and $B\ge0$. Put $L_\nu=L(\mu_{\ell^\nu})$ and let $\gamma_\nu$ act on these roots by exponent $1+\ell^c$. Assume for each $\nu\ge c$ that there are at most $B$ class group homomorphisms
$$
\theta:\operatorname{Cl}(L_\nu)\to\mathbb Z/\ell^\nu\mathbb Z,\qquad
\theta(\gamma_\nu^{-1}P)=(1+\ell^c)^e\theta(P).
$$
Then the length $s(L,\ell,e)$ of the localization kernel for $(\mathbb Q_\ell/\mathbb Z_\ell)(-e)$, unramified outside $\ell$ and trivial locally at $\ell$, is finite and $\ell^{s(L,\ell,e)}\le B$. This is `SSha`, whose input allows all layers satisfying `Lay`; these are the ones used here.

## Detecting a class over the infinite tower

Set $M=(\mathbb Q_\ell/\mathbb Z_\ell)(-e)$, $\alpha=\chi_\ell^{-e}$ and $L_\infty=\bigcup_\nu L_\nu$. On $G_{L_\infty}$ the action is trivial, so a restricted cocycle is an additive homomorphism determined by its class. This restriction is injective on classes. If the restriction vanishes, the cocycle descends to $\operatorname{Gal}(L_\infty/L)\simeq\mathbb Z_\ell$. Let $\gamma$ be its generator with cyclotomic value $1+\ell^c$. Since $e\ge1$, $\alpha(\gamma)-1$ is nonzero and acts surjectively on the divisible module. Subtract a coboundary to make the value at $\gamma$ zero. The cocycle identity and continuity give zero on its dense integer powers and their closure. See also the [tower cokernel formula](../zh/%E5%88%86%E5%9C%86%E5%A1%94%E4%B8%8A%E7%9A%84%E5%90%8C%E8%B0%83%E6%A0%B8%E4%B8%BA%E4%BB%80%E4%B9%88%E5%8F%98%E6%88%90%E4%BD%99%E6%A0%B8%E9%95%BF%E5%BA%A6.md).

## Descending a finite family to a common layer

Choose distinct classes in a finite family with continuous cocycles $z_i$. The cocycles have finite image in the discrete module by compactness. Also choose one coboundary parameter on each decomposition group above $\ell$ for every $z_i$. Take $\nu$ large enough that all these values and parameters are killed by $\ell^\nu$. The action on this layer of coefficients is trivial over $G_{L_\nu}$, so the restrictions are homomorphisms to $M[\ell^\nu]$.

These are unramified. Away from $\ell$ this follows from the original condition. At a chosen place above $\ell$ the coboundary value $(\alpha(h)-1)m$ vanishes for $h\in G_{L_\nu}$ because $m\in M[\ell^\nu]$. For conjugate groups use
$$
z_i(ghg^{-1})=\alpha(g)z_i(h)+(1-\alpha(h))z_i(g).
$$
The last term also vanishes. Class field theory over the totally imaginary field $L_\nu$ gives homomorphisms $\theta_i$ on its class group. Under $\mathbb Z/\ell^\nu\mathbb Z\simeq M[\ell^\nu]$, the displayed conjugation formula with a lift of $\gamma_\nu^{-1}$ gives exactly multiplication by $(1+\ell^c)^e$. The Artin map takes conjugate primes to conjugate elements, so these $\theta_i$ belong to the [twisted class group count](counting-twisted-characters-with-class-groups-and-units.md).

If two $\theta_i$ coincide, then their pullbacks agree over $G_{L_\nu}$, hence over $G_{L_\infty}$. Injectivity there gives equal original classes. Thus any finite family injects into one finite-layer set of size at most $B$. This bounds the whole kernel's size by $B$, and a finite $\mathbb Z_\ell$-module of length $s$ has cardinality $\ell^s$.

## Lean correspondence

- [`sSha`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/RingEquivalences/OrderOfOneAddPrimePowZmodPrimePow.lean#L490) uses `LayEx_holds`, `ClInj_holds`, `good_of`, `card_le` and `ShaAsm_holds` for the finite-layer construction and count.
- [`SSha` and `TopRoot`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/LemmaKOfSteps.lean#L140) state the inputs and output.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
