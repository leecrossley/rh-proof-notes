# 缺失的 Hodge–Tate 权怎样控制近似不变量

## 命题

沿用[分圆生成元上的记号和全部条件](%E5%88%86%E5%9C%86%E7%94%9F%E6%88%90%E5%85%83%E7%9A%84%E4%BD%99%E4%B8%8D%E5%8F%98%E9%87%8F%E4%B8%BA%E4%BB%80%E4%B9%88%E7%94%B1%E6%9D%83%E5%B7%AE%E4%B9%98%E7%A7%AF%E6%B6%88%E5%8E%BB.md)。即给定素数 $\ell$、有限扩域 $K/\mathbb Q_\ell$、$m\ge1$（$\ell=2$ 时 $m\ge2$）、秩 $r\ge0$、分圆生成元 $g\in G_m$、整数矩阵表示 $U$ 和秩 $r$ 的 Hodge–Tate 基，其权属于有限集 $J$。设 $i\in\mathbb Z\setminus J$，令 $A(\sigma)=A_i(\sigma)$ 为按 $i$ 扭曲的半线性作用，$B\subset C^r$ 为闭单位球。对任意加法子群 $M\subseteq C^r$，假设 $B\subseteq M$ 且 $\ell M\subseteq B$。那么，对任意 $y\in C^r$，若

$$
A(\sigma)y-y\in M\qquad(\sigma\in G_m),
$$

则

$$
\ell^{2+N}y\in M,\qquad
N=\max\left(1,\sum_{u\in J\setminus\{i\}}(m+v_\ell(u-i))\right).
\tag{1}
$$

这就是 `prime_pow_smul_mem_of_twistedInvariant_mod_lattice`。缺失权条件 $i\notin J$ 确保真实的不变量为零。为从模 $M$ 的近似不变量走到真实不变量，还需要一次整数一阶上同调比较。

## 先估计整数一阶上同调的扭结

记 $\delta x(\sigma)=A(\sigma)x-x$。现取任意连续余闭链 $c:G_m\to B$，即 $c(\sigma\tau)=c(\sigma)+A(\sigma)c(\tau)$。假设某个非负整数 $k$ 及 $x_0\in B$ 满足 $\ell^k c=\delta x_0$。要证 $\ell^{1+N}c=\delta z$ 对某个 $z\in B$ 成立。这是 `cocycle_twist_coboundary_on_ball`，此处对 $i$ 无缺失权要求。

在 $H_\infty$ 上，$U=I$、$\chi=1$，因而 $A$ 就是逐坐标的伽罗瓦作用。使用分圆塔的 Tate 整数上同调结论。对这种作用的每条连续单位球值余闭链，其类被 $K_\infty$ 整数环中任一绝对值小于 $1$ 的元素消去。将它用在 $c|_{H_\infty}$ 和 $\ell$ 上，得 $x_1\in B$，使 $\ell c(h)=\delta x_1(h)$ 对所有 $h\in H_\infty$ 成立。定义 $c_1=\ell c-\delta x_1$。它仍为 $B$ 值余闭链，且 $c_1|_{H_\infty}=0$。

$c_1(g)$ 被 $H_\infty$ 固定。确切地说，对 $h\in H_\infty$，利用正规性比较

$$
c_1(hg)=A(h)c_1(g),\qquad
c_1(g(g^{-1}hg))=c_1(g).
$$

因此由 Tate 的分圆塔固定域定理，$c_1(g)\in\widehat{\mathcal O}_\infty^r$。同样 $x_2=\ell x_0-\ell^k x_1\in B$ 满足 $\ell^k c_1=\delta x_2$。限制到 $H_\infty$，$x_2$ 也在同一个固定整环内。

现在在生成元 $g$ 处应用[余不变量消去定理](%E5%88%86%E5%9C%86%E7%94%9F%E6%88%90%E5%85%83%E7%9A%84%E4%BD%99%E4%B8%8D%E5%8F%98%E9%87%8F%E4%B8%BA%E4%BB%80%E4%B9%88%E7%94%B1%E6%9D%83%E5%B7%AE%E4%B9%98%E7%A7%AF%E6%B6%88%E5%8E%BB.md)。由 $\ell^k c_1(g)=A(g)x_2-x_2$，可找到 $z_0\in\widehat{\mathcal O}_\infty^r$，使 $\ell^N c_1(g)=A(g)z_0-z_0$。因为 $z_0$ 被 $H_\infty$ 固定，所以 $d=\ell^N c_1-\delta z_0$ 在 $g$ 和 $H_\infty$ 都取零值。$g$ 的像拓扑生成 $G_m/H_\infty$：分圆特征在该商上识别 $1+\ell^m\mathbb Z_\ell$，$v_\ell(\chi(g)-1)=m$ 及二进条件使其在每个有限层的阶等于该层的群阶，见幂差赋值公式。余闭链公式使取零的集合为子群，且连续性使其闭。因此 $d$ 在 $G_m$ 上恒为零。展开得

$$
\ell^{N+1}c=\delta(z_0+\ell^N x_1).
\tag{2}
$$

右边的原像在 $B$ 中。

## 从余闭链回到原向量

令 $c(\sigma)=\ell(A(\sigma)y-y)$。它取值于 $B$，连续性及余闭链关系来自 $A$ 的半线性表示律。取充分大的 $k$，使 $\ell^{k+1}y\in B$，则 $\ell^k c=\delta(\ell^{k+1}y)$。将 (2) 用于这条 $c$，得到 $z\in B$ 使

$$
\delta(\ell^{N+2}y-z)=0.
$$

设 $v=\ell^{N+2}y-z$，用 Hodge–Tate 基写 $v=\sum_a v_a e_a$。对每个 $\sigma\in G_m$，固定性给 $\chi(\sigma)^{i-u_a}\sigma(v_a)=v_a$。由 $i\notin J$，每个 $i-u_a\ne0$。Tate 的权不变量定理断言，对有限扩域的绝对伽罗瓦群，$C$ 以任一非零整数次分圆特征扭曲后其固定向量空间为零。因此每个 $v_a=0$。于是 $\ell^{N+2}y=z\in B\subseteq M$，得到 (1)。

## 源码对照

- `torsion_killed` 先在无限分圆域的固定群上清掉一阶余闭链，再把剩下的方程压到一个生成元。[CocycleTwistCoboundaryOnBall.lean 第 244 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CocycleTwistCoboundaryOnBall.lean#L244)
- `cyclotomic_tate_maximalIdeal_kills_first_cohomology` 给单位球值一阶上同调的消去，`invariants_twist` 给非零扭曲的固定向量为零。[CyclotomicTateMaximalIdealKillsFirstCohomologyStatement.lean 第 7 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CyclotomicTateMaximalIdealKillsFirstCohomologyStatement.lean#L7) · [TateInvariantsCyclotomicTwist.lean 第 54 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TateInvariantsCyclotomicTwist.lean#L54)
- `pow_smul_mem_of_invariant_mod` 从 (2) 推出 (1)，所用 `Frame`、`HTBasis` 精确规定 $U$ 和权基。[PrimePowSmulMemOfTwistedInvariantModLattice.lean 第 254 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/PrimePowSmulMemOfTwistedInvariantModLattice.lean#L254) · [HTBasis.lean 第 66 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/Foundations/HTBasis.lean#L66)

以上为源码对读。两项 Tate 结论和固定整数环是明列的上游输入，消去指数怎样从它们和一个生成元的估计得出，已在正文展开。
