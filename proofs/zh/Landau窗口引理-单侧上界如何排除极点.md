# Landau 窗口引理

[阅读入口](landau-window.md)

## 第 1 节 · 黎曼猜想 · 《从窗口估计到黎曼猜想》续篇

**定理。** 任取实数 `0 < θ < 1`、`δ > 0`，函数 `g: ℝ → ℝ`、`Φ: ℂ → ℂ`，以及集合 `Z ⊆ ℂ`。假设下列三条成立，则每个 `ρ ∈ Z` 都满足 `Re ρ ≤ θ`。

**（一）增长与变换。** `g` 可测，存在实常数 `C₀`，对所有 `u ≥ 0` 有 `|g(u)| ≤ C₀ e^{2u}`。对每个 `Re s > 2` 的 `s`，有

```text
Φ(s) = ∫_{0}^{∞} g(u)e^{−su} du.
```

**（二）极点。** `Z` 位于 `Re s > 0` 内。该半平面中每个点都有一个去心邻域与 `Z` 不交。`Φ` 在该半平面除去 `Z` 后全纯。对每个 `ρ ∈ Z`，在 `ρ` 的某个去心邻域内，

```text
Φ(s) = c_{ρ}/(s − ρ) + h_{ρ}(s),
```

其中 `h_{ρ}` 在 `ρ` 附近全纯，`c_{ρ} ≠ 0`。若 `ρ` 为实数，则 `c_{ρ}` 为正实数。

**（三）窗口上的单侧上界。** 对每个实数 `η > 0` 和每个实数 `U₀`，存在 `U ≥ U₀` 及实值函数 `R: ℝ → ℝ`。在 `I = [U, (1 + δ)U]` 上，`R(u)e^{−θu}` 可积，且每一点都满足 `R(u) ≥ 0` 和 `g(u) ≤ R(u)`，并有

```text
∫_{I} R(u)e^{−θu} du ≤ e^{ηU}.
```

前两条合起来是 Lean 的 `PoleData g Φ Z`，即变换、增长和极点的全部资料。第三条是 `WindowHypU g θ δ`，即对数坐标里的窗口条件。在原讲义第 3 节，`g(u)` 是加权素数和的误差在 `y = e^{u}` 处的值，`Z` 来自狄利克雷 `L` 函数的零点。第 5 节说明如何代入。

## 第 2 节 · 让窗口外的积分足够小

对整数 `k ≥ 0` 和 `Re s > 2`，记

```text
A_{k}(s) = (−1)^{k}Φ^{(k)}(s)/k! = ∫_{0}^{∞} g(u) [u^{k}e^{−su}/k!] du. （1）
```

等式来自逐次对积分求导。取定 `s` 后，可在其邻域内保持 `Re s ≥ 2 + ε`，其中 `ε > 0`。由（一），第 `j` 次求导的积分差商可用 `C₀u^{j}e^{−εu}` 控制。这个界可积，故可用支配收敛。同样由（一），变换在任意 `Re s ≥ σ₀ > 2` 上满足 `|Φ(s)| ≤ C₀/(σ₀ − 2)`。若某个极点的实部大于 2，取 `2 < σ₀ < Re ρ`，这个有界性就与（二）的非零留数矛盾。因此 `Re ρ ≤ 2` 对所有 `ρ ∈ Z` 成立。

将选定一个只依赖 `δ` 的实数 `σ > 2`。对每个 `U ≥ 1`，写 `V = (1 + δ)U`、`s₀ = σ − 2`，并记窗外的积分核质量为

```text
T = ∫_{(0,∞) ∖ [U,V]} u^{k}e^{−s₀u}/k! du.
```

对 `0 ≤ ℓ < s₀`，在 `u > V` 一端乘上 `e^{ℓ(u−V)} ≥ 1`，在 `0 < u < U` 一端乘上 `e^{ℓ(U−u)} ≥ 1`。将两项积分各自扩至整个正半轴，再用分部积分公式 `∫_{0}^{∞}u^{k}e^{−au}/k! du = a^{−k−1}`（`a > 0`），便得到

```text
T ≤ e^{−ℓV}/a_{+}^{k+1} + e^{ℓU}/a_{−}^{k+1}, a_{±} = σ − 2 ∓ ℓ.
```

沿用原证明的取值，令 `ℓ = 2 + 6/δ`、`M = ℓ(1 + δ)`、`σ = M(ℓ + 2)`，以及 `k = ⌈(1 + δ/2)σU⌉`。此时 `σ − 2 > ℓ`、`M − 1 ≥ 1`、`k ≥ U`。用 `log(σ/a) ≤ (σ − a)/a`（`a > 0`）估计上式乘以 `σ^{k}` 后的两项。

