# Why the terminal Fourier factor descends to a coset

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $P$ be one of the bad places of the chain, with local ring $\mathcal O=\mathcal O_{E,P}$ and $q=\operatorname{Norm}(P)$. Fix integers $M\ge1$ and $D\ge1$ and a local additive character $\psi:q^{-D}\mathcal O\to K^\times$ that is equal to $1$ on $\mathcal O$. At a twist place assume $D\ge2M$. For a row vector $\ell:E^n\to E$ and $y\in E^n$, the terminal Fourier factor is
$$
\mathcal F(\ell,y)=
\begin{cases}
\mathbf 1_{\ell\in\mathcal O^{1\times n}}\;\psi(-\ell y), & P\text{ a type place},\\
q^{-Mn}\mathbf 1_{q^M\ell\in\mathcal O^{1\times n}}\;\psi(-\ell y), & P\text{ a twist place}.
\end{cases}
$$
In this notation a failed integrality test gives zero, with no evaluation of $\psi$ needed. Assume $qy$ is integral at a type place and $q^M y$ is integral at a twist place. This is the denominator condition on representatives of the source coset of the terminal kernel.

For $\kappa\in\mathrm{GL}_n(\mathcal O)$ and another vector $y_*$ assume that $\kappa y_*-y$ lies in $\mathcal O^n$ at a type place or $q^M\mathcal O^n$ at a twist place. Then
$$
\mathcal F(\ell\kappa,y_*)=\mathcal F(\ell,y).
$$
Also, if a row perturbation $z$ has all its entries in $q^B\mathcal O$ for $B\ge\max(1,M)$, then $\mathcal F(\ell+z,y)=\mathcal F(\ell,y)$.

### Proof

Multiplication by $\kappa$ preserves the entrywise integrality condition on $\ell$ or $q^M\ell$ in both directions, since $\kappa^{-1}$ is also integral. If the condition fails, both values in the first identity are zero. Otherwise $\ell y$ belongs to $q^{-1}\mathcal O$ in the type case and $q^{-2M}\mathcal O$ in the twist case. Both groups lie in the domain of $\psi$ by the depth bounds. The difference
$$
(\ell\kappa)y_*-\ell y=\ell(\kappa y_*-y)
$$
is integral in either case. This uses $\ell\in\mathcal O^{1\times n}$ in the type case and $\ell\in q^{-M}\mathcal O^{1\times n}$ in the twist case. Thus the two additive characters agree. The normalization factor depends only on the place and $n$ and hence is the same on both sides.

The same argument gives the row perturbation law. Because $z$ is integral, the integrality test of either branch is unchanged by adding $z$. The supported argument $\ell y$ lies in the domain of $\psi$ as before. The product $zy$ is integral by the lower bound on $B$, so that the character again stays the same.

The first law applies in particular with $\kappa=1$, proving independence of the representative of a source coset. Under an integral change of source frame the term $\ell\kappa$ accounts for the matrix change and $\kappa y_*$ returns the new representative to the old coordinates. Any difference of representatives is within precisely the indicated coset period.

### Lean correspondence

- [`ftY`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L1150) defines the last-row factor. [`ybSet`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L1128) specifies the denominators and periods of its coset argument.
- [`intAt_form_comp_iff`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/IntAtFormOfMemStdAt.lean#L23) checks the support condition in both frames. [`psi_add_int`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/IntAtFormOfMemStdAt.lean#L33) and [`ftY_comp_glint`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/IntAtFormOfMemStdAt.lean#L52) prove the character equality under the integral frame move.
- [`ftY_add`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/DatumPeriodicMulLatticeFinal.lean#L304) is the row perturbation law used in [`xiTop_invariant`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/XiTopInvariant.lean#L17).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
