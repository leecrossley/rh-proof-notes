# A theta intertwiner refines the weighted coset sum

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $U$ be an $\mathcal O_E$-module for a number field $E$, $V$ a complex vector space, and $j:U\to V$ an injective additive map. Let $H$ be a Hermitian form on $V$, linear in its first variable, with alternating pairing $A(x,y)=\operatorname{Im}H(x,y)$. For $\alpha:V\to\mathbb C$ define
$$
(T_x F)(z)=F(z+x)e^{-\pi H(z,x)-\frac{\pi}{2}H(x,x)},\qquad W(x)=\alpha(x)T_x .
$$
On a subgroup $L$ where $\alpha$ is a semicharacter, its values on $L$ are $\pm1$, and $\alpha(x+y)=\alpha(x)\alpha(y)e^{\pi i A(x,y)}$ for $x,y\in L$. If $L$ is self-dual for $A$, then $A(x,y)\in\mathbb Z$ on $L$. In these circumstances $W(x)W(y)=W(x+y)$ on $L$. Indeed the exponential in $T_xT_y$ differs from the one in $T_{x+y}$ by $e^{-\pi i A(x,y)}$, and $e^{-\pi i A(x,y)}=e^{\pi i A(x,y)}$ for integral $A(x,y)$. The same semicharacter identity at $0$ and at $x,-x$ gives $\alpha(0)=1$ and $\alpha(-x)=\alpha(x)$ on $L$.

Let $B,L_1,L_2\subset U$ be submodules with
$$
B\cap L_2\subseteq L_1,\qquad
L_1=(L_1\cap B)+(L_1\cap L_2),\qquad
[B:B\cap L_2]<\infty.
$$
Assume $j(B)$ and $j(L_1)$ are self-dual for $A$ and $\alpha$ is a semicharacter on each. Let $\theta:V\to\mathbb C$ satisfy $W(j(l))\theta=\theta$ for $l\in L_2$, and suppose $\Xi:U\to\mathbb C$ is invariant on $B$ under translation by $B\cap L_1$. With sums over any chosen representatives, put
$$
\begin{aligned}
(\mathcal I_{L_2\to L_1}\theta)(z)
&= [L_1:L_1\cap L_2]^{-1/2}
\sum_{y\in L_1/(L_1\cap L_2)}(W(j(y))\theta)(z),\\
C_B(L,F)(z)
&=\sum_{t\in B/(B\cap L)}\Xi(t)\big(W(-j(t))F\big)(z).
\end{aligned}
$$
The relevant sums are finite and independent of the representatives, and
$$
C_B(L_1,\mathcal I_{L_2\to L_1}\theta)
=[L_1:L_1\cap L_2]^{-1/2}C_B(L_2,\theta).
\tag{1}
$$

### Representatives for the two quotients

Choose representatives $r$ for $B/(B\cap L_1)$ and $y$ for $(B\cap L_1)/(B\cap L_2)$. These are finite by the first and third hypotheses. The $y$'s also represent $L_1/(L_1\cap L_2)$ because every element of $L_1$ is a sum of an element of $B\cap L_1$ and an element of $L_1\cap L_2$. Their kernel under this change of quotient is exactly $B\cap L_2$. The complete representative system in $B/(B\cap L_2)$ can be taken to be all $r-y$. In fact each element of $B$ differs from an $r$ by an element of $B\cap L_1$; its negative can then be replaced by a $y$ modulo $B\cap L_2$. If two of the differences represent the same class, they first give equal classes of $r$ modulo $B\cap L_1$, then equal classes of $y$ modulo $B\cap L_2$.

The summand $W(j(y))\theta$ is constant under replacing $y$ by another representative, since $W$ is multiplicative on $j(L_1)$ and the difference is in $L_2$. The same argument on $j(B)$ works for $C_B(L_2,\theta)$ because $B\cap L_2\subseteq B\cap L_1$. Also $\mathcal I_{L_2\to L_1}\theta$ is fixed by $W(j(L_1))$. Multiplication by $W(j(l))$ for $l\in L_1$ translates the representatives bijectively in the quotient and hence preserves the average. This proves representative independence for the left side of (1) as well.

### Multiplying the two translations

Insert the $y$-sum into $C_B(L_1,\mathcal I_{L_2\to L_1}\theta)$. Both $r$ and $y$ belong to $B$, giving
$$
W(-j(r))W(j(y))\theta=W(-j(r-y))\theta,\qquad
\Xi(r)=\Xi(r-y).
$$
The double sum is therefore the refined sum over $r-y$ on the right of (1), times the original inverse square root. Thus changing the theta vector and refining the quotient require only the one index of $L_1\cap L_2$ in $L_1$. This is the step used twice in reducing a moved kernel to a common theta sum.

### Lean correspondence

- [`altE` and `opU`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/IsSemiChar.lean#L19) give the operators, [`IsSemiChar`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/IsSemiChar.lean#L39) gives the sign law, and [`inter`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/IsSemiChar.lean#L65) fixes the direction of the index.
- [`alpha_opU_add`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/IntegralDensEqZero.lean#L94) gives the normalized multiplication law on a self-dual subgroup.
- [`alpha_neg`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/IsTransvSurjInv.lean#L66) justifies the sign convention in `cosSum`. [`cosSum_inter`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/IsTransvSurjInv.lean#L92) proves (1) by constructing the two new transversals. The function `cosSum` uses $\alpha(j(t))$ with $T_{-j(t)}$, which is $W(-j(t))$ because the semicharacter is even on $j(B)$.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