第一项至多为 `a_{+}^{−1} exp(−MU + k/(M − 1))`，因为 `ℓV = MU` 且 `(σ − a_{+})/a_{+} = 1/(M − 1)`。由 `(1 + δ/2)σ = M(M − 1)` 及向上取整，指数至多为 `1/(M − 1) ≤ 1`。第二项至多为 `a_{−}^{−1} exp(ℓU − k(ℓ − 2)/a_{−})`。这里 `(1 + δ/2)(ℓ − 2) = ℓ + 1` 且 `ℓa_{−} ≤ (ℓ + 1)σ`，所以 `k(ℓ − 2) ≥ ℓUa_{−}`，指数至多为零。因此

```text
T ≤ C_{1}/σ^{k}, C_{1} = e/a_{+} + 1/a_{−}. （2）
```

## 第 3 节 · 用实轴上的导数吸收负值

固定上节选定的 `σ`，令 `E = σ − θ > 0`。任取 `η > 0` 和阈值 `U₀`，按（三）取 `U ≥ max{1, U₀}` 与 `R`，并按上节从这个 `U` 选 `k`。写

```text
w(u) = u^{k}e^{−σu}/k! (u ≥ 0).
```

任取 `γ ∈ ℝ`。按（1），因为 `|e^{−iγu}| = 1` 且 `g` 为实值，有

```text
|A_{k}(σ + iγ)| + Re A_{k}(σ) ≤ ∫_{0}^{∞} (|g(u)| + g(u))w(u) du.
```

这里 `|g| + g = 2 max(g, 0)`。所以在窗内，即使 `g` 取很大的负值，也有 `|g| + g ≤ 2R`。又由指数级数的第 `k` 项 `(Eu)^{k}/k! ≤ e^{Eu}`，得 `w(u) ≤ e^{−θu}/E^{k}`。条件（三）把窗内积分控制在 `2e^{ηU}/E^{k}` 以内。

窗外用增长上界 `|g| + g ≤ 2C₀ e^{2u}`，积分至多为 `2C₀T`。由（2），再利用 `E < σ` 及 `e^{ηU} ≥ 1`，得到同一个 `k ≥ U` 对所有 `γ` 都满足

```text
|A_{k}(σ + iγ)| + Re A_{k}(σ) ≤ C e^{ηU}/E^{k}, C = 2 + 2C₀C_{1}. （3）
```

`σ` 和 `C` 在选择 `η` 及窗口前已经固定。接下来只需证明，有一个实部大于 `θ` 的极点，就会产生一个增长太快的项。具体而言，若有固定的 `c_{*} > 0`、`M_{*} ≥ 0` 及 `0 < d < b ≤ E`，使（3）蕴含

```text
c_{*}/d^{k} ≤ M_{*}/b^{k} + C e^{ηU}/E^{k}, （4）
```

就取 `η = ½ log(b/d) > 0`，再取足够大的 `U₀ ≥ 1`。把（4）的右端除以左端，因 `k ≥ U`，所得比值至多为 `[(M_{*} + C)/c_{*}]e^{−ηU}`，它对所有足够大的 `U` 都小于 1。这将与（4）矛盾。

## 第 4 节 · 选圆盘，比较导数增长

假设 `ρ₀ ∈ Z` 且 `Re ρ₀ > θ`。以 `B(z,r)` 表示开圆盘。完全位于右半平面的闭圆盘只含有限多个 `Z` 中的点，否则紧致性会给出一个聚点。令 `D` 为 `E` 以及 `σ` 到闭圆盘 `|s − σ| ≤ E` 内各极点的距离的最小值。若闭圆盘内无极点，就有 `D = E`。于是 `0 < D ≤ E`，且 `B(σ,D)` 中无极点。

先说明两个圆盘估计。若 `Φ` 在 `B(z,r)` 全纯，柯西公式给出 `|A_{k}(z)| ≤ M/b^{k}`，其中 `0 < b < r`，`M` 可取半径 `b` 的圆周上的模最大值。若圆盘只有一个极点 `ρ ≠ z`，减去 `c_{ρ}/(s − ρ)` 后的函数在圆盘内全纯，连同 `ρ` 处也由（二）补成全纯函数。对它用同一估计并求出极点项的导数，得到

```text
|A_{k}(z) − c_{ρ}/(z − ρ)^{k+1}| ≤ M/b^{k} (0 < b < r).
```

