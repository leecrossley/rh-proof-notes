# Smoothing the lattice minimum

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E5%B9%B3%E6%BB%91%E6%A0%BC%E7%9A%84%E6%9C%80%E7%9F%AD%E5%90%91%E9%87%8F%E5%87%BD%E6%95%B0.md)

## Statement

Fix a number field $L$ with ring of integers $R$, $N\ge1$, and its embedded lattice $\Lambda=R^N$. For positive Hermitian forms $h=(h_w)$ let $Q_h(v)=\sum_w v_w^*h_wv_w$, with nonzero lattice minimum $\lambda(h)$ and $\lambda_D(h)=\lambda(h^{-\mathsf T})$. There is a smooth function $\mu$ on the positive cone, invariant under $\mathrm{GL}_N(R)$ congruence, with $\lambda_D(h)/4\le\mu(h)\le4\lambda_D(h)$. For $0\le\delta\le1/4$, if a Hermitian $k$ satisfies $|Q_k(z)-Q_h(z)|\le\delta Q_h(z)$ for all vectors, then $k$ is positive and $|\mu(k)-\mu(h)|\le C(L,N)\delta\mu(h)$.

## Proof

First smooth $\lambda$. Take a smooth nonincreasing $\rho:\mathbb R\to[0,1]$ equal to one at $t\le1$ and zero at $t\ge4$. Put $Z_s(h)=\sum_{v\in\Lambda}\rho(Q_h(v)/s)$ for $s>0$. The sum is locally finite by lattice discreteness and local comparison of positive forms. It is one for $4s\le\lambda(h)$ and at least two for $s\ge\lambda(h)$. Take smooth nondecreasing $\chi:\mathbb R\to[0,1]$ zero at $t\le0$ and one at $t\ge1$, and $X_j(h)=\chi(Z_{4^j}(h)-1)$. These increase from a zero tail to a one tail. Set
$$
\nu(h)=\sum_{j\in\mathbb Z}4^j(X_j(h)-X_{j-1}(h)).
$$
The coefficients are nonnegative and sum to one. A nonzero coefficient implies $4^j>\lambda(h)/4$ and $4^j<4\lambda(h)$ by the two cutoffs. Thus $\nu$ has the desired factor-four comparison with $\lambda$. Only finitely many scales occur uniformly nearby, giving smoothness, and each sum is invariant by permutation of lattice points.

If $h,k$ have relative error $\varepsilon\le1/2$, their minima differ by factors $1\pm\varepsilon$. The union of active scales and their neighbors is a uniformly bounded number with $s\asymp\lambda(h)$. If a lattice point contributes to either $Z_s$, then $Q_h(v)\le8s$. Choose a bounded positive integer $m$ with $32s/m^2<\lambda(h)$. Two such vectors in the same class modulo $m\Lambda$ would give a nonzero lattice difference divided by $m$ of squared length at most $32s/m^2$, impossible. Thus at most $m^{[L:\mathbb Q]N}$ vectors occur uniformly. Bounded derivatives of $\rho,\chi$ and $|Q_k(v)-Q_h(v)|/s=O(\varepsilon)$ then give $|X_j(k)-X_j(h)|=O_{L,N}(\varepsilon)$. Sum with the scales to get $|\nu(k)-\nu(h)|\ll_{L,N}\varepsilon\nu(h)$.

Now set $\mu(h)=\nu(h^{-\mathsf T})$. The comparison $(1-\delta)h\le k\le(1+\delta)h$ makes $k$ positive. Inversion and transpose give relative error at most $2\delta$ for these forms, so the last estimate applies. Inverse transpose is smooth and takes congruence to congruence by the inverse transpose matrix. Thus invariance and comparison hold for $\mu$.

## Lean correspondence

- [`Smoothing` and `SmMin`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/PartitionUnitySmooth/Smoothing.lean#L30) give the conditions on the positive cone.
- [`Xk`, `Tk` and `nu`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/PartitionUnitySmooth/GSmMin.lean#L163) give the scales. [`nu_lip`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/PartitionUnitySmooth/GSmMin.lean#L338) uses a general lattice-ball count, realized above by reduction modulo $m\Lambda$ in the required range. [`gSmMin`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/PartitionUnitySmooth/GSmMin.lean#L443) passes to the inverse transpose.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
