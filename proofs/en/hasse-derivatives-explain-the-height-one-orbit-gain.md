# Hasse derivatives explain the height-one orbit gain

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $p>2$ be prime, $v(p)=1$, and work over a nonarchimedean coefficient field of characteristic zero with this valuation. Let $S=\mathbb Z/(2d)\mathbb Z$, $d\ge1$, and $T\subset S$ the top places. Use $r_0\times r_1$ matrices $Y_s$ and integral coefficients $u_s$. Define
$$
S_s(Y_{a,b})=\sum_{j\ge0}(-1)^j Y_{s-2j,a,b}^{p^{2j}},\qquad
H(Y)=\sum_{s,a,b}u_s S_s(Y_{a,b})^p S_{s+1}(Y_{a,b}).
$$
Suppose a series $\Theta_0$ lies in the class
$\Theta_0=\sum_{i\ge0}p^{-i}H^i U_i$, with each $U_i$ integral. The sum is interpreted coefficientwise since $H(0)=0$. We derive the local estimate for the product of minors on this rescaled series. The actual theta-series argument must supply this class identity.

For each $s\in T$ use one integral row vector $\xi_s$ in the height-one factors of the determinant operator. The number of factors in column $b$ is $e_{s,b}$, and $\alpha_s=\sum_b e_{s,b}$, zero for $s\notin T$. The other factors are minors of integral linear row substitutions at prescribed places, and their product $Q$ has total degree $L_s$ at place $s$, counting the sum of their heights. Let $C_s$ be their number at $s$. Put $D=\sum_s(\alpha_s+L_s)$. The formal coefficient pairing sends a monomial $Y^m$ to $m![Y^m]\Theta_0$. Denote the result by $J$ when applied to $Q\prod_{s,b}(\sum_a\xi_{s,a}Y_{s,a,b})^{e_{s,b}}$.

Introduce top variables $X_{s,b}$ by making the linear substitution $Y_{s,a,b}\mapsto Y_{s,a,b}+\xi_{s,a}X_{s,b}$ on $T$, leaving the other places unchanged. The factorial pairing is adjoint to the transpose linear substitution, as follows by expanding $(Y+\xi X)^m$ and using $\binom{m}{j}j!(m-j)!=m!$. Thus $J$ is the pairing of $X^eQ(Y)$ against the substituted series. We only need terms up to degree $D$.

Modulo $p$, powers of degree a power of $p$ distribute over the linear substitution. Expand $S_s^pS_{s+1}$ there. A monomial uses a $p^{2j+1}$-st power at $q=s-2j$ and a $p^{2k}$-th power at $q'=s+1-2k$. They have opposite place parity and the shifts satisfy $q+2j+1=q'+2k$ in $S$. There are just three kinds of terms after separating the top and the residual $Y$ variables.

- Pure top terms use one power at each of $q,q'$, both in $T$.
- Terms linear in $Y$ take the first power in a top variable and $k=0$ for the second. For the source top place $q$, odd shift $h=2j+1$ and column $b$, they are an integral scalar times $X_{q,b}^{p^h}$ times a linear form on column $b$ of $Y_{q+h}$. Its row direction consists of the coefficients $\xi_q^{p^h}$. Summation over the row index $a$ gives precisely this one direction.
- All other monomials that use $Y$ have $Y$-degree at least $p$.

The difference between this sum and the substituted series $H$ is $p$ times an integral series, since each coefficient was computed modulo $p$. This gives the needed decomposition at all degrees up to $D$, with finitely many possible powers.

