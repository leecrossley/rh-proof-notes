# 为什么小二进导子的 V 类只需下降到有界次数的域

## 命题

固定本原 Dirichlet 特征 $\chi$，模数 $Q$、阶 $o$。取 [宿主](%E6%AD%A3%E5%8F%B7%E4%B8%8A%E5%90%8C%E8%B0%83%E7%9A%84%E4%B8%83%E7%A7%8D%E9%95%BF%E5%BA%A6%E4%BC%B0%E8%AE%A1%E6%80%8E%E6%A0%B7%E9%80%89%E7%94%A8.md) $h$，其基础特征为 $\chi$，模数为 $N$，取整数 $t$ 使 $h.\mathrm{Big}(t)$。取任意一份 $\mathbb Q$ 的代数闭包、奇素数 $\ell\in B_\chi$、项目允许的有限 $\ell$-进整数环 $O$，以及在 $H$ 上平凡、满足 $\psi(-1)=-1$ 的模 $N$ 的 $O$-值 Dirichlet 特征 $\psi$。令 $c_2=c_2(\psi)$ 为模二幂分量的导子指数，$n_0=v_2(\ell^{f_0}-1)$ 如 [二进层数](%E4%B8%BA%E4%BB%80%E4%B9%88II%E7%B1%BB%E5%92%8CIII%E7%B1%BB%E4%BD%BF%E7%94%A8%E7%9A%84%E4%BA%8C%E8%BF%9B%E5%B1%82%E6%95%B0%E6%9C%89%E5%A4%9A%E9%A1%B9%E5%BC%8F%E9%AB%98%E5%BA%A6.md)。设

$$
2^{c_2}<R_1,\qquad R_1=16o(\ell Q)^2\,4^{n_0}.
$$

假设全局 Poitou–Tate 对偶、局部有限性和局部 Tate 对偶。又给定实数 $C_K$ 并假设 [`LemmaK $C_K$`](%E5%B0%8F%E6%8C%87%E6%A0%87%E7%9A%84%E4%BA%8C%E9%98%B6%E4%B8%8A%E5%90%8C%E8%B0%83%E7%95%8C%E6%80%8E%E6%A0%B7%E7%94%B1%E8%AE%A1%E6%95%B0%E5%90%88%E6%88%90.md)。则存在整数 $C$，只依赖 $\chi,C_K$，使对上述所有数据，$V_{\ell,1}(\psi)$ 的 $O$-长度有限且

$$
\frac{\operatorname{length}_O V_{\ell,1}(\psi)}{v_O(\ell)}\log\ell
\le(\ell N)^C.
$$

这里 $V_{\ell,e}(\psi)$ 是 [II、III 类主稿](%E4%B8%BA%E4%BB%80%E4%B9%88II%E7%B1%BB%E5%92%8CIII%E7%B1%BB%E7%9A%84%E9%95%BF%E5%BA%A6%E5%8F%AF%E4%BB%A5%E5%90%88%E7%94%A8%E7%A7%A9%E5%9B%9B%E6%96%B9%E6%B3%95.md) 定义的一阶局部化核。这个分支是 `CountVs`。

## 证明

令 $b=\max B_\chi$，由定义 $B_\chi$ 至少含 $3$，且只依赖 $\chi$。模二幂分量 $\psi_2$ 通过模 $2^{c_2}$ 单位群，故阶整除 $2^{c_2}$。对奇素数的每个模素幂分量，宿主条件使其阶整除 $o$ 或 $2$。所以 $\operatorname{ord}\psi\mid 2o\,2^{c_2}$。由 $2^{n_0}<\ell^{\varphi(4o)}$，小导子条件给出

$$
\ell\operatorname{ord}\psi
\le 2o\bigl(16o(bQ)^2 b^{2\varphi(4o)}\bigr)b=:D_0 .
\tag{1}
$$

关键是右边与宿主的增大参数无关。

