# Local lengths and divisibility give the lattice slope formulas

[Chinese proof](../zh/%E5%B1%80%E9%83%A8%E9%95%BF%E5%BA%A6%E4%B8%8E%E6%95%B4%E9%99%A4%E6%80%8E%E6%A0%B7%E5%90%88%E6%88%90%E5%95%86%E6%A0%BC%E7%9A%84%E6%96%9C%E7%8E%87%E5%85%AC%E5%BC%8F.md)

## Statement

Let $K$ be totally imaginary of degree $d$, with full lattices $N_0\subseteq M$ in a rank $r>0$ space, using the same Hermitian metric. For a finite place $w$ let $\mathfrak p_w$ be its prime, $e_w>0$ its ramification degree, $b_w=\log\mathrm N\mathfrak p_w/d$, $\lambda_w=e_w b_w$, and $L_w=\operatorname{length}_{O_{K,w}}(M_w/N_{0,w})/e_w$. Take finite $W$ containing all places where they differ. For $w\in W$ assume $N_{0,w}\subseteq\mathfrak p_w^{e_w\tau_w}M_w$ with $\tau_w$ a nonnegative integer. For real $s_w$, put $s'_w=\lfloor e_ws_w\rfloor/e_w$, $I=\prod_{w\in W}\mathfrak p_w^{-\lfloor e_ws_w\rfloor}$, and $N=IN_0$. Then
$$
\begin{aligned}
\mu(N)&=\mu(M)+2\sum_w\lambda_w(s'_w-\tau_w)
 -2\sum_w\lambda_w(L_w/r-\tau_w),\\
\mu_{\max}(N)&\le\mu_{\max}(M)+2\sum_w\lambda_w(s'_w-\tau_w),
\end{aligned}
$$
and $s'_w\le s_w$. These are the lattice formulas in `places_at_of` for `NuLat`, `MramL` and `Nu`, used in [the two slope estimates](quotient-slope-bounds.md).

## Mean and maximum slopes

The finite quotient splits over primes, with $e_wL_w$ residue field factors at $w$. Thus $\log[M:N_0]=\sum_w e_wL_w\log\mathrm N\mathfrak p_w$. Compute heights on a free sublattice given by a common basis in $N_0$. Gram determinants coincide and the index ratio is $[M:N_0]$. With slope equal to the negative logarithm of height divided by $dr/2$, this gives $\mu(N_0)=\mu(M)-(2/r)\sum_w\lambda_w L_w$. For a fractional ideal $A$ and full lattice $P$, $\mu(AP)=\mu(P)-(2/d)\log\mathrm N A$: for integral ideals the index calculation gives $\mathrm N(A)^{\operatorname{rank}P}$ by local lengths on each basis direction, and clearing a denominator extends it to fractional ideals. This is the [length and norm comparison](local-lengths-and-lattice-slopes.md). Apply it to $I$ for the addition $2\sum_w\lambda_w s'_w$, then add and subtract the $\tau_w$ sums.

Let $J=\prod_{w\in W}\mathfrak p_w^{e_w\tau_w}$. The local containments at all places give $N_0\subseteq JM$. Otherwise the nonzero class in $V/JM$ has a proper annihilator inside some maximal ideal and remains nonzero after localization there. Thus $N\subseteq IJM$. The maximum slope is monotone for containment by taking the supremum over nonzero sublattices. Ideal multiplication shifts it by $-(2/d)\log\mathrm N A$, since multiplication is invertible on sublattices and the mean shift is independent of rank. Apply this with $IJ$ for the second inequality. The rounding bound follows from $e_w>0$.

## Places in the application

On support away from residue characteristic $T$, `LinkG` supplies the containment and $L_w\le d_M(\tau_w+io_w)$ through the [local length input](cohomology-and-divisibility-loss.md). Integral $\tau_w$ makes the floor in the exponent redundant. At $T$ on support, `placesF_min'` gives $\tau_w=0$ from $T\ge X'$. There `adm26` bounds the weighted length directly by $C|TT|m(a/k+b')\log T$, the term $P_T$ in the lower slope bound. Off support, at $p\ne T$ one has $p>X''$ and the record set is empty. At $T$, the first-layer error $E(u,1,w)$ is zero off support but would include a positive $fN(m)$ and other nonnegative terms if the place occurred. Hence the operator is an empty product, the identity, and the reference and local lattices coincide.

## Lean correspondence

- [`le_prod_smul`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/PlacesP.lean#L31), [`mu_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/PlacesP.lean#L129) and [`muMax_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/PlacesP.lean#L171) give the formulas. [`lenLoc_atT_zero` and `places_at_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/PlacesP.lean#L260) handle the support.
- [`placesF_min'`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/PlacesMin.lean#L23) works on the same family. [`Places_at` and `slopesN_at_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/TopDensityNGeSixteen.lean#L1516) use the conditions.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
