# 为什么晶体格满射的 Wach 余核可被两种幂杀掉

## 命题

设 $\ell$ 为素数。取局部域 $K/\mathbb Q_\ell$、分圆层 $s\ge1$、包含所需单位根的系数域 $L/\mathbb Q_\ell$ 及其整数环 $O$，满足项目的好分圆层条件。设

$$
0\longrightarrow T_0\longrightarrow T_1\xrightarrow{f}T_2\longrightarrow0
$$

为 $G_K$ 的有限自由 $O$-格的短正合列，且三个格张成的 $L$-表示都晶体。记 $A=\prod_{i\in\mathbb Z/n\mathbb Z}O[[U]]$ 为分圆系数环，$X=(1+U)^{\ell^{s-1}}-1$，$Q=\Phi_{\ell^s}(1+U)$。记 $N_j=N(T_j)$ 为整 Wach 模，$D_j$ 为扩大到分圆周期系数环 $E$ 的 étale 模。此处 $E$ 是把 $U$ 反演后再作 $\ell$-进完备化的环。在工程的局部周期模型中，

$$
\exists c\ge0\quad \ell^cN_2\subset f(N_1),\qquad U^cN_2\subset f(N_1).
\tag{1}
$$

两个乘积的原像允许分别选择。这个结论尚未给出 $c$ 的数值。下游用单位差与 Frobenius 递推把它替换为[仅由过滤跨度决定的指数](%E6%80%8E%E6%A0%B7%E6%8A%8A%E4%B8%A4%E4%BE%A7%E7%9A%84Wach%E9%AB%98%E5%BA%A6%E7%95%8C%E8%BD%AC%E6%88%90%E4%BD%99%E6%A0%B8%E7%9A%84%E7%BB%9F%E4%B8%80%E7%95%8C.md)。

使用的周期模型比较为：$D_1\to D_2$ 满射，$E\otimes_A N_j\simeq D_j$，并且 $f$ 与 $\varphi,\gamma$ 相容。Wach 格自由，$(\gamma-1)N_j\subset UN_j$，且对每个 $z\in N_j$，分别有某些 $Q$ 的幂把 $\varphi(z)$ 送回 $N_j$、把 $z$ 送进 $A\varphi(N_j)$。还使用[反演 $X$ 后的周期比较](%E4%B8%BA%E4%BB%80%E4%B9%88%E4%B8%A4%E4%B8%AAWach%E6%A0%BC%E5%8F%8D%E6%BC%94%E5%8F%82%E6%95%B0%E5%90%8E%E7%9B%B8%E5%90%8C.md)：具有相同 étale 模及两侧 Frobenius 性质的两个自由格，各自乘某个 $X$ 幂后进入对方。

## 证明

设 $P=f(N_1)\subset N_2$，并令 $S$ 为[双重饱和](%E4%B8%BA%E4%BB%80%E4%B9%88%E5%8F%8C%E9%87%8D%E9%A5%B1%E5%92%8C%E7%9A%84%E5%AD%90%E6%A0%BC%E4%BB%8D%E6%98%AF%E8%87%AA%E7%94%B1%E6%A8%A1.md)，即 $S$ 由满足 $\ell^k x,U^k x\in P$ 的 $x\in N_2$ 组成。$S$ 自由且 $E\otimes_A S=D_2$。余下的工作是验证 $S$ 满足和 $N_2$ 相同的分圆作用及 Frobenius 条件。

**分圆作用。** $\gamma$ 固定 $\ell$，而 $\gamma(U)=Uv(U)$，其中 $v(0)=u\in O^\times$，所以 $v$ 在 $A$ 中可逆。由 $P$ 稳定，$\ell^k x,U^k x\in P$ 蕴含 $\ell^k\gamma(x),U^k\gamma(x)\in P$。既然 $x\in N_2$，有 $(\gamma-1)x=Uy$ 对某个 $y\in N_2$ 成立。因 $\ell^k x=f(a)$ 对某个 $a\in N_1$ 成立，取 $a'\in N_1$ 使 $(\gamma-1)a=Ua'$。于是

