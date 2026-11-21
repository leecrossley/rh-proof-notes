# 为什么一个分圆生成元的 Herr 坐标能给出整个群上的值

## 命题

沿用[整 Herr 比较](Herr%E4%BD%99%E9%97%AD%E9%93%BE%E6%80%8E%E6%A0%B7%E5%92%8C%E6%95%B4Galois%E4%B8%8A%E5%90%8C%E8%B0%83%E5%AF%B9%E5%BA%94.md)在 $G=G_{K_s}$ 的情形。即 $G$ 是紧 Galois 群，到分圆群 $\Gamma_1\simeq\mathbb Z_\ell$ 的核为 $H$，$g_0$ 的像为拓扑生成元 $\gamma$。设晶体格 $T$ 具有 étale 模 $D(T)$、Wach 格 $N(T)\subset D(T)$ 及比较 $J:D(T)\to P(T)$。记 $A=\prod_i O[[U]]$。在工程的弱周期拓扑下，$J(UN(T))$ 是 $P(T)$ 中的闭加法子群，群作用的轨道及常值格向量嵌入连续。$UN(T)$ 在 $G$ 下稳定。

给定 $y,z\in D(T)$，假定 $z\in UN(T)$ 且 $(\gamma-1)y=(\varphi-1)z$。则存在唯一的函数 $z_\sigma$ 具有以下性质：对每个 $b\in P(T)$ 满足 $(\varphi-1)b=J(y)$，可取一个连续的整代表 $c_b$ 属于 ${\rm cl}_T(y,z)$，且对所有 $\sigma\in G$,

$$
J(z_\sigma)=1\otimes c_b(\sigma)+(\sigma-1)b,\qquad
 z_\sigma\in UN(T),\qquad
 (\gamma-1)z_\sigma=(\sigma-1)z .
\tag{1}
$$

这使一个生成元处的解析求解能用于全部群元素。

## 证明

先取一个 $b$。由 Herr 类代表公式，可取 $c_b$ 使 $Z(\sigma)=1\otimes c_b(\sigma)+(\sigma-1)b$ 在 $H$ 上为零，且 $Z(g_0)=J(z)$。函数 $Z$ 是连续余闭链。令 $G'$ 为所有满足 $Z(\sigma)\in J(UN(T))$ 的 $\sigma$。这是闭子群。乘积情形来自 $Z(\sigma\tau)=Z(\sigma)+\sigma Z(\tau)$ 和 $UN(T)$ 的稳定性，逆元情形来自 $Z(\sigma^{-1})=-\sigma^{-1}Z(\sigma)$。因为 $H,g_0$ 都在 $G'$，它包含两者生成的稠密子群。稠密性可在商 $\mathbb Z_\ell$ 中看见，$\gamma$ 的整数幂对应稠密的整数。故 $G'=G$。于是每个 $Z(\sigma)$ 都有唯一的 $z_\sigma\in UN(T)$ 作原像。

因为 $H$ 固定 $J(D(T))$，且 $Z$ 在 $H$ 上为零，$Z$ 可视作分圆群值于 $J(UN(T))$ 的余闭链。分圆群交换，比较 $Z(g_0\sigma)$ 和 $Z(\sigma g_0)$，得到 $(g_0-1)Z(\sigma)=(\sigma-1)J(z)$。由 $J$ 的相容性和单射性得 (1) 的最后一式。

若更换 $b$，各自得到的 $Z$ 都在 $H$ 上为零且在 $g_0$ 处等于 $J(z)$。两者的差是连续余闭链，其零集是闭子群，包含 $H,g_0$，故处处为零。于是 $z_\sigma$ 与 $b$ 的选择无关。

闭性也有一个便于核对的理由。$N(T)$ 有有限 $A$-基，$O[[U]]$ 在逐系数的整数拓扑中紧。工程的弱拓扑比较使从有限个整幂级数系数到 $J(UN(T))$ 连续，因此后者是 Hausdorff 空间中的紧集，故闭。这样无需另给 $z_\sigma$ 定义一个极限求和公式。

## Lean 对照

- `eq_top_of_closed` 用紧致性和整数在 $\mathbb Z_\ell$ 中的稠密性检测全群。`mem_and_comm` 在全群验证分母条件及交换关系，`uniq` 处理换解 $b$。[ZgFormula.lean:13](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ZgFormula.lean#L13) · [同文件:43](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ZgFormula.lean#L43) · [同文件:78](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ZgFormula.lean#L78)
- `zg_formula_let` 代入模型的连续性、闭性和源类代表。[同文件:106](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ZgFormula.lean#L106)

状态为源码级推导。另行未重新编译。闭性使用工程的弱拓扑比较。
