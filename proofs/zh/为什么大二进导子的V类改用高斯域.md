# 为什么大二进导子的 V 类改用高斯域

## 命题

取 [宿主参数](%E6%AD%A3%E5%8F%B7%E4%B8%8A%E5%90%8C%E8%B0%83%E7%9A%84%E4%B8%83%E7%A7%8D%E9%95%BF%E5%BA%A6%E4%BC%B0%E8%AE%A1%E6%80%8E%E6%A0%B7%E9%80%89%E7%94%A8.md) $h,\chi,Q,o,N,t,\ell,O,\psi$，其中 $\ell\in B_\chi$，$0<e<t$、$e=1$、$\psi$ 在 $H$ 上平凡且 $\psi(-1)=-1$。各条件的量词与 [小导子分支](%E4%B8%BA%E4%BB%80%E4%B9%88%E5%B0%8F%E4%BA%8C%E8%BF%9B%E5%AF%BC%E5%AD%90%E7%9A%84V%E7%B1%BB%E5%8F%AA%E9%9C%80%E4%B8%8B%E9%99%8D%E5%88%B0%E6%9C%89%E7%95%8C%E6%AC%A1%E6%95%B0%E7%9A%84%E5%9F%9F.md) 相同，这里改要求 $R_1\le2^{c_2(\psi)}$。结论是在下列变形与自守输入下，存在固定整数 $C'$ 使长度有限且

