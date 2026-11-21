# 怎样为 II 类和 III 类构造秩四参考数据

## 命题

固定一份 $\mathbb Q$ 的代数闭包。取 [II 或 III 类](%E4%B8%BA%E4%BB%80%E4%B9%88II%E7%B1%BB%E5%92%8CIII%E7%B1%BB%E7%9A%84%E9%95%BF%E5%BA%A6%E5%8F%AF%E4%BB%A5%E5%90%88%E7%94%A8%E7%A7%A9%E5%9B%9B%E6%96%B9%E6%B3%95.md) 的宿主 $h$、整数 $t,\ell,e$ 与系数环 $O$ 上的特征 $\psi$，满足该篇陈述的全部宿主、范围和奇偶性条件。另要求 $O$ 含原始 $2^{n_2}$ 次及 $2^{n_3}$ 次单位根，其中 $n_2,n_3$ 为 [二进层数](%E4%B8%BA%E4%BB%80%E4%B9%88II%E7%B1%BB%E5%92%8CIII%E7%B1%BB%E4%BD%BF%E7%94%A8%E7%9A%84%E4%BA%8C%E8%BF%9B%E5%B1%82%E6%95%B0%E6%9C%89%E5%A4%9A%E9%A1%B9%E5%BC%8F%E9%AB%98%E5%BA%A6.md)。假定剩余余闭链消失定理 `CorX`，其量词及使用见[从 Bernoulli 单位到剩余上同调消失](%E5%A4%A7%E7%9A%84%E4%BA%8C%E8%BF%9B%E5%AF%BC%E5%AD%90%E6%80%8E%E6%A0%B7%E4%BD%BF%E5%89%A9%E4%BD%99%E4%BD%99%E9%97%AD%E9%93%BE%E6%88%90%E4%B8%BA%E4%BD%99%E8%BE%B9%E7%95%8C.md)。

**结论。** 可以构造 `Raw D` 的数据，满足 `D.Good` 及 `Aut.OfCase`。在 II 类取 $n=n_2$、$P=1$ 和平凡 $\xi_0$；在 III 类取 $n=n_3$、$P=p_1$ 和模 $p_1$ 的 $\xi_0$，阶为 $\operatorname{ord}\psi$。两种情形均取一个模 $2^n$ 的本原奇特征 $\xi_2$。令

$$
S=\{p:p\mid2\ell NP\},\quad
\xi=(\xi_0)_G(\xi_2)_G,\quad
\Psi=\varepsilon_\ell^e\psi_G,\quad
\alpha=\varepsilon_\ell\omega^{-1}\xi,\quad \beta=\Psi/\alpha,\quad \nu=\alpha\Psi ,
$$

其中 $\omega$ 为 $\varepsilon_\ell\bmod\ell$ 的 Teichmüller 提升，即在 $O$ 中将约化特征取成相同约化的 $(\ell-1)$ 次单位根。参考表示为 $\operatorname{diag}(\nu,\Psi,\alpha,1)$，余项为其按 $O$ 的极大理想约化。辛形式在坐标 $0,3$ 及 $1,2$ 配对，四个对角值成对相乘均为 $\nu$。这给出了辛相似因子。

## 一、所需的局部数据

选定每个有理素数之上的一处，各取其分解群中的算术 Frobenius $F_v$。在 $v=\ell$ 时，可乘以一个惯性元素使 $\varepsilon_\ell(F_\ell)=1$，因为 $\ell$ 上的惯性在 $\mathbb Z_\ell^\times$ 上满射。替换不改变剩余域上的 Frobenius。取
$\varphi=\lim_{j\to\infty}F_\ell^{\,\ell^{j!}}$。极限在 $F_\ell$ 生成的紧循环群中存在，因为在每个有限商里，$\ell^{j!}$ 对阶的 $\ell$-幂部分最终为零，对互素部分最终为一。另取 $s$ 在 $\ell$ 处惯性中，使 $\varepsilon_\ell(s)=1+\ell$，对 $s$ 取正整数幂，进入有限阶 $\psi_G,\omega$ 的两个核，同时保留 $\varepsilon_\ell(s)$ 的无穷阶。这给源码的 $s_0$。

记

$$
T=\{\ell\}\cup\{v\in S\setminus\{\ell\}:\ \ell\mid|\psi_G(I_v)|\}.
$$

