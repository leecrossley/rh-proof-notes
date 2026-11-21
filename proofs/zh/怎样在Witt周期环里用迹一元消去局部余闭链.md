# 怎样在 Witt 周期环里用迹一元消去局部余闭链

## 命题

设 $K_0/\mathbb Q_\ell$ 为有限非分歧扩张，$K_\infty=K_0(\mu_{\ell^\infty})$，$H={\rm Gal}(\overline{\mathbb Q}_\ell/K_\infty)$。设 $O$ 为有限 $\mathbb Q_\ell$ 扩张的整数环，$T$ 为有限自由 $O$-模，带连续的 $H$ 作用。记 $W=W(\mathbb C_\ell^\flat)$，

$$
P=(O\otimes_{\mathbb Z_\ell}W)\otimes_O T.
$$

这里 $H$ 对 $P$ 作系数和 $T$ 的对角作用。则任意连续整余闭链 $c:H\to T$，在 $P$ 中都是余边界。即存在 $b\in P$，使 $1\otimes c(h)=hb-b$ 对每个 $h\in H$ 成立。

工程将此项与 $P$ 上 Frobenius 减一的满射及其核 $1\otimes T$ 合成 `FNatW`。后两项在正文末尾说明。三项合用是 Herr 类映射的周期输入。

## 在 Witt 环里取得迹为一的元素

给定 $H$ 的任意开正规子群 $H_1$，令 $F/K_\infty$ 为其有限 Galois 固定域，取 $S\subset H$ 为陪集代表。先在倾斜域找一个 $H_1$-固定元，使其对代表 $S$ 的迹为一。

