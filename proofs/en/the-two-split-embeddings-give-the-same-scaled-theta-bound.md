# The two split embeddings give the same scaled theta bound

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Let $\Lambda\subset\mathbb C^n$ be a full lattice, stable under the quadratic CM integer ring in the construction, and self-dual for the alternating form $e$ of the positive definite Hermitian form $H$. Use the quadratic semicharacter $\alpha$ of this lattice and a theta section $\theta$ with $\alpha(b)U_b\theta=\theta$ for $b\in\Lambda$. Here $U_b$ denotes the Heisenberg translation, with convention
$$
U_xU_y=\exp(-\pi_{\mathbb R} i e(x,y))U_{x+y}.
$$
The notation $\pi_{\mathbb R}$ distinguishes the real constant from the CM integer $\pi$ below. Work under the good CM curve and normalized theta hypotheses of the standard kernel, at an odd prime $p$ away from the quadratic discriminant. Use the chosen comparison $\iota:\mathbb C\to\mathbb C_p$ of coefficient fields to measure norms. Assume $\pi,\bar\pi$ are conjugate quadratic integers with $\pi\bar\pi=p$. Take representatives $S_a,S_b$ of
$$
(\bar\pi/\pi)\Lambda/\bar\pi\Lambda,\qquad
\Lambda/\bar\pi\Lambda
$$
respectively. Let $Q=p^n$ and let $\Psi$ have $|\iota\Psi(b)|\le1$ on $S_b$. Set
$$
\widehat\Psi(a)=Q^{-1}\sum_{b\in S_b}\Psi(b)\exp(-2\pi_{\mathbb R}i e(b,a)),\qquad
G=\sum_{a\in S_a}\widehat\Psi(a)\alpha(a)U_a\theta .
$$
For finitely many $k$, suppose $r_k\in\mathbb C,\ t_k\in\mathbb C^n$ satisfy $|\iota r_k|\le1$ and $N t_k\in\Lambda$ for a positive integer $N$ prime to $p$. Use finitely many frame directions $v_j$ sending the CM curve period lattice into $\Lambda$ by scalar multiplication. For each differentiation variable $z_i$ let the direction over $\mathbb C_p$ be $\sum_j\iota(v_j)A_{ji}$, with $|A_{ji}|\le|\iota\bar\pi|$. Then every derivative at zero of the $p$-adic Taylor series of $Q\sum_k r_k U_{t_k}G$ after this linear substitution is integral. A derivative of multi-index $m$ means $m!$ times the corresponding Taylor coefficient.

The input from torsion translates, `EtLoc`, is the following. Under the same good curve and normalized theta hypotheses, take finite translates $\theta_\ell=U_{w_\ell}\theta$ with $\beta w_\ell,M w_\ell\in\Lambda$, where $\beta$ is a CM integer of $p$-adic norm one and $M>0$ an integer. For integral coefficients $c_\ell$ and any matrix of frame coefficients bounded in norm by $|M|_p$, all derivatives of $\sum_\ell c_\ell \theta_\ell$ after the induced linear substitution are integral. The [fourfold transfer proof](a-prime-to-p-lattice-index-transfers-scaled-derivatives.md) gives this input, which is used with $M=Np$ on both sides of the split.

## When the conjugate CM integer is a nonunit

The trace $\pi+\bar\pi$ is prime to $p$ by the [split lattice calculation](the-split-prime-part-of-the-heisenberg-cosets.md), so at least one of the two integers has norm $1$. Since their norm product is $|p|_p$, when $|\iota\bar\pi|<1$ we have $|\iota\pi|=1$ and $|\iota\bar\pi|=|p|_p$.

Write $a=(\bar\pi/\pi)\ell$ with $\ell\in\Lambda$, for $a\in S_a$. Then $p a=\bar\pi^2\ell\in\Lambda$ and $\pi a=\bar\pi\ell\in\Lambda$. Thus $p e(b,a)\in\mathbb Z$ for $b\in S_b$. The phases in $Q\widehat\Psi(a)$ are roots of unity and have norm $1$, so $Q\widehat\Psi(a)$ is integral. Because multiplication by $\bar\pi/\pi$ preserves $H$, the quadratic phase $\alpha(a)$ equals $\alpha(\ell)$, a sign. The Heisenberg multiplication law rewrites $U_{t_k}U_a\theta$ as $U_{t_k+a}\theta$ times the phase $\exp(-\pi_{\mathbb R}i e(t_k,a))$, also a root of unity since $Np\,e(t_k,a)$ is an integer. Thus $Q\sum_k r_kU_{t_k}G$ is a sum of ordinary translates with integral coefficients. Each translation point $t_k+a$ is sent into $\Lambda$ by both $N\pi$ and $Np$. Use $\beta=N\pi$ in `EtLoc`. The frame coefficients satisfy $|A_{ji}|\le|p|_p=|Np|_p$, giving the conclusion.

