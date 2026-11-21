# 周期基上的矩阵怎样读出 Weil 表示的迹

## 命题

取素数 $\ell$，记 $\Omega_\ell=\overline{\mathbb Q}_\ell$，$F\subset\Omega_\ell$ 为 $\mathbb Q_\ell$ 的最大无分歧扩张。取项目中一对已对接的局部与全局周期环，记晶体环为 $B$，半稳定环为 $B_{\rm st}$。常数项嵌入 $\beta:B\to B_{\rm st}$ 尊重 Frobenius、伽罗瓦作用和 $\mathbb Q_\ell$ 标量。记 $u:F\to B$ 为该对接给出的系数映射，因而 $\beta(u(x))=x\cdot1$。固定系数同构 $\iota:\Omega_\ell\xrightarrow{\sim}\mathbb C$。

让 $K,L\subset\Omega_\ell$ 为有限扩域，$R:G_K\to{\rm GL}_a(L)$ 为一条表示，满足源码所用的 $D_{\rm pst}^{\rm ur}(R)$ 在 $F$ 上有限维，且复 Weil–Deligne 空间 $W$ 的维数恰为 $a$。这里 $D_{\rm st}(R)=(L^a\otimes_{\mathbb Q_\ell}B_{\rm st})^{G_K}$，而 $D_{\rm pst}(R)$ 允许先限制到有限扩张的伽罗瓦群再取不变量。$W$ 由 $D_{\rm pst}(R)$ 变换标量得到。固定一个通过局部分解群对接到 $G_K$ 的 Weil 元素 $g$，记它在 $W$ 上的算子为 $T_g$，令 $p=\iota^{-1}(\operatorname{tr}T_g)$。取 $n_1,n_2\ge0$，满足 Weil 次数 $\alpha(g)=n_2-n_1$。

再取 $\rho:G_K\to{\rm GL}_d(\mathbb Z_\ell)$、矩阵 $b_1,\ldots,b_d\in M_a(L)$ 与 $e_1,\ldots,e_d\in\mathbb Z_\ell$。对任意 $h\in G_K$ 及 $j$，假设 $R(h)b_j=\sum_i\rho(h)_{ij}b_i$，并设 $\sum_i e_i b_i=I_a$。设 $U\in{\rm GL}_d(B)$ 满足每个 $h\in G_K$ 的周期基恒等式 $\rho(h)h(U)=U$。对任意 $s\in B$、$V\in M_d(B)$，若

$$
V\varphi^{n_2}(U)=s\varphi^{n_1}(U),
$$

则令 $v=Ve$，$t_i=\operatorname{tr} b_i$ 后，对每个 $F$-线性泛函 $\lambda:\Omega_\ell\to F$，有

$$
\sum_i v_i\,u(\lambda(t_i))=s\,u(\lambda(p)).
\tag{1}
$$

这里 $e$ 的各项视为 $B$ 中的整数。结论是源码的 `IsTr`。它为[晶体迹闭性的误差计算](%E4%B8%BA%E4%BB%80%E4%B9%88%E4%BB%BB%E6%84%8F%E7%B2%BE%E5%BA%A6%E7%9A%84%E6%99%B6%E4%BD%93%E8%BF%B9%E8%AF%AF%E5%B7%AE%E5%BF%85%E9%A1%BB%E4%B8%BA%E9%9B%B6.md)提供基准迹等式和每层种子迹等式。

## 证明

先解周期基方程。记 $U_1=\varphi^{n_1}(U),U_2=\varphi^{n_2}(U)$，其中 Frobenius 逐项作用。因为环同态保存逆矩阵，$U_2$ 可逆。取 $w=U_2^{-1}e$，则

$$
U_2w=e,\qquad Ve=VU_2 w=sU_1w.
\tag{2}
$$

把 $b_i$ 的第 $k$ 列记作 $b_{i,k}$，置

$$
m_{jk}=\sum_i b_{i,k}\otimes\beta(U_{ij}).
$$

