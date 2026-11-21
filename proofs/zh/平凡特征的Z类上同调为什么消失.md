# 平凡特征的 Z 类上同调为什么消失

**命题。** 设 $\ell\ge5$ 为素数，$O$ 为有限 $\ell$-进扩张的整数环，$F$ 为其分式域。设 $e\ge2$ 为偶数，$\ell-1\mid2e$。令 $A=(F/O)(\varepsilon_\ell^{-e})$，即同一个可除 $O$-模 $F/O$，Galois 作用为乘 $\varepsilon_\ell(g)^{-e}$。则

$$
\ker\!\left(
H^1(G_{\mathbb Q},A)
\longrightarrow
\prod_{v\text{ 有限}} H^1(I_v,A)
\ \times\ H^1(D_\ell,A)
\right)=0 .
$$

每个 $I_v,D_\ell$ 都取自一个绝对素处，换成其共轭仍是同一消失条件。由此，对 [宿主中的 Z 类](%E6%AD%A3%E5%8F%B7%E4%B8%8A%E5%90%8C%E8%B0%83%E7%9A%84%E4%B8%83%E7%A7%8D%E9%95%BF%E5%BA%A6%E4%BC%B0%E8%AE%A1%E6%80%8E%E6%A0%B7%E9%80%89%E7%94%A8.md)，$\psi=1$、$\ell\notin B_\chi$、$\ell-1\mid2e$ 时，$V_{\ell,e}(1)=0$。源码在 Z 类的逐项界可取指数 $0$。

## 只需检查被 $\ell$ 杀死的类

因 $A$ 有离散拓扑，连续余闭链在紧群 $G_{\mathbb Q}$ 上只有有限多个值，因而都被同一个 $\ell$ 的幂杀死。所以若局部化核有非零类，取其倍数可得到一个非零且被 $\ell$ 杀死的类。对这样一个类取代表 $z$。因为 $\ell z$ 是余边界，存在 $b\in A$ 使 $\ell z(g)=g b-b$。由 $A$ 的可除性，取 $b'\in A$ 使 $\ell b'=b$，从 $z$ 减掉 $g b'-b'$。于是可以假设 $z$ 的所有取值都在 $A[\ell]$。

对 $p\ne\ell$，$I_p$ 上圆分特征平凡。局部类在 $I_p$ 上为余边界，故 $z$ 在 $I_p$ 上恒为零。后面只看模 $\ell$ 的圆分特征的 $-e$ 次幂。

## 情形一：$\ell-1\mid e$

这时 $A[\ell]$ 是平凡模，$z$ 是连续加法同态，只可能在 $\ell$ 处分歧。其像有限且被 $\ell$ 杀死，故对应一个有限阿贝尔商，其每个元素的阶整除 $\ell$。由 Kronecker–Weber 及导子只含 $\ell$，它经过某个 $\operatorname{Gal}(\mathbb Q(\mu_{\ell^j})/\mathbb Q)$。奇素数的模 $\ell^j$ 单位群为循环群，其阶为 $(\ell-1)\ell^{j-1}$。其中每个被送到指数 $\ell$ 的商的同态，都消去 $\ell$ 次幂子群，所以 $z$ 已经过模 $\ell^2$ 的单位群。特别地 $z=0$ 于 $G_{\mathbb Q(\mu_{\ell^\infty})}$。

在最初的可除系数模 $A$ 上，这便足以推出余边界。因为 $z$ 已经过 $\Gamma=\operatorname{Gal}(\mathbb Q(\mu_{\ell^\infty})/\mathbb Q)\simeq\mathbb Z_\ell^\times$，取 $\Gamma$ 的一个拓扑生成元 $\sigma$。它在 $A$ 上作用的标量为 $\varepsilon_\ell(\sigma)^{-e}\ne1$，因为 $\sigma$ 无穷阶且 $e\ne0$。乘此标量减 $1$ 在 $A$ 上满射，故可以再减一个余边界，让 $z(\sigma)=0$。余闭链等式使其在 $\sigma$ 的所有整数幂上为零，连续性使其在整个 $\Gamma$ 上为零。