先说明怎样在 $F$ 内逼近 $\ell$ 次根。任取 $0<|a|<1$ 的 $a\in K_\infty$，且 $|a|>\rho_\ell=\ell^{-1/(\ell-1)}$。给定 $b_0\in\mathcal O_F$，在代数闭包中取 $\beta^\ell=b_0$，则 $|\beta|\le1$。令 $F'/K_\infty$ 是含 $F,\beta$ 的有限 Galois 扩张。用[整数迹几乎满射](%E4%B8%BA%E4%BB%80%E4%B9%88%E5%88%86%E5%9C%86%E5%A1%94%E9%A1%B6%E4%B8%8A%E7%9A%84%E6%95%B4%E6%95%B0%E8%BF%B9%E5%87%A0%E4%B9%8E%E6%BB%A1%E5%B0%84.md)选 $e\in\mathcal O_{F'}$ 使 $\operatorname{Tr}_{F'/K_\infty}e=a$。记 $d=\operatorname{Tr}_{F'/F}e$，则 $|d|\ge|a|$，因为再取一次迹是 $a$，且所有共轭等距。对每个 $\sigma\in{\rm Gal}(F'/F)$，要么 $\beta=0$，要么 $\sigma(\beta)/\beta$ 是 $\ell$ 次单位根，故 $|\sigma(\beta)-\beta|\le\rho_\ell$。令

$$
b_1=\frac{\operatorname{Tr}_{F'/F}(e\beta)}{d}\in F.
$$

分子减去 $\beta d$ 后的各项绝对值至多 $\rho_\ell$，故 $|b_1-\beta|\le r=\rho_\ell/|a|<1$。所以 $b_1\in\mathcal O_F$，且对整数的 $\ell$ 次幂用因式分解，得 $|b_1^\ell-b_0|\le r$。这个 $r$ 与 $b_0$ 无关。

用整数迹结论再次选择 $b_0\in\mathcal O_F$，使其对 $F/K_\infty$ 的迹绝对值严格大于 $\max(r,|\ell|)$。这可取越来越深的分圆根减一作为欲指定的迹。反复用上段取 $b_1,b_2,\ldots\in\mathcal O_F$，使 $|b_{j+1}^\ell-b_j|\le r$。取整数 $k$ 使 $r^{\ell^k}\le|\ell|$。于是

$$
x_i=b_{i+k}^{\ell^k}\bmod\ell,\qquad i\ge0,
$$

在模 $\ell$ 环中满足 $x_{i+1}^{\ell}=x_i$。这是因为差在特征 $\ell$ 中等于 $(b_{i+k+1}^\ell-b_{i+k})^{\ell^k}$ 的像。所得倾斜整数 $x=(x_i)_i$ 仍被 $H_1$ 固定。

其迹非零。对单位球里的整数取 $\ell$ 次幂不会放大差，反复比较得到 $|b_k^{\ell^k}-b_0|\le r$。取 $S$ 上的迹也不会放大误差，所以 $\sum_{s\in S}s(b_k^{\ell^k})$ 的绝对值等于原来的迹绝对值，严格大于 $|\ell|$。因此 $\sum_{s\in S}s(x)$ 的第零坐标非零。它被 $H$ 固定，因为 $S$ 列出 $H/H_1$ 的全部元素。于是在倾斜**域**中用 $x$ 除以该迹，得到 $H_1$-固定的 $\beta_0\in\mathbb C_\ell^\flat$，其迹为 $1$。

取 Witt 向量的 Teichmüller 提升 $[\beta_0]$，其迹 $u=\sum_s s([\beta_0])$ 模 $\ell$ 等于 $1$。由 $\ell$-进完备性，$u$ 在 $W$ 中可逆，且为 $H$-固定。因此 $\beta=[\beta_0]/u\in W$ 被 $H_1$ 固定，迹恰为 $1$。这里可以使用倾斜域的所有 Witt 向量，所以能除以非零的倾斜迹。

## 对整余闭链逐次求解

给定精度 $r_0\ge1$，连续性与 $c(1)=0$ 保证可选 $H_1$ 使 $c(H_1)\subset \ell^{r_0}T$。事实上 $T$ 是有限自由格，$\ell^{r_0}T$ 在 $T$ 的诱导拓扑中开。用上一节的迹元 $\beta$，取

$$
b_{r_0}=-\sum_{s\in S}s(\beta)\,(1\otimes c(s)).
$$

与[整数迹版的陪集计算](%E6%80%8E%E6%A0%B7%E7%94%A8%E6%95%B4%E6%95%B0%E8%BF%B9%E5%B9%B3%E5%9D%87%E6%B6%88%E6%8E%89%E5%88%86%E5%9C%86%E5%A1%94%E9%A1%B6%E7%9A%84%E4%B8%80%E9%98%B6%E4%BD%99%E9%97%AD%E9%93%BE.md)相同，把 $hs$ 写为新代表乘 $H_1$ 元素，可得 $1\otimes c(h)-(h b_{r_0}-b_{r_0})\in\ell^{r_0}P$。对于 $P$ 里的余闭链，只要其值在单位元附近属于任意 $\ell^rP$，同一计算也成立。

从 $r_0=1$ 开始。误差是一个 $P$ 值的余闭链且处处被 $\ell$ 整除。把误差除以 $\ell$，它仍是余闭链，并且在单位元附近能达到任意 $\ell$-进精度。这里可直接检查误差的组成。每个有限步的解是若干来自有限层而被开子群固定的系数乘格向量的和。作用于系数的变化在足够小的开子群上为零，作用于格向量的变化因连续性趋于零，所以余闭链及其除后的差都符合所需的邻域条件。对除过的误差再用同样方法求模 $\ell$ 的解，如此得到修正序列 $\ell^j d_j$。$P$ 有限自由于 $\ell$-进完备的 $W$ 上，故修正收敛。对每个固定的 $h$，作用保持 $\ell^rP$，取极限即得要求的等式。

## Frobenius 差的另外两项

$W/\ell W=\mathbb C_\ell^\flat$，该倾斜域代数闭。于是 $u^\ell-u=v$ 模 $\ell$ 总有解，且其核为 $\mathbb F_\ell$。对 $(\varphi-1)w=y$，选模 $\ell$ 的解并提升到 $W$，余项除以 $\ell$ 后再解。由于 $\varphi(\ell)=\ell$，用 $\ell$-进完备性拼接便得满射。若 $\varphi(w)=w$，逐 Witt 坐标直接得到 $w\in W(\mathbb F_\ell)=\mathbb Z_\ell$。在 $T$ 的 $\mathbb Z_\ell$-基下应用于各坐标，得到 $\varphi-1:P\to P$ 满射、核为 $1\otimes T$。

## Lean 对照

- `approx_root` 用商的迹逼近每次取根。`exists_tilt` 令各级近似在特征 $\ell$ 下成为相容坐标。`TraceTilt.main` 归一化倾斜迹和 Witt 迹。[NormRootSubOneLt.lean:191](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/NormRootSubOneLt.lean#L191) · [同文件:268](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/NormRootSubOneLt.lean#L268) · [同文件:345](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/NormRootSubOneLt.lean#L345)
- `avg_step` 与 `avg_cob` 做有限陪集平均并拼接误差，`cob_TW` 代入有限自由格。最后的 `main` 合并这些输入为 `FNatW`。[TensorRight.lean:95](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TensorRight.lean#L95) · [同文件:146](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TensorRight.lean#L146) · [LatticeNhds.lean:275](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/LatticeNhds.lean#L275) · [同文件:342](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/LatticeNhds.lean#L342)
- `as_TW` 取 Frobenius 差的满射和核。上面的证明使用倾斜域代数闭及 Witt 逐级提升，源码另外给出直接的 Artin–Schreier–Witt 证明。[LatticeNhds.lean:265](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/LatticeNhds.lean#L265) · [FrobeniusSubOneSurjectiveWittTilt.lean:129](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/FrobeniusSubOneSurjectiveWittTilt.lean#L129)

状态为源码级推导。另行未重新编译。
