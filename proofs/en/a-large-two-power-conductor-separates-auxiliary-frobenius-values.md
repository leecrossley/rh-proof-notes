# A large two-power conductor separates auxiliary Frobenius values

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E5%A4%A7%E7%9A%84%E4%BA%8C%E8%BF%9B%E5%AF%BC%E5%AD%90%E8%83%BD%E5%88%86%E5%BC%80%E8%BE%85%E5%8A%A9Frobenius%E5%80%BC.md)

Let $O$ be an integral domain, $n,a\ge0$, and $\xi$ a primitive $O$-valued Dirichlet character modulo $2^n$. If $v>1$ is odd and $u>0$ odd, then
$$
\xi(v)^{2^a u}=1\quad\Longrightarrow\quad 2^n<v^2 2^a.
$$
[Lean theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/TwoPowLtSqMulOfPrimitiveCharPowEqOne.lean#L61)

**Proof.** For $n\le1$ the inequality is automatic. Otherwise reduction from units modulo $2^n$ to modulo $2^{n-1}$ has kernel $\{1,1+2^{n-1}\}$, and primitivity requires $\xi(1+2^{n-1})\ne1$. Put $s=v_2(v^2-1)\ge3$. Squaring $z\equiv1\bmod4$ with $z>1$ increases $v_2(z-1)$ by one because $v_2(z+1)=1$. An odd power preserves it by the geometric sum. Thus $(v^2)^{2^a u}-1$ has valuation $s+a$. If $s+a<n$, square the base $(v^2)^{2^a u}$ another $n-1-s-a$ times, obtaining $1+2^{n-1}\bmod2^n$. Its character value is $1$ by hypothesis, a contradiction. Therefore $2^n\le2^{s+a}<v^2 2^a$.

**Primitive odd choices.** For $n\ge3$, if $O$ contains a primitive $2^{n-2}$-th root $\zeta$, the same valuation formula gives $5$ order $2^{n-2}$ modulo $2^n$. Thus its powers give all units congruent to $1\bmod4$; every unit is uniquely $(-1)^\epsilon5^j$. Set its character value to $(-1)^\epsilon\zeta^j$. At $5^{2^{n-3}}\equiv1+2^{n-1}$ it is nontrivial, so is primitive, and it is odd. The root assumption excludes characteristic two. A character of two-component conductor $2^c$, $c<n$, is trivial on the last reduction kernel, so multiplying by it preserves primitivity of $\xi$ while allowing its sign to change. The Lean twist lemma also permits a character initially at any modulus $N$, with the claimed values on integers prime to $2N$. These statements supply the [rank-four base choices](constructing-rank-four-base-data-for-cases-ii-and-iii.md). [Primitive odd character](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/ExistsPrimitiveOddDirichletCharacterTwoPow.lean#L16) · [Lower conductor twist](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/ExistsPrimitiveTwoPowTwistMul.lean#L3)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
