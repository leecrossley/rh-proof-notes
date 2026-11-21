# 为什么分圆展开的单项由 de Rham 过滤决定

## 命题

设 $L$ 为域，$B$ 为带整数过滤的周期域，含有 $L$，并取 $t_B\in B^\times$。假定过滤递减、分离、穷尽、与乘法相容，且

$$
\operatorname{Fil}^aB=t_B^aB^+,\qquad B^+=\operatorname{Fil}^0B.
$$

假定 $L\subset B^+$，且评价 $e:L[[t]]\to B^+$ 把 $t$ 送到 $t_B$，并满足

$$
e(a)\in t_B^mB^+\quad\Longleftrightarrow\quad a\in t^mL[[t]]
\qquad(m\ge0).
$$

对每个非零展开，其第一项的非零 $L$ 系数在 $B^+$ 中是单位，这正是此条件的含义。

设 $V$ 是有限维 $L$-空间，$p:V\to B^n$ 为 $L$-线性坐标映射。给定 $r\le n$ 条 $V$ 值 Laurent 展开 $g_1,\ldots,g_r$，其张成的 $L[[t]]$-子模记为 $\Lambda$。给每条 $g_j$ 一个对应的 $\psi_j\in (B^+)^n$。设 $\psi_j$ 生成 $(B^+)^n$，并与 Laurent 系数相容，即对任何 $a_j\in L[[t]]$，若 $f=\sum_j a_jg_j$，则 $\sum_j e(a_j)\psi_j$ 在 $B^n$ 中有 $p(f_k)$ 为第 $k$ 项的 $t_B$-进展开。精确含义是先乘任意足够大的 $t_B^N$ 去掉负指数，再逐次截断比较模 $t_B^bB^+$ 的余项。

再假定 $\Lambda$ 包含 $t^m V[[t]]$ 对某个整数 $m$ 成立。则对 $d\in V,k\in\mathbb Z$，

$$
dt^k\in\Lambda
\quad\Longleftrightarrow\quad
p(d)\in(\operatorname{Fil}^{-k}B)^n .
$$

应用中 $V$ 是固定系数分量的晶体周期空间，$p$ 投影到指定嵌入的 de Rham 空间，然后在原 $L$-表示的一组基下取坐标。

## 证明

先把比较里的展开等式写明。假如 $dt^k=\sum_j a_j g_j$，按输入左边在 $B^n$ 中对应 $t_B^k p(d)$，所以

$$
t_B^k p(d)=\sum_j e(a_j)\psi_j.
\tag{1}
$$

其中只需从所有有限阶截断的一致性推出等式。两侧乘足够大的 $t_B^N$ 后，每个 $b$ 的截断之差在 $\operatorname{Fil}^b B$ 中。由过滤分离性，两侧确实相等。因 $e(a_j)\in B^+$ 且 $\psi_j\in(B^+)^n$，(1) 表明 $t_B^kp(d)\in(B^+)^n$，也就得到 $p(d)\in(\operatorname{Fil}^{-k}B)^n$。

反过来设 $t_B^kp(d)\in(B^+)^n$。先在 $B^+$ 中写成

$$
t_B^kp(d)=\sum_j b_j\psi_j,\qquad b_j\in B^+ .
\tag{2}
$$

$\psi_j$ 生成 $(B^+)^n$，所以也生成 $B^n$。又 $r\le n$，故它们是 $B^n$ 的一组基，表示唯一。取足够大的整数 $h\ge0$，使 $k+h\ge m$。根据满尾部的假设，$dt^{k+h}\in\Lambda$，取 $a_j\in L[[t]]$ 使 $\sum_j a_jg_j=dt^{k+h}$。用 (1) 及 (2)，有

$$
\sum_j e(a_j)\psi_j=t_B^{k+h}p(d)
                  =\sum_j t_B^h b_j\psi_j .
$$

基的线性无关给出 $e(a_j)=t_B^h b_j$，所以都属于 $\operatorname{Fil}^h B$。于是 $t^h\mid a_j$ 在 $L[[t]]$ 中成立。将级数等式除以 $t^h$，得到 $dt^k=\sum_j(a_j/t^h)g_j$，即所求。

## 如何回到局部表示

设 $V_0$ 是原 $L$-表示，$\iota:L\hookrightarrow B_{\rm dR}$ 是取系数分量所用的嵌入。在 $V_0\otimes_{\mathbb Q_\ell}B_{\rm dR}$ 中，将 $cv\otimes b$ 与 $v\otimes\iota(c)b$ 识别，得到 $V_0\otimes_{L,\iota}B_{\rm dR}$。取 $V_0$ 的基 $v_\alpha$，这个商的坐标为 $\sum_\alpha v_\alpha\otimes b_\alpha\mapsto(b_\alpha)_\alpha$。因此，原张量空间中「模掉系数关系后属于第 $a$ 级过滤」等价于每个 $b_\alpha\in\operatorname{Fil}^a B_{\rm dR}$。工程的 `FilAt` 在晶体周期分量上便用这一比较识别对应的 de Rham 过滤。

在源码的应用中，Wach 模原基的像 $\psi_j$ 生成 $(B_{\rm dR}^+)^n$。其构造来自当前分圆层的 de Rham 比较映射。先用低层或满秩结果得到展开格包含全部高次项，再用本篇识别单项，最后靠[逐次分离](%E4%B8%BA%E4%BB%80%E4%B9%88%E5%88%86%E5%9C%86%E5%B1%95%E5%BC%80%E6%A0%BC%E5%8F%AF%E4%BB%A5%E9%80%90%E4%B8%AA%E6%AC%A1%E6%95%B0%E6%A3%80%E6%9F%A5.md)就得到

$$
f\in\Lambda \quad\Longleftrightarrow\quad
f\ \text{下方有界且}\ f_k\in\operatorname{Fil}^{-k}\ \text{对所有 }k .
$$

## Lean 对照

- `single_mem_iff` 用 `Rep.unique` 比较有限阶截断，再用 $\psi_j$ 的线性无关把 $t_B^h$ 的整除传到每个形式幂级数系数。[WachLatticeEqFiltrationSumAtLevel.lean:80](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeEqFiltrationSumAtLevel.lean#L80) · [同文件:180](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeEqFiltrationSumAtLevel.lean#L180)
- `mem_sup_iff` 证明坐标判据，`lat_eq_fil` 把单项结果用于晶体周期的系数分量，并调入分圆层的 de Rham 比较。[WachLatticeEqFiltrationSumAtLevel.lean:404](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeEqFiltrationSumAtLevel.lean#L404) · [同文件:423](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeEqFiltrationSumAtLevel.lean#L423)

状态为源码级推导。另行未重新编译。这篇展开比较映射给定后的数学；比较映射本身由工程的分圆层实现提供。
