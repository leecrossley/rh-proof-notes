# Siegel 集合里的体积怎样控制高度矩

## 命题

设 $L$ 为全虚数域，$A\ge0$ 是整数，$N\ge A+2$。令 $S=\prod_{w\mid\infty}\mathrm{SL}_N(\mathbb C)$，$\Gamma=\mathrm{SL}_N(O_L)$ 按各处嵌入。则存在 $\Gamma$ 的一个有限 Haar 测度基本域 $D\subset S$，使

$$
\int_D\mathrm{ht}(x)^A\,d\mu(x)<\infty.
$$

这里 $\mathrm{ht}$ 是[格及逆转置形式的最短向量所定的高度](%E6%A0%BC%E4%B8%8E%E5%AF%B9%E5%81%B6%E6%A0%BC%E7%9A%84%E6%9C%80%E7%9F%AD%E5%90%91%E9%87%8F%E6%80%8E%E6%A0%B7%E5%AE%9A%E4%B9%89%E9%AB%98%E5%BA%A6.md)。此为 `SMom` 实际采用的 $N$ 起点。它使增长至多为 $\mathrm{ht}^{a(k+1)}$ 的形式，当 $N$ 足够大时可做平方积分。

## 一、把无穷远分成对角指数盒

对 $\sum_i s_i=0$ 的实向量 $s=(s_0,\ldots,s_{N-1})$，记 $a(s)=\operatorname{diag}(e^{s_i})$，各复处取同一矩阵。定义

$$
W(s)=\sum_{i=0}^{N-2}|s_i-s_{i+1}|,\qquad
\Phi(s)=\sum_{i<j}(s_i-s_j).
$$

这儿的 Siegel 集合由 $p\,a(s)\,k$ 组成，$p$ 为各处上三角矩阵，条目统一有界且对角模长统一远离零，每列的对角模长在各处的乘积为 $1$。$k$ 为各处特殊酉矩阵。对 $s$ 要求 $s_{i+1}\le s_i+T$。把这组 $p$ 记作 $P$，它是紧集。将 $s_i$ 限制在 $[m_i,m_i+1]$，其中 $m_i\in\mathbb Z$，所得部分记为 $X_m$，也是紧集。所有 $X_m$ 覆盖 Siegel 集合，因为每个 $s_i$ 可取下整。

源码的体积估计是：对 $X_m$ 里任意一份允许的 $s^{(0)}$，有

$$
\mu(X_m)\le C\,e^{-2\Phi(s^{(0)})},
$$

其中 $C$ 与 $m,s^{(0)}$ 无关。下面写出 `pack` 的证明。

固定一个复处。在该处取上三角幺幂矩阵 $u$，令每个 $i<j$ 条目独立遍历模长至多 $2e^{s^{(0)}_i-s^{(0)}_j}$ 的高斯整数，其余处取单位阵。每个圆盘由内接正方形数整点，半径参数小于一时仍有零点。故这样的 $u$ 至少有 $C_1e^{2\Phi(s^{(0)})}$ 个，$C_1>0$ 仅依赖固定维数。源码逐项数矩形格点。

所有平移 $uX_m$ 都在 $a(s^{(0)})$ 乘一个固定紧集之内。确实 $a(-s^{(0)})u a(s^{(0)})$ 各上三角条目有界。$a(-s^{(0)})p a(s^{(0)})$ 也有界，因为对 $i<j$ 乘的 $e^{s^{(0)}_j-s^{(0)}_i}$ 至多 $e^{(j-i)T}$。剩余因子为 $a(s-s^{(0)})k$，由两个 $s$ 在同一整数盒中仍有界。行列式为一，故把所有这些有界矩阵放入一个固定紧集。

