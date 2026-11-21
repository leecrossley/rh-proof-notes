# Recovering primitive Dirichlet characters from inertia averages

[Chinese proof](../zh/%E6%83%AF%E6%80%A7%E5%B9%B3%E5%9D%87%E6%80%8E%E6%A0%B7%E8%BF%98%E5%8E%9F%E7%8B%84%E5%88%A9%E5%85%8B%E9%9B%B7%E7%89%B9%E5%BE%81.md) · [Reading and review status](../../STATUS.md)

The finite character expansion of a class count uses coefficients defined by averaging over inertia. This note identifies those coefficients with the values of primitive Dirichlet characters. It also computes the weights of the characters kept in the final sum and bounds the contribution of the characters discarded there.

## Arithmetic data and the coefficient identity

Let $H$ be a finite abelian group, $H_0\le H$, and $o=[H:H_0]$. Write $A=(\mathbb Z/2\mathbb Z)^2\times H$ additively. Fix a positive integer $N$ and a surjective homomorphism $r:(\mathbb Z/N\mathbb Z)^\times\to A$. In the application the Artin map of the field specified by `HostAx` supplies $r$. The first binary coordinate records `iod`. The character $s(i,j,h)=(-1)^j$ corresponds to `psC`.

For each prime $p$ write $N=p^kM_p$ with $p\nmid M_p$. Let $I_p$ be the image under $r$ of the kernel of reduction to $(\mathbb Z/M_p\mathbb Z)^\times$. The Chinese remainder theorem gives a unique unit $u_p$ modulo $N$ with $u_p\equiv p\pmod{M_p}$ and $u_p\equiv1\pmod{p^k}$. Set $F_p=r(u_p)$. The definition includes $k=0$.

Given a complex character $\psi$ of $A$, extend $\psi\circ r$ by zero on nonunits modulo $N$. Let $\chi_\psi$ be the primitive Dirichlet character inducing the resulting character, and let $f_\psi$ be its conductor. For $n\ge1$ put

$$
P_\psi(n)=\prod_{p\mid n}\frac1{|I_p|}\sum_{u\in I_p}
\psi\bigl(v_p(n)F_p+u\bigr).
$$

**Claim.** For all $\psi$ and all integers $n\ge1$, $P_\psi(n)=\chi_\psi(n)$. The map $\psi\mapsto\chi_\psi$ is injective and takes the trivial character to the trivial character of conductor $1$.

Indeed, reduction to $(\mathbb Z/M_p\mathbb Z)^\times$ is surjective by the Chinese remainder theorem. Consequently $\psi$ is trivial on $I_p$ exactly when $\psi\circ r$ descends to a character modulo $M_p$. This is equivalent to $f_\psi\mid M_p$, or to $p\nmid f_\psi$ since $f_\psi\mid N$. Fix an exponent $i\ge1$. If $p\nmid f_\psi$, all the terms of the average on the coset $iF_p+I_p$ equal $\psi(F_p)^i$. Since $u_p\equiv p\pmod{M_p}$ and $f_\psi\mid M_p$, we have $\psi(F_p)=\chi_\psi(u_p)=\chi_\psi(p)$. If $p\mid f_\psi$, choose $v\in I_p$ with $\psi(v)\ne1$. Translation by $v$ permutes the summands and multiplies the sum by $\psi(v)$, so it is zero. In this case $\chi_\psi(p^i)=0$ as well. Multiplying the prime-power identities proves the claim for $n>1$. Both sides equal $1$ at $n=1$.

If two inducing primitive characters agree, the characters they induce modulo $N$ agree on all units. Surjectivity of $r$ then gives equality of the original characters of $A$. The trivial character clearly induces the character of conductor $1$.

For a nontrivial $\psi$, let the finite-group error be

$$
G_\psi(y)=\sum_{1\le n\le y}\Lambda(n)P_\psi(n)(y/n-1)+y\ell(\psi).
$$

For the trivial group character use the correction $-y\log y+(1+\gamma_E)y$ instead. Write $g_\chi(y)$ for the corresponding analytic error, with $\chi(n)$ in place of $P_\psi(n)$ and, for nonprincipal $\chi$, with the correction $y(L'/L)(1,\chi)$. Thus if $\ell(\psi)=(L'/L)(1,\chi_\psi)$ for each nontrivial $\psi$, the coefficient identity implies $G_\psi(y)=g_{\chi_\psi}(y)$ for every positive $y$. In the Lean application `HostAddCharCompatible` supplies this equality of correction coefficients whenever a primitive character agrees with $P_\psi$ on the positive integers.

## The retained family and its weights

Keep the preceding data. Fix $x>0$, real parameters $\varepsilon,C$, and a finite set $T\subseteq H$. Let $\Psi$ consist of the characters of $A$ trivial on $\{(0,0,h):h\in H_0\}$. Let $K$ be a finite set of primitive characters, containing the trivial one and closed under inversion, with an optional distinguished real odd character $\chi_0\in K$. Put $K_p=\{\psi:\chi_\psi\in K\}$. Here the subscript is just a label for the preimage.

Assume every $\chi\in K$ has a preimage in $\Psi$ trivial at $(1,0,0)$. If $\chi_0$ is specified, require $\chi_0=\chi_s$. Otherwise require $\chi_s\notin K$. Assume the following two bounds whenever $\psi\in\Psi$ and either $\psi(1,0,0)=-1$ or $\psi(1,0,0)=1$ with $\psi\notin K_p$:

