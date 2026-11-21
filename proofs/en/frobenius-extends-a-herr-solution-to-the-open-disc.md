# Frobenius extends a Herr solution to the open disc

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E7%94%A8Frobenius%E6%8A%8AHerr%E6%96%B9%E7%A8%8B%E7%9A%84%E8%A7%A3%E5%BB%B6%E6%8B%93%E5%88%B0%E6%95%B4%E4%B8%AA%E5%BC%80%E5%9C%86%E7%9B%98.md)

Let $L/\mathbb Q_\ell$ be finite with integers $O$. Take $s\ge1$, with $s\ge2$ if $\ell=2$, and $u\in1+\ell^s\mathbb Z_\ell$ with $v_\ell(u-1)=s$. On series let $\gamma$ and $\varphi$ substitute $(1+U)^u-1$ and $(1+U)^\ell-1$, respectively. They commute. Set $X=(1+U)^{\ell^{s-1}}-1,\ Q=\Phi_{\ell^s}(1+U)$, so $\varphi(X)=XQ$. Fix nonnegative $m,k$ and a finite multiset $J$ of nonnegative integers, with $\Lambda=\prod_{j\in J}\varphi^j(Q)$.

For $i\in\mathbb Z/n\mathbb Z$, $n\ge1$, take $G_i,P_i,P'_i\in M_r(O[[U]])$ and $y_i,z_i\in O[[U]]^r$ with $G_i(0)=I$, $z_i(0)=0$, $P_iP'_i=Q^kI$. In $L[[U]]$ form
$$
A_i=\begin{pmatrix}G_i&z_i\\0&1\end{pmatrix},\qquad
F_i=\begin{pmatrix}Q^{-m}P_i&\Lambda^{-1}y_i\\0&1\end{pmatrix}.
$$
Assume $A_i\gamma(F_i)=F_i\varphi(A_{i-1})$. Then $G_i\gamma(w_i)-w_i=z_i$ has a unique $w_i\in UL[[U]]^r$, and $(\log(1+U))^{m+|J|}w_i$ converges coordinatewise on $|U|<1$.

**Proof.** First seek $V_i$ satisfying $A_i\gamma(V_i)=V_i$ with $V_i(0)=I$. At degree $d>0$ the coefficient of the unknown matrix is $u^d-1$, since the substitution begins $uU+O(U^2)$. Its valuation is $s+v_\ell(d)$, so recurrence gives a unique invertible formal solution. If $M_d$ is the maximum of $1$ and the norms of the first $d$ coefficients, integrality of the known factors gives
$$
M_d\le |u^d-1|^{-1}M_{d-1}\le\ell^{sd+v_\ell(d!)}\le\ell^{(s+1/(\ell-1))d}.
$$
Thus $V_i$ converges on every closed disc of radius below $\ell^{-(s+1/(\ell-1))}$. Its bottom row is $(0,1)$: a $\gamma$-fixed series is constant by comparing its first nonconstant coefficient. Its last column above that row is $-w_i$. The same coefficient recurrence proves uniqueness of $w_i$ with zero constant term.

Let $\tau=\log(1+U)/X$, $p=m+|J|$. The identity
$$
\tau=\ell^{-(s-1)}\left.\frac{\log(1+v)}v\right|_{v=X}
$$
gives convergence on the open unit disc. We have $\varphi(\tau)=\ell\tau/Q$, so
$$
\tau=\ell^{-j-1}\varphi^{j+1}(\tau)\prod_{b=0}^j\varphi^b(Q)\qquad(j\ge0).
$$
In particular each $\tau/\varphi^j(Q)$, and therefore $\tau^{|J|}/\Lambda$ with multiplicity, has a series convergent throughout the disc.

The block compatibility gives $A_i\gamma(F_i\varphi(V_{i-1}))=F_i\varphi(V_{i-1})$. Compared with $V_i$, this invertible solution differs by an invertible right constant factor, since $\gamma$ fixes each entry of $V_i^{-1} F_i\varphi(V_{i-1})$. Write $V_i=F_i\varphi(V_{i-1})B_i$. With $C_i=\operatorname{diag}(\tau^p I_r,1)V_i$ we get
$$
C_i=H_i\varphi(C_{i-1})B_i,\qquad H_i=
\begin{pmatrix}\ell^{-p}Q^{p-m}P_i&(\tau^p/\Lambda)y_i\\0&1\end{pmatrix}.
$$
All entries of $H_i$ converge on the open disc by the divisibility identities and $p\ge m$.

For a fixed $0<R<1$, the Frobenius substitution has Gauss norm at most $\max(\ell^{-1}R,R^\ell)$ on the disc of radius $R$. While the radius is at most $R$, each substitution reduces it by a factor at most $\max(\ell^{-1},R^{\ell-1})<1$. Iterate the recurrence until the innermost series converges by the small-disc estimate. All intervening factors converge on the disc of radius $R$, so $C_i$ does too. Its upper-right column is $-\tau^p w_i$; multiply by $X^p$ to finish.

`exists_basis_bd` controls the initial disc, `block_relation` compares the two bases, `tau_eq` and `prod_dvd` clear the factors, and `letterwise` applies the recurrence in `exists_cocycle_solution_conv`. [Initial disc](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsCocycleSolutionConv.lean#L104) · [Constant comparison](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsCocycleSolutionConv.lean#L38) · [Logarithm](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsCocycleSolutionConv.lean#L168) · [Divisibility](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsCocycleSolutionConv.lean#L211) · [Recurrence](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsCocycleSolutionConv.lean#L238) · [Result](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsCocycleSolutionConv.lean#L405)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
