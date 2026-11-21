# Hecke 迭代怎样把周期积分归到不变形式

## 命题

设 $L$ 为全虚数域，$k\ge0$ 且 $k+1<r_2(L)$。对每个指定下界 $N_0$，可取 $N\ge N_0$，使下述结论成立。令 $G_N=\mathrm{GL}_N(O_L)$，$X_N$ 是各个复处的 $N$ 阶正定 Hermitian 矩阵的乘积。对任意 $G_N$ 的平凡实系数齐次 $(k+1)$ 阶余闭链 $c$，存在 $\prod_{w\mid\infty}\mathrm{GL}_N(\mathbb C)$ 不变的 $(k+1)$ 阶形式 $\omega_b$，使 $c$ 和 $\omega_b$ 在所有 $G_N$ 的 $(k+1)$ 阶周期 $z$ 上取值相同。形式的取值是对以 $g_iI$ 为各顶点的仿射单形积分，再对 $z$ 线性延拓。这是 `SSurj`，用于[消掉高权之后的秩比较](%E4%B8%BA%E4%BB%80%E4%B9%88%E9%87%8D%E5%A4%8D%E7%9F%A9%E9%98%B5%E5%9D%97%E4%BB%A5%E5%90%8E%E5%8F%AA%E5%89%A9%E6%AF%8F%E4%B8%AA%E5%A4%8D%E5%A4%84%E4%B8%80%E4%B8%AA%E6%96%B9%E5%90%91.md)。

## 一、先把余闭链做成可积分的形式

写 $G_\infty=\prod_w\mathrm{GL}_N(\mathbb C)$。若 $\omega$ 是 $X_N$ 上的形式，记 $F_\omega(x)$ 为把 $\omega_{x\cdot I}$ 沿 $x$ 的切向作用搬回 $I$ 的张量，源码记作 `fr`。令 $(\mathcal D,\mu)$ 是 $SL_N(O_L)$ 在 $\prod_w SL_N(\mathbb C)$ 上左作用的有限测度基本域和 Haar 测度，把 $y\in\mathcal D$ 在 $G_\infty$ 中的像写作 $x_y$。

选择生成一个绝对范数至少 $25$ 的素理想的素元 $\pi$。对 $N$ 的选择还须满足 $N\ge3$、Hecke 周期判别的起点和下面的高度矩条件。各条件所给的起点与 $c$ 无关。`SPU` 先取统一指数 $a$，给一个由高度 $\mathrm{ht}^a$ 控制的等变单位分解。`SMom` 允许 $N$ 充分大，使某个上述域满足

$$
\int_{\mathcal D}\mathrm{ht}(x_y)^{2a(k+1)}\,d\mu(y)<\infty .
$$

平滑化与中心化 `SWhit`、`SCen` 在这里给出如下结论：对任意所给余闭链 $c$，存在连续的 $(k+1)$ 阶形式 $\omega'$，在 $G_N$ 和无穷处全中心下不变，单形积分构成闭的齐次余链，在所有周期上与 $c$ 的取值相同，且

