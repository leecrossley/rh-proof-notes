# 为什么扩到周期环的正合性能传回 étale 模

## 命题

令 $O$ 为有限扩张 $L/\mathbb Q_\ell$ 的整数环，$\varpi$ 为其素元，$k=O/\varpi O$。设 $A=\prod_{i=1}^nO[[U]]$，$n\ge1$，$E=\widehat{A[1/U]}$ 为 $\ell$-进完备化。设 $E\hookrightarrow B$ 是一个交换环嵌入，$\ell\in\operatorname{Jac}(B)$。对有限自由 $O$-格 $T$，设工程的 étale 模 $D(T)$ 是同秩的有限自由 $E$-模，有单射

$$
J_T:D(T)\longrightarrow B\otimes_O T
$$

对 $E\hookrightarrow B$ 半线性，其像在 $B$ 上生成右侧。假定它对格的映射自然，即 $J_{T'}\circ D(f)=(1\otimes f)\circ J_T$。则对任意有限自由 $O$-格的短正合列

$$
0\longrightarrow T_0\xrightarrow{a}T_1\xrightarrow{b}T_2\longrightarrow0,
$$

对应的 $D(T_j)$ 列仍然短正合。

在项目里 $T_j$ 还带有局部 Galois 作用，$D(T_j)$ 也带有 Frobenius 及分圆作用。结论是底层模的正合性。这给出[定性 Wach 余核](%E4%B8%BA%E4%BB%80%E4%B9%88%E6%99%B6%E4%BD%93%E6%A0%BC%E6%BB%A1%E5%B0%84%E7%9A%84Wach%E4%BD%99%E6%A0%B8%E5%8F%AF%E8%A2%AB%E4%B8%A4%E7%A7%8D%E5%B9%82%E6%9D%80%E6%8E%89.md)用到的 $D(T_1)\to D(T_2)$ 满射。

## 证明

先检查一个系数环条件。$E$ 是 $\ell$-进完备环，因而每个极大理想都含 $\ell$，也含 $\varpi$。把 $E$ 模 $\varpi$，所得正是 $\prod_i k((U))$。所以每个极大理想 $\mathfrak m$ 都由 $\varpi$ 与某个 $1-e_i$ 生成，其中 $e_i$ 是相应分量的幂等元。它在 $B$ 中生成的理想仍为真理想。若 $1=\varpi x+(1-e_i)y$ 在 $B$ 中成立，乘 $e_i$ 就会给 $e_i\in\varpi B$。但 $\varpi\in\operatorname{Jac}(B)$，非零幂等元不能属于此根基。这里 $e_i$ 的非零由 $E\hookrightarrow B$ 保证。这便验证了每个 $E$ 的极大理想在 $B$ 中延拓后仍为真理想。

接下来说明如何识别 $D=D(T)$ 的子模。因为 $D$ 与 $T$ 同秩，$D$ 的任意 $E$-基在 $J_T$ 下给出 $B\otimes T$ 的 $B$-基。这由半线性、生成以及生成矩阵是方阵得到。设 $M\subset D$，且 $J_T(M)$ 生成 $B\otimes T$。若 $M\ne D$，因为 $D/M$ 有限生成且非零，存在非零简单商 $E/\mathfrak m$。例如取 $D/M$ 的极大真子模，存在性由有限生成及 Zorn 引理给出。故有满射 $\lambda:D\to E/\mathfrak m$ 消去 $M$。把每个 $E$-基向量的 $\lambda$ 值送到 $B/\mathfrak m B$，用相应 $B$-基得到 $B$-线性映射 $\Lambda:B\otimes T\to B/\mathfrak m B$。由坐标公式，$\Lambda\circ J_T$ 就是 $\lambda$ 在此商环中的像。它消去 $J_T(M)$ 从而全为零，但 $\lambda$ 的满射性使某个像为 $1$，而 $B/\mathfrak m B\ne0$。矛盾，故 $M=D$。

原短正合列在 $O$-模意义下分裂，因为 $T_2$ 自由。扩大到 $B$ 后仍短正合。先用 $J_{T_0},J_{T_1}$ 的自然性及单射性，得到 $D(a)$ 单射。再由 $1\otimes b$ 满射和 $J_{T_1}(D(T_1))$ 的生成性，$J_{T_2}(\operatorname{im}D(b))$ 张成 $B\otimes T_2$。以上子模判据给出 $D(b)$ 满射。

还要证明中间正合。由自然性，$D(b)D(a)=0$。因为 $D(T_2)$ 自由，选 $D(b)$ 的一个 $E$-线性截面 $s$。设 $M=\operatorname{im}D(a)+\operatorname{im}s$。在 $B\otimes T_1$ 中，$J_{T_1}(M)$ 的 $B$-张成包含 $1\otimes b$ 的核，因为该核由 $1\otimes a$ 的像给出。其像又覆盖 $B\otimes T_2$，因为包含 $J_{T_2}(D(T_2))$。所以它生成 $B\otimes T_1$。子模判据给出 $M=D(T_1)$。于是任给 $x\in\ker D(b)$，写 $x=D(a)y+s(z)$。对等式施以 $D(b)$ 便得到 $z=0$，所以 $x\in\operatorname{im}D(a)$。

## Lean 对照

- `eq_top_of_span_image` 用极大真子模和剩余域构造检测满生成的线性泛函。[EqTopOfSpanImage.lean:13](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/EqTopOfSpanImage.lean#L13)
- `span_range_map` 用比较的自然性识别像的张成。`exact_of_tie` 先得满射再取截面，处理正合的中间项。[同文件:274](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/EqTopOfSpanImage.lean#L274) · [同文件:283](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/EqTopOfSpanImage.lean#L283)
- `map_ne_top_of_tie` 使用更一般的系数稠密性证明极大理想仍为真理想。上面用显式完备化模型给出这一段。`DD_exact` 是局部入口。虽然声明带有 `adm9`，证明开头用通配符略去这一参数，实际只调用系数饱和与比较性质。[同文件:348](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/EqTopOfSpanImage.lean#L348) · [同文件:424](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/EqTopOfSpanImage.lean#L424)

状态为源码级推导。另行未重新编译。使用的 étale 比较 $J_T$ 是工程的周期模型输入。
