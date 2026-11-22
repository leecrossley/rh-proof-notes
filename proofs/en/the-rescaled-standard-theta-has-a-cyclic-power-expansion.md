# The rescaled standard theta has a cyclic power expansion

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $p>2$ be prime and $K$ a characteristic-zero ultrametric field with $v(p)=1$, containing $\varpi$ with $\varpi^{p^2-1}=p$. Write $R$ for its valuation ring. Use $d\ge1$ and $S=\mathbb Z/(2d)\mathbb Z$. A series belongs to the class of a zero-constant series $H\in R[[Y]]$ if it can be written coefficientwise as
$$
\sum_{i\ge0}p^{-i}H^i U_i,\qquad U_i\in R[[Y]].
\tag{1}
$$
We show how the standard theta phase yields the class used in [the height-one estimate](hasse-derivatives-explain-the-height-one-orbit-gain.md).

Use the two-variable series
$$
A(x,y)=\sum_{0\le i\le j}\frac{x^{p^{2i}}y^{p^{2j+1}}}{p^{i+j+1}},
\qquad
G(x,y)=c A(x,y)-c' A(y,x),\qquad c,c'\in R .
$$
The required normal form is that the two-variable exponent is congruent to $G$ modulo exponents with integral exponential. In the source $c'=\sigma(c)$, where $\sigma$ is unramified Frobenius. The [normal-form proof](two-additivity-laws-force-the-triangular-biextension.md) obtains this from the two additivity laws and the torus condition. For each row and column index $(a,b)$ and each frame index $r=1,\ldots,d$, introduce one copy of the phase, and allow any integral multiplicative correction $U$ on all these pairs. The congruence allows replacement of the exponent by $G$ after absorbing its integral unit in $U$.

Write $\ell(t)=\sum_{j\ge0}t^{p^{2j}}/p^j$ and $\lambda(t)=\ell(\varpi t)/\varpi$. This is integral with linear coefficient $1$, since the coefficient at degree $p^{2j}$ is $p^{1+p^2+\cdots+p^{2j-2}-j}$ for $j\ge1$. At $j=1$ this coefficient is $1$, and for $j\ge2$ it is divisible by $p$. Thus modulo $p$, $\lambda(t)=t+t^{p^2}$. The inverse $\mu$ exists over $R$ by recursion. Its reduction is $\sum_{i\ge0}(-1)^i t^{p^{2i}}$, as follows by substituting into $t+t^{p^2}$ and using the $p^2$-power map in the residue ring $R/pR$.

Take integral arrays $\omega_{r,s},\widetilde\omega_{r,s}$ on $r,s$ with
$$
\omega_{r,s}^p\equiv\omega_{r,s+1},\quad
\widetilde\omega_{r,s}^p\equiv\widetilde\omega_{r,s+1}\pmod{pR},\qquad
\sum_r\widetilde\omega_{r,s}\omega_{r,t}=\mathbf 1_{s=t}
\quad(s,t\text{ of the same parity}).
\tag{2}
$$
For a fixed entry $(a,b)$, the rescaled phase is obtained by substituting $x=\varpi\mu(L_r)$, $y=\varpi\mu(M_r)$, where $L_r=\sum_{s\ {\rm even}}\widetilde\omega_{r,s}Y_{s,a,b}$ and $M_r=\sum_{s\ {\rm odd}}\omega_{r,s}Y_{s,a,b}$. These are the Frobenius trace-dual coordinates in the source.

First rescale $G(x,y)$ by $\varpi$ in each variable. The term $i=j=0$ becomes
$$
\frac{\varpi^{p+1}}p\,(c\,xy^p-c'x^py).
$$
Each remaining coefficient of the rescaled $G$ has valuation at least $1/(p-1)$. Indeed for $j\ge1$ and $i\le j$ its lower bound is
$$
\frac{p^{2i}+p^{2j+1}}{p^2-1}-(i+j+1)\ \ge\ \frac1{p-1}+p-2.
$$
The expression is increasing in each of $i,j$ and the smallest value in this range occurs at $i=0,j=1$. These terms exponentiate to an integral correction: in the $h$-th term of the formal exponential the coefficient valuations are at least $h/(p-1)-v_p(h!)\ge0$. The same is true after the integral substitution by $\mu$ at the linear forms. For the leading term, $\varpi^{p+1}$ has valuation $1/(p-1)$, so $\varpi^{(p+1)i}/i!$ is integral. Expanding its exponential therefore gives the power class (1) for the sum of the leading polynomials $c\,\mu(L_r)\mu(M_r)^p-c'\,\mu(L_r)^p\mu(M_r)$ over all $r,a,b$.

We can replace the series defining a class by any congruent series modulo $p$, provided both have zero constant term. In fact if $H_1=H+pV$, write $p^{-i}H_1^i=\sum_{k\le i}p^{-k}H^k\binom{i}{k}V^{i-k}$. The new multiplier at $H^k$ is integral, and the sum defining it is coefficientwise finite since $V$ has zero constant term. Integral multiplication also preserves the class. Thus it suffices to simplify the leading polynomial sum modulo $p$.

With $S_s=\sum_{j\ge0}(-1)^jY_{s-2j,a,b}^{p^{2j}}$ as in the height-one estimate, the two inverses reduce to $\mu(L_r)\equiv\sum_{s\ {\rm even}}\widetilde\omega_{r,s}S_s$ and $\mu(M_r)\equiv\sum_{t\ {\rm odd}}\omega_{r,t}S_t$. Indeed raising the linear forms to $p^{2j}$ and using (2) shifts the coefficient index forward by $2j$. Then
$$
\sum_r\mu(L_r)\mu(M_r)^p\equiv
\sum_{\substack{s\ {\rm even}\\t\ {\rm odd}}}
\Big(\sum_r\widetilde\omega_{r,s}\omega_{r,t+1}\Big)S_sS_t^p
=\sum_{t\ {\rm odd}} S_t^p S_{t+1}.
$$
The other product gives the sum over even $t$, by the same identities with the factors interchanged. Consequently the phase produces (1) with
$$
H=\sum_{s,a,b}u_s S_s(Y_{a,b})^p S_{s+1}(Y_{a,b}),\qquad
u_s=\begin{cases}c,&s\text{ odd},\\-c',&s\text{ even}.\end{cases}
$$
This is the claimed shape. The coefficient extraction for the rescaled series adds $\rho D$ to the original valuation at total degree $D$, since $v(\varpi)=\rho=1/(p^2-1)$.

**Lean correspondence.** The leading term calculation is [`RescaleExact_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/TopsChoicePartB.lean#L386), and invariance of the class is in the same file at [`classChange_statement`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/TopsChoicePartB.lean#L148). The trace comparison and combination with the rescaled logarithm are [`two_sums`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/TheoremSFromKOneOf.lean#L606) and [`ThmSCore_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/TheoremSFromKOneOf.lean#L682). The input congruence `BetaIsG` and the standard phase are assembled in [`theorem_s_uniform`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/OmegaOfTraceDuality.lean#L31), followed by the generic Gauss coefficient estimate in [`kernel_bounds_generic_of_uniform`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/EGaussK.lean#L222).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
