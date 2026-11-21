# Herr denominator bounds give a crystalline finite class

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E9%99%90%E5%88%B6Herr%E5%AF%B9%E7%9A%84%E5%88%86%E6%AF%8D%E5%B0%B1%E8%83%BD%E5%BE%97%E5%88%B0%E6%99%B6%E4%BD%93%E6%9C%89%E9%99%90%E7%B1%BB.md)

Let $K,L/\mathbb Q_\ell$ be finite, $K_0$ the maximal unramified subfield of $K$, and $K_s=K_0(\mu_{\ell^s})$, with $s\ge1$ and $s\ge2$ at $\ell=2$. Assume $K\subset K_s$ and $L$ contains all $\mathbb Q_\ell$-embedding images of $K_s$. Let $T$ be a finite free $\mathcal O_L$-lattice with crystalline rational representation $V=T[1/\ell]$, étale module $D(T)$ and Wach lattice $N(T)$. Set $Q=\Phi_{\ell^s}(1+U)$. For a finite multiset $I$ of nonnegative integers, put $\Lambda=\prod_{j\in I}\varphi^j(Q)$. Suppose $y,z\in D(T)$ satisfy $\Lambda y\in N(T)$, $z\in UN(T)$ and $(\gamma-1)y=(\varphi-1)z$ for the cyclotomic generator over $K_s$. Then the Herr class belongs to
$$
H_f^1(G_{K_s},T)
=\ker\!\left(H^1(G_{K_s},T)\to H^1(G_{K_s},V\otimes_{\mathbb Q_\ell}B_{\rm cris})\right).
$$
If the class comes from $G_K$, its original class is finite there as well.

The project uses a crystalline period comparison $\beta:B^+\to L\otimes_{\mathbb Q_\ell}B_{\rm cris}$ from the integral Witt coefficient ring. A Witt period vector with integral multiple $a v$ and $\beta(a)$ invertible has image obtained by dividing the comparison of $av$ by $\beta(a)$. Cross-multiplication gives independence, additivity and equivariance, and a lattice vector maps to its constant period. The open-disc comparison $J_{\rm disc}$ is a ring map defined on componentwise series converging on $|U|<1$, including integral series; on integral series it agrees with $\beta$. It is equivariant for the cyclotomic substitutions and takes $\log(1+U)$ to a unit $\mathbf t$ in $B_{\rm cris}$. These are the `Val` and `Disc` inputs. [Integral comparison](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsWachModulePeriodMapToBcris.lean#L63) · [Disc comparison](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/PeriodDiscExtensionTateElement.lean#L260)

**Proof.** Choose $b$ in the Witt period module with $(\varphi-1)b=J(y)$ by [surjectivity](trace-one-averaging-in-the-witt-period-ring.md). The [denominator argument](herr-period-solutions-have-invertible-denominators.md) gives its crystalline value $b_{\rm cris}$. The [all-elements formula](a-herr-coordinate-at-one-generator-determines-all-values.md) supplies an integral representative $c$ and $z_\sigma\in UN(T)$ with
$$
J(z_\sigma)=1\otimes c(\sigma)+(\sigma-1)b,\qquad
(\gamma-1)z_\sigma=(\sigma-1)z .
$$
Each $z_\sigma$ and each Wach basis vector also has a crystalline value, since multiplying the Wach lattice by $X^M$ brings it into the integral period module for some $M$, and $\beta(X)$ is invertible.

In the Wach basis, $y$ has integral coordinates divided by $\Lambda$. The two Frobenius height conditions write its matrices as $Q^{-m}P_i$ with $P_iP'_i=Q^k I$ by taking common exponents on the finite bases. The cyclotomic matrix has constant $I$, and $z$ has zero constant coordinates. Commutation and the cocycle identity give the compatibility in the [open-disc argument](frobenius-extends-a-herr-solution-to-the-open-disc.md). Thus there is a formal vector $w$ with zero constant coordinates and $(\gamma-1)w=z$, for which each coordinate multiplied by $(\log(1+U))^p$ converges on the disc, for $p=m+|I|$.

The formal vector $(\sigma-1)w-z_\sigma$ is $\gamma$-fixed by the displayed commutation identity and has zero constant coordinates. A first nonzero coefficient of degree $d>0$ would be multiplied by $\chi(\gamma)^d\ne1$ because the cyclotomic matrix has constant $I$, a contradiction. Therefore $(\sigma-1)w=z_\sigma$. For Wach basis $e_j$, set
$$
w_{\rm cris}=\mathbf t^{-p}\sum_j J_{\rm disc}((\log(1+U))^p w_j)e_{j,{\rm cris}} .
$$
Multiply the formal equality by the powers of the logarithm and its $\sigma$-transform so each expression is in the disc comparison domain. After applying the map, cancel the two invertible period factors using compatibility on integral coordinates. This gives $(\sigma-1)w_{\rm cris}=z_{\sigma,{\rm cris}}$. The crystalline image of the representative is therefore the coboundary $(\sigma-1)(w_{\rm cris}-b_{\rm cris})$, proving finite membership.

If $c$ was defined over $G_K$, subtract this period coboundary there. The remaining cocycle vanishes on $G_{K_s}$, hence descends to $\operatorname{Gal}(K_s/K)$ with values in the $G_{K_s}$-invariant period vectors. Averaging over the finite group kills $H^1$ since its order is invertible on a $\mathbb Q_\ell$-vector space. This proves finite membership before restriction.

`coord_eq` treats the generator, `exists_val` evaluates the analytic solution, and `core`, `mem_of_layers` and `main` supply `P7`. [Coordinates](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/HerrCocyclePolesFrobeniusQCrystalline.lean#L152) · [Evaluation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/HerrCocyclePolesFrobeniusQCrystalline.lean#L240) · [Core](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/HerrCocyclePolesFrobeniusQCrystalline.lean#L335) · [Finite class](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/HerrCocyclePolesFrobeniusQCrystalline.lean#L423) · [Main result](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/HerrCocyclePolesFrobeniusQCrystalline.lean#L539) · [Statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/DeltaInvariantLattices.lean#L199)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
