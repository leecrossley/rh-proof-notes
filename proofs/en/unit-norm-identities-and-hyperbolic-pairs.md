# Unit norm identities and hyperbolic pairs

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $K$ be a field of characteristic zero, $R$ a subring, and $\lambda(t)=t+O(t^2)$ a formal logarithm over $K$ with inverse for composition. Assume $F(x,y)=\lambda^{-1}(\lambda(x)+\lambda(y))$ has coefficients in $R$. Write $x+_F y=F(x,y)$ and $[a]x=\lambda^{-1}(a\lambda(x))$. Let $\phi(t)$ be a one-variable series with $\phi(0)=0$. For zero-constant series $P,Q$ over $K$, write $P\sim Q$ if $\exp(P-Q)$ has coefficients in $R$; its constant term is $1$. Put
$$
b_0(x,y)=\phi(x+_F y)-\phi(x)-\phi(y).
$$
Call a point integral if it is a series with coefficients in $R$ and zero constant term. We use the relation $\sim$ in arbitrarily many finite collections of variables. It is preserved by substitution of integral points and by addition of equivalent pairs. It also admits multiplication by any $z\in K$ with $\binom{z}{j}\in R$ for every $j\ge0$. In fact if $\exp(P-Q)=1+H$, then $\exp(z(P-Q))=\sum_{j\ge0}\binom{z}{j}H^j$, with only finitely many contributions in each degree. The same definitions and proofs extend to arbitrary sets of variables with the coefficientwise operations of the Lean power series ring.

## From unit norms to an adjoint for every scalar

Take a commutative ring $O$ with an involution $\alpha\mapsto\bar\alpha$ and a unital map $\tau:O\to K$. In formulas write $[\alpha]$ and $\alpha P$ for $[\tau(\alpha)]$ and $\tau(\alpha)P$. Assume the following.

