# 怎样用 Frobenius 把 Herr 方程的解延拓到整个开圆盘

## 命题

设 $\ell$ 为素数，$O\subset L$ 为有限扩张 $L/\mathbb Q_\ell$ 的整数环。取 $s\ge1$，若 $\ell=2$ 则 $s\ge2$。令 $u\in1+\ell^s\mathbb Z_\ell$ 且 $v_\ell(u-1)=s$。在级数 $f(U)$ 上定义

$$
\gamma f(U)=f((1+U)^u-1),\qquad
 \varphi f(U)=f((1+U)^\ell-1).
$$

这两个代入交换。设 $n\ge1$，指标 $i\in\mathbb Z/n\mathbb Z$，每个分量用同一个 $O[[U]]$。取 $X=(1+U)^{\ell^{s-1}}-1$、$Q=\Phi_{\ell^s}(1+U)$，其中 $\varphi(X)=XQ$。给定 $m,k\ge0$ 和有限多重集 $J$ 的非负整数，记 $\Lambda=\prod_{j\in J}\varphi^j(Q)$。

对每个 $i$ 设 $G_i,P_i,P_i'\in M_r(O[[U]])$，$y_i,z_i\in O[[U]]^r$，满足 $G_i(0)=I$、$z_i(0)=0$、$P_i P_i'=Q^k I$。在 $L[[U]]$ 中 $Q,\Lambda$ 因常数项非零而可逆，定义

$$
A_i=\begin{pmatrix}G_i&z_i\\0&1\end{pmatrix},
 \qquad F_i=\begin{pmatrix}Q^{-m}P_i &\Lambda^{-1}y_i\\0&1\end{pmatrix}.
$$

假定 $A_i\gamma(F_i)=F_i\varphi(A_{i-1})$。这正是项目的两项矩阵假设，左上块来自 $\gamma,\varphi$ 交换，右上块来自 Herr 余闭链等式。则有唯一一组 $w_i\in UL[[U]]^r$ 满足

$$
G_i\gamma(w_i)-w_i=z_i .
\tag{1}
$$

而且 $\log(1+U)^{m+|J|}w_i$ 的每个系数级数都在 $|U|<1$ 收敛。这里 $\log(1+U)^{p}$ 表示先取对数、再取 $p$ 次幂。这一结论是把 Herr 余闭链的分圆解送入晶体周期环所需的解析部分。

## 原点附近的解

先求矩阵 $V_i(U)$ 使

$$
A_i\gamma(V_i)=V_i,\qquad V_i(0)=I .
\tag{2}
$$

按 $U$ 次数递推。因为 $A_i(0)=I$，而 $(1+U)^u-1=uU+O(U^2)$，第 $d$ 次项中未知矩阵的系数是 $u^d-1$，低次项已知。这不是零，由[单位差赋值](%E4%B8%BA%E4%BB%80%E4%B9%88%E5%9D%97%E9%97%B4%E5%88%86%E6%AF%8D%E7%9A%84%E8%B5%8B%E5%80%BC%E6%98%AF%E5%88%86%E5%9C%86%E5%B1%82%E6%95%B0%E5%8A%A0%E9%98%B6%E4%B9%98%E8%B5%8B%E5%80%BC.md)有 $v_\ell(u^d-1)=s+v_\ell(d)$。因此 (2) 唯一有形式解，且可逆。若 $M_d$ 是前 $d$ 阶系数的最大绝对值和 $1$ 的较大者，递推右侧的标量均为整数，故

$$
M_d\le |u^d-1|^{-1}M_{d-1}
     \le \ell^{sd+v_\ell(d!)}\le\ell^{(s+1/(\ell-1))d}.
$$

所以 $V_i$ 在任意半径小于 $\ell^{-(s+1/(\ell-1))}$ 的闭圆盘收敛。它的最后一行是 $(0,1)$，因为此行逐系数由 $\gamma$ 固定，而一个 $\gamma$-固定级数若有非常数项，其最低次项违反 $u^d\ne1$。右上列取负，得到 (1)。直接比较两个解的最低非零次数，也给出置零常数项后的唯一性。

## 怎样找出可清除的分母

