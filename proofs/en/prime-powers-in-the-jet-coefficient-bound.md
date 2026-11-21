# Prime powers in the jet coefficient bound

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

On a Frobenius orbit of even length, the local proof has to control coefficients of a formal exponential. The two parities are the two kinds of orbit slots. The difficult monomials use one variable of each kind, each to a power of the local prime. This note derives that restriction and explains why a shift by $i$ costs $p^i$ in the degree problem.

## Statement of the local coefficient estimate

The construction of the series that satisfies the following hypotheses is given in [Why the averaged biextension meets the jet hypotheses](why-the-averaged-biextension-meets-the-jet-hypotheses.md).

Let $p$ be an odd prime and $d\ge2$ even. Work over a characteristic-zero nonarchimedean field $K$ with valuation $v$ normalized by $v(p)=1$, and a subfield $K_0$ whose nonzero elements have integral valuation. Assume $K$ has a root of unity $\zeta$ of order $p^d-1$. Let $S=\mathbb Z/d\mathbb Z$ and write its elements using representatives $0,\ldots,d-1$. Put
$$
\rho=\frac1{p^2-1},\qquad c=\frac1{p-1},\qquad \gamma=c-\rho=\frac p{p^2-1}.
$$
For a monomial $X^n$ and real weights $r=(r_i)$, the weighted valuation of its coefficient $b_n$ is $v(b_n)+\sum_i n_i r_i$, with $v(0)=+\infty$.

Take a formal series $b$ in $X_s$ with coefficients in $K_0$. Assume it is fixed by $X_s\mapsto\zeta^{(-1)^s p^s}X_s$. Each nonzero monomial has positive degree on both parities, with pair of degrees different from $(1,1)$. For either parity, duplicate its variables as $X_s,Y_s$. Let $\Delta b$ be $b$ at the sums $X_s+Y_s$ on that parity, minus $b$ at $X_s$ there and minus $b$ at $Y_s$ there. In the other parity use $X_s$ throughout. For both such differences assume that substituting the logarithms
$$
\mathcal L_s(X)=\sum_{e\ge0}\frac{X_{s-2e}^{p^{2e}}}{p^e}
$$
in each copy into $\exp(\Delta b)$ gives integral coefficients and constant term one. These are the assumptions `BHyp` together with the integrality of the value group of $K_0$.

