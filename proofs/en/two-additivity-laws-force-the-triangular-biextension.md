# Two additivity laws force the triangular biextension

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Let $p>2$ be prime. Let $K$ be a complete ultrametric field of characteristic zero with value group $p^{\mathbb Z}$, $|p|=p^{-1}$, and an endomorphism $\sigma$ whose reduction on its valuation ring $R$ is Frobenius modulo $pR$. Assume $K$ contains a primitive root of order $p^2-1$. Define
$$
\ell(t)=\sum_{i\ge0}\frac{t^{p^{2i}}}{p^i},\qquad
g(t)=p^{-1}\ell(t^p),\qquad
A(x,y)=\sum_{0\le i\le j}\frac{x^{p^{2i}}y^{p^{2j+1}}}{p^{i+j+1}}.
$$
Let $F\in R[[x,y]]$ have zero constant coefficient and satisfy $\ell(F(x,y))=\ell(x)+\ell(y)$. Write $P\sim Q$ if $P-Q$ has zero constant coefficient and $\exp(P-Q)$ has integral coefficients. Suppose $b\in xy K[[x,y]]$ satisfies
$$
\begin{aligned}
 b(F(x,x'),y)&\sim b(x,y)+b(x',y),\\
 b(x,F(y,y'))&\sim b(x,y)+b(x,y'),\\
 b(\zeta x,y)&\sim b(x,\zeta^p y)\quad(\zeta^{p^2-1}=1).
\end{aligned}
$$
Then there is a $c\in R$ with $\sigma^2 c=c$ and
$$
b(x,y)\sim c A(x,y)-\sigma(c) A(y,x).
$$
This is the normal form used before the [cyclic expansion of the standard theta](the-rescaled-standard-theta-has-a-cyclic-power-expansion.md).

## Proof

For a series $V$ of zero constant coefficient put
$$
\mathcal D V=\frac{(\sigma V)(x^p,y^p)-pV(x,y)}p,
$$
with the same definition in any number of variables. By [Dwork's test](dworks-integrality-test-for-the-formal-exponential.md), $V\sim0$ holds exactly when $\mathcal D V$ is integral. Thus these equivalences can be added and divided by integers prime to $p$. Integral substitutions with zero constant terms also preserve the equivalences, by substitution in their exponentials.

Average $b(\zeta x,\zeta^{-p}y)$ over the $p^2-1$ roots and call the result $G$. Each summand is equivalent to $b$, so $G\sim b$. On a monomial $x^iy^j$, the sum of multipliers $\zeta^{i-pj}$ is zero unless $i\equiv pj\pmod{p^2-1}$. Hence $G$ has this support and is still divisible by $xy$. Its two split defects are still equivalent to zero. Denote the defect in the first variable by $\delta_1 G$ and the corresponding one for the second variable by $\delta_2 G$.

If $\exp V$ is integral and has constant coefficient $1$, every first derivative of $V$ is integral by the logarithmic derivative identity. In $\delta_1G$, differentiate in the added variable $x'$ and set $x'=0$. The identity for $F$ gives $\partial_2F(x,0)=1/\ell'(x)$, because $\ell'(0)=1$. Since $\ell'$ is integral, we get
$$
\partial_xG(x,y)-\ell'(x) f(y)\in R[[x,y]],\qquad f(y)=\partial_xG(0,y).
$$
The derivative in $x$ of $\delta_2G$ at $x=0$ gives the integral defect $f(F(y,y'))-f(y)-f(y')$. By the [one-variable classification](integral-formal-coboundaries-determine-the-logarithmic-terms.md), $f=cg+a\ell+I$ with $c\in R$ and $I$ integral. In $f$ only degrees $j\equiv p\bmod(p^2-1)$ can occur. Projecting to these degrees retains $cg$ and removes $a\ell$. Thus
$$
\partial_x(G-c\ell(x)g(y)),\qquad
\partial_y(G-c' g(x)\ell(y))
$$
are integral for some $c,c'\in R$. Swapping the two variables preserves the support condition since $p^2\equiv1\bmod(p^2-1)$.

Apply the first splitting to $\mathcal D G$. Put $U=F(x,x')$ and $V=F(x^p,x'^p)$. The coefficients of $F$ lie in $\mathbb Z_p$, since $F=\ell^{-1}(\ell(x)+\ell(x'))$ has rational coefficients and is integral. Thus $U^p\equiv V\bmod p$. Direct substitution gives
$$
\delta_1\mathcal D G=\mathcal D(\delta_1G)
+\frac{(\sigma G)(U^p,y^p)-(\sigma G)(V,y^p)}p .
$$
The first summand is integral by Dwork's test. In the second summand, replacing $\sigma G$ by $\sigma(c)\ell(x)g(y)$ changes the result by an integral series. Indeed the discarded series has integral partial derivative in $x$. For a term $a_m X^m$, the binomial expansion of its difference between $X+pY$ and $X$ has $r$-th term with factor
$$
a_m\binom mr p^{r-1}=(m a_m)\binom{m-1}{r-1}\frac{p^{r-1}}{r}
$$
after division by $p$. This is integral for all $r\ge1$, since $v_p(r)\le r-1$. The other variables can be treated as coefficient variables in this calculation.

Now $\ell(U^p)-\ell(V)=p(g(U)-g(x)-g(x'))$, by the identity for $\ell$ at $V$. The one-variable defect $\delta g=g(U)-g(x)-g(x')$ is integral: its expression as a quotient by $p$ follows from the same binomial calculation with $\ell'$ integral. As $g(y^p)=\ell(y)-y$, we conclude that
$$
\delta_1\mathcal D G-\sigma(c)\,\delta g(x,x')\ell(y)
$$
is integral. The second split has the corresponding correction $\sigma(c')\ell(x)\,\delta g(y,y')$. Consequently
$$
H=\mathcal D G-\sigma(c)g(x)\ell(y)-\sigma(c')\ell(x)g(y)
$$
has ordinary integral split defects in both variables. The two-variable classification in the same [integral-defect proof](integral-formal-coboundaries-determine-the-logarithmic-terms.md) expresses $H=d\ell(x)\ell(y)+J$ with $J$ integral. The product of two logarithms has support in the degrees $i,j\equiv1\bmod(p^2-1)$, disjoint from $i\equiv pj$. The support of $H$ lies in the latter set, so its coefficients there are coefficients of $J$, and $H$ is integral.

At $(1,p^{2j+1})$ the first derivative relation gives $G_{1,p^{2j+1}}-c/p^{j+1}\in R$. Integrality of $H$ gives $-G_{1,p^{2j+1}}-\sigma(c')/p^{j+1}\in R$, because the $p$-power substitution contributes no first power of $x$. Adding for every $j$ yields $c+\sigma(c')=0$. Applying the same comparison with the variables exchanged yields $c'+\sigma(c)=0$. In particular, $\sigma^2 c=c$.

Finally, the triangular range gives the identities
$$
A(x^p,y^p)=p\bigl(g(x)\ell(y)-A(y,x)\bigr),\qquad
A(y^p,x^p)=p\bigl(\ell(x)g(y)-A(x,y)\bigr).
$$
For the first identity the $p$-power substitution changes the even index in the $y$ degrees from $j$ to $j+1$. This takes $i\le j$ to the strict range $i<j+1$ in $g(x)\ell(y)$, whose complementary range is exactly $A(y,x)$. The second identity exchanges the variables. It follows that
$$
\mathcal D(cA(x,y)-\sigma(c)A(y,x))
=\sigma(c)g(x)\ell(y)-c\ell(x)g(y).
$$
This is the correction subtracted from $\mathcal D G$ in the definition of $H$. Dwork's test now proves $G\sim cA-\sigma(c)A^{\mathrm{swap}}$, and thus the asserted equivalence for $b$.

## Lean correspondence

- [`BetaHyp` and `BetaIsG`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/IsLawOfLog.lean#L89) give the hypotheses and conclusion.
- [`StepI_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/ConstantCoeffLawFirstTwoOfThree.lean#L411) gives the partial derivative correction.
- [`StepII_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/PartialCoboundaryLinear.lean#L225) passes through the Frobenius difference and uses the binomial perturbation bound.
- [`StepH_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/ConstantCoeffFirstTwoOfThree.lean#L277) gives the integral corrected difference, followed by the comparison at degrees $1,p^{2j+1}$ and the final Dwork step.
- [`BetaIsG_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/NormLiftLeOne.lean#L32) combines the steps.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