**情形一。** 有一个极点 `ρ₁` 满足 `σ − Re ρ₁ < D`。把圆心从 `z₀ = σ + i Im ρ₁` 沿直线 `Re z = σ` 略作移动，仍有 `|z − ρ₁| < D`。同时可使距新圆心最近的极点唯一。具体地，取足够小的 `ε > 0`，使半径 `D + ε` 的 `z₀` 闭圆盘仍在右半平面。对 `|z − z₀| < ε`，离 `z` 小于 `D` 的极点都在这个有限候选集内。两不同候选到 `σ + iγ` 等距时，比较距离平方可知，虚部不同时至多排除一个 `γ`，虚部相同时因二者实部均小于 `σ` 而不可能等距。避开这些有限个值即可。

设最近极点为 `ρ`，令 `d = |z − ρ|`，取 `d < r ≤ D` 使 `B(z,r)` 只含这个极点，再取 `d < b < r`。单极点估计给出 `|A_{k}(z)| ≥ |c_{ρ}|/d^{k+1} − M/b^{k}`。实轴上的无极点圆盘 `B(σ,D)` 给出 `Re A_{k}(σ) ≥ −M′/b^{k}`。把两项相加代入（3），便是（4），其中 `c_{*} = |c_{ρ}|/d`、`M_{*} = M + M′`。

**情形二。** 每个极点都满足 `σ − Re ρ ≥ D`。由假想的 `ρ₀` 得 `D < E`，所以确有极点到 `σ` 的距离等于 `D`。距离不小于水平距离，等号迫使该极点是实数 `β = σ − D`。因此它是唯一达到距离 `D` 的极点。可取 `D < r ≤ E` 使 `B(σ,r)` 中只含 `β`，再取 `D < b < r`。由留数 `c_{β} > 0`，单极点估计给出 `Re A_{k}(σ) ≥ c_{β}/D^{k+1} − M/b^{k}`。对（3）取 `γ = 0`，其左端至少为 `Re A_{k}(σ)`，再次得到（4），其中 `d = D`、`c_{*} = c_{β}/D`。

两种情形都与（4）的增长比较矛盾，故 `Re ρ ≤ θ` 对每个 `ρ ∈ Z` 成立。证毕。

## 第 5 节 · 怎样把极点结论用于 RH？

取任意有限指标集 `J`。对每个 `j ∈ J`，取模数 `N_{j} ≥ 1`、狄利克雷特征 `χ_{j}` 和实权重 `a_{j} > 0`。要求 `N_{j} = 1` 或 `χ_{j}` 非平凡。这就是 Lean 的 `CharFamily`。对 `y > 0`，记 `S_{χ}(y) = ∑_{1≤n≤y} Λ(n)χ(n)(y/n − 1)`，空和为零。这里 `Λ(p^{m}) = log p`（`p` 为素数，`m ≥ 1`），其余为零。定义

```text
G_{𝟙}(y) = S_{𝟙}(y) − y log y + (1 + γ_{E})y,
G_{χ}(y) = S_{χ}(y) + y L′(1,χ)/L(1,χ) (χ 非平凡),
G_{F}(y) = ∑_{j∈J} a_{j} Re G_{χ_{j}}(y), g(u) = G_{F}(e^{u}).
```

这里 `𝟙` 是模 1 的平凡特征，`γ_{E}` 是欧拉常数。把 `Z` 取为所有满足 `Re ρ > 0` 且某个 `L(ρ,χ_{j})` 或 `L(ρ̄,χ_{j})` 为零的 `ρ`。

**此处引用的极点引理。** 对上述每个有限特征族，取刚定义的 `g` 与 `Z`，存在 `Φ: ℂ → ℂ` 使第 1 节的（一）（二）全部成立。这是 `Deduction.poleData` 的完整结论，本节用它来核实 Landau 引理的变换与极点前提。[极点引理的中文证明](%E4%BB%8E%E5%8A%A0%E6%9D%83%E7%B4%A0%E6%95%B0%E5%92%8C%E5%88%B0%E6%9E%81%E7%82%B9-%E7%95%99%E6%95%B0%E4%B8%BA%E4%BD%95%E4%B8%8D%E6%8A%B5%E6%B6%88.md)

极点引理里留数的来源是对数导数。若 `m_{j}(ρ)` 为 `ρ` 作为 `L(s,χ_{j})` 零点的重数，无零点时取 0，则引理在 `ρ ∈ Z` 给出的留数为

```text
−1/[ρ(ρ−1)] · ∑_{j∈J} (a_{j}/2) [m_{j}(ρ) + m_{j}(ρ̄)].
```

取实部带来共轭项，正权重使重数和严格为正。实极点在 `0 < ρ < 1`，所以留数为正。项目用 `Re s ≥ 1` 上的狄利克雷 `L` 函数非零定理处理该边界与右侧。

