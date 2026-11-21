# Reading and review status / 译稿与复核状态

[English home](README.md) · [中文首页](README.zh-CN.md) · [Sources / 来源](SOURCES.md) · [Contributing / 贡献说明](CONTRIBUTING.md)

All 340 full-length notes in the [Chinese proof catalogue](PROOFS.zh-CN.md) have corresponding English notes. The [English proof catalogue](PROOFS.en.md) records these pairs, additional English reconstructions from Lean, and two adapted reading guides. The English and Chinese catalogues follow the same topic order for the paired proofs. The complete English exposition of RH and Dirichlet GRH is in progress.

[中文证明目录](PROOFS.zh-CN.md)收录 340 篇正文，已逐篇配对英文稿。[英文证明目录](PROOFS.en.md)另收录从 Lean 展开的英文新稿和两篇改编导读，并登记各篇的出处与状态。认领或复核时请写明对应篇目和 Lean 声明。

**Draft / 草稿** means prose with Lean references. **Human-reviewed / 人工复核** requires a named reviewer and a record of the portion reviewed. The scope of each note is its stated implication.

| Deduction / 推导 | 中文 | English | Prose review / 正文复核 | Scope and open input / 范围与待补输入 |
| --- | --- | --- | --- | --- |
| Window estimates to RH / 窗口估计到 RH | [中文](proofs/zh/from-windows-to-rh.md) | [English](proofs/en/from-windows-to-rh.md) | Draft / 草稿 | Starts from a uniform estimate on arbitrarily late windows / 窗口上界作为输入 |
| Landau window lemma / Landau 窗口引理 | [中文](proofs/zh/landau-window.md) | [English](proofs/en/landau-window.md) | Draft / 草稿 | Analytic deduction from growth, pole and window hypotheses / 给定增长、极点与窗口条件 |
| Pole data of the weighted sum / 加权和的极点资料 | [中文](proofs/zh/pole-data.md) | [English](proofs/en/pole-data.md) | Draft / 草稿 | Mellin transforms and the residue calculation / Mellin 变换与留数计算 |
| From count discrepancies to prime sums / 从计数差到素数和 | [中文](proofs/zh/%E5%B9%B3%E7%A7%BB%E5%B9%B3%E5%9D%87%E5%A6%82%E4%BD%95%E7%BB%99%E5%87%BA%E7%B4%A0%E6%95%B0%E5%92%8C%E7%9A%84%E9%80%90%E7%82%B9%E4%BC%B0%E8%AE%A1.md) | [English](proofs/en/translation-averaging.md) | Draft / 草稿 | Starts from a uniform count-discrepancy bound / 以计数差的一致界为输入 |
| A common window / 共用窗口 | [中文](proofs/zh/common-window.md) | [English](proofs/en/common-window.md) | Draft / 草稿 | Propagates two existence estimates to the same pair and scale / 将两个存在性输入落在同一对素数与尺度 |
| Period valuations to integral maps / 周期赋值到整格映射 | [中文](proofs/zh/integral-lattice-map.md) | [English](proofs/en/integral-lattice-map.md) | Draft / 草稿 | The actual period bounds and local identification of the target lattice are inputs / 周期界与目标格的局部识别为输入 |
| RH from the right half-plane / 从右半平面无零点推出 RH | [中文主线第 3 节](proofs/zh/from-windows-to-rh.md#3-反射到右半平面) | [English](proofs/en/rh-from-right-half-plane.md) | Adapted draft / 改编草稿 | Uses the functional equation and the stated nonvanishing hypothesis / 使用函数方程与明列的无零点前提 |
| From Dirichlet nonvanishing to RH / 狄利克雷无零点到 RH | To write / 待写 | [English](proofs/en/from-dirichlet-nonvanishing.md) | Adapted draft / 改编草稿 | Specializes the hypothesis to modulus 1 / 将无零点前提用于模 1 |

## Local origin of the prime-power weights

The signal-prime branch begins with an expansion in logarithmic variables for every Frobenius orbit. The drafts derive this expansion from host integrality, the curve norm and additivity identities, and a hyperbolic frame. They construct the trace-dual lists and show that the unit-root average supplies the coefficient-field, parity and integrality hypotheses of the jet estimate. [Expansion from host integrality](proofs/en/from-host-integrality-to-the-all-place-theta-expansion.md) · [Jet hypotheses for the mean](proofs/en/why-the-averaged-biextension-meets-the-jet-hypotheses.md)

In the determinant estimate, the exceptional two-power monomials give the $p^e$ cost in the cyclic degree problem. The top-row capacities give the positive parts $(a/p^e-w)_+$. The local valuations add over all the orbits at a prime, and the gains match the signal-prime summands in the count. The proof uses the orbit shape and size conditions. [Determinant proof](proofs/en/generic-frames-for-the-determinant-jet.md) · [Gluing over orbits](proofs/en/how-local-jet-valuations-add-over-frobenius-orbits.md) · [Local-to-count comparison](proofs/en/from-orbit-valuations-to-the-prime-power-count.md)

The curve input is now developed from the classical singular-modulus theorem. The local good model is obtained using torsion products, an integral parameter change is obtained from the height-two Frobenius equation, and an isogeny product gives the unit norm law. The curve's two-variable parallelogram gives the additivity of its exponent. [Curve data](proofs/en/assembling-the-inert-cm-curve-data.md) · [Additivity of the curve exponent](proofs/en/from-formal-sigma-addition-to-the-curve-biextension.md)

The remaining inputs on this route are the actual kernel family's host integrality and its comparison with the standard bases. The other prime classes and their losses are needed for the full arithmetic comparison. [Kernel family entry](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/AdmissibleKernelSeriesInertPrimeNonConjugateFrob.lean#L24)

## Upstream links to complete / 待串联的上游证明

- **Simultaneous realization of the data / 同时构造算术和几何数据.** Trace how the same family meets all pointwise conditions. [Lean entry](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/DesWin.lean#L11) · [O’Desky’s outline](https://andrewodesky.com/rh/s/assembly-existence.html).
- **Actual period bounds / 实际周期界.** The integrality note starts with valuations already supplied by `adm2`. Trace the base and twisted comparisons that produce them. [Lean entry](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/ClosedFamilyAdmissibleTwistLink.lean#L12).
- **The Galois input / 伽罗瓦表示的来源.** Connect the geometric construction and theta lift to the representation with the required local compatibility. [Lean entry](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/IntegralStructures/RowSrc.lean#L6) · [English reading guide](https://riemann.tamnd.com/proof/galois-row/).

## Lean verification / Lean 核验

The published source has been built and replayed independently. Sutherland's public report records compilation and Lean kernel replay of all 175,187 modules. The audit of the five unconditional final statements in `Main.lean`, including RH and Dirichlet GRH, lists only `propext`, `Classical.choice` and `Quot.sound`. The present prose edition checks source references against the pinned mirror and records the hypotheses of each step. [Sutherland's public report](https://math.mit.edu/~drew/grh/) · [Final RH statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Main.lean#L4)

公开报告记录了原工程的全量编译和内核重放。`Main.lean` 的五条最终声明在公理查询中只依赖 `propext`、`Classical.choice` 和 `Quot.sound`。各篇文字推导的复核进度见上表。