Expand $p^{-i}H^iU_i$ multinomially. For a nonzero term of the resulting pairing, let $a$ be the total number of pure top terms used, $b_{s,h,b'}$ the multiplicity of a linear term from top place $s$, shift $h$, column $b'$, and $b_0=\sum_{s,h,b'}b_{s,h,b'}$. Write $c$ for the number of terms of $Y$-degree at least $p$. Copies of the remainder $p$ times an integral series cancel their powers of $p^{-1}$. The top consumption by the first two kinds must fit coordinatewise in $e_{s,b'}$.

Define the directional Hasse derivative of $Q$ with given multiplicities $b_{s,h,b'}$ as the coefficient of the corresponding parameter monomial in $Q(Y+\sum_k T_k v_k)$, with $v_k$ the indicated row directions in their destination columns. Under the factorial pairing multiplication of the series by the corresponding linear forms in $Y$ is adjoint to this derivative times $\prod_k b_k!$. This follows by differentiating the translated monomials, or applying the linear substitution identity and extracting each parameter. The multinomial coefficient in the expansion contains the factor needed to replace $\prod_k b_k!$ by $b_0!$ times an integer: partition its count first into the $b_0$ linear factors and the other kinds and then count the assignments among the $b_0$ factors. The derivative has integral coefficients and, if nonzero, total degree $\sum_s L_s-b_0$. For a contributing monomial $Y^m$, $\sum_{a,b'}m_{s,a,b'}\le L_s$, and $pc\le |m|$ because the remaining $c$ factors each use at least $p$ residual $Y$-variables. The term in the pairing therefore has valuation at least
$$
v(e!)+v(b_0!)+v(m!)-(a+b_0+c).
\tag{1}
$$
All remaining coefficients used to extract this term are integral. As the pairing is a finite sum at degree $D$, it is enough to lower bound (1) for every contributing selection.

For a fixed $s,h$, put $i_{s,h}=\sum_{b'}b_{s,h,b'}$. Each such term needs $p^h$ top powers at $s$, so $p^h i_{s,h}\le\alpha_s$. When $i_{s,h}>0$, the Hasse derivative must hit a minor at $s+h$ once for each of these $i_{s,h}$ occurrences. In any one affected determinant, two chosen columns from this group would be proportional, since before the common row map they use the same direction $\xi_s^{p^h}$. In a single column a determinant is linear, so it cannot be hit twice there either. A nonzero coefficient is therefore possible only if $i_{s,h}\le C_{s+h}$. This is where the capacity in the positive part enters.

For the pure top terms, charge each occurrence to the place with the larger exponent $p^A$. If the other exponent is $p^{A'}$, then $A-A'>0$ is odd and the other place is reached by shift $A-A'$ from the charged place. The least positive shift $\delta$ between the same two places is at most $A-A'$ and is still odd, since the period is even. It lies in the finite set $D_s^{\rm exc}=\{\delta<2d:\delta\text{ odd},\ s+\delta\in T\}$ at the charged place $s$. Write $c_{s,h}$ for the total charge at $(s,h)$. Each charge consumes at least $p^h$ top powers at $s$, and so $p^h(c_{s,h}+i_{s,h})\le\alpha_s$, since those charged and mixed uses come from the same coordinatewise consumption bound.

Set $\rho=1/(p^2-1)$, $\gamma=p/(p^2-1)$, and $c_p=1/(p-1)=\rho+\gamma$. Using the digit bound for factorials, the three positive terms in (1) have sum at least $c_pD-\mathcal D$, where
$$
\mathcal D=\sum_s(r_1\ell_p(\alpha_s)+r_0r_1\ell_p(L_s))+\sum_{s\in T}\ell_p(\alpha_s)^2.
$$
For $e!$ and $m!$, use the bound on their entries by $\alpha_s,L_s$, respectively. For $b_0!$, its valuation is at least $\sum_{s,h}v(i_{s,h}!)$, since the ratio is a multinomial integer. At most $\ell_p(\alpha_s)$ shifts have positive $i_{s,h}$, by $p^h\le\alpha_s$, and each $\ell_p(i_{s,h})\le\ell_p(\alpha_s)$, yielding the squared loss. The main terms sum to $c_pD$ because $|m|+b_0=\sum_sL_s$. Finally $c\le p^{-1}\sum_s L_s\le\gamma\sum_s L_s$. Therefore every term has valuation at least
$$
\rho D+\gamma\sum_s\alpha_s-\mathcal D-\sum_{s,h}(c_{s,h}+i_{s,h}).
$$
The identity $\gamma=\sum_{h\ge1,\ h\ {\rm odd}}p^{-h}$ allows summation over shifts. For excluded shifts $c_{s,h}+i_{s,h}\le\alpha_s/p^h$. For the other shifts $c_{s,h}=0$ and $i_{s,h}\le\min(\alpha_s/p^h,C_{s+h})$. This gives
$$
v(J)\ge \rho D-\mathcal D+
\sum_{s\in T}\sum_{\substack{h\ge1\ {\rm odd}\\h\notin D_s^{\rm exc}}}
(\alpha_s/p^h-C_{s+h})_+ .
$$
If $\Theta_0(Y)=\Theta(\varpi Y)$ where $v(\varpi)=\rho$, the rescaling has added exactly $\rho D$ to the valuation of the jet. Removing it gives the desired height-one estimate for the original series.

**Lean correspondence.** The rescaled class and $H$ are [`InClass`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/OddLogRelation.lean#L76) and [`hhS`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/CyclicPowerClassOfExpEquiv.lean#L85). The decomposition, factorial pairing, and capacity are [`decomposition_of_hh`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/EDecomp.lean#L498), [`TermBound_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/NormNatCastLeOfDvd.lean#L495), and [`HitsCapPos_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/MinorProdBlockDegree.lean#L36). The valuation loss and charged gain are [`gainFactorialInequality`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/ABArith.lean#L103) and [`entryExcessBound_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/EntryAOneParity.lean#L177).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