**Claim.** Every coefficient $b_n$ has $v(b_n)+\rho|n|\ge c-1$. The stronger $v(b_n)+\rho|n|\ge c$ holds unless the monomial is $X_s^{p^\alpha}X_{s'}^{p^\beta}$ with opposite parities, $\alpha+\beta>0$, and $s+\alpha=s'+\beta$ in $S$. This is `LemmaS` in normalized valuation notation. [Hypotheses and Lemma S](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GaussJetBounds/Statement.lean#L85) · [Assembly of Lemma S](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GaussJetBounds/OneLetterRadius.lean#L17)

## Integral split exponentials give the stronger weight on each difference

The substitution by $\mathcal L_s$ has a formal inverse $g_s$. The linear term is the identity, and the remaining terms uniquely determine each coefficient of $g_s$ recursively in its degree. Every coefficient of $g_s$ has weighted valuation at least $\rho$ with uniform variable weight $\rho$. The degree-one coefficient has this bound. At a higher degree use
$$
g_s=X_s-\sum_{e\ge1}p^{-e} g_{s-2e}^{p^{2e}}.
$$
Every factor in a term of given degree in $g_{s-2e}^{p^{2e}}$ has smaller positive degree, so induction bounds the product's weighted valuation from below by $p^{2e}\rho$. The factor $p^{-e}$ leaves at least $\rho$, since $(p^{2e}-1)\rho=1+p^2+\cdots+p^{2(e-1)}\ge e$. The ultrametric inequality preserves the bound on summing. This also works with any finite set of labels and any fixed map in place of the step back by two. [Inverse logarithm weight](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GaussJetBounds/GenLogInverse.lean#L24)

Write $D=\Delta b$ for either difference. Subtract one from the integral substituted series and substitute the inverse. An integral series with zero constant term has uniform weighted valuation at least $\rho$. Replacing a variable of weight $\rho$ by a series of weighted valuation at least $\rho$ preserves this bound. Indeed in each coefficient of a fixed degree only finitely many products contribute, and the lower bound for each follows by adding weights in a product. Therefore $\exp D-1$ has weighted valuation at least $\rho$.

Its coefficients belong to $K_0$, since the splitting maps have integer coefficients and the exponential has rational coefficients. The duplicated action, with the same root-of-unity factor on both copies of a label, leaves $D$ and $\exp D$ invariant. Thus any nonzero coefficient of degree $m$ satisfies the congruence that its sum of signed weights $(-1)^s p^s$ with multiplicity is zero modulo $p^d-1$. Modulo $p+1$, all signed weights equal one and $p^d-1$ is divisible by $p+1$. Hence $m$ is a multiple of $p+1$. For these coefficients $v(a)+\rho m$ lies in $(p-1)^{-1}\mathbb Z$, since $v(a)$ is an integer. Its lower bound $\rho>0$ then implies the stronger lower bound $c$. [Quantization of the weight](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GaussJetBounds/GaussJetProofs/OneLetterRadiusIdentity.lean#L48) · [Applying it to both differences](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GaussJetBounds/GaussJetProofs/ConstantCoeffEvenDerivativeEqZero.lean#L165)

Now recover this bound for $D$ itself by induction on positive total degree. In $\exp D-1=D+\sum_{k\ge2}D^k/k!$, the higher powers contributing to the current coefficient involve only smaller positive degrees of $D$. Their weighted valuations are at least $kc-v_p(k!)\ge c$, since $v_p(k!)\le(k-1)/(p-1)$. By subtraction, the coefficient of $D$ also has weighted valuation at least $c$. [Induction from the exponential to its logarithm](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GaussJetBounds/GaussJetProofs/LogStep.lean#L36)

## Only pure powers can escape the bound

If a nonzero term of $b$ uses two distinct variables of one parity, send the whole exponent of one of them to the second copy and leave the other in the first. The coefficient of the resulting monomial in the difference is exactly $b_n$. The two subtracted terms contribute zero because both copies occur. Total degree is unchanged, so $v(b_n)+\rho|n|\ge c$.

If a parity has only one variable, with exponent $m$, an interior split at $j$ gives the coefficient $\binom mj b_n$. For $m$ different from every $p^\alpha$ there is an interior $j$ with $\binom mj$ prime to $p$. This follows by expanding $(1+t)^m$ modulo $p$ as $\prod_a(1+t^{p^a})^{m_a}$ for the base-$p$ digits $m_a$. Some nonzero digit occurs at a place $a$ with $0<p^a<m$, and the coefficient at $j=p^a$ is $m_a$. If $m=p^\alpha$ with $\alpha\ge1$, an interior split at $j=p^{\alpha-1}$ has binomial valuation one. The identity $\binom{p^\alpha}{j}=(p^\alpha/j)\binom{p^\alpha-1}{j-1}$ and the all-$p-1$ digits of $p^\alpha-1$ give this.

Consequently an exception to the stronger bound must have exactly one variable of each parity, with exponents $p^\alpha,p^\beta$. At least one exponent exceeds one by the bidegree hypothesis, so the split of valuation one proves the weaker bound. Torus invariance gives $p^{s+\alpha}\equiv p^{s'+\beta}\pmod{p^d-1}$ after putting the even label first. Reducing each exponent modulo $d$ gives two powers between $1$ and $p^{d-1}$. Congruence forces equality, proving $s+\alpha=s'+\beta$. In particular $\alpha+\beta$ is odd, because $d$ is even and $s,s'$ have opposite parity. This proves the claim. [Coefficient extraction for even splitting](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GaussJetBounds/GaussJetProofs/SwappedParitySeriesBinomialForm.lean#L327) · [Coefficient extraction for odd splitting](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GaussJetBounds/GaussJetProofs/SwappedParitySeriesBinomialForm.lean#L356) · [Exceptional monomials and the one-unit loss](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GaussJetBounds/GaussJetProofs/SwappedParitySeriesBinomialForm.lean#L761)

## Recover the jet bound with a choice of radii

Here is the normalized valuation form of `LemmaRA` used for these jets. For integers $N_0,N_1\ge0$ let $Z=S\times\{1,\ldots,N_0\}\times\{1,\ldots,N_1\}$. Define $\mathcal L$ and its inverse $g$ on these variables by shifting only the $S$-label. Let $\mathcal U$ be integral on $Z$, and let $M_{z,i}\in K$ be integral coefficients with $i$ in a finite set $I$, each carrying a label $\lambda(i)\in S$. Require $M_{(s,a,b),i}=0$ unless $\lambda(i)=s$. Put $L_z(X)=\sum_i M_{z,i}X_i$. Let $B$ be the sum of the copies of the preceding $b$ under $X_s\mapsto L_{(s,a,b)}(X)$, one copy for each pair $(a,b)$. Take $\epsilon\in\{1,-1\}$ and let
$$
J(X)=\mathcal U(g(L(X)))\exp(\epsilon B(X)).
$$
For an exponent vector $\kappa$ with each $\kappa_i\le A$, take an integer $A\ge1$ and weights $\tau_i\ge0$. Suppose that for every monomial $X_i^{p^\alpha}X_j^{p^\beta}$ dividing $X^\kappa$ whose coefficient in $B$ fails the uniform bound $c$, we have
$$
p^\alpha\tau_i+p^\beta\tau_j\ge1 .
$$
Then
$$
v\!\left(\left(\prod_i\kappa_i!\right)[X^\kappa]J\right)
\ge\sum_i\kappa_i(\gamma-\tau_i)-|I|(\log_p A+1).
$$
Here the factorials are the conversion from coefficients to the derivatives at zero used in the jet. [Full jet coefficient statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GaussJetBounds/StatementG.lean#L12) · [Proof of the weighted jet bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GaussJetBounds/GaussJetProofs/LemmaRA.lean#L55)

To prove this, a linear substitution with integral coefficients preserves uniform weighted lower bounds under multiplication and summation. In the reduction modulo $p$ of a $p^\alpha$-th power of a linear form, only pure $p^\alpha$-th powers of single variables remain, since all mixed multinomial coefficients are divisible by $p$. Thus the one-unit defect described above can persist only on the same kind of two-power monomial in $B$. Label preservation ensures its labels still obey $\lambda(i)+\alpha=\lambda(j)+\beta$ and have opposite parity. The added weights $\tau$ supply the missing unit. Hence coefficients dividing $X^\kappa$ in $B$ now have weighted valuation at least $c$ for weights $r_i=\rho+\tau_i$.

The constant term of $B$ vanishes. In the exponential, the term $B^k/k!$ has weighted valuation at least $kc-v_p(k!)\ge0$ on these divisors. By the inverse-logarithm bound, $\mathcal U(g(L(X)))$ has weighted valuation at least zero with uniform weight $\rho$, hence also with $r_i\ge\rho$. Multiplication gives $v([X^\kappa]J)\ge-\sum_i\kappa_i r_i$. Legendre's formula $v_p(m!)=(m-s_p(m))/(p-1)$, with $s_p(m)$ the sum of its base-$p$ digits, gives $v_p(\kappa_i!)\ge c\kappa_i-(\log_p A+1)$ since $\kappa_i\le A$. Add these bounds and use $c-\rho=\gamma$.

For two ordinary variables put $\tau_i=\sigma_{\lambda(i)}$, with $\sigma$ the [cyclic dual weights](cyclic-degree-budgets-and-flow-duality.md). If $\alpha\ge\beta$, put $e=\alpha-\beta$ and $s=\lambda(i)$. The congruence identifies $\lambda(j)=s+e$, and $e$ is positive odd. Thus $p^\alpha\tau_i+p^\beta\tau_j=p^\beta(p^e\sigma_s+\sigma_{s+e})\ge1$. If $\beta>\alpha$, interchange the roles. This is the constraint with coefficients $(p^e,1)$ in the degree problem. It comes from the exponents of the two variables and the one unit of valuation needed in the exponential. The top rows of the determinant use different weights. Their contribution leads to the positive parts in the [next proof](top-row-capacities-and-prime-power-ramps.md). [The radii inequalities](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GaussJetBounds/GaussJetProofs/OneLetterRadiusIdentity.lean#L124) · [Use for determinant monomials](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GaussJetBounds/GaussJetProofs/TheoremAOneMonomialLogLoss.lean#L15)

Status. Source-based reconstruction draft. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