这些平移的重叠数也一致有界。若 $u p a(s) k=u' p' a(s') k'$，则

$$
u^{-1}u'=p\,a(s)(k k'^{-1})a(-s')p'^{-1}.
$$

在所选复处，左边与其余非酉因子都上三角，所以 $kk'^{-1}$ 上三角。上三角酉矩阵是对角矩阵，故 $a(s)(kk'^{-1})a(-s')=a(s-s')(kk'^{-1})$ 有界。$p,p'^{-1}$ 在紧集内，故 $u^{-1}u'$ 的高斯整数条目统一有界。固定 $u$ 后只有有限个可能的 $u'$，数目由同一个常数控制。用 Haar 左不变，对各平移的指示函数求和积分，得 $\#\{u\}\mu(X_m)$ 至多为固定紧集的体积乘这个重叠数，给上面的指数界。

## 二、体积衰减胜过高度增长

对一个固定的有理平移 $c\in S$，这里“有理”系指各处等于一个 $\mathrm{GL}_N(L)$ 矩阵的像乘标量，有

$$
\mathrm{ht}(c p a(s) k)\le C_c e^{2W(s)} .
$$

按 `sHtB` 的两条最短向量证明：写 $c_w=z_w w(g)$。取共同正整数 $d$ 清 $g^{-1}$ 和 $g^\mathsf{T}$ 的分母。对第一个最小值 $m((c p a(s) k)^{-1})$，向量先经 $g^{-1}$，再经 $p_w^{-1}$、$a(-s)$ 和酉矩阵。选 $g^{-1}y$ 最后一个非零坐标，因 $p_w^{-1}$ 上三角，该坐标只乘 $p_w^{-1}$ 的对角元。该元模长有统一正下界，且 $d(g^{-1}y)_i$ 是非零代数整数，至少一处的绝对值 $\ge1$。于是该最小值至少为常数乘 $e^{-2\max_i s_i}$。对第二个最小值 $m((c p a(s) k)^\mathsf{T})$，选 $g^\mathsf{T}y$ 第一个非零坐标，因为 $p_w^\mathsf{T}$ 下三角。得下界为常数乘 $e^{2\min_i s_i}$。两界取乘积后再倒数，且 $\max s-\min s\le W(s)$，即得所报估计。

令 $h_i=s_i-s_{i+1}\ge-T$。由于

$$
\Phi(s)=\sum_{i=0}^{N-2}(i+1)(N-i-1)h_i,
$$

每个正 $h_i$ 的系数至少 $N-1$，每个负 $h_i$ 的绝对值至多 $\max(T,0)$。因此 $\Phi(s)\ge(N-1)W(s)-C_T$。对 $B<2(N-1)$，有常数 $C'$ 和 $\epsilon>0$，使

$$
B W(s)-2\Phi(s)\le C'-\epsilon\sum_i |s_i|.
$$

这里用 $\sum_i |s_i|\le N W(s)$，由 $\sum_i s_i=0$ 及首尾之间的总变差界得到。在每个 $X_m$ 上，把点的 $e^{B W(s)}$ 界与同一 $s$ 的体积界相乘，用 $\sum_i |s_i|\ge\sum_i|m_i|-N$，即可将积分界成常数乘 $e^{-\epsilon\sum_i |m_i|}$。对所有整数盒求和，等于有限个一维收敛几何级数相乘。因此取 $B=2A$ 时该高度矩在每个有理平移的 Siegel 集合上有限，因为 $A+1<N$。

## 三、从覆盖得到基本域积分

还用定量归约 `SRed`：对全虚 $L$ 和 $N\ge1$，存在有限个上述有理平移 $c_i$ 与共同的 $P,T$，使 $S$ 的每个点经某个 $\Gamma$ 左移后，都落在 $\bigcup_i c_i\,\mathrm{Sieg}(P,T)$。这个结论提供有限个可积集合的覆盖，源码先给一般线性群的归约，再经单位模 $N$ 次幂的有限商调整为特殊线性群。

对任意非负 $\Gamma$-不变函数，在一个基本域上的积分至多为在上述覆盖集上的积分。用基本域展开，右侧等于按每个点的轨道落入覆盖集的次数加权，覆盖给重数至少一。应用于 $\mathrm{ht}^A$，第二节给有限性。应用于常数 $1$，也得到基本域有限体积。故可以取这样的 $D$，并在其上使用 $L^2$ 等式。

## 源码对照

- `Sieg`、`W`、`SHtB`、`SIntB`、`SRed`，[InstLCSL.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/MomentEntryBounds/InstLCSL.lean)。第一节的 `pack`，[MtInvUpper.lean 第 62 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/IntegralMomentReduction/MtInvUpper.lean)。
- `sHtB`，[PrimalY.lean 第 125 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/IntegralMomentReduction/PrimalY.lean)。整数盒上积分与收敛级数 `main_of_pack`，[SetLIntegralLeOfMul.lean 第 37 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/IntegralMomentReduction/SetLIntegralLeOfMul.lean)。
- `sRed_of`，[SRedOf.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/IntegralMomentReduction/SRedOf.lean)。`sMom_of_parts`、`sMom_of`，[SetLIntegralPreimageMulLeft.lean 第 68 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/MomentEntryBounds/SetLIntegralPreimageMulLeft.lean)、[SMomOf.lean 第 10 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/IntegralMomentReduction/SMomOf.lean)。

本篇为源码对读。有限个有理平移覆盖的归约结论按第三节的完整形式使用。高度点态界、指数盒的体积和可积性已经展开。