$$
|g_{\chi_\psi}(x)|\le x^{1/2+\varepsilon},
\qquad
|(L'/L)(1,\chi_\psi)|\le C\log x.
$$

Assume also the compatibility of $\ell$ just described, and for every $Q\in H/H_0$ assume

$$
\left||T\cap Q|-\frac{3+\mathbf 1_{Q=H_0}}{3o+1}|T|\right|
\le x^{-1+\varepsilon}|T|.
$$

These are the error and distribution inputs used here from `EAtH` and `HostAddCharCompatible`.

Put $c=1/(3o+1)$. For $\psi\in K_p$ set $w(\psi)=1$ when $\psi$ is trivial on all of $H$, and $w(\psi)=c$ otherwise. For nontrivial $\chi\in K$ set $v(\chi)=1$ if $\chi=\chi_0$ is specified and $v(\chi)=c$ otherwise. Then for all $y>0$,

$$
\sum_{\psi\in K_p}w(\psi)\operatorname{Re}G_\psi(y)
=G_1(y)+\sum_{\chi\in K\setminus\{1\}}v(\chi)\operatorname{Re}g_\chi(y). \tag{1}
$$

The discarded contribution $\Sigma(x)=\sum_{\psi\in\Psi\setminus K_p}|G_\psi(x)|$ satisfies $\Sigma(x)\le4o x^{1/2+\varepsilon}$. Furthermore, for each $\psi\in\Psi$ nontrivial on $H$,

$$
\left|\sum_{t\in T}\psi(0,0,t)-c|T|\right|
\le o x^{-1+\varepsilon}|T|. \tag{2}
$$

### Proof of the three conclusions

By the coefficient identity and injectivity, the map $\psi\mapsto\chi_\psi$ gives a bijection $K_p\to K$. The preimage hypothesis implies $K_p\subseteq\Psi$, with every member trivial at $(1,0,0)$. If a member is also trivial on $H$, only the second binary coordinate can contribute a sign. Such a member is therefore $1$ or $s$. By the condition on $\chi_0$, the latter is retained exactly when the distinguished character is specified. Consequently the weights agree under the bijection, with the trivial term separated. Substituting $G_\psi(y)=g_{\chi_\psi}(y)$ gives (1).

Pullback from the quotient identifies $\Psi$ with the character group of $(\mathbb Z/2\mathbb Z)^2\times(H/H_0)$, so $|\Psi|=4o$. For each discarded character, its first sign is either $1$ or $-1$ and in both cases the hypotheses give $|G_\psi(x)|\le x^{1/2+\varepsilon}$. Summing gives the claimed bound on $\Sigma(x)$. The same hypotheses bound $|\ell(\psi)|$ by $C\log x$ on the discarded set. For a nontrivial retained character its coefficient is bounded in modulus by $\sum_{\chi\in K\setminus\{1\}} |(L'/L)(1,\chi)|$. Lean also allows the trivial entry to be included in the sum with its stipulated value. Only nontrivial terms need this bound in the argument.

Finally, if $\psi|_H$ is nontrivial, its values descend to a nontrivial quotient character $\theta$ of $H/H_0$. Write $|T\cap Q|=(3+\mathbf1_{Q=H_0})c|T|+E(Q)$ with $|E(Q)|\le x^{-1+\varepsilon}|T|$. Then

$$
\sum_{t\in T}\psi(0,0,t)
=3c|T|\sum_Q\theta(Q)+c|T|\theta(H_0)+\sum_Q\theta(Q)E(Q)
=c|T|+\sum_Q\theta(Q)E(Q).
$$

The first term vanishes by character orthogonality and $\theta(H_0)=1$. The error has at most $o$ summands, each of modulus at most $x^{-1+\varepsilon}|T|$. This proves (2). If $\psi|_H$ is trivial the original sum is exactly $|T|$. The extra share assigned to the identity coset produces the weight $c$ for nontrivial quotient characters.

## Role in the pointwise bound

The translation-average estimate `ch_core` bounds the retained sum of finite-group errors and gathers the discarded terms into $\Sigma$. Equation (1) identifies the retained sum with the analytic character family used to detect zeros. The bound on $\Sigma$ allows the discarded terms to be absorbed in the final exponent. This argument applies at each point where the host and analytic hypotheses are available. To use it on an entire window one needs a family providing those inputs at every point.

- The Artin map and local data are [`recH`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/PrimitiveCosets/RecH.lean#L21). The inertia and primitive value lemmas are [`trivial_on_inertia_iff`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ChainSlopeWindows/GaloisMapComplexConjugation.lean#L129), [`cosetMean_eq_primitive`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ChainSlopeWindows/GaloisMapComplexConjugation.lean#L209), and [`primitive_value_primitive`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ChainSlopeWindows/GaloisMapComplexConjugation.lean#L233).
- See [`prim_inj`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/PrimitiveCosets/PrimInj.lean#L6) and [`prim_read`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/PrimitiveCosets/PrimRead.lean#L48) for injectivity and the error identification.
- The input is [`EAtH`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/RamificationFrobenius/TotientGaloisClasses/ExplicitFormulaErrorOfHostConditions.lean#L144). The retained sum, character count, discarded error and distribution calculation are [`gmA_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/PrimitiveCosets/GmAEq.lean#L61), [`card_PsiA`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/PrimitiveCosets/CardPsiA.lean#L60), [`sigA_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/PrimitiveCosets/SigALe.lean#L38), and [`tops_sum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/PrimitiveCosets/TopsSum.lean#L75).

English translation draft. The two analytic inequalities are hypotheses of this deduction. The notes on [translation averaging](translation-averaging.md) and [auxiliary prime selection](prime-pair-selection.md) explain the next use and the origin of the inputs, respectively.
