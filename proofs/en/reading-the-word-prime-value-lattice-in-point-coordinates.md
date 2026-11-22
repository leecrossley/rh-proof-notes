# Reading the word-prime value lattice in point coordinates

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Fix a layer $0\le i\le m$ of the true column chain, of rank $n$. Let $E$ be its host CM field, $K$ its coefficient field and $\sigma:K\to\mathbb C$ the complex embedding. Fix a coefficient prime $w$ above the rational word prime $T$. Use the split point realization, with selected primes $\mathcal T$ of $E$ above $T$ and no conjugate pair among them. By the [embedding selection](choosing-the-embedding-that-sees-each-split-word-prime.md), each $P\in\mathcal T$ corresponds bijectively to a block $\tau=\tau_w(P)$. The embedding $\iota_\tau:E\to K$ contracts $w$ to $P$ in the selected case and to $\bar P$ in the conjugate case. The case is common to all $P$ at this $w$.

An arithmetic point $d$ has a self-dual lattice $N\subset E^n$ for the standard Hermitian pairing and a nonzero residue functional $f_P:N_P\to k_P$ at every $P\in\mathcal T$. Here $N_P=\mathcal O_{E,P}N$ and $k_P=\mathcal O_E/P$. Let
$$
L=\{x\in N:f_P(x)=0\text{ for every }P\in\mathcal T\},
\qquad
L^\sharp=L^\# .
$$
The Hermitian dual is $M^\#=\{y:\overline y^{\mathsf t}x\in\mathcal O_E\text{ for every }x\in M\}$. For $P_0\in\mathcal T$ put $L^\sharp_{P_0,\ker}=\{x\in L^\sharp:f_{P_0}(x)=0\}$, using $(L^\sharp)_{P_0}=N_{P_0}$. For a full host lattice $M$ write $W_w(M)=\operatorname{ev}(\mathcal O_{K,w}\Delta(M))$. Here $\Delta(M)$ is the [coefficient value lattice](a-local-frame-identifies-the-weyl-value-lattice.md), and $\operatorname{ev}$ embeds its coefficients in $\mathbb C$ and evaluates on invertible frames with the prescribed determinant weights.

At $p=\operatorname{pt}(d)$ and for $J\subseteq\mathcal T$, the point test `valB` chooses a basis of $N_P$ if $w$ is in the selected case and $P\notin J$, and a basis of $\ker f_P$ otherwise. It applies the point coordinate move to the standard localized Weyl span. Call the resulting set of values $V_{w,J}(p)$. Then
$$
\begin{aligned}
V_{w,\varnothing}(p)&=W_w(L^\sharp) &&\text{in both cases},\\
V_{w,\mathcal T}(p)&=W_w(L) &&\text{in the selected case},\\
V_{w,\{P_0\}}(p)&=W_w(L^\sharp_{P_0,\ker}) &&\text{in the selected case}.
\end{aligned}
$$

### Which dual basis occurs

Write $\operatorname{co}(y)$ for the complex polynomial recovered from a value $y$ in the standard frame. Recovery is unique by injectivity of evaluation on invertible matrices with nonzero determinant. Thus $\operatorname{co}(y)$ equals the coefficient image of $F$ if and only if $y=\operatorname{ev}(F)$. The true and point weights in layer $i$ both subtract the common integer $i(t+1)/2$ from the reference weight, since the rank parameter $t$ is odd. This keeps the nonnegative polynomial weights $\nu_\tau$ unchanged. The standard Weyl span in the point formula is then the coefficient image of the localized standard lattice $\Delta^0_w$.

