# From local lattice slopes to a global slope bound

[Chinese proof](../zh/%E5%B1%80%E9%83%A8%E6%A0%BC%E7%9A%84%E6%96%9C%E7%8E%87%E6%80%8E%E6%A0%B7%E9%99%90%E5%88%B6%E5%85%A8%E5%B1%80%E6%96%9C%E7%8E%87.md)

## Setting and conclusion

Let $K$ be a totally imaginary field of degree $n$ with $h_\infty$ infinite places. Let $I$ be finite nonempty and $W,V_i$ finite-dimensional $K$-spaces with bases. Write $D=\dim W$, $d_i=\dim V_i$, and $R=\sum_i d_i>0$. Choose full finitely generated $\mathcal O_K$-lattices $L\subset W$ and $N_i\subset V_i$. At each infinite place $w$, give the Euclidean metrics by sending the embedded coordinates through the inverses of invertible complex matrices $X'_w,X_{i,w}$ and taking real and imaginary parts. The unnormalized slope of any positive-rank lattice is the negative log of its covolume in its real span divided by its $\mathbb Z$-rank. Maximal slope is the supremum over nonzero $\mathcal O_K$-sublattices, and minimal slope is the infimum over nonzero quotients by saturated sublattices with the orthogonal quotient metric. The project doubles each number and adds $-\log 2+\log|\operatorname{disc}K|/n$ to define $\mu$, $\mu_{\max}$ and $\mu_{\min}$.

