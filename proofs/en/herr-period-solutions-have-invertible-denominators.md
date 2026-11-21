# Herr period solutions have invertible denominators

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E8%AE%A9Herr%E6%96%B9%E7%A8%8B%E7%9A%84%E5%91%A8%E6%9C%9F%E8%A7%A3%E5%8F%AA%E5%B8%A6%E5%8F%AF%E9%80%86%E5%88%86%E6%AF%8D.md)

Use $A,B^+,B,X,Q,\varphi,J$ from the [period lattice comparison](two-wach-lattices-agree-after-inverting-the-parameter.md), with Wach lattice $N=N(T)$ and $P^+=B^+\otimes_O T\subset P=B\otimes_O T$. Assume $X,Q$ are units in $B$, $\varphi(X)=XQ$, and $X^M J(N)\subset P^+$ for $M\ge0$. Given a finite multiset $I$ of nonnegative integers, let $\Lambda=\prod_{j\in I}\varphi^j(Q)$ and take $y\in D(T)$ with $\Lambda y\in N$. For any $b\in P$ with $(\varphi-1)b=J(y)$, let $m\ge0$ bound the entries of $I$ (take zero if empty), $X_*=\prod_{j=0}^m\varphi^j(X)$, and $a=M+|I|$. Then $X_*^a b\in P^+$. If the comparison $\beta:B^+\to L\otimes B_{\rm cris}$ sends $X$ and its Frobenius iterates to units, $b$ has a well-defined image in the crystalline period module.

**Proof.** Set $L_*=\prod_{j=0}^m\varphi^j(Q)$. We have $\varphi(X_*)=X_*L_*$ and $X^M\Lambda\mid(X_*L_*)^a$ over $A$: $X\mid X_*$ and $\Lambda\mid L_*^{|I|}$, with multiplicities counted. For $v=X_*^a b$, semilinearity gives
$$
\varphi(v)=L_*^av+(X_*L_*)^aJ(y).
$$
The error term is integral, since $X^M\Lambda J(y)=X^M J(\Lambda y)\in P^+$ and the quotient of the scalars is in $A$. In the $T$-basis this is a [Witt integrality equation](frobenius-matrix-equations-force-witt-integrality.md) with integral coefficients, hence $v\in P^+$.

Map $v$ by $\beta$ and divide by $\beta(X_*^a)$. Any other permitted denominator gives the same value by cross-multiplication before applying $\beta$. The project takes $X$ corresponding to $[\epsilon_1]-1$, whose comparison image is assumed invertible in the chosen model; Frobenius compatibility makes the iterates invertible as well.

`φ_prod` and `multiset_dvd` give the product and divisibility, `of_sand` supplies the matrix equation, and `main` applies it. `isUnit_prod` proves the final invertibility. [Product](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/MemRangeOfFrob.lean#L72) · [Divisibility](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/MemRangeOfFrob.lean#L79) · [Integral equation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/MemRangeOfFrob.lean#L114) · [Application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/MemRangeOfFrob.lean#L163) · [Invertibility](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/HerrCocyclePolesFrobeniusQCrystalline.lean#L406)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