对任意 $h\in G_K$，在张量积上同时作用于两因子。应用 $R(h)b_{i,k}=\sum_{i'}\rho(h)_{i'i}b_{i',k}$，再把标量 $\rho(h)_{i'i}$ 移到右因子，就得到 $b_{i',k}$ 的周期系数 $\sum_i \rho(h)_{i'i}h(U_{ij})=U_{i'j}$。所以 $m_{jk}\in D_{\rm st}(R)$。Frobenius 与 $\beta$ 相容并只作用在右因子上，故 $\varphi^n m_{jk}=\sum_i b_{i,k}\otimes\beta(\varphi^n U_{ij})$。

现在取 $x_{jk}=\varphi^{n_2}m_{jk}\in D_{\rm pst}(R)$。在这个空间里，Weil 算子先作用 $\varphi^{-\alpha(g)}$，再作用 $g$ 的伽罗瓦分量。两作用可交换，且 $m_{jk}$ 被后者固定。因为 $n_2-\alpha(g)=n_1$，$x_{jk}$ 经 Weil 算子便成为 $\varphi^{n_1}m_{jk}$。以下仍把 $x_{jk}$ 记为它在 $W$ 中的像。

令 $C=\Omega_\ell\otimes_F B_{\rm st}$，$\kappa:\mathbb C\to C$ 为 $z\mapsto\iota^{-1}(z)\otimes1$。取坐标图 $\psi:W\to C^a$。这里的坐标图是加性的，并满足 $\psi(zx)=\kappa(z)\psi(x)$。对于来自 $D_{\rm pst}$ 的元素，其坐标正是把 $L^a\otimes_{\mathbb Q_\ell}B_{\rm st}$ 中的张量逐坐标送到 $\Omega_\ell\otimes_F B_{\rm st}$。该图的构造输入为 `CoordEx` 和 `CoordWD`。前者将纯张量的 $r$ 坐标 $z_r\otimes b$ 定义为 $z_r\otimes b\in C$，由 $\mathbb Q_\ell$-平衡性延拓。后者在 $D_{\rm pst}$ 上限制这个映射，它此时是 $F$-线性的，再用 $\iota$ 变换标量延拓到 $W$。

限制到 $D_{\rm pst}$ 后，分别乘以 $L$ 和 $F$ 的元素，都等于在 $C$ 的左张量因子中乘相应的系数。$L$ 的线性来自逐坐标定义，$F$ 的线性来自 $F$ 上张量积的平衡关系。由此坐标公式与两种标量扩张相容。

于是 $\psi(x_{jk})_r=\sum_i (b_i)_{rk}\otimes\beta((U_2)_{ij})$，同样 $\psi(T_g x_{jk})_r$ 用 $U_1$ 代替 $U_2$。把 $j$ 的权取作 $c_j=1\otimes\beta(w_j)$。先对 $j$ 求和，再用 (2) 将整数从张量右侧移到左侧，得到

$$
\sum_j c_j\psi(x_{jk})_r
=\sum_i(b_i)_{rk}\otimes\beta((U_2w)_i)
=\Bigl(\sum_i e_i(b_i)_{rk}\Bigr)\otimes1
=\delta_{rk}.
\tag{3}
$$

**加权取迹。** 设一般地 $W_0$ 是 $k_0$ 上 $a$ 维向量空间，$C_0$ 为交换环，$\kappa_0:k_0\to C_0$ 为环同态，$\psi_0:W_0\to C_0^a$ 为 $\kappa_0$-半线性加法映射。有限组 $x_{jk}$ 与权 $c_j$ 若满足 (3)，则任意 $k_0$-线性算子 $T$ 都满足

$$
\sum_{j,k}c_j\psi_0(Tx_{jk})_k=\kappa_0(\operatorname{tr}T).
\tag{4}
$$

为证此式，选 $W_0$ 的基，把基向量的 $\psi_0$ 坐标作列组成矩阵 $X$。以 $\sum_j c_j\kappa_0([x_{jk}])$ 为第 $k$ 列组成 $X'$，其中 $[x_{jk}]$ 为基坐标，$\kappa_0$ 逐项作用。(3) 就是 $XX'=I$。交换环上由行列式及伴随矩阵知 $X$ 可逆，故 $X'X=I$。令 $T_m$ 为 $T$ 的矩阵逐项施以 $\kappa_0$ 的结果，则 (4) 左侧等于 $\operatorname{tr}(XT_m X')=\operatorname{tr}(T_m)$。这就证明了 `TrLin`。

将 (4) 用到 $T_g$，代入 $\psi(T_g x_{jk})$ 的公式，对 $k$ 求和读出 $\operatorname{tr}b_i=t_i$，得到

$$
\sum_i t_i\otimes \beta((U_1w)_i)
=p\otimes1\qquad\text{于 }C.
$$

对任意 $\lambda$，施以张量积映射 $x\otimes b\mapsto\lambda(x)b$，它由 $F$-线性定义良好。结果两边都在 $B_{\rm st}$ 的晶体常数项中，借 $\beta$ 的单射性回到 $B$，得到
$\sum_i u(\lambda(t_i))(U_1w)_i=u(\lambda(p))$。
再乘 $s$，用 (2) 化为 (1)。

## 源码对照

- `TieRep2` 给上述全称命题，`tieRep_holds` 将所列坐标、列不变性、Weil 作用和加权取迹引理组装成它。[IsOp2One.lean 第 69 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/IsOp2One.lean#L69) · [TieRep.lean 第 64 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/TieRep.lean#L64)
- `colInv_holds` 证明列给不变周期，`weilPhi_core` 依次数将 $n_2$ 降到 $n_1$。[ColInv.lean 第 33 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/ColInv.lean#L33) · [WeilPhi.lean 第 8 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/WeilPhi.lean#L8)
- `coordEx_holds`、`coordWD_holds` 构造坐标，`trLin_holds` 证明 (4)，`testTr_holds` 用线性泛函读回 (1)。[CoordEx.lean 第 21 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/CoordEx.lean#L21) · [CoordWD.lean 第 106 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/CoordWD.lean#L106) · [TrLinHolds.lean 第 7 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/TrLinHolds.lean#L7) · [TestTr.lean 第 7 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/TestTr.lean#L7)

本文按发布版源码对读。这里对接周期环和局部桥是输入，维数等式和周期基是显式假设。