设 $\psi_{(\ell)}$ 为 $\psi$ 的 $\ell$-幂阶部分，令
$T_b=\{\ell\}\cup\{v\mid N:\ v\ne\ell,\ (\psi_{(\ell)})_v\ne1\}$。
这里的下标 $v$ 表示模 $v^{v_v(N)}$ 的局部分量。圆分惯性在 $v$ 处只进入 $v$ 分量，故 $T\subseteq T_b$。宿主的奇素数分量限制给出每个 $v\in T_b$ 都是奇素数且 $v\mid\ell Q$。若 $v\ne\ell$，$\ell\mid\varphi(v^j)$ 意味着 $v\equiv1\bmod\ell$。所以在每个 $v\in T$ 均有 $\overline{\varepsilon_\ell(F_v)}=1$，因为 $v=\ell$ 已安排为 $1$，其余由该合同式给出。

## 二、选择使局部值互相分开的特征

在 II 类，去掉 $\ell$-幂阶部分及 $\ell$ 分量后的特征 $\chi_P$ 有偶阶，故非平凡。置 $a=c_2(\psi)+1+v_2(o)$，令 $u$ 为 $o$ 的奇数部分乘以 $\operatorname{ord}(\psi_{(\ell)})$。则 $u$ 为奇数，且 $\psi^{2^a u}=1$。这是把模二幂分量的阶、模奇数部分的阶和 $\ell$-幂阶部分分别合并。此时 $\xi_0=1$。二进层数 $n_2$ 的定义给 $n>c_2(\psi)$ 和对每个 $v\in T_b$ 的 $v^2 2^a\le2^n$，后一项用 $v\le\ell Q$ 和 $2^{v_2(o)}\le o$。

在 III 类，$\psi\ne1$ 且阶为奇数，故其模二幂分量平凡。$\ell\notin B_\chi$ 及 $\ell-1\mid2e$ 给 $\ell\nmid N o$，于是 $\chi_P=\psi$、$T_b=\{\ell\}$。宿主的奇数阶约束还给 $\operatorname{ord}\psi\mid o_{\mathrm{odd}}$、$\operatorname{cond}(\psi)\mid Q$。因 $p_1\equiv1\bmod o_{\mathrm{odd}}$，循环群 $(\mathbb Z/p_1\mathbb Z)^\times$ 可映至 $\psi$ 的像，取到同阶的 $\xi_0$。它为偶特征，因为阶为奇数。取 $a=0$、$u=\operatorname{ord}\psi$，由 $2^n\ge8\ell^2$ 得 $v^2 2^a\le2^n$。

在两类中 $n\ge3$，故可用 [本原奇特征的构造](%E4%B8%BA%E4%BB%80%E4%B9%88%E5%A4%A7%E7%9A%84%E4%BA%8C%E8%BF%9B%E5%AF%BC%E5%AD%90%E8%83%BD%E5%88%86%E5%BC%80%E8%BE%85%E5%8A%A9Frobenius%E5%80%BC.md) 取 $\xi_2$。$P$ 与 $2^n$ 均不含 $T_b$ 中的素数，因此 $\xi$ 在各 $I_v$ 上平凡。它的阶与 $\ell$ 互素，在复共轭上等于 $-1$。$\Psi$ 在复共轭上等于 $1$，因为 $\psi(-1)=(-1)^e$。任一 $v\in T$ 与 $i\in\mathbb Z$，若

$$
\overline{(\xi\Psi^i)(F_v)}=1,
$$

则取 $2^a u$ 次幂后，$\psi,\xi_0$ 消失，圆分因子此处约化为 $1$，剩下 $\overline{\xi_2(v)^{2^a u}}=1$。$\xi_2(v)$ 的阶是二的幂，约化在此类根上单射，于是 $\xi_2(v)^{2^a u}=1$。[二进导子界](%E4%B8%BA%E4%BB%80%E4%B9%88%E5%A4%A7%E7%9A%84%E4%BA%8C%E8%BF%9B%E5%AF%BC%E5%AD%90%E8%83%BD%E5%88%86%E5%BC%80%E8%BE%85%E5%8A%A9Frobenius%E5%80%BC.md) 给 $2^n<v^2 2^a$，矛盾。这样得到 `D.Good.condD`。