$$
\frac{\operatorname{length}_O V_{\ell,1}(\psi)}{v_O(\ell)}\log\ell\le(\ell N)^{C'}.
$$

这是 `CountV`。$V_{\ell,e}(\psi)$ 是 $G_{\mathbb Q}$ 对 $(\operatorname{Frac}O/O)(\varepsilon_\ell^{-e}\psi_G^{-1})$ 的一阶上同调中，在全部惯性群及 $\ell N$ 各素因子的分解群上限制为零的部分。

## 从大导子条件得到变形数据

令 $T=\{\ell\}\cup\{v\mid N:v\ne\ell,\ (\psi_{(\ell)})_v\ne1\}$，其中 $\psi_{(\ell)}$ 为 $\psi$ 的 $\ell$-幂阶部分。它的定义与 [秩四参考数据](%E6%80%8E%E6%A0%B7%E4%B8%BAII%E7%B1%BB%E5%92%8CIII%E7%B1%BB%E6%9E%84%E9%80%A0%E7%A7%A9%E5%9B%9B%E5%8F%82%E8%80%83%E6%95%B0%E6%8D%AE.md) 的 $T_b$ 相同，所以 $v\in T$ 蕴含 $v\mid\ell Q$。又 $n_0\ge2$，故

$$
R_1=16o(\ell Q)^2\,4^{n_0}\ge16\cdot9\cdot16>2^{11},
\qquad
8o\,v^2<R_1\le2^{c_2(\psi)} .
$$

因此 $c_2(\psi)\ge12$ 且 $2\ell Q\,4^{n_0}\le2^{c_2(\psi)}$。后者和从 $\psi$ 删除 $\ell$-幂阶分量及模二幂分量后所得 $\theta$ 的 $\operatorname{cond}(\theta^2)\mid Q$ 一起，给剩余 $-2$ 权消失所需的 `XData`。本段还用到宿主给每个奇素数分量互素阶部分的阶整除 $2o$。这些是 `HostData` 的数值条件。

令 $S=\{p:p\mid\ell N\}$，$\Gamma=G_{\mathbb Q,S}$，即允许在 $S$ 以及无穷处分歧的 Galois 群。记 $\eta$ 为模 $4$ 的二次特征，$\Psi=\varepsilon_\ell^e\psi_G$。因 $2\mid N$，$\eta,\Psi$ 均经 $\Gamma$ 分解。选定复共轭 $c$ 和每处的分解群、惯性群。这个数据称作 `HostFrame`。参考表示 $r_0(g)$ 的矩阵部分为 $\operatorname{diag}(\Psi(g),1,\Psi(g)^{-1})$，另一分量为 $\eta(g)$。矩阵部分在 $\eta(g)=1$ 的子群上是通常的表示，在另一陪集上按对偶自同构相乘。具体半直积在源码中用转置取逆再经反序矩阵共轭定义。于是 $\ker\eta$ 对应 $\mathbb Q(i)$，不可约性和迹计数都在这个固定高斯域中表述。

## 用分次变形估计长度

下面是实际调用的输入及它们提供的东西。

- `ThmS6_s` 给一个标记元素 $g_1\in\ker\eta$，使 $\Psi(g_1)^2-1$ 为单位。以此归一化表示的矩阵基，取满足指定局部条件的泛变形环。其环面权零部分有限于 $O$。每个在 $\ker\eta$ 上不可约的特征零点有 `BPrime_s`，即在高斯域的开子群及圆分核上仍不可约，并有高斯域的自守见证。
- `HostRigid_s` 在这些自守点给无穷小刚性，即保持局部条件的连续对偶数变形都为全局共轭。[`HostNumber_s`](%E6%80%8E%E6%A0%B7%E5%9C%A8%E9%AB%98%E6%96%AF%E5%9F%9F%E9%80%89%E5%90%8C%E4%B8%80%E4%B8%AA%E7%B4%A0%E5%A4%84%E4%BC%B0%E8%AE%A1%E7%A7%A9%E4%B8%89%E8%BF%B9%E5%B7%AE.md) 给一个固定 $\sigma\in\Gamma$ 及指数 $C$，使这些点的参考迹差 $\Delta_r=\operatorname{tr}r(\sigma)-\operatorname{tr}r_0(\sigma)$ 非零。对任意有限族在 $\ker\eta$ 上两两不同构的这些点，有 $\sum_r -\log|\Delta_r|_\ell\le(\ell Ne)^C$。所选 $\sigma$ 在选族之前给定。
- [`HostVanE`](%E6%80%8E%E6%A0%B7%E6%8A%8A%E9%9D%9E%E6%AD%A3%E6%9D%83%E7%9A%84%E6%95%B4%E7%B3%BB%E6%95%B0%E5%88%87%E5%90%91%E7%B1%BB%E5%8F%98%E6%88%90%E6%89%AD%E7%BB%93.md)、[`HostXpp`](%E4%B8%BA%E4%BB%80%E4%B9%88V%E7%B1%BB%E7%9A%84%E5%89%A9%E4%BD%99%E8%B4%9F%E4%BA%8C%E6%9D%83%E6%B2%A1%E6%9C%89%E4%B8%80%E9%98%B6%E7%B1%BB.md)、`Cl1` 分别给非正权整系数切向类的扭结性、剩余 $-2$ 权带局部条件的一阶消失、以及高斯域类数为一所给的非分歧一维特征消失。局部与全局有限性、Tate 对偶、Poitou–Tate 对偶及 Euler 特征给每个权的方程和变量的个数差。

在泛变形环，以 $\operatorname{diag}(t,1,t^{-1})$ 共轭给出的权对矩阵位置赋值为 $1,0,-1$ 之差。故各坐标权处于 $-2,-1,0,1,2$。将 $\operatorname{tr}u(\sigma)-\operatorname{tr}r_0(\sigma)$ 视为该环中元素 $a$。它为权零，且在参考点为零。每个正负权同时非零的两侧点都是 `BPrime_s` 中的点，故 $a$ 在它们上非零，其方程切空间也由共轭刚性约束在环面方向。

应用共用的 [分次长度引理](%E5%88%86%E6%AC%A1%E9%95%BF%E5%BA%A6%E5%BC%95%E7%90%86%E6%80%8E%E6%A0%B7%E5%8C%96%E6%88%90%E6%9C%89%E9%99%90%E8%BD%A8%E9%81%93%E4%B8%8A%E7%9A%84%E8%B5%8B%E5%80%BC%E4%BC%B0%E8%AE%A1.md)。它给一个有限轨道覆盖 $r_i$，并把次数 $-1$ 的余切长度 $V$ 界在迹差赋值之和之内。同一 $\ker\eta$ 上的同构可以由这个环面实现，故取最小覆盖后 $r_i|_{\ker\eta}$ 两两不同构。另一方面，有限商 $O/(a_0)$ 上的任意合条件的一阶类给次数 $-1$ 的余切对偶元素，$a_0$ 为任意非零标量。`abstract_count` 把这些步骤写成

$$
\operatorname{length}_O\operatorname{Sha}_{F}(O/(a_0))\le V
\le2v_O(\ell)\sum_i\frac{-\log|\Delta_{r_i}|_\ell}{\log\ell}
\qquad(a_0\ne0).
$$

这里有限系数的局部化核 $\operatorname{Sha}_F$ 的精确条件及如何返回 $V_{\ell,e}$，见 [有限层回到可除系数](%E6%80%8E%E6%A0%B7%E7%94%B1%E6%AF%8F%E4%B8%AA%E6%9C%89%E9%99%90%E7%B3%BB%E6%95%B0%E5%B1%82%E6%8E%A7%E5%88%B6%E5%8F%AF%E9%99%A4%E7%B3%BB%E6%95%B0%E7%9A%84%E6%80%BB%E9%95%BF%E5%BA%A6.md)。该比较给 $\operatorname{length}_O V_{\ell,e}(\psi)\le V$。现在乘 $\log\ell/v_O(\ell)$，再用选定 $\sigma$ 的迹差和上界，至多 $2(\ell Ne)^C\le(\ell Ne)^{C+1}$，最后令 $e=1$。这完成大导子分支。

## Lean 对照

- [`hostData_of_host`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeDeformations/HostDataOf.lean#L9) 由 $R_1$ 得局部输入。[`IsHostFrame`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeDeformations/IsHostFrame.lean#L32)、[`exists_hostFrame`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeDeformations/HostEx.lean#L55) 给 $\Gamma,\eta,\Psi$ 与素处的构造。
- [`ThmS6_s`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/ThmS6CoreS.lean#L17) 和 [`HostRigid_s`、`HostNumber_s`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/HostNumberS.lean#L12) 是各输入的精确量词。
- [`abstract_count`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeDeformations/AbstractCount.lean#L25)、[`vlen_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeDeformations/HostSha.lean#L131) 连接余切长度和上同调长度。
- [`countV_of_finiteness_duality_euler_host`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/CountVOf.lean#L33) 选取高斯域，合并各步。主窗口实际入口是 [`count_v_of_printed_bound_k_reduced_unitary_lift`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/LinkedUnlE.lean#L55) [`count_v_of_printed_bound_k_reduced_unitary_lift`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/LinkedUnlE.lean#L55)。本篇为发布版源码对照。