## 情形二：$\ell-1\nmid e$

因为 $\ell-1\mid2e$，$e\equiv(\ell-1)/2\bmod\ell-1$。偶数 $e$ 使 $\ell\equiv1\bmod4$。于是模 $\ell$ 的 $\varepsilon_\ell^{-e}$ 是 Legendre 二次特征，其固定域为 $L=\mathbb Q(\sqrt{\ell})$。具体地，模 $\ell$ 二次 Gauss 和平方为 $\ell$，在 $g$ 下乘上 $(\varepsilon_\ell(g)/\ell)$，因此它生成这一固定域。该实二次域的判别式为 $\ell$。

在 $\ell$ 处固定一个分解群。因 $\ell$-进圆分特征在惯性上的像为 $\mathbb Z_\ell^\times$，可选 $\delta\in I_\ell$ 使 $\varepsilon_\ell(\delta)^{-e}-1$ 为单位。局部类在 $D_\ell$ 上为零，所以 $z|_{D_\ell}$ 是由某个 $b_\ell\in A$ 产生的余边界。对 $\delta$ 取值，左边被 $\ell$ 杀死，且乘子的差为单位，故 $b_\ell\in A[\ell]$。减掉这个余边界可同时保留 $z$ 的取值在 $A[\ell]$，并使 $z(\delta)=0$。

限制到 $G_L$ 时，$A[\ell]$ 平凡，所以 $z|_{G_L}$ 是加法同态。对任意 $\ell$ 上方的分解群，能同样选择惯性元素并得到一个局部参数 $b_\ell'\in A[\ell]$，所以 $z$ 在该分解群与 $G_L$ 的交上为零。对于其他有限处，惯性上已经为零。实无穷处复共轭的阶为二，向指数 $\ell$ 的加法群的同态也消去它。类域论于是使限制同态经过 $\mathrm{Cl}(L)$。

而 $h_L<\ell$。事实上，Minkowski 定理给每个理想类一个范数至多 $x=\sqrt\ell$ 的整理想。对正整数 $n$，范数恰为 $n$ 的理想数至多 $d(n)$，因为在二次域中每个 $p^a$ 至多给 $a+1$ 种分配。故

$$
h_L\le\sum_{n\le x}d(n)\le x(1+\log x)<x^2=\ell.
$$

中间式把 $n=ab$ 按 $a$ 求和并用调和和积分。最后用 $1+\log x<x$ 对 $x>1$。于是 $\mathrm{Cl}(L)$ 的阶与 $\ell$ 互素，$z|_{G_L}=0$。而 $\delta$ 代表非平凡陪集，且 $z(\delta)=0$，再用余闭链等式得到 $z=0$ 于全群。这完成情形二，进而证明原核无非零类。

在 Z 类中，$\ell\ge5$ 因为 $3\in B_\chi$ 且 $\ell$ 是奇素数。特征平凡加 $\psi(-1)=(-1)^e$ 给 $e$ 偶，$e>0$ 给 $e\ge2$。$V_{\ell,e}(1)$ 比原命题还多在 $N$ 的素因子处分解群上消失的条件，因此包含于已证为零的核。

## Lean 对照

- [`zOne`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/TorsClass.lean#L97) 用 `control` 登记对全分圆塔的限制单射，[`kwl`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/KwlOnto.lean#L69) 给同态在固定 $\ell^2$ 次单位根的群上消失。本稿用循环商直接解释这两步。
- [`zQuad`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/ZqField.lean#L228) 用在 $\delta$ 处为零的有限阶余闭链处理二次情形。[`hQuad`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/HQuad.lean#L10) 给与 $\ell$ 互素所需的类数界。
- [`propZ`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/PropZ.lean#L11) 分两个情形，[`countZ`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/CountZ.lean#L5) 接回宿主的 Z 类。本篇为发布版源码对照。
