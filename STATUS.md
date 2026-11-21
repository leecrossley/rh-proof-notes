# Reading and review status / 译稿与复核状态

[English home](README.md) · [中文首页](README.zh-CN.md) · [Sources / 来源](SOURCES.md) · [Contributing / 贡献说明](CONTRIBUTING.md)

The [Chinese proof catalogue](PROOFS.zh-CN.md) lists 340 full-length notes. Five Chinese reading guides and six English notes provide entry points. The table tracks these routes and records the provenance of the two English adaptations.

[中文证明目录](PROOFS.zh-CN.md)收录 340 篇正文。下面跟踪 5 篇中文导读和 6 篇英文稿所覆盖的入门路线，并标明两篇英文改编稿。目录中各篇的默认状态是草稿。认领或复核时请写明对应篇目和 Lean 声明。

**Draft / 草稿** means prose with Lean references. **Human-reviewed / 人工复核** requires a named reviewer and a record of the portion reviewed. The scope of each note is its stated implication. The open items below concern links needed to read the full route end to end.

| Deduction / 推导 | 中文 | English | Prose review / 正文复核 | Scope and open input / 范围与待补输入 |
| --- | --- | --- | --- | --- |
| Window estimates to RH / 窗口估计到 RH | [中文](proofs/zh/from-windows-to-rh.md) | [English](proofs/en/from-windows-to-rh.md) | Draft / 草稿 | Starts from a uniform estimate on arbitrarily late windows / 窗口上界作为输入 |
| Landau window lemma / Landau 窗口引理 | [中文](proofs/zh/landau-window.md) | [English](proofs/en/landau-window.md) | Draft / 草稿 | Analytic deduction from growth, pole and window hypotheses / 给定增长、极点与窗口条件 |
| Pole data of the weighted sum / 加权和的极点资料 | [中文](proofs/zh/pole-data.md) | To write / 待写 | Draft / 草稿 | Mellin transforms and the residue calculation / Mellin 变换与留数计算 |
| A common window / 共用窗口 | [中文](proofs/zh/common-window.md) | [English](proofs/en/common-window.md) | Draft / 草稿 | Propagates two existence estimates to the same pair and scale / 将两个存在性输入落在同一对素数与尺度 |
| Period valuations to integral maps / 周期赋值到整格映射 | [中文](proofs/zh/integral-lattice-map.md) | [English](proofs/en/integral-lattice-map.md) | Draft / 草稿 | The actual period bounds and local identification of the target lattice are inputs / 周期界与目标格的局部识别为输入 |
| RH from the right half-plane / 从右半平面无零点推出 RH | [中文主线第 3 节](proofs/zh/from-windows-to-rh.md#3-反射到右半平面) | [English](proofs/en/rh-from-right-half-plane.md) | Adapted draft / 改编草稿 | Uses the functional equation and the stated nonvanishing hypothesis / 使用函数方程与明列的无零点前提 |
| From Dirichlet nonvanishing to RH / 狄利克雷无零点到 RH | To write / 待写 | [English](proofs/en/from-dirichlet-nonvanishing.md) | Adapted draft / 改编草稿 | Specializes the hypothesis to modulus 1 / 将无零点前提用于模 1 |

## Upstream links to complete / 待串联的上游证明

- **Simultaneous realization of the data / 同时构造算术和几何数据.** Trace how the same family meets all pointwise conditions. [Lean entry](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/DesWin.lean#L11) · [O’Desky’s outline](https://andrewodesky.com/rh/s/assembly-existence.html).
- **Actual period bounds / 实际周期界.** The integrality note starts with valuations already supplied by `adm2`. Trace the base and twisted comparisons that produce them. [Lean entry](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/ClosedFamilyAdmissibleTwistLink.lean#L12).
- **The Galois input / 伽罗瓦表示的来源.** Connect the geometric construction and theta lift to the representation with the required local compatibility. [Lean entry](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/IntegralStructures/RowSrc.lean#L6) · [English reading guide](https://riemann.tamnd.com/proof/galois-row/).

## Lean verification / Lean 核验

The published source has been built and replayed independently. The public report lists only `propext`, `Classical.choice` and `Quot.sound` for the five final statements in `Main.lean`. [Sutherland’s public report](https://math.mit.edu/~drew/grh/) · [Final RH statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Main.lean#L4)

公开报告记录了原工程的全量编译和内核重放。`Main.lean` 的五条最终声明在公理查询中只依赖 `propext`、`Classical.choice` 和 `Quot.sound`。各篇文字推导的复核进度见上表。
