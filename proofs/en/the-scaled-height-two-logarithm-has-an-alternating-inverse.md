# The scaled height-two logarithm has an alternating inverse

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $p$ be prime, $K$ a field of characteristic zero containing $\varpi$ with $\varpi^{p^2-1}=p$, and
$$
\ell(T)=\sum_{j\ge0}\frac{T^{p^{2j}}}{p^j}.
$$
Put $\lambda(T)=\ell(\varpi T)/\varpi$. There is a unique zero-constant inverse $\mu\in K[[T]]$. Its coefficients are integers in $K$, and
$$
\mu(T)\equiv\sum_{j\ge0}(-1)^jT^{p^{2j}}\pmod{p\mathbb Z[[T]]}.
$$
This is the comparison needed when the normal phase is expressed in the served slot frame. [The height-two logarithm](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/OddLogRelation.lean#L13) · [`sx_mu_alt_int`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/SxMuAltInt.lean#L187)

Indeed $p^{2j}-1=(p^2-1)\sum_{a=0}^{j-1}p^{2a}$, so the coefficient of $T^{p^{2j}}$ of $\lambda$ is the integer $p^{\sum_{a<j}p^{2a}-j}$. The exponent is zero for $j=0,1$, and positive for $j\ge2$. The constant term is zero and the linear coefficient is one. Solving $\lambda(\mu(T))=T$ degree by degree gives an integral inverse: the coefficient of $\mu$ of degree $n>0$ occurs with coefficient one, and every higher-power contribution uses coefficients of smaller degree. This also proves uniqueness. [Divisibility of the scaled coefficients](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/SxMuAltInt.lean#L13) · [Integral composition inverse](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/IntRPsubst.lean#L124)

Reducing modulo $p$ gives $\lambda(T)=T+T^{p^2}$ in $\mathbb F_p[[T]]$. Write $A(T)=\sum_{j\ge0}(-1)^jT^{p^{2j}}$. Frobenius in characteristic $p$ gives $A+A^{p^2}=T$: the two coefficients in each degree $p^{2j}$ for $j\ge1$ cancel. This includes $p=2$, where opposite signs are equal and add to zero. The reduced inverse is unique because its linear coefficient in the defining equation is one. Therefore the difference of $\mu$ and $A$ has coefficients divisible by $p$. In any coefficient ring containing $\mathbb Z$, the same congruence holds and remains valid after every zero-constant integral substitution. [Coefficientwise divisibility by the prime](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/SxMuAltInt.lean#L325) · [Use in a component](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/ThLinKConst.lean#L113)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
