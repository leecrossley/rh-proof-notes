# 为什么限制 Herr 对的分母就能得到晶体有限类

## 命题

设 $\ell$ 为素数，$K,L/\mathbb Q_\ell$ 为有限扩张，$K_0$ 为 $K$ 的最大非分歧子域。取 $s\ge1$，$\ell=2$ 时要求 $s\ge2$，且 $K\subset K_s=K_0(\mu_{\ell^s})$，$L$ 包含 $K_s$ 的全部 $\mathbb Q_\ell$-嵌入像。令 $T$ 为有限自由 $\mathcal O_L$-格，其有理表示 $V=T[1/\ell]$ 晶体。记 $D(T)$ 为 étale 模，$N(T)$ 为整 Wach 格，$U$ 为分圆参数，$Q=\Phi_{\ell^s}(1+U)$。给定非负整数的有限多重集 $I$，以及 $y,z\in D(T)$ 满足

$$
\left(\prod_{j\in I}\varphi^j(Q)\right)y\in N(T),\qquad
 z\in UN(T),\qquad
 (\gamma-1)y=(\varphi-1)z ,
\tag{1}
$$

其中 $\gamma$ 为 $G_{K_s}$ 的分圆像的拓扑生成元。则这对元素的整 Herr 类属于

$$
H_f^1(G_{K_s},T)
 =\ker\!\left(H^1(G_{K_s},T)\longrightarrow
          H^1(G_{K_s}, V\otimes_{\mathbb Q_\ell}B_{\rm cris})\right).
\tag{2}
$$

下文说明实际证明使用的开圆盘周期比较。若同一类本来来自 $G_K$ 上的整上同调，则该原类也有有限性。

## 两个周期比较输入

设 $P=B\otimes_{\mathcal O_L}T$ 为 Witt 周期模，$P^+$ 用整子环 $B^+$ 定义，$J:D(T)\to P$ 是 étale 比较。晶体比较 $\beta:B^+\to L\otimes_{\mathbb Q_\ell}B_{\rm cris}$ 对分圆和 Galois 作用相容。一个 $P$ 中的向量若乘 $B^+$ 中的标量 $a$ 后落在 $P^+$，且 $\beta(a)$ 可逆，则得到它在 $V\otimes B_{\rm cris}$ 的像，定义为比较分子后除以 $\beta(a)$。这个像由交叉相乘唯一，兼容相加和 Galois 作用。比较把 $1\otimes t$ 送到 $t\otimes1$。

另有开圆盘比较，适用于系数 $L[[U]]$ 的各分量。它在一个含整幂级数的子环上给出环映射 $J_{\rm disc}$ 到 $L\otimes B_{\rm cris}$。需要的性质为：

- 任何在 $|U|<1$ 收敛的各分量级数都在这个子环中，$\log(1+U)$ 的像 $\mathbf t$ 在 $B_{\rm cris}$ 可逆。
- 在整幂级数上，$J_{\rm disc}$ 等于 $\beta$ 与标量嵌入的复合。它和分圆代入及 Galois 作用相容。