- For all $\alpha\in O$, $[\alpha]$ has integral coefficients.
- For every $z=\bar z$ in $O$, all $\binom{\tau(z)}{j}$ are in $R$, and for all integral points $x,y$, $b_0(x,[z]y)\sim z\,b_0(x,y)$.
- For all integral points $x,x',y$, $b_0(x+_F x',y)\sim b_0(x,y)+b_0(x',y)$.
- $2$ is a unit of $O$, $1/2$ belongs to $R$, and every element of $O$ is a sum of two units of $O$.
- For every unit $u\in O^\times$, $\phi([u]t)\sim u\bar u\,\phi(t)$ as one-variable series.

Then for all $\alpha\in O$ and integral points $x,y$,
$$
\phi([\alpha]x)\sim \alpha\bar\alpha\,\phi(x),\qquad
b_0([\alpha]x,y)\sim b_0(x,[\bar\alpha]y).
$$
The one-variable norm relation and the universal adjoint relation are the conclusions of `NormAdjAll`. Symmetry of $b_0$ follows from commutativity of $F$, so the assumed additivity also holds in the second argument. [NormAdjAll and its hypotheses](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/SecondCoefficientNorms/IsotropicVanish.lean#L61)

For a unit $u$, $[u](x+_F y)=[u]x+_F[u]y$ because both sides have logarithm $u(\lambda(x)+\lambda(y))$. Apply the unit norm law to $x+_F y$, $x$ and $y$, all integral. Subtracting gives
$$
b_0([u]x,[u]y)\sim u\bar u\,b_0(x,y)\sim b_0(x,[u\bar u]y).
$$
In the last step $u\bar u$ is self-adjoint. Substitute $[u^{-1}]y$ for $y$ to obtain the adjoint relation for $u$. When $\alpha=u+v$, $[\alpha]x=[u]x+_F[v]x$ by taking logarithms. Additivity, the two unit adjoints, and additivity in the second argument turn $b_0([\alpha]x,y)$ into $b_0(x,[\overline{u+v}]y)$ modulo $\sim$. Thus every $\alpha$ has the claimed adjoint. [From unit norms to all scalar adjoints](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/SecondCoefficientNorms/BinomialSeriesCoefficients/UnitaryInverseIdentity.lean#L424)

For the norm of $u+v$, expand using the defining coboundary:
$$
\phi([u+v]x)\sim (u\bar u+v\bar v)\phi(x)+b_0([u]x,[v]x).
$$
Write $D=b_0([u]x,[v]x)$. The adjoint gives $D\sim b_0(x,[\bar u v]x)$, and by first interchanging the arguments it also gives $D\sim b_0(x,[\bar v u]x)$. Put $z=\bar u v+\bar v u$. Adding the two equivalences, using additivity and then self-adjoint linearity, gives $2D\sim z b_0(x,x)$. The norm law for the unit $2$ gives $b_0(x,x)=\phi([2]x)-2\phi(x)\sim2\phi(x)$. As $z$ is self-adjoint, multiplication by $\tau(z)$ preserves equivalence. We obtain $2D\sim2z\phi(x)$. To remove the factor $2$, note that if $\exp(2H)$ is integral and $H(0)=0$, then $\exp(H)^2=\exp(2H)$ proves integrality of $\exp(H)$ by induction on degree, since $1/2\in R$. Therefore $D\sim z\phi(x)$, and $u\bar u+v\bar v+z=(u+v)\overline{(u+v)}$ proves the asserted norm. [Polarization of the norm beyond units](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/HookFormulaTorsion/CocycleIsCoboundary.lean#L10)

## Sums with isotropic or orthonormal vectors

For this step assume the all-scalar norm and adjoint relations just obtained, the integrality of the endomorphisms, additivity of $b_0$, and the binomial condition on self-adjoint scalars. With finite index sets $I,J$, take $a_j=(a_{j,i})_{i\in I}\in O^I$ and integral input points $t_j$, $j\in J$. Let $j<k$ refer to any total ordering of $J$. Define $Q_i=\sum_{j\in J}^{F}[a_{j,i}]t_j$, where the sum uses the group law $F$. Applying the identity defining $b_0$ repeatedly and using its additivity gives
$$
\phi(Q_i)\sim
\sum_j \phi([a_{j,i}]t_j)+
\sum_{j<k} b_0([a_{j,i}]t_j,[a_{k,i}]t_k).
$$
For each diagonal term use the norm law. For each pair $j<k$ use the adjoint in the first argument and additivity in the second to sum over $i$. Summing the displayed equivalence gives
$$
\sum_i\phi(Q_i)\sim
\sum_j\langle a_j,a_j\rangle\,\phi(t_j)
+
\sum_{j<k}b_0(t_j,[\langle a_j,a_k\rangle]t_k),\qquad
\langle a,b\rangle=\sum_i\bar a_i b_i .
$$
The diagonal vanishes for isotropic vectors, and it contributes $\sum_j\phi(t_j)$ if the columns $a_j$ are orthonormal. This proves the readjustment of the logarithmic factor under a unitary matrix in `UnitaryInv`. [Unitary invariance of the one-variable sum](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/SecondCoefficientNorms/BinomialSeriesCoefficients/UnitaryInverseIdentity.lean#L461) · [Expansion by diagonal and cross terms](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/HookFormulaTorsion/HyperbolicPlaneSplit.lean#L98)

In the hyperbolic case take two families $f_e,f'_e\in O^I$ indexed by a finite set $E$, with
$$
\langle f_e,f_k\rangle=\langle f'_e,f'_k\rangle=0,\qquad
\langle f_e,f'_k\rangle=\delta_{ek}.
$$
For any integral $x_e,y_e$, use the vectors $f_e$ with inputs $x_e$ before all the vectors $f'_k$ with inputs $y_k$. Every diagonal term vanishes, and the only surviving cross terms are those with $e=k$ in the two families. Thus
$$
\sum_{i\in I}\phi\!\left(\sum_e^F\bigl([f_{e,i}]x_e+_F[f'_{e,i}]y_e\bigr)\right)
\sim\sum_e b_0(x_e,y_e).
$$
This is `HyperbolicSum`. The isometry conditions are used on the exact coefficients inside the brackets, before taking the exponential class. [Full hyperbolic sum statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/SecondCoefficientNorms/IsotropicVanish.lean#L101) · [Formal application to the logarithmic class](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/SecondCoefficientNorms/BinomialSeriesCoefficients/UnitaryInverseIdentity.lean#L476)

## The fixed scalars in the unramified application

Use $K_0,p,\sigma$ satisfying `UnrOK` and $O=\{a\in K_0:|a|\le1,\ \sigma^2(a)=a\}$, with $\bar a=\sigma(a)$. The map $\tau$ is inclusion in the coefficient field. The endomorphism condition is the inverse functional equation for $\lambda$. For a fixed integral $z=\sigma z$, its residue $z_0$ satisfies $z_0^p=z_0$, so it has the residue of some integer $n_0\in\{0,\ldots,p-1\}$. Repeatedly apply this to $(z-n_0)/p$, which is integral and fixed by $\sigma$. The partial sums of the digits are nonnegative integers converging to $z$. The binomial functions in $z$ are polynomial over $K_0$, so their values at $z$ are limits of integers and hence integral. For nonnegative integers $n$, $b_0(x,[n]y)\sim n b_0(x,y)$ follows from additivity and $b_0(x,0)=0$. At each degree the coefficients of the difference and of its exponential are polynomial functions of the scalar. Taking limits gives the same equivalence for $z$. For the sum-of-two-units property, $O$ is local with units precisely the norm-one elements. If $\alpha$ has norm $1$, then $(\alpha/2)+(\alpha/2)$ works. If $\lVert\alpha\rVert<1$, use $1+(\alpha-1)$. The element $2$ and its inverse are integral since $p>2$. The norm hypothesis on the units is still required. In the curve application it comes from the chosen CM model. [Fixed coefficients and the two-unit decomposition](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussSumParity/KummerThetaLogarithms/SecondLevelOfNormHolds.lean#L182) · [Applying the norm and adjoint argument to the curve](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/UniformGaussModels/OrthogonalGaussModels/OfClosedInt.lean#L108)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
