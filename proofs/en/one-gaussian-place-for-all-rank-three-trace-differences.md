# One Gaussian place for all rank-three trace differences

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E5%9C%A8%E9%AB%98%E6%96%AF%E5%9F%9F%E9%80%89%E5%90%8C%E4%B8%80%E4%B8%AA%E7%B4%A0%E5%A4%84%E4%BC%B0%E8%AE%A1%E7%A7%A9%E4%B8%89%E8%BF%B9%E5%B7%AE.md)

## Statement

Take $\ell,O,N,e,\psi,\Gamma=G_{\mathbb Q,S},r_0,g_1$ from the [Gaussian frame](the-large-conductor-v-case-over-the-gaussian-field.md), allowing any $e\ge1$ satisfying `HostData` including its parity and conductor conditions. Fix $K=\mathbb Q(i)$ and $\iota:\overline{\mathbb Q}_\ell\simeq\mathbb C$. Consider normalized characteristic-zero points $r$ satisfying the local conditions, irreducible on $\ker\eta$, with `BPrime_s`. Given the automorphic and local-level inputs and [rank-three integer trace separation `NumberU3U_s`](a-frobenius-trace-difference-product-is-a-nonzero-integer.md), there are common $\sigma\in\ker\eta$ and integer $C$ with $\Delta_r=\operatorname{tr}r(\sigma)-\operatorname{tr}r_0(\sigma)\ne0$ for all such points and
$$
\sum_{r\in\mathcal R}-\log|\Delta_r|_\ell\le(\ell Ne)^C
$$
for any finite family pairwise nonisomorphic on $\ker\eta$.

## Proof

Put $m=\ell N$. Since $12m-1\equiv3\bmod4$, some prime divisor $p$ is $3\bmod4$. Since $3$ does not divide $12m-1$, $p\ge7$. Also $p\nmid m$ and $p\le12m$. This prime is inert in $K$ and the unique place $w$ above it has residue size $q=p^2$. Choose an absolute place and let $F_w$ be arithmetic Frobenius in $G_K$ there. Take $\sigma$ to be the image of $F_w^{-1}$ in $\Gamma$. As $\varepsilon_\ell(F_w)=q$, the reference complex trace is
$$
E(q,e,z)=q^{-e}z+1+q^ez^{-1},\qquad z=\iota\big(\psi_G(F_w^{-1})\big).
$$
The character modulo $N$ gives $z^{\varphi(N)}=1$.

Each `BPrime_s` witness chooses an embedding of $K$ and a representation $\rho$ on the corresponding $G_K$. It is the restriction of the matrix part of $r$, with $\rho\otimes\varepsilon_\ell^{-1}$ having a conjugate-self-dual automorphic witness. Local-level transfer and `hostUnlE_alt` put $\rho$ in the admissible family for `NumberU3U_s`, at level $N$ and weights $(e,0,-e)$. Continuity, irreducibility and admissible local conditions come from the point, its irreducibility on $\ker\eta$, and local comparison, respectively.

First sum over the subfamily for one embedding. The image of $G_K$ is $\ker\eta$, so isomorphic $\rho$ would imply isomorphism on this subgroup. Apply `NumberU3U_s` with the list of all $\varphi(N)$th roots of unity, assigning the given family at its actual reference value $z$ and empty families at the other entries. The result is a nonzero integer $B$, all $\Delta_r\ne0$, and
$$
|B|_\ell\le\prod_r|\Delta_r|_\ell,\qquad
\log|B|\le a\varphi(N)[N(e+1)]^b\log p
$$
with $a,b$ from the common theorem. Singletons give individual nonvanishing. Since $\ell^{v_\ell(B)}$ divides $B$, this bounds the subfamily's sum of negative logs by $\log |B|$.

There are at most two subfamilies, one for each embedding. The place above $p$ is unique and the chosen Frobenius fixes $K$, so the same $\sigma$ applies. The total bound is $2a\varphi(N)[N(e+1)]^b\log p$. For $X=\ell Ne\ge6$, use $p\le12\ell N\le X^3$, $\varphi(N)\le X$, $N(e+1)\le X$, and $2a\le X^{2a}$. The exponent $C=2a+1+b+3$ works, giving the trace estimate for the V case.

## Lean correspondence

- [`exists_p` and `normV_inert`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/EHostNumberU.lean#L39) give the prime and norm $p^2$.
- [`trace_rz`, `adm3` and `admissible_unitary_three_point`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/EHostNumberU.lean#L144) compute the reference trace and check the family.
- [`key`, `final_bound` and `hostNumberUE_alt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/EHostNumberU.lean#L212) handle the integer bound and combine the embeddings. The main theorem is at [line 317](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/EHostNumberU.lean#L317).

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