$$
\|F_{\omega'}(x)\|\le K\mathrm{ht}(x)^{a(k+1)}\qquad(x\in G_\infty).
$$

先用单位分解把 $c$ 平滑化，其积分周期保持不变，得到各中心分量绝对值相等时的不变性。再用中心化获得全中心不变性。后一步对紧集右移后的高度只需改变常数，`SHt` 给出的恰是这种控制。于是 $F_{\omega'}$ 在 $\mathcal D$ 上平方可积，因测度有限也可积。

这四项构造见[轨道单位分解](%E6%80%8E%E6%A0%B7%E4%BB%8E%E5%8E%9A%E9%83%A8%E6%9E%84%E9%80%A0%E5%85%A8%E7%A9%BA%E9%97%B4%E7%9A%84%E5%8D%95%E4%BD%8D%E5%88%86%E8%A7%A3.md)、[余闭链的平滑](%E5%8D%95%E4%BD%8D%E5%88%86%E8%A7%A3%E6%80%8E%E6%A0%B7%E6%8A%8A%E7%BE%A4%E4%BD%99%E9%97%AD%E9%93%BE%E5%8F%98%E6%88%90%E5%BE%AE%E5%88%86%E5%BD%A2%E5%BC%8F.md)、[中心方向的平均](%E6%80%8E%E6%A0%B7%E6%B2%BF%E5%8D%95%E4%BD%8D%E6%96%B9%E5%90%91%E5%B9%B3%E5%9D%87%E5%87%BA%E4%B8%AD%E5%BF%83%E4%B8%8D%E5%8F%98%E5%BD%A2%E5%BC%8F.md)、[有限高度矩](Siegel%E9%9B%86%E5%90%88%E9%87%8C%E7%9A%84%E4%BD%93%E7%A7%AF%E6%80%8E%E6%A0%B7%E6%8E%A7%E5%88%B6%E9%AB%98%E5%BA%A6%E7%9F%A9.md)。

## 二、取平均并扣掉平均值

`SMean` 的陈述是：对任意连续、在 $G_N$ 与全中心下不变的 $q$ 阶形式，其 $F_\omega$ 若在 $\mathcal D$ 上可积，则存在全 $G_\infty$ 不变的 $q$ 阶形式 $\omega_b$，满足

$$
F_{\omega_b}(x)=\mu(\mathcal D)^{-1}\int_{\mathcal D}F_\omega(x_y)\,d\mu(y)\quad(x\in G_\infty).
$$

源码对 $\mu(\mathcal D)=0$ 使用逆元为零的约定。这里用它构造 $\omega_b$，再设 $\eta=\omega'-\omega_b$。给定任一组切向量 $u=(u_1,\ldots,u_{k+1})$，函数 $f_u(x)=F_\eta(x)(u)$ 连续，在 $G_N$ 与中心下不变，在 $\mathcal D$ 上平方可积且积分为零。平方可积由平方可积函数减常数得到。均值为零是把线性取值移进张量积分后直接相消。`SInv` 还给 $\omega_b$ 的单形积分余链闭性，故 $\eta$ 也有该性质。要证的只剩 $\eta$ 的周期取值为零。

平均为什么能延拓成不变形式，见[基本域上的张量平均](%E4%B8%BA%E4%BB%80%E4%B9%88%E5%9F%BA%E6%9C%AC%E5%9F%9F%E4%B8%8A%E7%9A%84%E5%BC%A0%E9%87%8F%E5%B9%B3%E5%9D%87%E8%83%BD%E5%BB%B6%E6%8B%93%E6%88%90%E4%B8%8D%E5%8F%98%E5%BD%A2%E5%BC%8F.md)。

## 三、从 $L^2$ 收缩得到每条周期上的收缩

记 $T$ 为源码以 $\pi$ 定义的归一化 Hecke 双陪集算子。`SGap` 的具体输入是：全虚 $L$、$|O_L/(\pi)|\ge25$、$N\ge3$ 时，对任一上述连续不变、平方可积且均值为零的实函数 $f$，$Tf$ 仍有这些性质，且 $\|Tf\|_{L^2(\mathcal D)}\le(3/5)\|f\|_{L^2(\mathcal D)}$。因此第 $r$ 次迭代的平方范数至多为 $(3/5)^{2r}\|f\|_2^2$。

对形式定义相应的有限 Hecke 平均 $\eta_r=T^r\eta$。搬回基点后在任一 $u$ 上取值，与先在 $u$ 上取值再做函数 Hecke 平均相同；有限平均也与单形积分及取边界交换。选 Hermitian 切空间的一组基，按所有有序 $(k+1)$ 元组 $u$ 取分量。有限维性给常数 $K_1$，使任意交替张量 $A$ 满足 $\|A\|^2\le K_1\sum_u|A(u)|^2$。逐项用上面的函数界，得到

$$
\int_{\mathcal D}\|F_{\eta_r}(x_y)\|^2d\mu(y)
\le K_1(3/5)^{2r}\sum_u\|f_u\|_2^2 .
$$

`SLoc` 说，对每个固定周期 $z$ 有常数 $C_z$，使任何上述连续、积分余链闭、在 $G_N$ 和中心下不变且搬回张量平方可积的形式 $\xi$ 都满足

$$
|I_{\xi,N}(z)|\le C_z\left(\int_{\mathcal D}\|F_\xi(x_y)\|^2d\mu(y)\right)^{1/2}.
$$

应用于 $\xi=\eta_r$，得 $|I_{\eta_r,N}(z)|\le C'_z(3/5)^r$，且 $C'_z$ 不依赖 $r$。

最后用 `SHecke` 的周期判别：在 $k+1<r_2(L)$ 且 $N$ 充分大时，对定义在 $\mathrm{GL}_N(L)$ 的齐次元组上、在 $\mathrm{GL}_N(O_L)$ 下不变的余闭链，若每个周期 $z$ 都有常数 $C'_z$ 使其第 $r$ 次 Hecke 迭代取值被 $C'_z(3/5)^r$ 控制，则原余闭链在所有周期上为零。应用于 $\eta$ 的单形积分余链，闭性已在上一节确认。于是 $I_{\eta,N}=0$ 于周期上，故 $c$ 的取值等于 $I_{\omega_b,N}$。

## 源码对照

- `SSurj`、`SHecke`、`SWhit`、`SCen`、`SGap`、`SLoc`、`SMean` 的量词在 [SBStar.lean 第 20 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/SBStar.lean) 和 [SBridgeAlt.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/SBridgeAlt.lean)。这里展开了 `JoinReconstruction.key` 的实际合成，[LemForm.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/IteratedHeckeBounds/LemForm.lean)。
- 均值消去 [LemLz.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/IteratedHeckeBounds/LemLz.lean)，平方范数迭代和周期比较 [LemBound.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/IteratedHeckeBounds/LemBound.lean)。
- `sHecke_of`、`sGap_of`、`sLoc_of` 的入口分别在 [SHeckeOf.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/SHeckeOf.lean)、[SGapOf.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/SGapOf.lean)、[SLocOf.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/CompactLocalSets/SLocOf.lean)。

本篇为源码对读。[Hecke 收缩](%E9%9B%B6%E5%9D%87%E5%80%BC%E7%9A%84Hecke%E5%B9%B3%E5%9D%87%E4%B8%BA%E4%BB%80%E4%B9%88%E6%94%B6%E7%BC%A9.md)、[周期的均方控制](%E6%80%8E%E6%A0%B7%E7%94%A8%E5%9D%87%E6%96%B9%E8%8C%83%E6%95%B0%E6%8E%A7%E5%88%B6%E4%B8%80%E6%9D%A1%E5%91%A8%E6%9C%9F%E7%A7%AF%E5%88%86.md)和[周期衰减判别](%E4%B8%BA%E4%BB%80%E4%B9%88Hecke%E5%91%A8%E6%9C%9F%E4%B8%8D%E8%83%BD%E4%BB%A5%E4%BA%94%E5%88%86%E4%B9%8B%E4%B8%89%E8%A1%B0%E5%87%8F.md)均有独立译稿。平滑化与中心化以及积分域的高度矩在正文逐项写出它们在此提供的结论。
