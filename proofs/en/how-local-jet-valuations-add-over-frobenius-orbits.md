# How local jet valuations add over Frobenius orbits

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

The local determinant estimate uses variables on one Frobenius orbit. At a rational prime the original theta series contains variables from many orbits. Its integral factor can mix all of them. This is why taking the product of the series obtained by restriction would not suffice. The gluing proof expands the integral factor in monomials to the degree tested by the determinant.

## Setting and statement

Let $p$ be prime and work over $\mathbb C_p$ with $v(p)=1$. Let $\mathcal P$ be a finite set with a Frobenius permutation whose orbits all have the same length $d\ge2$, with $d$ even. Choose representatives $R$. We write the $s$th place on the orbit of $r$ as $z_{r,s}$ for $s\in\mathbb Z/d\mathbb Z$. Fix matrix dimensions $N_0,N_1$ and put $Y_{r,s,a,b}=Y_{z_{r,s},a,b}$ for $1\le a\le N_0$ and $1\le b\le N_1$. The coordinate logarithms are
$$
\mathcal L_{r,s,a,b}(Y)=\sum_{j\ge0}p^{-j}Y_{r,s-2j,a,b}^{p^{2j}} .
$$
They preserve the orbit and matrix indices. For every $r$ let $B_r$ be a series in its block of variables with constant term zero. In the application it is the signed sum over $(a,b)$ of copies of the scalar biextension series $b_r(Y_{r,s,a,b}:s\in\mathbb Z/d\mathbb Z)$. The sign is $+1$ or $-1$. Take $\eta\in\mathbb C_p^\times$ of norm one. A global expansion is an identity
$$
\Theta(\eta\mathcal L(Y))=U(Y)\exp\!\left(\sum_{r\in R}B_r(\mathcal L(Y))\right),
\qquad v([Y^n]U)\ge0\quad\text{for all }n.
$$
This is `ThetaExpansionAllPlaces`. The conditions `BeOK` include the vanishing of the constant term of each $b_r$ via positive bidegrees. [Signed orbit series and global expansion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/Divisibility/OrbitPlaces.lean#L177)

Give every place a Young diagram. For each choice of column indices, take the product of the determinant operators of the [local jet estimate](from-orbit-valuations-to-the-prime-power-count.md). Write it as $P(X,Y)=\prod_{r\in R}P_r(X_r,Y_r)$, according to the orbits. The auxiliary variables $X_r$ and derivative variables $Y_r$ from different orbits are disjoint. For any such operator let
$$
P[\Theta](X)=P(X,\partial_Y)\Theta(0),
$$
which uses $\kappa![Y^\kappa]\Theta$ for the term $Y^\kappa$. A jet bound with exponent $\beta$ means that every coefficient of this polynomial has valuation at least $\beta$ for every allowed column choice.

Assume that for each $r$ every series $\Theta_r$ satisfying the single-orbit expansion
$$
\Theta_r(\eta\mathcal L_r(Y_r))=V_r(Y_r)\exp(B_r(\mathcal L_r(Y_r)))
$$
with any integral $V_r$ has jet bound $\beta_r$ on the diagrams of that orbit. Then every $\Theta$ satisfying the global expansion has jet bound $\sum_r\beta_r$. In addition, setting all variables outside one orbit to zero in $\Theta$ gives a solution of the single-orbit expansion with the restricted $U$. These are the gluing and restriction results `OrbitsAddLowerBound` and `OrbitRestriction`, expressed with the Frobenius orbits already labeled. [The two orbit statements](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/Divisibility/OrbitPlaces.lean#L208)

## Restriction to one orbit

For fixed $r$, evaluate every variable in a different orbit at zero. This sends all its logarithms to zero, so it commutes with the substitution on the remaining block. The other $B_{r'}$ have zero constant term and disappear from the exponent. Every coefficient of the restricted $U$ is an original coefficient of $U$ and remains integral. Relabel the variables by $s$ to obtain the asserted single-orbit identity. [Proof of restriction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/OrbitJetRestriction/OrbitRestriction.lean#L11) · [Restriction commutes with the logarithmic substitution](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/OrbitJetRestriction/RestrictedJetEquation.lean)

## Split a monomial, then add the mixed terms

The substitution $Y\mapsto\eta\mathcal L(Y)$ is a formal change of coordinates. Its linear part is $\eta$ times the identity, and the higher terms have degree at least two. To invert it one solves recursively for the coefficients of the inverse by degree. Both it and its inverse preserve the ideal of series with every coefficient of total degree below $n$ zero, for every $n$. The same facts hold on each orbit independently.

For any global monomial $Y^m$, let $m_r$ be its exponent vector restricted to orbit $r$, so $Y^m=\prod_rY_r^{m_r}$. Solve in each orbit
$$
F_{r,m_r}(\eta\mathcal L_r(Y_r))
=Y_r^{m_r}\exp(B_r(\mathcal L_r(Y_r))).
$$
Existence is the coordinate inversion just described. The monomial $Y_r^{m_r}$ has integral coefficients, so $F_{r,m_r}$ has jet bound $\beta_r$. Let $Q_m=\prod_r F_{r,m_r}$ in the disjoint blocks. The exponential of a finite sum of zero-constant formal series is the product of their exponentials, by the binomial formula degree by degree. Thus the substitution sends $Q_m$ to $Y^m\exp(\sum_r B_r(\mathcal L_r(Y_r)))$.

For the full determinant operator the disjointness gives
$$
P[Q_m](X)=\prod_{r\in R} P_r[F_{r,m_r}](X_r).
$$
Indeed a monomial of $P$ is differentiated separately in each block, and each factorial is the product of its block factorials. A coefficient in the product is the product of the uniquely specified block coefficients, with valuation at least $\sum_r\beta_r$. This supplies the bound for every $Q_m$. [Monomial solutions and their product](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/OrbitJetDegreeBound/ConstantCoeffZeroOfBoundGeneral.lean#L66) · [Product under substitution](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/OrbitJetDegreeBound/ConstantCoeffZeroOfBoundGeneral.lean#L76)

For a given $P$, choose $n$ greater than the largest total degree in its derivative variables. Write $U_{<n}=\sum_{|m|<n}u_mY^m$ for the finite truncation and $\Theta'=\sum_{|m|<n}u_mQ_m$. After the coordinate substitution, $\Theta-\Theta'$ equals $(U-U_{<n})\exp(\sum_r B_r(\mathcal L_r(Y_r)))$. All its terms have degree at least $n$, since multiplication by a formal series cannot lower the order of vanishing. The inverse coordinate substitution preserves this property. Hence $P[\Theta]=P[\Theta']$. Since $v(u_m)\ge0$, every coefficient of the finite sum on the right is a sum of terms each of valuation at least $\sum_r\beta_r$. The ultrametric inequality gives the result.

This is the step that turns the bound at each individual orbit into a divisibility estimate for the entire local jet. Its uniformity in the integral factor is essential. In the [determinant bound](generic-frames-for-the-determinant-jet.md), the same lower bound applies to all integral factors, so it supplies exactly that hypothesis. [Proof of gluing by truncation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/OrbitJetDegreeBound/ConstantCoeffZeroOfBoundGeneral.lean#L90)

The expansion and the individual orbit bounds are inputs to this statement. The proof applies to arbitrary such expansions, and it does not require the individual orbit bounds to have equal exponents or even positive exponents.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
