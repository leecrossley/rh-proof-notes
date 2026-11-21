# The CM endomorphism forces two Frobenius descents

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Let $K$ be a complete characteristic-zero ultrametric field with integral ring $\mathcal O$, a prime $p$ of norm $p^{-1}$, and a field endomorphism $\sigma$ acting isometrically and satisfying $\sigma(x)\equiv x^p\bmod p\mathcal O$ for $x\in\mathcal O$. Suppose the norm of every nonzero element is a power of $p$. Put $q=p^2,\ \tau=\sigma^2$, and write $T f=\tau(f)(X^q)$ for one-variable series. Let $F$ be an integral formal group law with logarithm $\ell=X+O(X^2)$. Assume there is $a\in\mathcal O$ fixed by $\tau$ with $\lVert \sigma(a)-a\rVert=1$ for which $A=\ell^{-1}(a\ell)$ is integral. Also assume the integral multiplication series $E=[p]_F=\ell^{-1}(p\ell)$ has some coefficient at degree at most $q$ of norm one. The conclusion proved here is that there are integral $c_i$, with $c_0$ a unit, such that
$$
p\ell-\sum_{i\ge0}c_i\,T^{i+1}\ell\ \in p\mathcal O[[X]].
\tag{1}
$$
Only finitely many terms of the sum contribute in each degree. This is the coefficient form of `hon_series`. It is used to obtain the single Frobenius equation in the height-two parameter comparison. [Integral law and CM endomorphism data](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/UnramifiedIntegrals/FgDefs.lean#L15) · [The iterated Frobenius expansion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/UnramifiedIntegrals/FgHonF.lean#L166)

We use a substitution fact. If $D'(X)$ is integral and $u,v$ are integral zero-constant series with $u-v\in p\mathcal O[[X]]$, then $D(u)-D(v)$ is divisible by $p$. Indeed $n[X^n]D$ is integral for $n\ge1$. By the power congruence in the [inverse functional equation proof](finding-integral-points-from-formal-logarithms.md), $u^n-v^n$ is divisible by $p^{1+v_p(n)}$, obtained by first iterating the $p$-power step and then raising to $n/p^{v_p(n)}$. Multiplying by the coefficient of $D$ leaves a factor $p$. The fact also holds when $u,v$ have several variables. For a logarithm of an integral law, differentiating $\ell(F(X,Y))=\ell(X)+\ell(Y)$ in $Y$ at zero gives $\ell'(X)F_Y(X,0)=1$. The other factor is an integral unit of constant term $1$, hence $\ell'$ is integral. [Congruence after substituting in a series with integral derivative](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/UnramifiedIntegrals/FgHonA.lean#L137) · [The derivative of the logarithm is integral](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/UnramifiedIntegrals/FgHonB.lean#L191)

## Descend the multiplication series twice in the residue field

Write an overline for reduction modulo $p$, and $F^{\sigma}$ for action of $\sigma$ on its coefficients. The formal group homomorphism $\overline E:\overline F\to\overline F$ has derivative zero at the origin. Any homomorphism $h:F_1\to F_2$ over the residue field with $h'(0)=0$ has $h'(X)=0$, by differentiating
$$
h(F_1(X,Y))=F_2(h(X),h(Y))
$$
in $Y$ at zero, since $(F_1)_Y(X,0)$ has constant term $1$. Thus every exponent of $\overline E$ is a multiple of $p$, and $\overline E(X)=\overline h_1(X^p)$. The descended series is a homomorphism $\overline{F^\sigma}\to\overline F$, because $F(X,Y)^p\equiv F^\sigma(X^p,Y^p)\bmod p$ and substitution by $X^p,Y^p$ is injective. Similarly, $\overline E$ commutes with $\overline A$, so $\overline h_1\circ\overline{A^\sigma}=\overline A\circ\overline h_1$. The linear coefficient of this equality is
$$
\overline h_1'(0)\bigl(\overline{\sigma(a)}-\bar a\bigr)=0.
$$
The difference is nonzero by hypothesis. Hence $\overline h_1'(0)=0$. Descend once more in exactly the same way to obtain $\overline E(X)=\overline h(X^q)$ where $\overline h$ is a homomorphism from $\overline{F^\tau}$ to $\overline F$ and intertwines $\overline{A^\tau}$ and $\overline A$. The coefficient hypothesis on $E$ says that the linear coefficient of $\overline h$ is nonzero, since all possible positive degrees of $\overline E$ are now multiples of $q$. Choose an integral zero-constant lift $h$ of $\overline h$; its linear coefficient is a unit. This is the shape calculation used before `hon_mu`. [A lifted homomorphism after the two descents](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/UnramifiedIntegrals/FgHonF.lean#L72)

Let $D_0=\ell(h)$. It has integral derivative by the chain rule. Its additivity defect relative to $F^\tau$, and its scalar defect $D_0(A^\tau)-aD_0$, are divisible by $p$ by the congruence for substitutions: apply $\ell$ to the two integral sides of the reduced homomorphism and scalar identities, and use the exact identities for $F,A$. We also have
$$
p\ell-D_0(X^q)\in p\mathcal O[[X]]
$$
by applying $\ell$ to $E\equiv h(X^q)$, and $D_0'(0)=h'(0)$ is a unit.

## Peel off the linear multiple of the logarithm and descend again

A series $D$ with zero constant term, integral derivative and both such defects divisible by $p$ is the datum `QCls`. The law and endomorphism may be any successive twist of $F,A$. For one such pair denote its normalized logarithm by $f$, and $c=D'(0)\in\mathcal O$. Write $U=D-cf$. It keeps the two defects, because $f$ satisfies the exact equations, and satisfies $U'\in p\mathcal O[[X]]$. In fact differentiating the additivity congruence of $D$ gives $D'(X)F_Y(X,0)-c\in p\mathcal O[[X]]$ for the law at this stage, and $f' F_Y(X,0)=1$; divide by that integral unit.

Define the descended series $V(X)=\sum_{j\ge1}[X^{pj}]U\, X^j$. The coefficients of $U$ at powers prime to $p$ are divisible by $p$, since $U'$ is, so $U\equiv V(X^p)\bmod p$. The congruence refers to the difference of series; $U$ and $V$ may have nonintegral coefficients individually. The derivative of $V$ is integral because $j[X^{pj}]U=(pj[X^{pj}]U)/p$. To pass the additivity defect down, replace $U(F)$ by $V(F^p)$ modulo $p$ using integral substitution in the difference $U-V(X^p)$. Replace $V(F^p)$ by $V(F^\sigma(X^p,Y^p))\bmod p$ using the substitution fact for $V'$. The resulting relation is the additivity congruence for $V$ and the once-twisted law, after removing the substitution by powers $p$. The identical replacement for $U(A)$ gives the scalar congruence for $V$ and the once-twisted endomorphism. This step uses $a\in\mathcal O$ when replacing $aU$ by $aV(X^p)$.

At the start of the peeling step, all pairs of law and scalar endomorphism were twisted an even number of times. After one further twist the linear coefficient of the scalar endomorphism is $\sigma(a)$, whereas the scalar on the right of the congruence is still $a$. Comparing degree one now gives $V'(0)(\sigma(a)-a)\in p\mathcal O$, so $V'(0)\in p\mathcal O$. The additivity defect then gives $V'\in p\mathcal O[[X]]$ by the same derivative identity. Descend again, with no further subtraction needed, obtaining $D_{\mathrm{next}}$ for the twice-twisted law and endomorphism and
$$
D-cf-D_{\mathrm{next}}(X^q)\in p\mathcal O[[X]] .
$$
The scalar endomorphism after two twists has linear coefficient $a$ since $\tau(a)=a$. This is the two-step coefficient extraction `lemmaQ`. [Extract a normalized term and descend twice](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/UnramifiedIntegrals/FgHonD.lean#L195)

Start with $D_0$ relative to the twice-twisted law. The coefficient extracted at stage $i$ is $c_i=D_i'(0)\in\mathcal O$, with $c_0$ a unit. Repeated substitution of the last congruence expresses $p\ell$, modulo $p\mathcal O[[X]]$, as the sum through $c_{m-1}T^m\ell$ plus $D_m(X^{q^{m+1}})$. Since every $D_m$ has zero constant term, the last term has no coefficient in any fixed degree when $m$ is large. This proves (1). [Assemble the coefficientwise expansion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/UnramifiedIntegrals/FgHonF.lean#L166)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
