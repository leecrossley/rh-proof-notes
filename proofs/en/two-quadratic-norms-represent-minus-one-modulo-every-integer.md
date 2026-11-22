# Two quadratic norms represent minus one modulo every integer

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $q,d$ be distinct rational primes with $q\equiv3\pmod8$. Let $E_0$ be a CM field containing $\xi,\eta$ with $\xi^2=-q$, $\eta^2=-d$, and write $z\mapsto\bar z$ for complex conjugation. Then for every positive integer $m$ there are $\ell\in\mathcal O_{E_0}$, $s\in\mathbb Z$ such that
$$
\bar\ell\ell=-1+ms.
\tag{1}
$$
In the project $d\equiv7\pmod{16}$, which ensures $d\ne q$. This is `NegOneNorm`, used to reverse the finite theta phase.

### A solution at each odd prime

Suppose $p$ is odd and $p\nmid c$. Over $\mathbb F_p$ the two sets
$$
\{x^2:x\in\mathbb F_p\},
\quad
\{-1-cy^2:y\in\mathbb F_p\}
$$
each have size $(p+1)/2$, since each nonzero square has two square roots and multiplication by $-c$ is invertible. They therefore intersect, giving $x^2+cy^2=-1$ modulo $p$. At least one of $x,y$ is nonzero. In that variable the partial derivative is $2x$ or $2cy$, a unit modulo $p$. Keep the other variable fixed and lift the equation to every $p^k$. At each step $j$, replacing the lifting variable $t_j$ by $t_j+p^j b$ changes the left side modulo $p^{j+1}$ by $p^j b$ times that unit derivative. Thus a choice of $b\bmod p$ removes the next error. This is the simple-root lifting used in the odd-prime proof.

### The solution at $2$

Take $c=q\equiv3\bmod 8$ and set $x=2$. At $y_3=1$ the expression $q y_3^2+5$ vanishes modulo $8$. Suppose an odd $y_j$ has been chosen with $q y_j^2+5\equiv0\bmod 2^j$, for $j\ge3$. On replacing $y_j$ by $y_j+b2^{j-1}$ with $b=0$ or $1$, this expression changes by
$$
b q y_j 2^j + q b^2 2^{2j-2}.
$$
The second term vanishes modulo $2^{j+1}$, while the first toggles the residue of the error divided by $2^j$ modulo $2$, since $q y_j$ is odd. Choose $b$ removing it. This gives the congruence $x^2+q y^2\equiv-1\bmod 2^k$ for every $k$. The same argument gives a solution in $\mathbb Z_2$ by taking the limit, since the corrections are divisible by increasing powers of $2$. Lean uses the Hensel inequality that $q+5$ has valuation at least three, while the derivative $2q$ has valuation one.

### Putting the two norm forms together

At $p=q$, use the odd-prime argument with $c=d$, which is nonzero modulo $q$, and set the $q$-form to $1$. At every odd $p\ne q$, use $c=q$ and set the $d$-form to $1$. At $2$ use the preceding lift for $q$. For every prime power dividing $m$ this gives four residues $a,b,c,e$ with
$$
(a^2+q b^2)(c^2+d e^2)\equiv-1
$$
modulo that prime power. Combining the four residue lists separately by the integer Chinese remainder theorem gives integers $a,b,c,e$ satisfying this congruence modulo $m$.

Both $\xi,\eta$ are integral because they satisfy monic quadratics over $\mathbb Z$, and $\bar\xi=-\xi,\bar\eta=-\eta$ because their complex squares are strictly negative. Set $\ell=(a+b\xi)(c+e\eta)$. Then $\ell$ is integral and $\bar\ell\ell=(a^2+q b^2)(c^2+d e^2)$. This is (1), with the integer $s=((a^2+q b^2)(c^2+d e^2)+1)/m$.

### Lean correspondence

- [`hensel_quad`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/IntegralSquareRoots/HenselQuad.lean#L7) applies the Hensel inequality. [`rep_odd`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/IntegralSquareRoots/HenselQuad.lean#L31) gives the odd-prime lift and [`rep_two`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/IntegralSquareRoots/HenselQuad.lean#L73) handles $2$.
- [`rep_pp`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/IntegralSquareRoots/HenselQuad.lean#L92) chooses the usable form at each prime, and [`rep_all` and `rep_int`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/IntegralSquareRoots/HenselQuad.lean#L126) assemble and lift the residues. [`negOneNorm`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/IntegralSquareRoots/SecondConstantHolds.lean#L27) realizes the resulting product as an integral CM norm for the host primes.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
