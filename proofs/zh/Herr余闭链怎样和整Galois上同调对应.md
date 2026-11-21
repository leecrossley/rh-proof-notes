# Herr 余闭链怎样和整 Galois 上同调对应

## 命题

设 $O$ 是有限 $\mathbb Q_\ell$ 扩张的整数环，$T$ 是带连续作用的有限自由 $O$-格。设局部 Galois 群 $G$ 连续映到分圆群 $\Gamma=\Delta\times\Gamma_1$，其中 $\Delta$ 为有限子群、$|\Delta|\in O^\times$，$\Gamma_1\simeq\mathbb Z_\ell$。令 $H$ 为核，$g\in G$ 的像 $\gamma$ 是 $\Gamma_1$ 的拓扑生成元。设 $D=D(T)$ 为对应的 étale 模，带可交换的 $\varphi,\Gamma$ 作用。取大周期模 $P$ 及单射 $J:D\to P^H$，与 $\varphi$ 和 $G$ 作用相容。这里 $G$ 通过 $\Gamma$ 作用在 $D$ 上。

在项目的周期模型中，使用以下条件：

1. $\varphi-1:P\to P$ 满射，其核是 $T$ 在 $P$ 中的像，以下将 $T\subset P$。每个连续 $T$-值余闭链限制到 $H$ 后，在 $P$ 中为余边界。[Witt 周期环上的证明](%E6%80%8E%E6%A0%B7%E5%9C%A8Witt%E5%91%A8%E6%9C%9F%E7%8E%AF%E9%87%8C%E7%94%A8%E8%BF%B9%E4%B8%80%E5%85%83%E6%B6%88%E5%8E%BB%E5%B1%80%E9%83%A8%E4%BD%99%E9%97%AD%E9%93%BE.md)
2. $\varphi-1$ 在 $P^H/J(D)$ 上双射。[固定周期商上的证明](%E4%B8%BA%E4%BB%80%E4%B9%88%E5%9B%BA%E5%AE%9A%E5%91%A8%E6%9C%9F%E5%95%86%E9%87%8C%E7%9A%84Frobenius%E5%87%8F%E4%B8%80%E5%8F%AF%E9%80%86.md)
3. 项目的类映射 ${\rm cl}$ 采用如下规则。对随 $\Delta$ 固定的 $(y,z)\in D^\Delta\times D^\Delta$ 使 $(\gamma-1)y=(\varphi-1)z$，取任意 $b\in P$ 使 $(\varphi-1)b=J(y)$。类映射的代表是一个连续 $T$-值余闭链，在 $\Delta$ 的各原像 $h$ 上取值 $- (h-1)b$，在 $\gamma$ 的各原像 $g'$ 上取值 $J(z)-(g'-1)b$。这里使用周期模型中类映射的存在及连续性条款。

则 ${\rm cl}$ 满射到 $H^1(G,T)$，其核恰为

$$
\{((\varphi-1)m,(\gamma-1)m):m\in D^\Delta\}.
\tag{1}
$$

这个对应与格映射相容。

项目有两处用法。对 $G_{K_s}$ 的局部版本，$\Delta=\{1\}$。在整个 $G_K$ 上用实际分圆像的有限挠群 $\Delta$，并且在 $\ell=2$ 时另要求 $K$ 含 $\sqrt{-1}$，确保选定的分圆生成元与有限挠群满足上述分解和阶数条件。

## 证明

同一个连续余闭链在 $G$ 的稠密生成集上确定。事实上，两个余闭链的差仍为余闭链，零集因乘积、取逆及连续性为闭子群。由 $H$、$\Delta$ 的原像以及一个 $\gamma$ 原像生成的子群在 $G$ 中稠密。因此只需在条件 3 指定的群元素上比较两个代表。

**给定整上同调类，求 Herr 对。** 取连续 $T$-值余闭链 $c$。由条件 1，有 $b_0\in P$ 使 $c(h)=(h-1)b_0$ 对每个 $h\in H$ 成立。由于 $c(h)$ 由 $\varphi$ 固定，$y_0=(\varphi-1)(-b_0)$ 在 $P^H$ 中。用条件 2 的满射，取 $d\in P^H$ 使 $y_0-(\varphi-1)d=J(y_1)$，$y_1\in D$。于是 $b_1=-b_0-d$ 满足

$$
(\varphi-1)b_1=J(y_1),\qquad c(h)+(h-1)b_1=0\quad(h\in H).
$$