## When the conjugate CM integer is a unit

Now $|\iota\bar\pi|=1$ and $|\iota\pi|=|p|_p$. Set $s=\pi/\bar\pi$, a complex isometry for $H$. The scalar change of the theta lattice used in Lean gives, for $\theta\ne0$, a complex number $c\ne0$ such that
$$
\theta(sz)=\frac c{\sqrt Q}\sum_{a\in S_a}\alpha(a)U_a\theta(z),
\qquad
c^8=(\bar\pi/\pi)^{4n}.
\tag{1}
$$
For this input put $\delta=\bar\pi/\pi$. The [split lattice calculation](the-split-prime-part-of-the-heisenberg-cosets.md) gives $\Lambda\cap\delta\Lambda=\bar\pi\Lambda$ and index $Q$, and the quadratic phase is invariant under $\delta$ since $\delta$ is an isometry. For the one-dimensional theta space, the [unitary scalar calculation](the-unitary-theta-scalar-from-a-cayley-gaussian.md) gives (1) because $\det\delta=\delta^n$. The one-dimensionality for the normalized kernel follows from its [theta line description](comparing-two-fourfold-theta-kernels.md). To apply it, first take $U_b$ of (1) for $b\in\Lambda$. The isometry changes $U_b$ on $\theta(sz)$ to $U_{sb}$ on $\theta$ at $sz$. On the right, the commutator identity and $\alpha(b)U_b\theta=\theta$ give the additional factor $\exp(-2\pi_{\mathbb R}i e(b,a))$ after multiplication by $\alpha(b)$. Weight by $\Psi(b)$ and sum over $S_b$. Comparing with the definition of $\widehat\Psi$ yields
$$
G(z)=D^{-1}\sum_{b\in S_b}\Psi(b)\alpha(b)U_{s b}\theta(sz),\qquad D=c\sqrt Q .
\tag{2}
$$
By (1), $D^8=(\bar\pi/\pi)^{4n}p^{4n}=\bar\pi^{8n}$. Hence $|\iota D|=1$ in this case.

The translate $U_{t_k}G$ in (2) is a sum of $U_{s(t_k+b)}\theta$ evaluated at $sz$. The coefficient is $D^{-1}\Psi(b)\alpha(b)$ times a Heisenberg phase, and multiplication by $r_k$ leaves it integral. The phase is a root of unity since $N e(s t_k,s b)=N e(t_k,b)\in\mathbb Z$. Each new point $w=s(t_k+b)$ satisfies $N\bar\pi w=N\pi(t_k+b)\in\Lambda$ and $Np\, w=N\pi^2(t_k+b)\in\Lambda$. Thus $\beta=N\bar\pi$ is a unit as required. The evaluation at $sz$ replaces $A_{ji}$ by $\iota(s)A_{ji}$, of norm at most $|p|_p=|Np|_p$. Applying `EtLoc` gives integral derivatives already for the unscaled sum. Multiplication by $Q$ preserves them. If $\theta=0$, the original sum vanishes, which also gives the result.

## Lean correspondence

- [`SelfDualLatticeThetaPadicIntegrality`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/AlgebraicTheory/StatementD.lean#L98) gives the full scaled conclusion; nearby are `XiEt`, `XiConn` and the Fourier definitions. [`EtLoc`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/AlgebraicTheory/StatementC.lean#L39) gives the torsion input.
- [`xiEt_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/AlgebraicTheory/AlgebraicTheoryProofs/DvdOfNormIntCastLt.lean#L299) treats the first case; [`xi_swap`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/AlgebraicTheory/AlgebraicTheoryProofs/DvdOfNormIntCastLt.lean#L233) gives (2).
- [`scalar_constant_value`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/AlgebraicTheory/AlgebraicTheoryProofs/ScalarConst.lean#L55) is (1). [`xiConn_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/AlgebraicTheory/AlgebraicTheoryProofs/XiConn.lean#L316) uses it for the unit case. [`split_bound_of_xi_lemmas`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/AlgebraicTheory/AlgebraicTheoryProofs/XiConn.lean#L464) combines the two cases.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