令 $\tau=\log(1+U)/X$ 作形式商，$p=m+|J|$。$\tau$ 在整个开圆盘收敛。确切地，写 $X=\varphi^{s-1}(U)$，用形式对数的代入等式可写

$$
\tau=\ell^{-(s-1)}
       \left.\frac{\log(1+v)}{v}\right|_{v=X}.
$$

当 $|U|<1$，$|X|<1$，右侧直接收敛。并且 $\varphi(\tau)=\ell\tau/Q$。迭代此式给

$$
\tau
 = \ell^{-j-1}\varphi^{j+1}(\tau)\prod_{b=0}^{j}\varphi^b(Q)
 \qquad(j\ge0).
\tag{3}
$$

所以对每个 $j$，$\tau/\varphi^j(Q)$ 都可按一个在整开圆盘收敛的级数来表示。按重数相乘，$\tau^{|J|}/\Lambda$ 也如此。

定义 $L_p=\operatorname{diag}(\tau^pI_r,1)$ 和 $C_i=L_pV_i$。先由矩阵相容性及 (2)，得到

$$
A_i\gamma(F_i\varphi(V_{i-1}))
 =F_i\varphi(A_{i-1}\gamma(V_{i-1}))
 =F_i\varphi(V_{i-1}).
$$

任何这样的不变矩阵在左乘 $V_i^{-1}$ 后，都逐系数受标量 $\gamma$ 固定，因而为常数。这个矩阵可逆，因为 $P_iP_i'=Q^kI$ 使 $F_i$ 在 $L[[U]]$ 可逆。因此存在可逆常数矩阵 $B_i$ 使 $V_i=F_i\varphi(V_{i-1})B_i$。乘 $L_p$ 后改写为

$$
C_i=H_i\varphi(C_{i-1})B_i,\qquad
 H_i=
 \begin{pmatrix}
  \ell^{-p}Q^{p-m}P_i & (\tau^p/\Lambda)y_i\\
 0&1
 \end{pmatrix}.
\tag{4}
$$

这里第一个系数正是 $\tau^p/(Q^m\varphi(\tau)^p)$。由于 $p\ge m$ 且 (3) 清掉 $\Lambda$ 的全部因子，$H_i$ 的每项都在整开圆盘收敛。

## 从小圆盘传到任意半径

对任意 $0<R<1$，Frobenius 代入的多项式 $f(U)=(1+U)^\ell-1$ 在半径 $R$ 的 Gauss 范数至多 $\max(\ell^{-1}R,R^\ell)$。因为低于 $\ell$ 的正次二项式系数都被 $\ell$ 整除。故反复代入可把这个圆盘送进任意小的有正半径的圆盘。更具体地，在半径不超过 $R$ 时每一步最多乘 $\max(\ell^{-1},R^{\ell-1})<1$。

现在迭代 (4)，直到最里面的 $\varphi^a(C_{i-a})$ 可以用原点附近的收敛性。外面的各个有限矩阵因子来自 $H_i$、其 Frobenius 代入及常数 $B_i$，在半径 $R$ 上都收敛。于是等式右边在这一半径收敛，作为形式级数等于 $C_i$。由于 $R$ 任意，$C_i$ 在整开圆盘收敛。其右上列为 $-\tau^p w_i$。乘上多项式 $X^p$ 即知 $\log(1+U)^p w_i$ 收敛，得到结论。

## Lean 对照

- `exists_basis_bd` 取得原点附近的收敛不变基。`block_relation` 用常数矩阵识别 Frobenius 后的不变基。[ExistsCocycleSolutionConv.lean:104](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsCocycleSolutionConv.lean#L104) · [同文件:38](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsCocycleSolutionConv.lean#L38)
- `tau_eq` 和 `prod_dvd` 用对数的 Frobenius 等式吸收分母。`letterwise` 逐分量取得递推，再调用开圆盘延拓。`exists_cocycle_solution_conv` 为总入口。[同文件:168](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsCocycleSolutionConv.lean#L168) · [同文件:211](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsCocycleSolutionConv.lean#L211) · [同文件:238](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsCocycleSolutionConv.lean#L238) · [同文件:405](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsCocycleSolutionConv.lean#L405)

状态为源码级推导。另行未重新编译。小圆盘处用直接的系数递推给出与源码一致的收敛半径。
