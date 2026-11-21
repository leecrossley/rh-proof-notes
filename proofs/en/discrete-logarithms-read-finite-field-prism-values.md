# Discrete logarithms read finite-field prism values

[Chinese proof](../zh/%E6%9C%89%E9%99%90%E5%9F%9F%E7%9A%84%E7%A6%BB%E6%95%A3%E5%AF%B9%E6%95%B0%E6%80%8E%E6%A0%B7%E8%AF%BB%E5%87%BA%E6%A3%B1%E6%9F%B1%E5%8F%96%E5%80%BC.md)

## Statement

Let $K$ be finite, $q\ge1$, $\zeta\in K^\times$ primitive of order $q$, $A=\mathbb Z/q\mathbb Z$, and $v:K^\times\to(A,+)$ a homomorphism. With $E=e+1$ for $e\ge0$, let
$$
z=\sum_{j_1,\ldots,j_E\bmod q}[c^{j_1}|c|\cdots|c^{j_E}|c]
$$
in the bar complex of $C_q=\langle c\rangle$. For $\chi_x(c)=\zeta^x$, $x\ge0$, some $A$-linear $t:C_{2E+1}(K^\times,A)\to A$ kills boundaries and satisfies
$$
t(\mathcal P_g((\chi_x)_*z))=x^Ev(g),\qquad g\in K^\times .
$$
The [conjugation prism](combining-conjugation-prisms-inside-a-subgroup.md) is used here in an abelian group. This is `SCoc`.

## Proof

Write $n=|K^\times|=qr$, choose a generator $a$, and write $\zeta=a^s$. Then $\gcd(n,s)=r$, so choose integer $B$ with $Bs\equiv r\bmod n$. For each $u=a^j$ choose an integer representative $j$ and set $\lambda(u)=Bj$. Thus $\lambda$ adds modulo $n$, and $\lambda(\zeta^x)\equiv rx\bmod n$. Set
$$
U(u,w)=(\lambda(u)+\lambda(w)-\lambda(uw))/n.
$$
It is integer and symmetric, with zero cochain differential by canceling its four expanded terms. Its reduction $\bar U$ mod $q$ is a two-cocycle. Set $t=\bar U^{\smile E}\smile v$, which kills boundaries by the cup-product differential. Its value on a tuple of length $2E+1$ is $\prod_{j=1}^E\bar U(g_{2j-1},g_{2j})\,v(g_{2E+1})$.

In the abelian group the prism inserts $g$ at all positions with alternating signs. For each pair, the two insertions before and after its first member cancel because $\bar U$ is symmetric. Insertion at the end survives with value $\prod_{j=1}^E\bar U(g_{2j-1},g_{2j})v(g)$. With $h=\zeta^x$, applying this to the cycle gives $(\sum_{j\bmod q}\bar U(h^j,h))^Ev(g)$. The integer sum satisfies
$$
n\sum_{j\bmod q}U(h^j,h)
=\sum_j\lambda(h^j)+q\lambda(h)-\sum_j\lambda(h^{j+1})
=q\lambda(h)
$$
since $h^q=1$. Thus this sum is $\lambda(h)/r$, which reduces to $x$ modulo $q$. This proves the value formula. The $q=1$ case has zero coefficients.

## Lean correspondence

- [`SCoc`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/LemmaKOfSteps.lean#L50) and [`zc`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/HasVal.lean#L39) give the functional and cycle.
- [`ex_log`, `F_coc`, `F_ins` and `sCoc`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/FProd.lean) carry out the discrete logarithm, cup product, and insertion sum. [`sThetaOf`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/SThetaOf.lean) passes to matrices.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