在分圆域 $E=\mathbb Q(\mu_{\ell N})$ 中取子域 $L$，对应于 $\operatorname{Gal}(E/\mathbb Q)$ 中同时消去 $\psi$ 和固定 $\mu_\ell$ 的公共核。于是 $L/\mathbb Q$ 阿贝尔，含 $\mu_\ell$，$\psi_G|_{G_L}=1$。公共核的指数至多两个像的阶的乘积。模 $\ell$ 单位群的阶为 $\ell-1$，而 $\psi$ 的值是 $\operatorname{ord}\psi$ 次单位根，个数至多 $\operatorname{ord}\psi$。故 $[L:\mathbb Q]=d\le \ell\operatorname{ord}\psi\le D_0$。因 $\ell$ 是奇素数，$L$ 全虚。分圆域的判别式公式给 $|\operatorname{disc}E|\le(\ell N)^{[E:\mathbb Q]}$，再用塔公式

$$
|\operatorname{disc}E|
=|\operatorname{disc}L|^{[E:L]}N_{L/\mathbb Q}(\mathfrak d_{E/L})
$$

及相对判别式范数至少 $1$，得到 $|\operatorname{disc}L|\le(\ell N)^d$。

将一阶类限制到 $G_L$，其扭曲中的 $\psi_G$ 消失。限制的像进入 $L$ 上权 $-1$ 的局部化核。限制的核，由膨胀限制，注入 $\operatorname{Gal}(L/\mathbb Q)$ 在不变元模上的一阶上同调。取整个有限群作生成集，至多 $D_0$ 个。一阶余闭链由生成元上的值决定，故这一部分的长度至多 $D_0$ 乘不变元长度。源码中 `upV` 把这两件事合并。由 [限制损失估计](%E9%99%90%E5%88%B6%E5%88%B0%E5%88%86%E5%9C%86%E5%B1%82%E6%97%B6%E4%B8%A2%E5%A4%B1%E7%9A%84%E4%B8%8A%E5%90%8C%E8%B0%83%E6%80%8E%E6%A0%B7%E4%BC%B0%E8%AE%A1.md) 的全局不变元界，权 $1$ 时其归一化长度至多 $2N$，所以这一部分至多 $2D_0N$。

对限制的像，换环将 $\mathbb Z_\ell$-长度乘上 $v_O(\ell)$。Poitou–Tate 的比较 `shaLeV` 给 $L$ 上的一阶核长度不超过 $H^2(G_{L,\{\ell\}},\mathbb Z_\ell(2))$ 的 $\mathbb Z_\ell$-长度。这里 $G_{L,\{\ell\}}$ 表示只允许在 $\ell$ 上方和无穷处分歧的 Galois 群。令 $K=\lceil C_K\rceil_{\mathbb N}$ 为非负整数上取整。`LemmaK` 给此二阶群有限且其基数对数至多

$$
\operatorname{kBound}(K,1,d,|\operatorname{disc}L|)
=\exp\big((2d)^K\log(2|\operatorname{disc}L|)\big).
$$

有限 $\mathbb Z_\ell$-模的基数是 $\ell$ 的长度次幂，而 $\log\ell\ge1/2$，故其长度至多上式的两倍。设 $X=\ell N\ge2$。由 $|\operatorname{disc}L|\le X^d$ 及 $d\le D_0$，上式至多 $X^{(2D_0)^K(D_0+1)}$。原局部化核的归一化长度因而至多

$$
2X^{(2D_0)^K(D_0+1)}+2D_0N.
$$

乘 $\log\ell\le\ell\le X$，并用 $X\ge2$ 吸收 $2(1+D_0)$，得到 $C=(2D_0)^K(D_0+1)+D_0+3$ 即可。这样给出小二进导子分支的逐项多项式界。

## Lean 对照

- [`vsOrd`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/PowTotientConductor.lean#L26) 给式 (1)。[`vsField`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/VsField.lean#L24) 取消去 $\psi$ 且含 $\mu_\ell$ 的阿贝尔域。
- [`Win.disc`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LayeredIsomorphisms/Imports.lean#L6) 是给判别式的塔公式比较，[`Chr.upV`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CharacterLevelBounds/LiftGens.lean#L24) 是限制到 $L$ 的长度比较。
- [`Win.klen`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LayeredIsomorphisms/Klen.lean#L23) 从基数对数改为长度，[`countVs`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/CountVs.lean#L86) 完成 $C$ 的选择。本篇为发布版源码对照。
