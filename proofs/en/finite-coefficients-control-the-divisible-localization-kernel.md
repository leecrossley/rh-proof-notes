# Finite coefficients control the divisible localization kernel

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E7%94%B1%E6%AF%8F%E4%B8%AA%E6%9C%89%E9%99%90%E7%B3%BB%E6%95%B0%E5%B1%82%E6%8E%A7%E5%88%B6%E5%8F%AF%E9%99%A4%E7%B3%BB%E6%95%B0%E7%9A%84%E6%80%BB%E9%95%BF%E5%BA%A6.md)

## Statement

Fix $\ell,O$ and a [Gaussian deformation frame](the-large-conductor-v-case-over-the-gaussian-field.md) with $\Gamma=G_{\mathbb Q,S}$, character $\Psi$, and $T\subseteq S$. Use the images of the chosen $D_v,I_v$ for $v\in S$. Set $A=(\operatorname{Frac}O/O)(\Psi^{-1})$ and $A_a=(O/aO)(\Psi^{-1})$ for $a\ne0$. Let $S_a$ be the submodule of $H^1(\Gamma,A_a)$ spanned by classes of cocycles that vanish on $N_v=\ker((\eta,\bar\Psi)|_{I_v})$ for $v\notin T$ and are coboundaries with parameters in $A_a$ on $D_v$ for $v\in T$.

Assume $\Psi|_{N_v}=1$ for $v\notin T$, and each $D_v$ for $v\in T$ contains $g_v$ with $\Psi(g_v)^2-1\in O^\times$. These are `teich` and `x` in `Ok`. If $\operatorname{length}_O S_{\ell^k}\le V$ for all $k\ge0$, then the kernel $L$ of the restrictions from $H^1(\Gamma,A)$ to all the indicated $D_v$ has length at most $V$.

## Proof

Let $x\in L[a]$ and choose a representative $z$. Since $ax=0$, $az(g)=gb-b$ for $b\in A$. Write $b=ab'$ by divisibility and subtract the coboundary of $b'$. The new cocycle $z'$ takes values in $A[a]$. The map $[t]\mapsto[t/a]$ is an equivariant identification $A_a\simeq A[a]$.

At each $D_v$, $z'(g)=gm_v-m_v$ for a parameter $m_v\in A$ because $x$ restricts to zero. For $v\notin T$, $\Psi$ is trivial on $N_v$, so $z'|_{N_v}=0$. For $v\in T$,
$$
0=az'(g_v)=\bigl(\Psi(g_v)^{-1}-1\bigr)a m_v.
$$
The scalar is a unit because $\Psi(g_v)^2-1$ is a unit. Thus $m_v\in A[a]$. This verifies the finite-coefficient conditions and shows that $L[a]$ is contained in the image of $S_a$ in $H^1(\Gamma,A)$. Hence $\operatorname{length}_O L[a]\le\operatorname{length}_O S_a$.

Every continuous cocycle has finite image by compactness and each value is killed by a power of $\ell$. Thus $L=\bigcup_k L[\ell^k]$. This increasing sequence has lengths bounded by $V$. Once its length reaches a maximum it stabilizes, since strict inclusion increases length. Therefore $\operatorname{length}_O L\le V$.

## Application to the absolute Galois group

The twist $\varepsilon_\ell^{-e}\psi_G^{-1}$ is unramified outside $S$. A class restricting to zero at every inertia group has representatives vanishing on inertia outside $S$ because the action there is trivial. The cocycle vanishes on the closed normal subgroup they generate, so descends to $\Gamma$. Conversely, on $S$ the decomposition-group condition implies the inertia condition. The decomposition-group coboundary requirement descends to each image because the action and cocycle factor through the quotient. This identifies $V_{\ell,e}(\psi)$ with $L$ for the host frame.

## Lean correspondence

- [`ShaO`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeDeformations/IsCharZeroPt.lean#L94) gives the finite coefficients. [`Ok`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeDeformations/AdjointDiagonalRepPreservesWeightPiece.lean#L147) provides the local unit and inertia conditions.
- [`len_union`, `tors_le` and `sha_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeDeformations/HostSha.lean#L10) compare the finite layers and take their union.
- [`vlen_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeDeformations/HostSha.lean#L131) uses `litV` and `factorGS` for the passage to $\Gamma$.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
