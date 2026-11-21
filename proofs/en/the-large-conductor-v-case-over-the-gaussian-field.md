# The large-conductor V case over the Gaussian field

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E5%A4%A7%E4%BA%8C%E8%BF%9B%E5%AF%BC%E5%AD%90%E7%9A%84V%E7%B1%BB%E6%94%B9%E7%94%A8%E9%AB%98%E6%96%AF%E5%9F%9F.md)

## Statement

Take the [host parameters](choosing-among-seven-positive-sign-length-estimates.md) $h,\chi,Q,o,N,t,\ell,O,\psi$. As in the [small-conductor case](bounded-degree-descent-for-the-small-conductor-v-case.md), $\ell\in B_\chi$, $0<e<t$, $e=1$, $\psi|_H=1$, and $\psi(-1)=-1$. Now require $R_1\le2^{c_2(\psi)}$. Under the deformation and automorphic inputs specified below there is a fixed integer $C'$ such that $V_{\ell,1}(\psi)$ has finite length and
$$
\frac{\operatorname{length}_O V_{\ell,1}(\psi)}{v_O(\ell)}\log\ell
\le(\ell N)^{C'}.
$$
This is `CountV`. Here $V_{\ell,e}(\psi)$ consists of the classes of $G_{\mathbb Q}$ with coefficients $(\operatorname{Frac}O/O)(\varepsilon_\ell^{-e}\psi_G^{-1})$ restricting to zero on all inertia and on decomposition groups at primes dividing $\ell N$.

## Deformation data

Set $T=\{\ell\}\cup\{v\mid N:v\ne\ell,\ (\psi_{(\ell)})_v\ne1\}$, where $\psi_{(\ell)}$ is the $\ell$-power-order part. As for the [rank-four data](constructing-rank-four-base-data-for-cases-ii-and-iii.md), $v\in T$ implies $v\mid\ell Q$. Since $n_0\ge2$,
$$
R_1=16o(\ell Q)^2 4^{n_0}\ge16\cdot9\cdot16>2^{11},
\qquad 8o\,v^2<R_1\le2^{c_2(\psi)}.
$$
It follows that $c_2(\psi)\ge12$ and $2\ell Q4^{n_0}\le2^{c_2(\psi)}$. The second inequality and $\operatorname{cond}(\theta^2)\mid Q$ for the character $\theta$ obtained by deleting the $\ell$-power-order and the mod-$2$-power parts give `XData` for residual weight $-2$. The host also bounds the prime-to-$\ell$ part of each odd-prime component by order dividing $2o$. These are numerical conditions in `HostData`.

Put $S=\{p:p\mid\ell N\}$ and $\Gamma=G_{\mathbb Q,S}$, allowing ramification at $S$ and infinity. Use $\eta$ for the quadratic character modulo $4$ and $\Psi=\varepsilon_\ell^e\psi_G$. Since $2\mid N$, both factor through $\Gamma$. With complex conjugation and the decomposition and inertia groups chosen, these give `HostFrame`. The reference $r_0(g)$ has diagonal matrix part $(\Psi(g),1,\Psi(g)^{-1})$ and other component $\eta(g)$. The matrix part multiplies as usual on $\ker\eta$ and with the duality automorphism on the other coset. This automorphism is inverse transpose conjugated by a reversing matrix. Thus the restriction in the irreducibility and trace counts is to the fixed Gaussian field.

## Inputs to the graded length argument

- `ThmS6_s` supplies $g_1\in\ker\eta$ with $\Psi(g_1)^2-1$ a unit. Normalize the basis using $g_1$ and take the universal deformation ring for the specified local conditions. Its weight-zero algebra is finite over $O$. Each characteristic-zero point irreducible on $\ker\eta$ has `BPrime_s`, giving irreducibility on the required open subgroups and the cyclotomic kernel, and an automorphic witness over the Gaussian field.
- `HostRigid_s` makes continuous dual-number deformations preserving the local conditions into global conjugations at such points. [`HostNumber_s`](one-gaussian-place-for-all-rank-three-trace-differences.md) chooses $\sigma$ before the family, with $\Delta_r=\operatorname{tr}r(\sigma)-\operatorname{tr}r_0(\sigma)\ne0$ and $\sum_r-\log|\Delta_r|_\ell\le(\ell Ne)^C$ for each finite family pairwise nonisomorphic on $\ker\eta$.
- [`HostVanE`](nonpositive-weight-integral-tangent-classes-are-torsion.md), [`HostXpp`](residual-weight-minus-two-vanishes-in-case-v.md) and `Cl1` give torsion of integral nonpositive-weight tangent classes, residual weight-$-2$ local-condition vanishing, and the unramified one-dimensional vanishing from class number one. Local and global finiteness, local Tate and Poitou–Tate duality, and the Euler characteristic supply the difference between equations and variables in each weight.

In the universal ring the torus $\operatorname{diag}(t,1,t^{-1})$ gives entry weights by differences of $1,0,-1$, so the coordinates have weights between $-2$ and $2$. The trace difference element $a=\operatorname{tr}u(\sigma)-\operatorname{tr}r_0(\sigma)$ has weight zero and vanishes at the reference point. The two-sided points, meaning points with positive and negative weights both nonzero somewhere, lie in `BPrime_s`. There $a$ is nonzero and rigidity constrains the tangent space to the torus direction.

Apply the [graded length lemma](the-graded-length-lemma-reduces-to-valuations-on-finite-orbits.md). It gives a finite orbit cover $r_i$ and bounds the degree-$-1$ cotangent length $V$ by the trace valuations. Isomorphism on $\ker\eta$ comes from the torus, so a minimal cover is pairwise nonisomorphic on this subgroup. Each admissible first cohomology class with coefficients $O/(a_0)$ yields an element of the dual of that cotangent piece. The combined inequality in `abstract_count` is
$$
\operatorname{length}_O\operatorname{Sha}_{F}(O/(a_0))\le V
\le 2v_O(\ell)\sum_i \frac{-\log|\Delta_{r_i}|_\ell}{\log\ell}
\qquad(a_0\ne0).
$$
[Passage from finite to divisible coefficients](finite-coefficients-control-the-divisible-localization-kernel.md) gives $\operatorname{length}_O V_{\ell,e}(\psi)\le V$. Multiply by $\log\ell/v_O(\ell)$ and use the simultaneous trace bound, obtaining at most $2(\ell Ne)^C\le(\ell Ne)^{C+1}$. Set $e=1$.

## Lean correspondence

- [`hostData_of_host`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeDeformations/HostDataOf.lean#L9) derives the local data. [`IsHostFrame`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeDeformations/IsHostFrame.lean#L32) and [`exists_hostFrame`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeDeformations/HostEx.lean#L55) give the frame.
- [`ThmS6_s`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/ThmS6CoreS.lean#L17) and [`HostRigid_s` and `HostNumber_s`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/HostNumberS.lean#L12) give exact quantifiers for the inputs.
- [`abstract_count`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeDeformations/AbstractCount.lean#L25) and [`vlen_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeDeformations/HostSha.lean#L131) compare the cotangent and cohomology lengths.
- [`countV_of_finiteness_duality_euler_host`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/CountVOf.lean#L33) makes the Gaussian choice and assembles the bound. [`count_v_of_printed_bound_k_reduced_unitary_lift`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/LinkedUnlE.lean#L55) is the window entry point.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
