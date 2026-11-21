# Period-basis matrices recover the Weil trace

[Chinese proof](../zh/%E5%91%A8%E6%9C%9F%E5%9F%BA%E4%B8%8A%E7%9A%84%E7%9F%A9%E9%98%B5%E6%80%8E%E6%A0%B7%E8%AF%BB%E5%87%BAWeil%E8%A1%A8%E7%A4%BA%E7%9A%84%E8%BF%B9.md)

## Statement

Fix $\ell$, $\Omega_\ell=\overline{\mathbb Q}_\ell$, its maximal unramified subfield $F$, and a field isomorphism $\iota:\Omega_\ell\simeq\mathbb C$. The project comparison gives a crystalline ring $B$, a semistable ring $B_{\rm st}$, and an injection $\beta:B\to B_{\rm st}$ preserving Frobenius, Galois action and $\mathbb Q_\ell$ scalars. There is $u:F\to B$ with $\beta(u(x))=x\cdot1$. For finite $K,L\subset\Omega_\ell$, let $R:G_K\to\mathrm{GL}_a(L)$ have finite-dimensional $D_{\rm pst}^{\rm ur}(R)$ over $F$ and Weil–Deligne space $W$ of complex dimension $a$. Here $D_{\rm st}$ is the $G_K$ invariants of $L^a\otimes B_{\rm st}$, and $D_{\rm pst}$ allows passage to finite extensions first. For a local Weil element $g$ identified through the local comparison, let $T_g$ be its operator on $W$ and $p=\iota^{-1}(\operatorname{tr}T_g)$. Take $n_1,n_2\ge0$ with Weil degree $\alpha(g)=n_2-n_1$.

Suppose $\rho:G_K\to\mathrm{GL}_d(\mathbb Z_\ell)$ and $b_i\in M_a(L)$ satisfy $R(h)b_j=\sum_i\rho(h)_{ij}b_i$. Take $e_i\in\mathbb Z_\ell$ with $\sum_i e_i b_i=I_a$ and a basis $U\in\mathrm{GL}_d(B)$ with $\rho(h)h(U)=U$. If $s\in B$, $V\in M_d(B)$ and $V\varphi^{n_2}(U)=s\varphi^{n_1}(U)$, put $v=Ve$ and $t_i=\operatorname{tr}b_i$. Then for every $F$-linear $\lambda:\Omega_\ell\to F$,
$$
\sum_i v_i u(\lambda(t_i))=s u(\lambda(p)).
\tag{1}
$$
This is `IsTr` as used in [crystalline trace closedness](arbitrarily-small-crystalline-trace-errors-vanish.md).

## Period columns

Write $U_i=\varphi^{n_i}(U)$ and $w=U_2^{-1}e$, so $U_2w=e$ and $Ve=sU_1w$. If $b_{i,k}$ is column $k$ of $b_i$, set $m_{jk}=\sum_i b_{i,k}\otimes\beta(U_{ij})$. The covariance of the $b_i$ lets one move $\rho(h)$ to the second tensor factor, where $\rho(h)h(U)=U$. Thus $m_{jk}\in D_{\rm st}$. Frobenius acts only on the second factor. On $x_{jk}=\varphi^{n_2}m_{jk}$, the Weil action is $\varphi^{-\alpha(g)}$ composed with the Galois action, which fixes $m_{jk}$ and commutes with Frobenius. Hence $T_g x_{jk}=\varphi^{n_1}m_{jk}$ after base change to $W$.

Set $C=\Omega_\ell\otimes_F B_{\rm st}$ and $\kappa:\mathbb C\to C$ given by $\kappa(z)=\iota^{-1}(z)\otimes1$. The coordinate maps `CoordEx` and `CoordWD` give a $\kappa$-linear map $\psi:W\to C^a$ using ordinary column coordinates in the tensor product. Indeed $L$ acts on the left coordinates by definition, and scalar action of $F$ agrees there by tensor balancing. Thus $\psi(x_{jk})_r=\sum_i(b_i)_{rk}\otimes\beta((U_2)_{ij})$, with $U_1$ for $T_gx_{jk}$. Put $c_j=1\otimes\beta(w_j)$. By $U_2w=e$ and $\sum_i e_i b_i=I_a$,
$$
\sum_j c_j\psi(x_{jk})_r=\delta_{rk}.
\tag{2}
$$

## Weighted trace

In general for an $a$-dimensional $k_0$-space, a ring map $\kappa_0:k_0\to C_0$ to a commutative ring, and a $\kappa_0$-linear $\psi_0$ with (2), choose a basis. Let $X$ have the $\psi_0$-coordinates of that basis as columns, and $X'$ have columns $\sum_j c_j\kappa_0([x_{jk}])$ from the basis coordinates. Then $XX'=I$, so also $X'X=I$ by determinant and adjugate. For any linear $T$, with base changed matrix $T_m$, the sum $\sum_{j,k}c_j\psi_0(Tx_{jk})_k$ is $\operatorname{tr}(XT_mX')=\kappa_0(\operatorname{tr} T)$. This is `TrLin`.

Apply it to $T_g$ and sum over column $k$ to get $\sum_i t_i\otimes\beta((U_1w)_i)=p\otimes1$. Apply $x\otimes b\mapsto\lambda(x)b$, well defined by $F$-linearity, and use injectivity of $\beta$ and $\beta(u(x))=x\cdot1$. This yields $\sum_i u(\lambda(t_i))(U_1w)_i=u(\lambda(p))$. Multiply by $s$ and use $Ve=sU_1w$ to obtain (1).

## Lean correspondence

- [`TieRep2`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/IsOp2One.lean#L69) and [`tieRep_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/TieRep.lean#L64) specify and assemble the trace identity.
- [`colInv_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/ColInv.lean#L33), [`weilPhi_core`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/WeilPhi.lean#L8), [`coordEx_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/CoordEx.lean#L21), and [`coordWD_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/CoordWD.lean#L106) give invariance, the Weil action and coordinates.
- [`trLin_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/TrLinHolds.lean#L7) gives the weighted trace, and [`testTr_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/TestTr.lean#L7) applies the functional.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