Let $B_i:V_i\to W$ be $K$-linear with $B_i(N_i)\subset L$. For each nonzero $B_i$ require its height to be at most $h_i\in\mathbb R$, where the height is the mean of $\log\|(X'_w)^{-1}B_i(w)X_{i,w}\|_{\mathrm{op}}^2$ over the infinite places. Assume $s,r,H\in\mathbb R$ satisfy
$$
sR\le\sum_i d_i(\mu(N_i)-h_i),\qquad r\ge0,\qquad
\mu_{\max}(N_i)-h_i\le s+r,\qquad s-\mu_{\min}(L)\le H,\qquad H\ge0.
$$
Zero-dimensional blocks contribute nothing.

At a chosen infinite place $v$ take arbitrary further invertible coordinate matrices $Y_i,Y'$. Let $D'=D+D_1$ with $D_1\ge0$ integral, and take $D'\times d_i$ matrices $A_i$ whose first $D$ rows are $(Y')^{-1}B_i(v)Y_i$. For positive weights $\gamma_i$, put $C_i=\sqrt{\gamma_i}A_i$ and $Q=\sum_i C_iC_i^*$. Suppose $0\le\delta<1$, $0\le e\le1/4$, $\eta\ge0$, and
$$
(1-\delta)D'\le D,\qquad
\sum_i\|C_i^*C_i-I_{d_i}\|_F^2\le eR,\qquad
\operatorname{tr}(Q^2)\le (1+\eta)\frac{(\operatorname{tr}Q)^2}{D'}.
$$
Here $\|\cdot\|_F$ is the Frobenius norm. If $D=0$, then $D'=0$ and the sum of block defects is $R$, a contradiction. Thus $D>0$. The conclusion of `TheoremFSharp` is
$$
\mu(L)\ge s-\frac{4r\log(1+H/r)+(\eta+4\sqrt e)H}{1-\delta}.
$$
At $r=0$ the log term means zero. The main route uses `TheoremF`, which subtracts a further $\log|I|\ge0$ on the right. [Full frame hypotheses](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/HarderNarasimhan/StatementFrameF.lean) · [Normalization and heights](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/HarderNarasimhan/StatementPl.lean) · [Use in the count discrepancy](quotient-slopes-and-count-discrepancy.md)

## Cut off the lower slopes in each source lattice

The Harder–Narasimhan input gives a descending list of $\operatorname{rank}_{\mathbb Z}M$ slopes, unnormalized sum $-\log\operatorname{covol}M$ and extremal entries the maximal and minimal slopes. After normalization its mean is $\mu(M)$. For a level $\lambda$, let $M^{\ge\lambda}$ be the sum of the nonzero sublattices of minimal normalized slope at least $\lambda$. This is saturated, its minimal slope is at least $\lambda$ if nonzero, and its $\mathbb Z$-rank counts the entries of the list at least $\lambda$. [Slope-list and cutoff properties](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/HarderNarasimhan/Statement.lean)

For $\tau\ge0$, the normalized slope lists of the $N_i$, shifted by $-h_i$, have $nR$ entries with mean at least $s$ and upper bound $s+r$. If $k$ of them are below $s-\tau$, their total sum is at most $nR(s+r)-k(r+\tau)$. Thus $k\le nR\,r/(r+\tau)$ for $r>0$. For $r=0$ all entries equal $s$ and we set this ratio to zero. Writing $\alpha(\tau)$ for the ratio and $N_i(\tau)=N_i^{\ge s-\tau+h_i}$, the total codimension in the $V_i$ is at most $\alpha(\tau)R$.

The slope comparison for a $K$-linear map $B$ in these metrics gives $\mu_{\min}(B(M))\ge\mu_{\min}(M)-\operatorname{ht}(B)$ whenever the lattice image is nonzero. For a lattice $T\supseteq B(M)$ it also gives $\mu_{\min}(M)\le\mu_{\max}(T)+\operatorname{ht}(B)$ when the image is nonzero, and $\mu_{\max}(M)\le\mu_{\max}(T)+\operatorname{ht}(B)$ when $B$ is injective on $M$. We use the first inequality. Each nonzero image $B_i(N_i(\tau))$ has minimal slope at least $s-\tau$. Consequently
$$
M(\tau)=\sum_i B_i(N_i(\tau))\subseteq L^{\ge s-\tau}.
$$
[Slope comparison under a lattice map](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/HarderNarasimhan/HarderNarasimhanProofs/SlopeIneqMean.lean)

## The retained subspaces have a large sum of images

Let $U_i\subset\mathbb C^{d_i}$ have total codimension at most $\alpha R$, and $S=\sum_i C_iU_i$. Let $P$ project onto $S^\perp$, put $m=\dim S^\perp$, and write $T=\operatorname{tr}Q$, $E_i=C_i^*C_i-I_{d_i}$. The target is $m\le(\eta+4\alpha+4\sqrt e)D'$, which holds immediately for $\alpha\ge1/4$. For $0\le\alpha<1/4$, trace Cauchy–Schwarz and the sum of squared block defects give $T\ge(1-\sqrt e)R\ge R/2$.

Let $P_i$ project onto $U_i^\perp$, of dimension $k_i$. Since $PC_i=PC_iP_i$,
$$
\operatorname{tr}(PQ)\le\sum_i\|C_iP_i\|_F^2
=\sum_i(k_i+\operatorname{tr}(P_iE_i))
\le R(\alpha+\sqrt{\alpha e}).
$$
The last inequality follows by summing $|\operatorname{tr}(P_iE_i)|\le\sqrt{k_i}\|E_i\|_F$. On the other hand, $Q$ is self-adjoint and $\|Q-(T/D')I\|_F^2=\operatorname{tr}(Q^2)-T^2/D'\le\eta T^2/D'$. Therefore
$$
\operatorname{tr}(PQ)\ge\frac{T}{D'}\bigl(m-\sqrt{m\eta D'}\bigr).
$$
Using $R/T\le2$ and $2\sqrt{m\eta D'}\le m+\eta D'$ yields $m\le D'(\eta+4\alpha+4\sqrt{\alpha e})$, giving the target bound. [Frame codimension estimate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/HarderNarasimhan/HarderNarasimhanProofs/FrameLinearAlgebraFirst.lean)

## Integrate the share of low global slopes

For each $\tau$, embed the $K$-span of $N_i(\tau)$ in the complex coordinates $Y_i$ at $v$ to obtain $U_i$ of the same rank. Projection of $\sum_i C_iU_i$ onto the first $D$ coordinates gives the complex span of $M(\tau)$ in the $Y'$ coordinates. Its codimension is at most that of $\sum_i C_iU_i$. Since $M(\tau)\subseteq L^{\ge s-\tau}$, the share of slopes of $L$ below $s-\tau$ is bounded by
$$
w(\tau)=\frac{\eta+4\alpha(\tau)+4\sqrt e}{1-\delta}.
$$
Indeed the common factor $n$ cancels between the $\mathbb Z$-ranks in the share, and $(1-\delta)D'\le D$ bounds the factor $D'/D$.

Every slope $z$ of $L$ satisfies $z\ge s-H$. Thus $(s-z)_+=\int_0^H\mathbf1_{z<s-\tau}\,d\tau$. Averaging shows $s-\mu(L)\le\int_0^H\min(1,w(\tau))\,d\tau\le\int_0^H w(\tau)\,d\tau$. When $r>0$, $\int_0^H\alpha(\tau)\,d\tau=r\log(1+H/r)$, and at $r=0$ the integral is zero. This gives the stated bound. [Global frame theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/HarderNarasimhan/HarderNarasimhanProofs/TheoremFSharp.lean) · [Layer-cake calculation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CorankShare/CorankShareProofs/LayerCakeFormula.lean)

In the count discrepancy proof, `sFrame` is the rank-weighted mean of the local slopes less the heights, and `uFrame` is the difference between the largest shifted maximal slope and that mean. The block hypotheses come from the matrix compression estimate. [Getting the block hypotheses](matrix-trace-bounds-after-compressing-the-blocks.md)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
