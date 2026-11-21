# The cyclic slope cycles have a relation

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E5%BE%AA%E7%8E%AF%E7%BE%A4%E7%9A%84%E8%BF%99%E4%BA%9B%E6%96%9C%E7%8E%87%E5%91%A8%E6%9C%9F%E5%BF%85%E6%9C%89%E5%85%B3%E7%B3%BB.md)

## Statement

Let $\ell$ be prime, $\nu,e\ge0$, $q=\ell^\nu$, $A=\mathbb Z/q\mathbb Z$, $E=e+1$, and $C_q=\langle c\rangle$ cyclic of order $q$. In the bar complex put
$$
z=\sum_{j_1,\ldots,j_E\bmod q}[c^{j_1}|c|\cdots|c^{j_E}|c]\in C_{2E}(C_q,A).
$$
For $0\le t\le2e+3$ define $d_t(u)=(u,u^t)$ into $C_q^2$. Then $z$ is a cycle and there are $n_t\in A$ with some $n_{t_0}$ a unit such that $\sum_t n_t(d_t)_*z$ is a boundary. These are `SZc` and `SRel` in the [integral cycle construction](../zh/%E6%80%8E%E6%A0%B7%E6%8A%8A%E6%89%AD%E6%9B%B2%E4%B8%BB%E5%9B%A0%E5%AD%90%E5%8F%98%E6%88%90%E4%B8%80%E4%B8%AA%E5%85%A8%E5%B1%80%E5%91%A8%E6%9C%9F.md).

## The cycle identity

The first bar boundary term deletes $c^{j_1}$, giving a factor $q=0$ in $A$. For $i<E$, merging the two entries in the $i$th pair gives a negative term, and merging its $c$ with the next $c^{j_{i+1}}$ gives a positive one. Their sums agree after translating $j_i$ or $j_{i+1}$ by one. Finally merging the last pair and deleting the final $c$ cancel after translating $j_E$. Thus the boundary is zero.

## Counting generators

For a surjection $G\to Q=C_q$ with kernel $K$, let $W=A^Q$ with translation action through $Q$. There is an exact sequence
$$
0\to A\to W\xrightarrow{\Delta}W\xrightarrow{\Sigma} A\to0
$$
with constant embedding, $\Delta f(j)=f(j+1)-f(j)$, and $\Sigma$ summation. The kernel of $\Delta$ is constant, and a vector of sum zero is a difference by partial sums that close around the cycle. Summation is onto by single-coordinate functions. All maps are equivariant. Let $U=\operatorname{im}\Delta$. For $B=A,W,U$ write $g_B(i)$ for the number of generators needed for $H_i(G,B)$. The two short exact sequences give
$$
g_A(i)\le g_W(i)+g_U(i-1),\qquad
g_U(i-1)\le g_W(i-1)+g_A(i-2)
$$
for $i\ge2$. At $i=1$ use right exactness in degree zero to omit the final term in the second bound. Submodules of $r$-generated $A$-modules need at most $r$ generators by lifting to subgroups of $\mathbb Z^r$. This justifies estimating the intervening images. By Shapiro, $H_i(G,W)=H_i(K,A)$.

For $G=Q$ with the identity map, the kernel is trivial. Thus $g_A(0)\le1$, $g_A(1)\le1$ and $g_A(i)\le g_A(i-2)$ for $i\ge2$. For $G=Q^2$ and the first projection, $K\simeq Q$, so $g_A(i)\le2+g_A(i-2)$. Therefore $H_{2E}(C_q^2,A)$ needs at most $2E+1=2e+3$ generators.

## A unit coefficient

Lift the $2e+4$ homology classes to $\mathbb Z^{2e+3}$ using a surjection from a generating set. Rational dependence, followed by clearing denominators, gives a nonzero integer relation there. Divide coefficients by their gcd, which preserves the relation since the lattice is torsion-free. At least one coefficient is prime to $\ell$ and is hence a unit modulo $q$. Projecting gives a zero homology class, as required. At $q=1$ all chains are zero and the unit condition uses the zero-ring convention.

## Lean correspondence

- [`zc` and `dt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/HasVal.lean#L39), [`SZc` and `SRel`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/LemmaKOfSteps.lean#L38) give the chain and statement.
- [`step`, `gen_cyc` and `gen_two`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/EtaleCohomology/CyclotomicDiscriminants/SRelTPf.lean#L188) give dimension shifting. [`Gen.rel`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/EtaleCohomology/CyclotomicDiscriminants/SRelTPf.lean#L50) and [`SRel_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/EtaleCohomology/CyclotomicDiscriminants/SRelTPf.lean#L304) produce the relation, used through [the final interface](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/EtaleCohomology/CyclotomicDiscriminants/FinSRel.lean#L6).

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
