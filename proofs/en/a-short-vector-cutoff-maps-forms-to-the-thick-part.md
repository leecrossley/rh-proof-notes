# A short-vector cutoff maps forms to the thick part

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E7%94%A8%E6%9C%80%E7%9F%AD%E5%90%91%E9%87%8F%E6%88%AA%E5%8F%96%E6%8A%8A%E6%AD%A3%E5%AE%9A%E5%BD%A2%E5%BC%8F%E9%80%81%E8%BF%9B%E5%8E%9A%E9%83%A8.md)

## Statement

Let $L$ be totally imaginary, $R=O_L$, and $N\ge1$. Use the forms $Q_h$ and the functions $\lambda,\lambda_D,\mu,\rho,Z_s$ of the [lattice smoothing argument](smoothing-the-lattice-minimum.md). Call simultaneous positive lower bounds for $\lambda,\lambda_D$ the thick part. The smooth equivariant map $H$ below has image there, with $\lambda(H(h))\ge c_1$ and $\lambda_D(H(h))\ge c_2$ for fixed positive constants. Also, if $k$ has relative quadratic form error at most $0\le\delta\le1/4$ from $h$, its image has relative error at most $C(1+(\lambda(h)\lambda_D(h))^{-1})\delta$ from $H(h)$. The comparison constants for $\mu$ may be arbitrary fixed positives.

## Construction

For $v\in R^N$ write $R_h(v)_w=(h_wv_w)(h_wv_w)^*$. Set
$$
T_s(h)=\frac{\sum_v\rho(Q_h(v)/s)R_h(v)}{s^2Z_s(h)},\qquad
H(h)=\mu(h)h+\sum_{j\in\mathbb Z}\rho(4^j\mu(h))T_{4^j}(h).
$$
By Cauchy–Schwarz and $Q_h(v)\le4s$ on the support, $0\le Q_{T_s(h)}(z)\le4Q_h(z)/s$. The numerator vanishes if $4s\le\lambda(h)$ and the outer factor vanishes if $s\mu(h)\ge4$. This makes both sums locally finite. Changing lattice coordinates under integral congruence gives equivariance, since $R_h(v)$ transforms by congruence and $\mu$ is invariant. In particular $H(h)\ge\mu(h)h$.

Use a lattice ball count in real dimension $d=[L:\mathbb Q]N$: the number of vectors with $Q_h\le16B$ is at most $m^d$ times the number with $Q_h\le B$, for integer $m\ge8$. In each class modulo $mR^N$ choose a representative $v_0$ from the larger ball. The map $v\mapsto(v-v_0)/m$ injects that class into the smaller ball by the triangle inequality.

## The two lower bounds

For $u\ne0$ in the original lattice write $a=Q_h(u)$. If $\mu(h)a\ge1/16$, the first term suffices. Otherwise take $s=4^j$ with $4a\le s\le16a$, so $\rho(s\mu(h))=1$. Let $B$ consist of lattice points of squared length at most $s/4$. Each pair $v,v+u$ for $v\in B$ has squared lengths at most $s$, so both inner weights are one. The inequality $|b|^2+|b+c|^2\ge|c|^2/2$ place by place gives
$$
Q_{R_h(v)}(u)+Q_{R_h(v+u)}(u)\ge
\tfrac12\sum_w(u_w^*h_wu_w)^2\ge a^2/(2r_2).
$$
Each vector is counted at most twice, and $Z_s\le m^d|B|$ by the ball count. Hence this scale contributes at least $a^2/(4r_2m^ds^2)\ge1/(1024r_2m^d)$.

For the inverse transpose lattice use the covering bound: every vector group $z$ is within squared distance $C_0/\lambda_D(h)$ of some lattice vector. For $0\ne f\in R^N$, take a shortest $v_0$ with $f^\mathsf Tv_0\ne0$ and write $b=Q_h(v_0)$. At some $w$ the nonzero algebraic integer pairing has modulus at least one. Put $y_w=h_w^{-1}\overline{f_w}$ and other $y$ components zero, and $S=Q_h(y)=f_w^\mathsf Ty_w>0$. Cauchy–Schwarz gives $Sb\ge1$. Scale $y$ to $z$ of squared length $5C_0/\lambda_D(h)$ and approximate by $v$ via the covering bound. Then $Q_h(v)<12C_0/\lambda_D(h)$ and
$$
|f_w^\mathsf T(z_w-v_w)|\le\sqrt{SC_0/\lambda_D(h)}<|f_w^\mathsf Tz_w|.
$$
Thus $f^\mathsf Tv\ne0$ and $b\le12C_0/\lambda_D(h)$. At scales $4s\le b$ all contributing lattice vectors pair to zero with $f$, so $Q_{T_s(h)}(y)=0$. At larger scales sum the bounds $4S/s$ geometrically. Together with $\mu(h)\ll\lambda_D(h)\ll1/b$ this gives $Q_{H(h)}(y)\ll S/b$. Cauchy–Schwarz in the new form gives $Q_{H(h)^{-\mathsf T}}(f)Q_{H(h)}(y)\ge S^2$, so its first factor is bounded below by a constant times $Sb\ge1$.

## Distortion

For a fixed scale take $Q=Q_h(z)$. On the union of contributing vectors $Q_h(v)\le6s$. The relative form inequality yields $|z_w^*(k_w-h_w)v_w|\le\delta\sqrt{Q_{h,w}(z_w)Q_{h,w}(v_w)}$ by normalizing $h_w$ to the identity. The squared terms vary by $O(\delta Qs)$ and the weights by $O(\delta)$. The ball count bounds their number by a constant times $Z_s(h)$, which counts at least the points of length squared $\le s$. The two denominators $Z_s(h),Z_s(k)$ are comparable by the same argument. Changing numerator and denominator therefore bounds the difference by $O(\delta Q/s)$. Summing over $s\gg\lambda(h)$ gives $O(\delta Q/\lambda(h))$. The outer cutoff changes at only a bounded number of scales $s\asymp1/\mu(h)$, with terms bounded by $O(\delta s\mu(h) Q/s)$. For sufficiently small $\delta$ this follows directly from comparability of the two $\mu$ values and bounded cutoff derivative. For the other $\delta\le1/4$ the values remain comparable by the factor bounds and inverse-transpose comparison, so the same conclusion holds after enlarging constants. The first term varies by $O(\delta\mu(h)Q)$. Divide the combined estimate by $Q_{H(h)}(z)\ge\mu(h)Q$ and use $\mu(h)\asymp\lambda_D(h)$.

## Lean correspondence

- [Definitions and hypotheses](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/PartitionUnitySmooth/Smoothing.lean#L17), [smoothness](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/PartitionUnitySmooth/GRSmooth.lean#L79), and [equivariance](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/PartitionUnitySmooth/RhoNonneg.lean#L113) give the map.
- [`term_low` and `pf_GRLow`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/PartitionUnitySmooth/QRNonneg.lean#L67), [`pf_GRDual`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/PartitionUnitySmooth/GRDual.lean#L120), and [`pf_GTrans`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/PartitionUnitySmooth/GTrans.lean#L104) give the thickness estimates. The covering bound compares the integral coordinate dual and the inverse-transpose lattice through the inverse different.
- [`pf_GTLip`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/PartitionUnitySmooth/RhoNonnegBis.lean#L239) and [`pf_GRLip`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/PartitionUnitySmooth/PfGRLip.lean#L364) give the relative error.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
