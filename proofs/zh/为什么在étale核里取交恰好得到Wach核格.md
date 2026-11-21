# 为什么在 étale 核里取交恰好得到 Wach 核格

## 命题

令 $O$ 为有限 $\mathbb Q_\ell$ 扩张的整数环，$A=\prod_{i=1}^nO[[U]]$，$n\ge1$，$E=\widehat{A[1/U]}$ 为 $\ell$-进完备化。设 $0\to T_0\xrightarrow{\iota}T_1\xrightarrow{q}T_2\to0$ 是有限自由 $O$-格的晶体短正合列。记 $D_j=D(T_j)$、$N_j=N(T_j)$。使用工程的 étale 周期比较，所以 $0\to D_0\to D_1\to D_2\to0$ 正合，各 $N_j$ 是自由 $A$-格，扩到 $E$ 后为 $D_j$。映射 $D(f)$ 送 Wach 格到相应的 Wach 格，并与 $\gamma,\varphi$ 交换。

设 $X=(1+U)^{\ell^{s-1}}-1$、$Q=\Phi_{\ell^s}(1+U)$，其中 $s\ge1$ 为好分圆层，$X,Q$ 在 $E$ 中可逆。各 Wach 格满足 $(\gamma-1)N_j\subset UN_j$ 和[两侧 Frobenius 格条件](%E4%B8%BA%E4%BB%80%E4%B9%88%E4%B8%A4%E4%B8%AAWach%E6%A0%BC%E5%9C%A8%E6%B6%88%E5%8E%BB%E5%88%86%E6%AF%8D%E5%90%8E%E5%BF%85%E9%A1%BB%E7%9B%B8%E7%AD%89.md)。则

$$
D(\iota)^{-1}(N_1)=N_0 .
\tag{1}
$$

这里 $D(\iota)^{-1}(N_1)$ 表示 $D_0$ 中被 $D(\iota)$ 送到 $N_1$ 的全部元素。以下把 $D_0$ 识别为 $D_1$ 的子模。

## 证明

记 $S=N_1\cap D_0=\ker(N_1\to N_2)$。因为 $E/A$ 平坦，取核与扩到 $E$ 交换。因此 $E\otimes_A S=D_0$。由于 $N_1$ 有限自由，$S$ 有限生成。要证自由，按[对 $U$ 的无挠判据](%E4%B8%BA%E4%BB%80%E4%B9%88%E5%8F%8C%E9%87%8D%E9%A5%B1%E5%92%8C%E7%9A%84%E5%AD%90%E6%A0%BC%E4%BB%8D%E6%98%AF%E8%87%AA%E7%94%B1%E6%A8%A1.md)逐分量处理。假设 $\ell x=Uy$ 且 $x,y\in S$。在 $N_1$ 的基下看常数项，得 $x=U x'$ 对某个 $x'\in N_1$ 成立。由于 $q(x)=0$ 且 $U$ 在目标 $D_2$ 上可逆，$q(x')=0$。所以 $x'\in S$。这说明 $S/US$ 没有 $\ell$ 挠，因而在 $O$ 上自由。提升其基再逐次除以 $U$，得到各分量的 $O[[U]]$ 基。各分量同秩来自 $E\otimes_A S=D_0$，因此拼成 $A$ 的自由基。

因为分圆作用稳定 $N_1,D_0$，它稳定 $S$。若 $x\in S$，写 $(\gamma-1)x=Uy$，其中 $y\in N_1$。取像后 $Uq(y)=0$，由 $U$ 可逆得 $y\in S$。因此 $(\gamma-1)S\subset US$。同理，由 $N_1$ 的 Frobenius 条件，可取 $Q^j\varphi(x)\in N_1$，它又在 $D_0$，故在 $S$。

反向 Frobenius 条件要用[整系数的 Frobenius 基](%E4%B8%BA%E4%BB%80%E4%B9%88Frobenius%E7%9A%84%E7%B3%BB%E6%95%B0%E5%B1%95%E5%BC%80%E5%8F%AF%E4%BB%A5%E5%9C%A8%E6%95%B4%E5%B9%82%E7%BA%A7%E6%95%B0%E7%8E%AF%E9%87%8C%E5%AE%8C%E6%88%90.md)。令 $u_a=(1+U)^a$，$0\le a<\ell$，它们是 $A$ 在 $\varphi(A)$ 上的基。给定 $x\in S$，取 $k$ 使 $Q^kx\in A\varphi(N_1)$。利用标量的 Frobenius 基和半线性，可写

$$
Q^kx=\sum_{a=0}^{\ell-1}u_a\varphi(w_a),\qquad w_a\in N_1.
$$

投到 $D_2$，右侧为 $\sum_a u_a\varphi(qw_a)=0$。

为从此等式求出 $qw_a=0$，取 $N_2$ 的 $A$-基 $b_j$。$\varphi(b_j)$ 在 $E$ 上是 $D_2$ 的基，因为它们的数目等于秩，并且 $Q^tN_2\subset A\varphi(N_2)$ 及 $Q\in E^\times$ 使它们张成 $D_2$。写 $qw_a=\sum_j c_{aj}b_j$，其中 $c_{aj}\in A$。比较 $\varphi(b_j)$ 坐标给出 $\sum_a u_a\varphi(c_{aj})=0$。这是 $A$ 中的等式，由 $u_a$ 的基性质得每个 $c_{aj}=0$。故所有 $w_a$ 都在 $S$，所以 $Q^kx\in A\varphi(S)$。

这证明 $S$ 是自由格，扩到 $E$ 后为 $D_0$，并满足两侧 Frobenius 条件及模 $U$ 的分圆条件。先用[反演 $X$ 后的比较](%E4%B8%BA%E4%BB%80%E4%B9%88%E4%B8%A4%E4%B8%AAWach%E6%A0%BC%E5%8F%8D%E6%BC%94%E5%8F%82%E6%95%B0%E5%90%8E%E7%9B%B8%E5%90%8C.md)给出 $S,N_0$ 之间的两个 $X$ 幂包含，再用[Wach 格唯一性](%E4%B8%BA%E4%BB%80%E4%B9%88%E4%B8%A4%E4%B8%AAWach%E6%A0%BC%E5%9C%A8%E6%B6%88%E5%8E%BB%E5%88%86%E6%AF%8D%E5%90%8E%E5%BF%85%E9%A1%BB%E7%9B%B8%E7%AD%89.md)去掉这两份分母，得 $S=N_0$。

## Lean 对照

- `isBaseChange_comap_of_exact` 把核与扩系数相容。`kernel_freeA` 用模参数的除法和秩比较，取得自由基。[IsBaseChangeComapOfExactFlat.lean:8](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/IsBaseChangeComapOfExactFlat.lean#L8) · [WachKernelIntersectionFreeOfBaseChange.lean:14](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachKernelIntersectionFreeOfBaseChange.lean#L14)
- `phispan_of` 将系数沿 Frobenius 基分组，投影到商后利用独立性消去每个分量。主入口给出实际分圆代入的基。[WachKernelMemFrobeniusSpanAfterQPow.lean:67](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachKernelMemFrobeniusSpanAfterQPow.lean#L67) · [同文件:103](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachKernelMemFrobeniusSpanAfterQPow.lean#L103)
- `mem_N_of_map_mem` 组装两侧条件，调用 Wach 格唯一性。[MemWachNOfMapMemSaturated.lean:19](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/MemWachNOfMapMemSaturated.lean#L19)

状态为源码级推导。另行未重新编译。