特别地，在 $v=\ell,i=0$ 时得到 $\bar\alpha\ne1$ 作为特征。另一方面，$\bar\Psi$ 可由去掉 $\ell$-幂部分的 $\psi$ 以及 $\overline{\varepsilon_\ell}^e$ 表示。分离出 $\psi$ 的模 $\ell$ 幂分量，它在约化后等于模 $\ell$ 圆分特征的某次幂。因此 $\bar\Psi=\overline{\varepsilon_\ell}^{\,b}\bar\chi_P$ 对某个整数 $b$ 成立。若它恒为 $1$，限制到 $\ell$ 的惯性上。这里 $\chi_P$ 不分歧，而圆分剩余特征在惯性上满射，故 $\ell-1\mid b$。于是 $\bar\chi_P=1$，由其阶与 $\ell$ 互素推出 $\chi_P=1$，与两类的选取矛盾。既然 $\bar\alpha,\bar\Psi$ 均非平凡，两个核的并不能覆盖群。若各有一个元素恰在另一个核里，则乘起来得到一个同时不在两个核里的 $g_0$，否则已有这样的元素。这给 `D.Good` 的两个指定非零约化值。

## 三、剩余余闭链的消失

记 $\theta$ 为从 $\psi$ 去掉 $\ell$-幂阶部分及其模二幂分量得到的特征，$f_0,n_0$ 为前篇的乘法阶和赋值。由定义，$\ell^{f_0}-1$ 同时被 $4,\ell-1,\operatorname{ord}\theta$ 整除。在 III 类，$\operatorname{ord}\xi_0=\operatorname{ord}\psi=\operatorname{ord}\theta$，所以两类的 $\xi_0$ 都有阶整除 $\ell^{f_0}-1$。导子的门槛为

$$
P\ell\,\operatorname{cond}(\theta)\,4^{n_0}\le2^n .
$$

II 类用 $\operatorname{cond}(\theta)\mid N$，III 类用 $\theta=\psi$ 及 $\operatorname{cond}(\psi)\mid Q$，正是 $n_2,n_3$ 的第一项。

由于 $\bar\alpha=\bar\xi$，$\bar\Psi=\overline{\omega^e\psi_2\theta}$，$\bar\beta=\bar\Psi/\bar\alpha$、$\bar\nu=\bar\alpha\bar\Psi$，三种特征 $\bar\alpha,\bar\beta,\bar\nu$ 都是奇特征。分别收集其奇数导子分量及二进分量。奇数导子一侧的本原化因子阶整除 $\ell^{f_0}-1$，导子整除 $P\ell\operatorname{cond}(\theta)$。二进一侧是 $\xi_2$ 或其逆乘导子严格小于 $2^n$ 的 $\psi_2$，从而仍有导子 $2^n$。这满足 `XData` 的奇偶、导子和阶条件。应用 `CorX` 经 `xvan` 的局部条件比较，得到 `D.XVan` 对 $\alpha,\beta,\nu$ 及其逆均成立。具体表述是：在这些剩余特征的系数下，局部上合条件的一阶余闭链全为余边界。这一步是辅助特征选择中使用 Bernoulli 非消失的地方。[剩余余闭链的论证](%E5%A4%A7%E7%9A%84%E4%BA%8C%E8%BF%9B%E5%AF%BC%E5%AD%90%E6%80%8E%E6%A0%B7%E4%BD%BF%E5%89%A9%E4%BD%99%E4%BD%99%E9%97%AD%E9%93%BE%E6%88%90%E4%B8%BA%E4%BD%99%E8%BE%B9%E7%95%8C.md)

最后，所有有限阶特征的分歧只在 $S$，$\xi$ 在 $T$ 处惯性平凡，所有 Frobenius 及 $s_0,\varphi,g_0$ 已选出。于是满足 `Good`；特征分解、指数和 $S$ 正是 `OfCase` 的条件。

## Lean 对照

- [`Raw`、`Good`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/DecompSigmaOrd.lean#L34) 给出数据和全部约束。[`rawEx`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/ReFrob.lean#L65) 构造 Frobenius、其极限和指定惯性元素。
- [`psi_ne`、`t_sub`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/DataEx.lean#L105) 用剩余圆分惯性及特征分量作区分，[`core`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/DataEx.lean#L201) 组合各性质。
- [`dataEx`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/DataEx.lean#L366) [`dataEx`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/DataEx.lean#L366) 对两类选不同的 $n,P,\xi_0$，按上述不等式调用 `core`。[`OfCase`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/AutomorphicCases/SymplecticGSp4.lean#L21) 记录分支。本篇为发布版源码对照。