源码把这些条件分别写在 `Val` 与 `Disc` 中。它们负责从收敛级数得到实际的晶体周期向量。这里 $\mathbf t$ 是可逆的周期，而 $U$ 是形式坐标，两个记号分开。[周期向量的可取值关系](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsWachModulePeriodMapToBcris.lean#L63) · [开圆盘比较](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/PeriodDiscExtensionTateElement.lean#L260)

## 证明

记 $\Lambda=\prod_{j\in I}\varphi^j(Q)$。先在 $P$ 中取 $b$ 使 $(\varphi-1)b=J(y)$。存在性来自[Witt 环上 Frobenius 减一满射](%E6%80%8E%E6%A0%B7%E5%9C%A8Witt%E5%91%A8%E6%9C%9F%E7%8E%AF%E9%87%8C%E7%94%A8%E8%BF%B9%E4%B8%80%E5%85%83%E6%B6%88%E5%8E%BB%E5%B1%80%E9%83%A8%E4%BD%99%E9%97%AD%E9%93%BE.md)。由[乘参数幂的整性证明](%E6%80%8E%E6%A0%B7%E8%AE%A9Herr%E6%96%B9%E7%A8%8B%E7%9A%84%E5%91%A8%E6%9C%9F%E8%A7%A3%E5%8F%AA%E5%B8%A6%E5%8F%AF%E9%80%86%E5%88%86%E6%AF%8D.md)，$b$ 有上述比较值，记为 $b_{\rm cris}$。

由[一个生成元扩到全群](%E4%B8%BA%E4%BB%80%E4%B9%88%E4%B8%80%E4%B8%AA%E5%88%86%E5%9C%86%E7%94%9F%E6%88%90%E5%85%83%E7%9A%84Herr%E5%9D%90%E6%A0%87%E8%83%BD%E7%BB%99%E5%87%BA%E6%95%B4%E4%B8%AA%E7%BE%A4%E4%B8%8A%E7%9A%84%E5%80%BC.md)，可取代表 $c$ 与全群的 $z_\sigma\in UN(T)$，使 $J(z_\sigma)=1\otimes c(\sigma)+(\sigma-1)b$ 且 $(\gamma-1)z_\sigma=(\sigma-1)z$。每个 $z_\sigma$ 也可取晶体比较值，因为整 Wach 向量在乘某个 $X^M$ 后进入整周期格，而 $\beta(X)$ 可逆。记 $z_{\sigma,{\rm cris}}$ 为该值。

取 $N(T)$ 的一组基 $e_j$。将 $y$ 写成 $\Lambda^{-1}$ 乘整坐标，将 $\varphi$ 在基上的矩阵写成 $Q^{-m}P_i$，其中 $m$ 是对有限基向量取的共同分母指数。两侧 Frobenius 条件给出 $P_iP_i'=Q^k I$ 对某个 $k\ge0$ 成立。因为 $\gamma$ 在模 $U$ 的作用平凡，其矩阵 $G_i(0)=I$，而 $z\in UN(T)$ 给出其坐标的常数项为零。两算子交换和 (1) 正好是[开圆盘延拓引理](%E6%80%8E%E6%A0%B7%E7%94%A8Frobenius%E6%8A%8AHerr%E6%96%B9%E7%A8%8B%E7%9A%84%E8%A7%A3%E5%BB%B6%E6%8B%93%E5%88%B0%E6%95%B4%E4%B8%AA%E5%BC%80%E5%9C%86%E7%9B%98.md)的块矩阵条件。因此存在形式向量 $w$，常数项为零，满足 $(\gamma-1)w=z$，并且各坐标的 $\log(1+U)^p w_j$ 在开圆盘收敛。

对任意 $\sigma\in G_{K_s}$，在同一个形式模中考虑 $(\sigma-1)w-z_\sigma$。由于算子交换及 $z_\sigma$ 的关系，它被 $\gamma$ 固定。它的常数项全为零，因为 $w,z_\sigma$ 的常数项全为零，且分圆标量代入无常数项。若它有非零项，比较最低非零次数 $d>0$，作用 $\gamma$ 会把其系数乘以 $u^d$，其中 $u=\chi(\gamma)$ 的正整数次幂从不等于 $1$。因为 $G_i(0)=I$，固定性会强迫该系数为零。故

$$
(\sigma-1)w=z_\sigma
\tag{3}
$$

对全群成立。

将 (3) 送入晶体周期环。具体地，用 $e_{j,{\rm cris}}$ 表示 Wach 基向量的晶体比较值，定义

$$
w_{\rm cris}
  =\mathbf t^{-p}\sum_j
       J_{\rm disc}\big(\log(1+U)^p w_j\big)e_{j,{\rm cris}} .
$$

为核对其差，把 (3) 的坐标式两边乘 $\log(1+U)^p$ 与其 $\sigma$ 变换的 $p$ 次幂，令等式两边都在开圆盘比较的定义域内。施加环映射，利用它对整系数的相容性，再消去两个可逆的周期因子。得到

$$
(\sigma-1) w_{\rm cris}=z_{\sigma,{\rm cris}}.
\tag{4}
$$

于是将代表公式也取晶体比较值，得到

$$
c(\sigma)\otimes1
 =z_{\sigma,{\rm cris}}-(\sigma-1)b_{\rm cris}
 =(\sigma-1)(w_{\rm cris}-b_{\rm cris}).
$$

因此 $c$ 进入晶体周期环后是余边界，正是 (2)。

若 $c$ 是 $G_K$ 上的类的代表，且进入晶体周期环后限制到 $G_{K_s}$ 为余边界，先从 $c$ 减去这一个余边界。新的周期余闭链在 $G_{K_s}$ 上为零，因 $K_s/K$ 为有限 Galois 扩张，它下降到有限群 ${\rm Gal}(K_s/K)$，取值于周期模的 $G_{K_s}$ 不变量。按有限群取平均即可写成余边界，因为 $[K_s:K]$ 在 $\mathbb Q_\ell$ 上可逆。故原类也有限。

## Lean 对照

- `coord_eq` 从生成元的解传到所有 $\sigma$，`exists_val` 用收敛级数及可逆周期实现 (4)，`core` 将开圆盘方程和整 Wach 基接起来。[HerrCocyclePolesFrobeniusQCrystalline.lean:152](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/HerrCocyclePolesFrobeniusQCrystalline.lean#L152) · [同文件:240](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/HerrCocyclePolesFrobeniusQCrystalline.lean#L240) · [同文件:335](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/HerrCocyclePolesFrobeniusQCrystalline.lean#L335)
- `mem_of_layers` 给出晶体周期中的余边界向量，`main` 构造各项周期比较后得 `P7`。[同文件:423](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/HerrCocyclePolesFrobeniusQCrystalline.lean#L423) · [同文件:539](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/HerrCocyclePolesFrobeniusQCrystalline.lean#L539)
- `p7` 的声明是所有分母条件满足时类进入 $H_f^1$。[DeltaInvariantLattices.lean:199](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/DeltaInvariantLattices.lean#L199)

状态为源码对读。另行未重新编译。[开圆盘周期比较 $J_{\rm disc}$ 的构造](%E6%80%8E%E6%A0%B7%E6%8A%8A%E5%BC%80%E5%9C%86%E7%9B%98%E7%BA%A7%E6%95%B0%E5%8F%96%E5%80%BC%E5%88%B0%E6%99%B6%E4%BD%93%E5%91%A8%E6%9C%9F%E7%8E%AF.md)已单独展开，并接到[分幂整环上的有界比较](%E4%B8%BA%E4%BB%80%E4%B9%88%E6%99%B6%E4%BD%93%E6%95%B4%E7%8E%AF%E5%9C%A8%E6%AF%8F%E5%B1%82deRham%E6%88%AA%E6%96%AD%E9%83%BD%E6%9C%89%E7%BB%9F%E4%B8%80%E5%88%86%E6%AF%8D.md)。最后一段是由有限群平均得到的数学推论。