若对某个固定实常数 `B`、`0 < θ < 1` 和 `δ > 0`，任给实数 `Y₀` 都可找到 `Y ≥ Y₀`，使 `G_{F}(y) ≤ B y^{θ}` 对 `[Y,Y^{1+δ}]` 上每个 `y` 成立，则对任给 `η > 0, U₀ ∈ ℝ` 可在足够远的窗口取 `U = log Y ≥ max{1,U₀}` 和 `R(u) = |B|e^{θu}`。窗内 `R(u) ≥ g(u)`，而 `∫_{I}R(u)e^{−θu}du = |B|δU ≤ e^{ηU}`。这就验证了（三）。由本引理及 `Z` 的定义，所有这些 `L(s,χ_{j})` 在 `Re s > θ` 无零点。

回到原讲义，取 `δ = λ − 1`。若有实部 `β > ½` 的 ζ 零点，选 `½ < θ < min{β, 1}`。在原讲义的算术前提下，指数 `½ + (e_{D} + e_{L} + 7)ε` 的系数先于 `ε` 固定，故取足够小的 `ε > 0` 即可在任意远的窗口上得到 `G_{F}(y) ≤ y^{θ}`。族中含有 `𝟙`，由此排除该零点。最后由 ζ 的函数方程排除左侧的非平凡零点。本篇所证的环节接受窗口上界作为输入。

## 第 6 节 · 证明对应与证明范围

### 逐步定位

下列声明给出各步的源码位置。

- 命题的增长、极点、窗口条件为 `Deduction.PoleData` 和 `Deduction.WindowHypU`。原文第 15、25 行。[LandauZeroFreeCriterion.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauZeroFreeCriterion.lean)
- （1）对应 `Deduction.landau_coeff`，第 10 行。极点实部至多为 2 对应 `Deduction.landau_pole_re_le`，第 29 行。[LandauCoeff.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/LandauCoeff.lean) · [LandauPoleReLe.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/LandauPoleReLe.lean)
- （2）对应 `Deduction.landau_tails`，第 80 行，其窗外积分界在同文件第 18 行。基本积分公式见 `Deduction.kernel_integral`，第 9 行。逐项查询了 `landau_tails`。[landauTails.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/landauTails.lean) · [kernelIntegral.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/kernelIntegral.lean)
- 窗口内核上界见 `Deduction.landau_kernel_max`，第 9 行。单侧积分估计见 `Deduction.landau_window_ineq`，第 27 行。（3）和（4）的反证分别是 `Deduction.landau_window_key` 和 `Deduction.landau_window_contra`，第 40、20 行。逐项查询了 `landau_window_ineq` 和 `landau_window_key`。[LandauKernelMax.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/LandauKernelMax.lean) · [landauWindowIneq.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/landauWindowIneq.lean) · [landauWindow.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/landauWindow.lean)
- 第 4 节的分情形和最近极点分别由 `Deduction.landau_dichotomy`（第 24 行）和 `Deduction.landau_nearest`（第 36 行）给出。去主部后的导数界是 `Deduction.landau_pole_asym`（第 19 行）。合起来给出 `Deduction.landau_window`（第 83 行），逐项查询了其公理。[LandauDichotomy.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/LandauDichotomy.lean) · [LandauNearest.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/LandauNearest.lean) · [LandauPoleAsym.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/LandauPoleAsym.lean) · [landauWindow.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/landauWindow.lean)
- 第 5 节对应 `Deduction.poleData`（第 248 行）、`Deduction.lemmaL`（第 13 行）和 `Deduction.zeroFree_of_rpow_window`（第 11 行）。三条均已在另行查询公理。原工程由 `UpperTheory.Comparison₂.formB`（第 8 行）调用最后一条。[poleData.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/poleData.lean) · [lemmaL.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/lemmaL.lean) · [ZeroFreeOfRpowWindow.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/ZeroFreeOfRpowWindow.lean) · [Imports.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/PrimitiveCosets/Imports.lean)

### 公理与数学前提

逐项查询的七条声明只依赖 `propext`（命题外延）、`Classical.choice`（经典选择）及 `Quot.sound`（商中等价代表元相等）。没有 `sorryAx` 或项目自设公理。第 1 节三条是命题的数学假设，其中窗口上界是应用时须另外给出的条件。

本文所写的解析推论以窗口上界为假设。原项目的最终声明 `riemannHypothesis` 由 `rhOfAll` 得到，陈述中无外加参数。[Main.lean 第 4 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Main.lean#L4) · [原项目的独立核验](../../STATUS.md)