A chart at $P$ identifies its field with $E$ and its integral ring with $\mathcal O_{E,P}$. Its basis is therefore the image of a matrix $g_P\in\mathrm{GL}_n(E)$ whose columns form a basis of the chosen local lattice. Suppose the local choices are the localizations of a full host lattice $M$, so $M_P=g_P\mathcal O_{E,P}^n$. The coefficient matrix for the local move in block $\tau=\tau_w(P)$ is
$$
B_\tau=
\begin{cases}
(\iota_\tau(g_P)^{-1})^{\mathsf t},& w\text{ in the selected case},\\
\iota_\tau(\overline{g_P}),&w\text{ in the conjugate case}.
\end{cases}
$$
Indeed the one-block point move uses the round action $f(Y)\mapsto\det(a)^{-d_\tau}f(a^{-1}Y)$, where $a=\iota_\tau(g_P)$ in the selected case and $a=(\iota_\tau(\overline{g_P})^{-1})^{\mathsf t}$ in the conjugate case. In the tensor polynomial action $\rho_\lambda$ this is the block matrix $B_\tau=(a^{-1})^{\mathsf t}$. Passing to $\mathbb C$ along $\sigma$ commutes with these actions.

In the selected case the local span of $\iota_\tau(M)$ over $\mathcal O_{K,w}$ has basis $\iota_\tau(g_P)$. Denominators outside $P$ map to units at $w$, so the local span agrees with that of the image of $M_P$. Taking the ordinary dot-product dual replaces the basis matrix by its inverse transpose. In the conjugate case the Hermitian dual of $M$ has basis $(\overline{g_P}^{-1})^{\mathsf t}$ at $\bar P$. In fact membership in this local dual means that $g_P^{\mathsf t}\overline y$ is integral at $P$, which is equivalent to $\overline{g_P}^{\mathsf t}y$ being integral at $\bar P$. Extending the dual lattice along $\iota_\tau$ and then taking an ordinary dot-product dual gives basis $\iota_\tau(\overline{g_P})$. Thus $B_\tau$ is the required basis for $\Delta(M)$ in the selected case and for $\Delta(M^\#)$ in the conjugate case.

By the local frame rule, applying $\rho_\lambda(B)$ to $\Delta^0_w$ gives the appropriate localized coefficient lattice. Embedding the coefficients and using polynomial recovery shows that the condition in the point test is exactly membership in $W_w(M)$ in the selected case and $W_w(M^\#)$ in the conjugate case. This applies to every tuple of admissible bases. Conversely each value of the corresponding lattice has standard coordinates in any such bases, and hence passes the test.

### Which host lattice to use

For every selected prime $P$, one has $L_P=\ker f_P$. Localization at $P$ discards the conditions at the other selected primes, since their target residue fields become zero. At every prime $Q$ outside $\mathcal T$ it gives $L_Q=N_Q$. In particular $L_{\bar P}=N_{\bar P}$. The Hermitian dual at $P$ depends on the lattice at $\bar P$, and $N^\#=N$, so $(L^\sharp)_P=N_P$. For $J=\varnothing$ the bases therefore come from $M=L^\sharp$ in the selected case. In the conjugate case every tested local lattice is $L_P$, so $M=L$ and the rule returns $W_w(L^\#)$.

In the selected case the test using all kernels has $M=L$. For a single kernel at $P_0$ take $M=L^\sharp_{P_0,\ker}$. It is a full lattice between $L$ and $L^\sharp$. Its localization at $P_0$ is $\ker f_{P_0}$, while at the other selected primes it gives $N_P$ because the quotient by this kernel is killed by $P_0$. These are the last two formulas.

### Lean correspondence

- [`Coord.mv`, `Coord.mov` and `Coord.valB`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/FormsStable.lean#L165) form the point test. [`co`, `co_eq_iff`, `natW_lam` and `lamT_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsCoordinatesValueLatticesEqWeylLattices.lean#L27) recover its polynomials and identify the two weights.
- [`basis_seen` and `basis_conj`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MemClosureIff.lean#L189) compute the dual bases. [`mov_eq` and `gm_iK`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsCoordinatesValueLatticesEqWeylLattices.lean#L126) compare the actions in those bases. [`frame_iff`, `gm_basis` and `valB_iff`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsCoordinatesValueLatticesEqWeylLattices.lean#L156) apply the comparison to the local tests.
- [`Deco.Ok.mem_locP_L`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/DecoFin.lean#L1192) identifies the localized kernel lattice. [`ker_iff`, `valIs` and `valB_single`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsCoordinatesValueLatticesEqWeylLattices.lean#L229) specialize the comparison to the three stated choices.

Status. Source-based reconstruction draft. The statement uses the split point realization and `Sees`. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
