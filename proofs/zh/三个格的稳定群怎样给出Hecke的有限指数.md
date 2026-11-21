# 三个格的稳定群怎样给出 Hecke 的有限指数

## 命题

设 $L$ 为数域，$R=O_L$，$\pi$ 为素元，$q=|R/(\pi)|\ge25$，$N\ge3$。令 $D_r=\operatorname{diag}(\pi,\ldots,\pi,1,\ldots,1)$ 有 $r$ 个 $\pi$，并令 $K_r=D_r^{-1}\mathrm{SL}_N(R)D_r$ 对 $r=0,1,2$。写 $E_{rs}=K_r\cap K_s$，$B=K_0\cap K_1\cap K_2$。则 $B$ 在各 $K_r$ 中指数有限，有

$$
[E_{02}:B]\ge25,\qquad [E_{01}:B]\ge25,
$$

且在 $K_0,K_1,K_2$ 中分别以 $E_{01},E_{12},E_{12}$ 为子群时，子群外至多一个双陪集。这是 `Arith` 及其返回的 `Tri`。若再假设 $L$ 全虚，则由 $K_0,K_1$ 生成的群在 $\prod_{w\mid\infty}\mathrm{SL}_N(\mathbb C)$ 中稠密。这是 `Dens`。两项共同用于 Hecke 谱隙。

## 一、交群在残余空间上稳定什么

设 $\mathbb F=R/(\pi)$。在 $K_r$ 中用 $\gamma=D_rgD_r^{-1}\in\mathrm{SL}_N(R)$ 表示 $g$。要 $g\in K_s$，等价于 $(D_sD_r^{-1})\gamma(D_sD_r^{-1})^{-1}$ 仍整。矩阵的行列式仍是 $1$，所以只需检查被除以 $\pi$ 的方块。

- 在 $K_0$ 的坐标中，$E_{01}$ 要求第一列在首项以外全是 $\pi$ 的倍数，即稳定 $\mathbb F e_0$。$E_{02}$ 对前两列在前两项之外提出同一要求，即稳定平面 $\langle e_0,e_1\rangle$。
- 在 $K_1$ 的坐标中，$D_2D_1^{-1}$ 只在第 $1$ 项乘 $\pi$，故 $E_{12}$ 稳定直线 $\mathbb F e_1$。
- 在 $K_2$ 的坐标中，$D_1D_2^{-1}$ 只在第 $1$ 项乘 $\pi^{-1}$，故 $E_{12}$ 要求第 $1$ 行在第 $1$ 项以外全是 $\pi$ 的倍数，即稳定坐标超平面 $x_1=0$。

从 $\mathrm{SL}_N(R)$ 到 $\mathrm{SL}_N(\mathbb F)$ 的约化满射，因为有限域上的特殊线性群由初等矩阵生成，每个初等矩阵可提起。这也说明在每套 $K_r$ 坐标中，模 $\pi$ 为单位阵的群包含在 $B$，所以指数有限。特殊线性群在有序的两条不同直线上传递。先把两条线的基向量分别送到指定线，再延拓为基变换并调整一个像向量的倍数，使行列式为 $1$。对偶空间给有序的两个不同超平面上的传递性。因而固定一条直线或超平面的子群在其余直线或超平面上传递，得到三个所报的双陪集条件。

在 $K_0$ 坐标中，$B$ 同时固定 $\ell_0=\mathbb Fe_0$ 和 $V_0=\langle e_0,e_1\rangle$。固定 $V_0$ 的群在 $V_0$ 内的直线上传递，可先在 $V_0$ 做变换，再在补空间调整行列式。因此 $[E_{02}:B]=q+1$。固定 $\ell_0$ 的群在包含它的平面上传递，例如按 $\mathbb F^N/\ell_0$ 的直线选基，再用缩放调整行列式。于是 $[E_{01}:B]=(q^{N-1}-1)/(q-1)$。由 $N\ge3$，两界都至少 $q+1\ge25$。这给出了源码所用的指数下界。

## 二、两个格稳定群生成稠密子群

记 $U_{ij}(a)=I+aE_{ij}$，$i\ne j$。$K_0$ 包含所有 $a\in R$ 的这种矩阵。$K_1$ 包含 $U_{0j}(a/\pi)$ 对 $j\ne0$ 成立，因为 $D_1$ 将该条目乘 $\pi$。令 $K=\langle K_0,K_1\rangle$。证明它包含所有 $U_{ij}(a/\pi^m)$ 对 $a\in R,m\ge0$。用三互异指标的直接矩阵恒等式

$$
[U_{ik}(b),U_{kj}(c)]=U_{ij}(bc).
$$

从 $m$ 到 $m+1$ 时，若 $i,j\ne0$，用 $U_{i0}(a/\pi^m)$ 和 $U_{0j}(1/\pi)$。若 $i=0$，取与 $0,j$ 不同的 $k$，用 $U_{0k}(1/\pi)$ 和 $U_{kj}(a/\pi^m)$。若 $j=0$，取与 $i,0$ 不同的 $k$，用已经得到的 $U_{ik}(a/\pi^{m+1})$ 和 $U_{k0}(1)$。这三种情况覆盖了全部不同指标。

全虚 $L$ 的 $R$ 在复处乘积内给一个满秩实格 $\Lambda$。$\bigcup_{m\ge0}\pi^{-m}\Lambda$ 稠密。为见此，若其闭包为真闭加法子群，可取一个非平凡实线性特征 $x\mapsto e^{2\pi i \lambda(x)}$ 在该闭包上恒为 $1$。这使用有限维实空间闭子群是向量子空间加一个离散格。于是 $\lambda$ 属于每个 $\pi^{-m}\Lambda$ 的对偶格，其交对应于 $\bigcap_m\pi^m\mathfrak D^{-1}$，其中 $\mathfrak D^{-1}$ 是迹对偶分式理想。交只有零，因为非零元素在 $(\pi)$ 的赋值有限。矛盾。源码 `dense_pow` 是这一稠密性步骤。

由参数的稠密性，$K$ 在无穷处的闭包包含对任意复向量 $(a_w)_w$ 的 $(U_{ij}(a_w))_w$。取只在一个无穷处非零的参数，再用各处的初等矩阵生成特殊线性群，得到整个乘积。这样完成稠密性。

## 源码对照

- `dg`、`Kg`、`Arith`、`Dens`，[Arith.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/Arith.lean)。`Tri`，[AEConst.lean 第 54 行附近](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/AEConst.lean)。
- `arith_holds`，[PArith.lean 第 721 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/PArith.lean)。源码用各胞腔的列或行条件，并用显式初等矩阵给两个指数下界。
- `mem_sup`、`dens_holds`，[IntegralTransvectionMemSlIntegersConjugateZero.lean 第 101、167 行附近](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/IntegralTransvectionMemSlIntegersConjugateZero.lean)。分母幂的稠密性 [PDensG.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/PDensG.lean)、[PDensM.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/PDensM.lean)。

本篇为源码对读。交群用模 $\pi$ 子空间表述了源码的矩阵条件。稠密性给出等价的迹对偶证明。
