# 零均值的 Hecke 平均为什么收缩

## 命题

设 $L$ 全虚，$R=O_L$，$\pi$ 为素元且 $|R/(\pi)|\ge25$，$N\ge3$。写 $G_\infty=\prod_w\mathrm{GL}_N(\mathbb C)$、$S=\prod_w\mathrm{SL}_N(\mathbb C)$。用各处嵌入把 $\Gamma=\mathrm{GL}_N(R)$ 视为 $G_\infty$ 子群，令 $D\subset S$ 是 $\mathrm{SL}_N(R)$ 的有限 Haar 测度基本域。$T$ 是以 $q_N=\operatorname{diag}(\pi,1,\ldots,1)$ 定义的归一化 Hecke 双陪集平均。

若 $f:G_\infty\to\mathbb R$ 连续，在左 $\Gamma$ 作用及左中心作用下不变，且 $f|_S$ 在 $D$ 上平方可积、均值为零，则 $Tf$ 仍有这些性质，且

$$
\int_D(Tf)^2\,d\mu \le (2/5)^2\int_D f^2\,d\mu.
$$

项目的 `SGap` 取较弱的 $(3/5)^2$。这个估计把[不变形式代表的构造](Hecke%E8%BF%AD%E4%BB%A3%E6%80%8E%E6%A0%B7%E6%8A%8A%E5%91%A8%E6%9C%9F%E7%A7%AF%E5%88%86%E5%BD%92%E5%88%B0%E4%B8%8D%E5%8F%98%E5%BD%A2%E5%BC%8F.md)中扣掉平均值的张量分量压到零。

## 一、把 Hecke 平均写成两个格群之间的投影

取 $L$ 上[三个格的稳定群](%E4%B8%89%E4%B8%AA%E6%A0%BC%E7%9A%84%E7%A8%B3%E5%AE%9A%E7%BE%A4%E6%80%8E%E6%A0%B7%E7%BB%99%E5%87%BAHecke%E7%9A%84%E6%9C%89%E9%99%90%E6%8C%87%E6%95%B0.md) $K_0,K_1,K_2$，沿无穷处嵌入 $S$，沿用同一记号。特别 $K_0=\mathrm{SL}_N(R)$，$K_1=q_N^{-1}K_0q_N$。在每个复处有标量使 $q_N$ 的像乘该标量后行列式为 $1$。记这个乘积中的元素为 $q_1\in S$。取 $D_0=D$，$D_1=q_1^{-1}D_0$ 为 $K_1$ 基本域。用同样方法给 $K_2$ 选基本域 $D_2$。左 Haar 测度给 $\mu(D_1)=\mu(D_0)$。令

$$
w(x)=f(q_1 x)\qquad(x\in S).
$$

它在 $K_1$ 下不变，在 $D_1$ 上平方可积且均值为零，平方积分等于 $f$ 在 $D_0$ 的平方积分。

写 $E_{01}=K_0\cap K_1$。在 $S$ 上，Hecke 平均等于

$$
v(x)=\frac1{[K_0:E_{01}]}\sum_{c\in E_{01}\backslash K_0} w(cx).
$$

理由是从 $\Gamma$ 和 $J=\Gamma\cap q_N^{-1}\Gamma q_N$ 的陪集，可改用 $K_0$ 的代表：对 $g\in\Gamma$，把 $\det g$ 放到首个对角元得到 $J$ 中同一行列式的矩阵，左除后便在 $K_0$。两个 $K_0$ 的代表相差左 $J$ 因子当且仅当相差左 $E_{01}$ 因子。又 $q_1$ 与 $q_N$ 的复嵌入只差中心，故 $f$ 取值相同。有限平均保持连续性，$\Gamma$ 左移置换右陪集，中心左移可逐项用不变性去掉。所以 $Tf$ 在整个 $G_\infty$ 上仍有连续性和两种不变性。

## 二、三个子群的几何给出 $2/5$

令 $B=K_0\cap K_1\cap K_2$，取 $B$ 的基本域 $D_B$。考虑 $B$-不变函数在 $D_B$ 上的 Hilbert 空间，约定以相等几乎处处为同一元素。对 $H\supseteq B$，写 $W(H)$ 为 $H$-不变子空间。有限陪集平均是到 $W(H)$ 的正交投影，基本域积分按指数伸缩。[陪集平均为何是投影](%E4%B8%A4%E7%B1%BB%E9%99%AA%E9%9B%86%E6%80%8E%E6%A0%B7%E6%8A%8A%E7%9B%B8%E5%85%B3%E6%80%A7%E5%8E%8B%E5%88%B0%E4%BA%94%E5%88%86%E4%B9%8B%E4%B8%80.md)

