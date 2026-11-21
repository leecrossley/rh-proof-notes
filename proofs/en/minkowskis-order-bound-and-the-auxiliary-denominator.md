# Minkowski's order bound and the auxiliary denominator

[Chinese proof](../zh/%E6%9C%89%E9%99%90%E7%9F%A9%E9%98%B5%E7%BE%A4%E7%9A%84%E9%98%B6%E6%80%8E%E6%A0%B7%E6%8E%A7%E5%88%B6%E8%BE%85%E5%8A%A9%E5%88%86%E6%AF%8D.md)

## Statement

For $n\ge0$ integral and $p$ prime define
$$
m_p(n)=\sum_{i\ge0}\left\lfloor\frac{n}{p^i(p-1)}\right\rfloor,\qquad
M(n)=\prod_{p\le n+1}p^{m_p(n)}.
$$
Then every finite subgroup $G\subset\mathrm{GL}_n(\mathbb Q)$ has $|G|\mid M(n)$, and $M(n)\mid(2n)!$. The project denotes $M(n)$ by `minkM` and the assertion for all finite groups by `MinkDiv`. The application bounds the prime factors and logarithm of the auxiliary denominator $D_\Gamma$.

## The allowed traces of a $p$-group

Let $P\subset\mathrm{GL}_n(\mathbb Z)$ be a finite $p$-group. Put $m=\lfloor n/(p-1)\rfloor$. Each $g\in P$ is annihilated by some $X^{p^a}-1$ and is diagonalizable in characteristic zero. Its rational characteristic polynomial contains each irreducible cyclotomic factor $\Phi_{p^j}$ with some multiplicity $b_j$, with $b_0$ for the root $1$. The primitive $p$th roots sum to $-1$. For $j\ge2$ the roots of $\Phi_{p^j}$ sum to zero, since $\Phi_{p^j}(X)=\sum_{i=0}^{p-1}X^{i p^{j-1}}$ has vanishing next-to-leading coefficient. Therefore $\operatorname{tr}g=b_0-b_1$ and
$$
n-\operatorname{tr}g=p b_1+\sum_{j\ge2}p^{j-1}(p-1)b_j=p y
$$
for an integer $y\ge0$. Comparing the terms in $(p-1)y$ to the degrees in the characteristic polynomial shows $(p-1)y\le n$, hence $y\le m$. If $y=0$ the only eigenvalue is $1$ and $g$ is the identity by diagonalizability. Thus the nonidentity traces lie in $n-p,\ldots,n-mp$. [Cyclotomic trace calculation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/MinkowskiBound/CharpolyDvdOfPowEqOne.lean)

## Isolate the identity with a polynomial in the trace

For $k\ge0$, the average $|P|^{-1}\sum_{g\in P}g^{\otimes k}$ on $(\mathbb Q^n)^{\otimes k}$ is idempotent, including the trivial representation at $k=0$. Multiplying by a group element permutes the terms. Its trace is its image dimension, so $|P|\mid\sum_{g\in P}(\operatorname{tr}g)^k$ by multiplicativity of trace under tensor products. Integer linear combinations give $|P|\mid\sum_g F(\operatorname{tr}g)$ for any $F\in\mathbb Z[X]$. Take $F(X)=\prod_{j=1}^m(X-(n-pj))$. All nonidentity terms vanish and $F(n)=p^m m!$. By Legendre's formula the $p$-valuation of this is $m+\sum_{i\ge1}\lfloor m/p^i\rfloor=m_p(n)$. Apply this to each Sylow subgroup to obtain $|G|\mid M(n)$ for finite $G$ over $\mathbb Z$. [Trace power sums](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/MinkowskiBound/PowerSum.lean) · [The isolating polynomial](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/MinkowskiBound/MinkowskiBoundOfSteps.lean) · [Sylow assembly](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/MinkowskiBound/Assemble.lean)

For finite $G\subset\mathrm{GL}_n(\mathbb Q)$, the sum $\sum_{g\in G}g\mathbb Z^n$ is a finitely generated torsion-free rank-$n$ $\mathbb Z$-module and is invariant under $G$. In its integral basis we get the integral case. Finally $\lfloor n/(p^i(p-1))\rfloor\le\lfloor2n/p^{i+1}\rfloor$, since $p\le2(p-1)$. Summing gives $m_p(n)\le v_p((2n)!)$ and hence $M(n)\mid(2n)!$. For $n\ge1$ this implies $\log M(n)\le2n\log(2n)$, and for $n=0$ both numbers equal $1$. [Invariant lattice](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/MinkowskiTorsionFree/Lattice.lean) · [Factorial comparison](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/FlagUnipotentLattices/MinkowskiFactorialBounds/MinkowskiNumberDvdFactorial.lean)

## The family denominator

For each row $i$ and word $u$ at scale $x$, put $A=fN(m)\ge2$, where $f$ is the even field-degree parameter and $N(m)$ the dimension parameter. Assume that beyond a uniform $x_0$ every such $D_\Gamma$ divides $M(2A)$, the condition `DGamDvdF`. For the positive denominators of the project the prime factors are then at most $2A+1$, and
$$
\log D_\Gamma\le\log M(2A)\le4A\log(4A)\le12A\log A.
$$
The last inequality follows from $\log 2\le\log A$. This gives `DGamSize` with constant $12$ in `designExists_of_choices`. The divisibility of the individual denominators is the input at this step. [Design bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/DesignExistsOfChoices.lean) · [Call in the main route](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/LinkEx.lean) · [Selection of the common family](joint-family-selection.md)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
