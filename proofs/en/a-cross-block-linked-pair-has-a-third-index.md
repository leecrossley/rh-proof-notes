# A cross-block linked pair has a third index

[Chinese proof](../zh/%E4%B8%80%E4%B8%AA%E8%B7%A8%E5%9D%97%E7%9A%84%E4%B8%A4%E7%BB%B4%E5%88%86%E9%87%8F%E4%B8%BA%E4%BB%80%E4%B9%88%E4%B8%80%E5%AE%9A%E8%BF%98%E8%BF%9E%E6%8E%A5%E7%AC%AC%E4%B8%89%E4%B8%AA%E6%8C%87%E6%A0%87.md)

## Statement

Fix an algebraic closure of $\mathbb Q$, the project prime $\ell$, the coefficient ring $O$, and rank-four data $D$. Assume `D.Good` and `LocalPublishedTheorems`. Let $r:G_{\mathbb Q}\to\mathrm{GSp}_4(\overline{\mathbb Q}_\ell)$ be an admissible characteristic-zero point (`EPt`). Write $\psi_i$ for the reference diagonal characters in order. The two blocks are $\{0,2\}$ and $\{1,3\}$. If $i,j$ in different blocks have $r(g)_{ij}\ne0$ and $r(h)_{ji}\ne0$ for some $g,h$, there is $k\ne i,j$ for which both directions between $i$ and $k$ occur.

We use the following inputs. The entries of $r$ lie in a finite $\ell$-adic integer ring $O'$ containing $O$. Residually $r$ is diagonal with entries $\bar\psi_i$, and each $E_{ii}$ is a finite $O'$-linear combination of the $r(g)$. At $D_\ell$ the representation has a full stable flag. For any cross-block root $\gamma=\bar\psi_i/\bar\psi_j$, `xvanExt` makes a continuous $\gamma$-cocycle an absolute coboundary if it vanishes on inertia outside the allowed ramification set and is a coboundary at every decomposition group in the set. This follows from the residual vanishing in $D$ after extension of coefficients. At allowed $p\ne\ell$, `locVanP`, under `LocalPublishedTheorems`, gives the coboundary condition for a normalized matrix entry that is a cocycle. The specified $s_\ell\in D_\ell$ has distinct residual character values in the two blocks.

## Proof

Write $a\leadsto b$ if some $r(g)_{ab}$ is nonzero. This is equivalent to membership of $E_{ab}$ in the matrix span, which is an algebra, so the relation is transitive. Suppose only $i,j$ are mutually linked to $i$. In computing the four entries $r(gh)_{ab}$ for $a,b\in\{i,j\}$, any nonzero contribution from a middle index $k$ gives $a\leadsto k\leadsto b$. Thus the multiplication formulas for these four entries use only $i,j$.

Put $P=\{k:k\leadsto i\}$. The coordinate subspace supported on $P$ is stable by transitivity. Projection onto the $i,j$ coordinates has stable kernel there. Indeed an arrow from $i$ or $j$ to $k\in P\setminus\{i,j\}$ would put $k$ in the same mutual-link class. Restricting the local full flag to this subspace and projecting gives a stable filtration on the two-dimensional quotient with steps of dimension at most one. Choose its stable line and order the two indices as $u,w$ so that a generator is $(v,1)$ with $|v|_\ell\le1$. Eliminate its eigenvalue to obtain for $g\in D_\ell$
$$
r(g)_{uu}v+r(g)_{uw}=(r(g)_{wu}v+r(g)_{ww})v.
$$

Choose a nonzero $b=r(g_0)_{uw}$ of least valuation from among such entries. This exists by discreteness of the valuation. Write $r(g)_{uw}=b c(g)$, so $c(g)\in O'$ and $c(g_0)=1$. Divide the two-term multiplication formula by $b$ and reduce. This gives the continuous cocycle
$$
z(g)=\bar c(g)/\bar\psi_w(g),\qquad z(gh)=z(g)+\frac{\bar\psi_u(g)}{\bar\psi_w(g)}z(h).
$$
It vanishes on unramified inertia and is a coboundary at the allowed $p\ne\ell$ by the local input.

Set $D(g)=r(g)_{ww}-r(g)_{uu}$. The line equation is $bc(g)=v(D(g)+v r(g)_{wu})$. Combining it with the equation at $s_\ell$ gives
$$
c(g)D(s_\ell)-c(s_\ell)D(g)
=v\bigl(c(s_\ell)r(g)_{wu}-c(g)r(s_\ell)_{wu}\bigr).
$$
The right side reduces to zero since $v,c(g),c(s_\ell)$ are integral and the cross-block entries reduce to zero. Because $\overline{D(s_\ell)}\ne0$, $\bar c(g)$ is a fixed multiple of $\overline{D(g)}$ on $D_\ell$. Dividing by $\bar\psi_w(g)$ gives a local coboundary. Apply `xvanExt` to obtain a residual scalar $m$ such that
$$
\bar c(g)=m\bigl(\overline{r(g)_{uu}}-\overline{r(g)_{ww}}\bigr)
$$
for all $g$. Write $E_{uu}=\sum_g a_g r(g)$ with finitely many $a_g\in O'$. Multiplying by $r(h)$ and inspecting the $u,w$ entry gives $c(h)=\sum_g a_g c(gh)$. The $u,u$ and $w,w$ entries give sums equal to $r(h)_{uu}$ and $0$, respectively. Substituting the coboundary expression into the sum for $c(h)$ gives $\bar c(h)=m\overline{r(h)_{uu}}$. At $h=1$ this forces $m=0$. At $h=g_0$ it contradicts $c(g_0)=1$. Thus there is a third index.

## Lean correspondence

- [The main lemma and `lattice`, `line`, `core`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/ExistsThirdIndexLinkedPair.lean) give normalization, the local stable line, and the contradiction.
- [`ordFlag`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/OrdFlag.lean#L25) gives the stable flag at $\ell$. [`eptInt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/EptInt.lean) gives an integer ring and integral projector expressions. [`xvanExt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/XvanExt.lean#L25) and [`locVanP`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/LocVanP.lean#L73) give the global and local cocycle vanishing.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