$$
U\ell^k y=(\gamma-1)(\ell^k x)=Uf(a'),
$$

消去 $U$ 后得 $\ell^k y\in P$。另一方面 $U^{k+1}y=U^k(\gamma(x)-x)\in P$。所以 $y\in S$，进而 $(\gamma-1)S\subset US$。

**Frobenius 的第一个方向。** 记 $J$ 为所有满足 $Q^j b\varphi(x)\in P$ 对某个 $j\ge0$ 成立的 $b\in A$。可增加 $j$ 到共同的上界再相加，故 $J$ 是理想。由 $\ell^k x,U^k x\in P$ 和 $Q$ 幂能将 $N_1$ 的 Frobenius 像送回 $N_1$，得 $\ell^k,\varphi(U)^k\in J$。又 $\varphi(U)=(1+U)^\ell-1\equiv U^\ell\bmod\ell$，故 $U\in\sqrt J$。于是某个 $U^b\in J$。再取一个足够大的 $j$，同时确保 $Q^j\varphi(x)\in N_2$ 和它分别乘 $\ell^k,U^b$ 后进 $P$。这说明 $Q^j\varphi(x)\in S$。

**Frobenius 的反向包含。** 若 $y\in P$，从源格的反向包含立刻得到 $Q^j y\in A\varphi(S)$ 对某个 $j$ 成立。若 $x\in S$，对 $\ell^k x,U^k x\in P$ 各作这一步，可取同一个 $j$ 使

$$
\ell^k Q^j x,\ U^k Q^j x\ \in A\varphi(S).
\tag{2}
$$

取 $S$ 的基 $b_1,\dots,b_r$，它也是 $D_2$ 的 $E$-基。向量 $c_i=\varphi(b_i)$ 在 $E$ 上张成 $\varphi(D_2)$ 的 $E$-张成。后一个空间是 $D_2$，因为 $N_2$ 的反向性质和 $Q$ 在 $E$ 中可逆，使 $N_2$ 的全部向量均在其中。于是 $r$ 个 $c_i$ 生成自由的秩 $r$ 模，在交换环上就是一组基。可用满射矩阵存在右逆、行列式为单位来验证。

在 $c_i$ 的基下，记 $Q^j x$ 的任一坐标为 $e\in E$。由 (2)，$a=\ell^ke$ 与 $b=U^ke$ 都在 $A$。完备化前后有 $\ell^k E\cap A=\ell^k A$，所以 $a=\ell^k a_0$ 对某个 $a_0\in A$ 成立。由 $U^k a=\ell^k b$ 及 $\ell$ 在 $A$ 上无挠，得到 $b=U^k a_0$。由于 $U$ 在 $E$ 中可逆，$e=a_0\in A$，证明 $Q^j x\in A\varphi(S)$。这里用了两种分母。关于 $\ell$ 的条件给出 $A$ 中的整坐标候选，关于 $U$ 的条件使其与原 $E$ 坐标相等。

现在 $S$ 与 $N_2$ 满足所列两侧 Frobenius 性质。反演 $X$ 的比较给出两个 $X$ 幂包含，再由[矩阵的整除与唯一性](%E4%B8%BA%E4%BB%80%E4%B9%88%E4%B8%A4%E4%B8%AAWach%E6%A0%BC%E5%9C%A8%E6%B6%88%E5%8E%BB%E5%88%86%E6%AF%8D%E5%90%8E%E5%BF%85%E9%A1%BB%E7%9B%B8%E7%AD%89.md)得到 $S=N_2$。选择 $N_2$ 的有限生成组，对每个生成元取定义 $S$ 时的指数，再取最大值作为 $c$。线性组合保持两种包含，遂得 (1)。

## Lean 对照

- `gam_sat` 证明分圆作用稳定且除以 $U$ 后仍留在饱和模。Frobenius 的两个方向分别由 `φD_satM_gen` 与 `Qpow_mem_φspan_satM` 给出，后者用 `mem_span_of_smul_mem` 降回 $A$ 坐标。[WachSaturationGammaStableAndSubOneMemPiSmul.lean:60](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachSaturationGammaStableAndSubOneMemPiSmul.lean#L60) · [WachSaturationFrobeniusMemUpToQPower.lean:33](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachSaturationFrobeniusMemUpToQPower.lean#L33) · [WachSaturationQPowerMemFrobeniusSpan.lean:206](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachSaturationQPowerMemFrobeniusSpan.lean#L206) · [同文件:128](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachSaturationQPowerMemFrobeniusSpan.lean#L128)
- `satM_free_and_spans` 使用 étale 模正合性与平坦性。主入口 `coker_killed` 用 Wach 格刻画取得等式，最后调用 `uniform` 取生成元的最大指数。[WachSaturationImageFreeAndSpans.lean:171](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachSaturationImageFreeAndSpans.lean#L171) · [WachNCokernelKilledByPower.lean:19](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachNCokernelKilledByPower.lean#L19) · [MemSatMOfSmul.lean:48](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/MemSatMOfSmul.lean#L48)

状态为源码级推导。另行未重新编译。上游的反演 $X$ 比较与系数环交式已另篇展开。[étale 模的正合性](%E4%B8%BA%E4%BB%80%E4%B9%88%E6%89%A9%E5%88%B0%E5%91%A8%E6%9C%9F%E7%8E%AF%E7%9A%84%E6%AD%A3%E5%90%88%E6%80%A7%E8%83%BD%E4%BC%A0%E5%9B%9E%C3%A9tale%E6%A8%A1.md)也已展开，使用工程的周期比较映射。
