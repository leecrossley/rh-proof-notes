# Normalizing the height-two logarithm

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Use $K,\mathcal O,p,\sigma,\tau=\sigma^2,q=p^2,Tf=\tau(f)(X^q)$ from [the two Frobenius descents](the-cm-endomorphism-forces-two-frobenius-descents.md). In addition assume the residue field is algebraically closed. Let $\ell=X+O(X^2)$ have zero constant term and suppose integral $c_i$ with $\lVert c_0\rVert=1$ satisfy
$$
p\ell-\sum_{i\ge0}c_i T^{i+1}\ell\in p\mathcal O[[X]] .
$$
Then there is a unit $\epsilon\in\mathcal O$ with
$$
\theta(X)=\ell^{-1}\!\left(\epsilon\sum_{j\ge0}p^{-j}X^{p^{2j}}\right)\in\mathcal O[[X]] .
$$
The conclusion is the parameter comparison needed in `CM3`. This note proves the steps following the Frobenius expansion. The first coefficient hypothesis for that expansion is the existence of a unit coefficient in the multiplication series at degree at most $p^2$. [Application to the formal curve in CM3](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/UnramifiedIntegrals/FgClose.lean#L25)

## Collapse the Frobenius expansion

For a bounded sequence $x=(x_i)_{i\ge0}$ over $K$, define
$$
(Bx)_m=\sum_{i=0}^m x_i\,\tau^i(c_{m-i}) .
$$
It is a triangular system with unit diagonal $\tau^m(c_0)$; off-diagonal entries have norm at most $1$. Thus every bounded right-hand side $y$ can be solved uniquely, by recursion on $m$, and $\sup_m\lVert(B^{-1}y)_m\rVert\le\sup_m\lVert y_m\rVert$ by the ultrametric inequality. In the complete space of bounded sequences, consider the map taking $x$ to the solution for the right-hand side $(c_0,p x_2,p x_3,\ldots)$. It sends sequences of norm at most $1$ to sequences of norm at most $1$, and its Lipschitz constant is at most $\lVert p\rVert<1$. Starting for example at the zero sequence, the successive differences decay geometrically, so the iterates converge uniformly to a fixed point $t$. Row $0$ gives $t_0=1$, and the later rows give
$$
\sum_{i=0}^{n-1}t_i\,\tau^i(c_{n-1-i})=p t_n\qquad(n\ge2).
$$
This is the bounded solution of `twisted_division`. The use of the unit $c_0$ is what makes backward equations soluble without amplifying any coefficient differences. [The triangular coefficient system](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/UnramifiedIntegrals/FgHonG.lean#L63)

Let $L=p\ell-\sum_i c_i T^{i+1}\ell$. For each $i$, $t_iT^i L$ has coefficients in $p\mathcal O$, because $\tau$ preserves $\mathcal O$ and fixes $p$. The series $\sum_i t_iT^i L$ is coefficientwise finite as $L(0)=0$ and $T$ raises the order of vanishing. Expand and group the terms with the same $T^n\ell$. The coefficient at $T^n\ell$ for $n\ge2$ is zero by the last equations, the coefficient at $\ell$ is $p$, and the coefficient at $T\ell$ is $p t_1-c_0$. With $c=c_0-p t_1$ this proves
$$
\ell-(c/p)T\ell\in\mathcal O[[X]],\qquad \lVert c\rVert=1.
$$
The norm assertion uses the strict inequality $\lVert p t_1\rVert<\lVert c_0\rVert$. The proof uses the coefficient action $T(af)=\tau(a)Tf$; treating $T$ as $K$-linear here would give different triangular equations. [The single Frobenius equation for the logarithm](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/UnramifiedIntegrals/FgHonH.lean#L220)

## Remove the unit by a semilinear equation

Solve $\epsilon=c\tau(\epsilon)$ with $\lVert\epsilon\rVert=1$. Modulo $p$ this amounts to $\bar\epsilon^{\,q-1}=\bar c^{-1}$, so there is a nonzero solution in the algebraically closed residue field. Choose an integral lift $\epsilon_1$. Suppose
$$
\epsilon_n/(c\tau(\epsilon_n))\equiv1\bmod p^n .
$$
Write the quotient as $1+p^n b$. Change the unit to $\epsilon_{n+1}=\epsilon_n(1+p^n a)$. Modulo $p^{n+1}$ the new quotient is $1+p^n(b+a-\tau(a))$, by multiplying out the numerator and using the inverse of $1+p^n\tau(a)$. Choose the residue of $a$ so that $\bar a^{\,q}-\bar a=\bar b$, which is solvable since the residue field is algebraically closed. This refines the congruence. The units converge to a unit $\epsilon$, and $\tau$ is an isometry, so the equation holds at the limit. [Lifting the semilinear unit equation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/UnramifiedIntegrals/SemilinNormPowSubPow.lean#L76)

## Invert the normalized logarithm

Let $f_0=\ell/\epsilon$. The equality for $\epsilon$ gives $\tau(\epsilon)^{-1}=c/\epsilon$, so
$$
f_0-p^{-1}Tf_0=\epsilon^{-1}\bigl(\ell-(c/p)T\ell\bigr)
$$
is integral. Because the substitution $X\mapsto\epsilon X$ is integral, $f(X)=f_0(\epsilon X)$ also has integral Frobenius defect, by the [substitution part of the functional equation lemma](finding-integral-points-from-formal-logarithms.md). Now $f$ has identity linear coefficient. The desired height-two logarithm $\lambda$ has integral defect $\lambda-p^{-1}T\lambda=X$. Apply the inverse direction of that lemma to solve $f(H)=\lambda$ with $H$ integral and zero-constant. Unwinding $f$ gives $\ell(\epsilon H)=\epsilon\lambda$. Thus the requested $\theta=\epsilon H$ is integral. [Integral comparison with the height-two logarithm](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/ReciprocityTheory/ReductiveGroups/UnramifiedIntegrals/FgFinA.lean#L115)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