取 $W_1=W(E_{01})$、$W_2=W(E_{02})$、$W_3=W(E_{12})$。依次取 $K_{12}=W(K_0), K_{13}=W(K_1), K_{23}=W(K_2)$。三个角度界由[有限陪集的相关性](%E4%B8%A4%E7%B1%BB%E9%99%AA%E9%9B%86%E6%80%8E%E6%A0%B7%E6%8A%8A%E7%9B%B8%E5%85%B3%E6%80%A7%E5%8E%8B%E5%88%B0%E4%BA%94%E5%88%86%E4%B9%8B%E4%B8%80.md)给出：分别在 $K_0,K_1,K_2$ 里比较 $E_{01}$ 与 $E_{02}$、$E_{12}$ 与 $E_{01}$、$E_{12}$ 与 $E_{02}$。两类双陪集条件与所需指数至少 $25$ 都来自上一节的三个格。于是每个角度满足 $1/5$ 界。

$v$ 是 $W(K_0)$ 中的元素，$w$ 是 $W(K_1)$ 中的元素。用两次陪集平均的复合，先平均到 $E_{01}$ 再到 $K_0$ 等于直接平均到 $K_0$。因为 $w$ 已在 $E_{01}$ 下不变，故 $v$ 恰是 $w$ 在 $W(K_0)$ 上的正交投影。展开基本域也给 $\int_{D_B}v=\int_{D_B}w=[K_1:B]\int_{D_1}w=0$。

现说明 $v$ 与三个 $W_i$ 的公共交集正交。一个公共不变类在整个 $S$ 上几乎处处地对 $E_{01},E_{02},E_{12}$ 不变。这可用 $B$ 的基本域把等式延拓到其可数多个平移得到。群 $K_0$ 由 $E_{01}$ 和 $E_{02}$ 生成：取 $E_{02}\setminus E_{01}$ 的一个元素，$K_0$ 的每个不在 $E_{01}$ 中的元素都在它的 $E_{01}$ 双陪集内。群 $K_1$ 同理由 $E_{12}$ 和 $E_{01}$ 生成。故该公共不变类在由 $K_0,K_1$ 生成的稠密子群下几乎处处不变。用 `AEConst`：在局部紧、第二可数的群上，可测实函数若对稠密子群中每个元素的左平移都几乎处处不变，则它几乎处处为常数。这可通过先截成有界函数、以紧支撑连续函数的卷积把平移不变延拓到闭包，再用逼近恒等元恢复原函数。于是公共交集只含常数，$v$ 的零积分给所需的正交。

因为 $v\in W_1\cap W_2$ 且 $w\in W_1\cap W_3$，[三子空间投影不等式](%E4%B8%89%E4%B8%AA%E5%AD%90%E7%A9%BA%E9%97%B4%E7%9A%84%E6%8A%95%E5%BD%B1%E6%80%8E%E6%A0%B7%E7%BB%99%E5%87%BA%E4%BA%94%E5%88%86%E4%B9%8B%E4%BA%8C.md)给 $|\langle v,w\rangle|\le(2/5)\|v\|\|w\|$。但 $v$ 是 $w$ 的正交投影，左边等于 $\|v\|^2$，故 $\|v\|\le(2/5)\|w\|$。这些范数都在 $D_B$ 上。换回 $D_0,D_1$，两个平方范数分别除以 $[K_0:B]$ 和 $[K_1:B]$。这两个指数相等，因为通过基本域展开，它们分别是 $\mu(D_B)/\mu(D_0)$ 和 $\mu(D_B)/\mu(D_1)$，且 $D_0,D_1$ 等体积。于是得到命题的平方收缩界。零均值也随同样的积分伸缩保留。

## 源码对照

- `SGap`，[SBridgeAlt.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/SBridgeAlt.lean)。`sGap_of`、`sGap_of_parts`，[SGapOf.lean 第 13 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/SGapOf.lean)、[SGapOfParts.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/SGapOfParts.lean)。后者对边界常数先给 $2/5$，再放宽为 $3/5$。
- `gapAbs_of`，[PGapAbs.lean 第 12 行附近](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/PGapAbs.lean)。几乎处处不变类与常数 [PAEConst.lean 第 80 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/PAEConst.lean)。
- 三个格群及其约化与稠密性 [Arith.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/Arith.lean)、[PArith.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/PArith.lean)、[IntegralTransvectionMemSlIntegersConjugateZero.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/IntegralTransvectionMemSlIntegersConjugateZero.lean)。

本篇为源码对读。有限基本域、Haar 测度展开以及稠密平移不变量的性质在证明中分别定位。