令 $u(x)=c(x)+(x-1)b_1$。它是 $P$-值余闭链，在 $H$ 上为零。由余闭链等式，它只依赖 $G$ 在 $\Gamma$ 的像，且所有值都在 $P^H$。例如对 $h\in H$，因 $hx=x(x^{-1}hx)$，比较两种乘积便得 $h\,u(x)=u(x)$。又

$$
(\varphi-1)u(x)=(x-1)J(y_1)\in J(D).
$$

于是由条件 2 的单射，每个 $u(x)$ 都在 $J(D)$。把它视作 $\Gamma$ 到 $D$ 的余闭链 $u_D$。

以下平均只用到 $|\Delta|$ 是单位。令

$$
m_0=\frac1{|\Delta|}\sum_{\delta\in\Delta}u_D(\delta).
$$

对 $\delta_0\in\Delta$，用 $\delta_0$ 置换和式指标，并利用余闭链等式，得 $(\delta_0-1)m_0=-u_D(\delta_0)$。令 $b=b_1+J(m_0)$、$y=y_1+(\varphi-1)m_0$，并令 $u'(x)=c(x)+(x-1)b$，这使 $u'$ 在 $\Delta$ 上为零，且仍是从 $\Gamma$ 到 $J(D)$ 的余闭链。对 $\delta\in\Delta$，有 $0=(\varphi-1)u'(\delta)=(\delta-1)J(y)$，由 $J$ 单射得 $y\in D^\Delta$。

写 $u'(\gamma)=J(z)$。因 $\Gamma$ 交换，比较 $u'(\delta\gamma)$ 与 $u'(\gamma\delta)$ 可知 $z\in D^\Delta$。再计算 $(\varphi-1)u'(\gamma)=(\gamma-1)J(y)$，便得到 $(\varphi-1)z=(\gamma-1)y$。所以 $(y,z)$ 是允许的 Herr 余闭链。由 $u'$ 的定义，它给出的两类生成元上的值都是 $c$；由连续性，两者在 $G$ 上相同，满射得证。

**识别核。** 若 ${\rm cl}(y,z)=0$，其代表余闭链为 $(x-1)t$，其中 $t\in T\subset P$。取 $(\varphi-1)b=J(y)$。在 $\Delta$ 的原像上，条件 3 给 $(x-1)(b+t)=0$，故 $b+t\in P^H$。又 $(\varphi-1)(b+t)=J(y)$，由条件 2 的单射可写 $b+t=J(m)$，$m\in D$。$\Delta$ 的固定性传回去得 $m\in D^\Delta$。在 $\gamma$ 的原像上有 $(x-1)(b+t)=J(z)$，所以 $z=(\gamma-1)m$，同时 $y=(\varphi-1)m$。反过来，若 $(y,z)$ 有 (1) 的形式，取 $b=J(m)$ 计算，两类生成元上的余闭链值都为零，所以原类为零。

**自然性。** 给格的映射 $T\to T'$，它相容地作用在 $D,P$ 上。将解 $b$ 送到目标周期模，就给出目标 Herr 对所需的解，生成元上的两个公式也一起传过去。连续性使代表在全群上相同，从而类映射自然。若换 $b$，差在 $\ker(\varphi-1)=T$，只改动一个余边界。

## Lean 对照

- `exists_pair` 从整余闭链构造 $b,y,z$，先用商的满射／单射，再按有限群平均。`exists_of_coboundary` 将类的消失传回 $D^\Delta$。[T2SpaceLocalLatticeRepresentationSpace.lean:18](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/T2SpaceLocalLatticeRepresentationSpace.lean#L18) · [同文件:133](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/T2SpaceLocalLatticeRepresentationSpace.lean#L133)
- `onto_and_kernel` 接上原类映射的代表公式并比较连续余闭链。`clK_natural` 与 `clNat` 做格映射比较，`herr_a` 代入两个局部群。[同文件:235](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/T2SpaceLocalLatticeRepresentationSpace.lean#L235) · [同文件:355](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/T2SpaceLocalLatticeRepresentationSpace.lean#L355) · [自然性源码:244](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/HausdorffOfModuleTopologyFiniteDimensional.lean#L244) · [同文件主入口:722](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/T2SpaceLocalLatticeRepresentationSpace.lean#L722)
- `HerrAat`、`HerrAsat` 分别写下 $G_K$ 与 $G_{K_s}$ 的结论。[LocalSituation.lean:201](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/LocalSituation.lean#L201) · [同文件:212](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/LocalSituation.lean#L212)

状态为源码级推导。另行未重新编译。正文用到周期模型中已经给出的类映射及其连续代表公式。关于有限子群的谱分解和晶体扩张类，还需沿后续兼容性定理核对。
