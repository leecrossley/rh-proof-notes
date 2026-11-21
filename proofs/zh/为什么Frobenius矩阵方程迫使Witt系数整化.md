# 为什么 Frobenius 矩阵方程迫使 Witt 系数整化

## 命题

设 $\ell$ 是素数，$k$ 为特征 $\ell$ 的完美赋值域，$R\subset k$ 为它的赋值环。设 $B=W(k)$、$B^+=W(R)$ 为 $\ell$-典型 Witt 环。令 $\Phi$ 逐 Witt 坐标施加 $x\mapsto x^\ell$，并逐系数作用于矩阵。对任意有限行列数 $d,e$，若 $Z\in M_{d,e}(B)$、$P\in M_d(B^+)$、$P'\in M_e(B^+)$、$Y\in M_{d,e}(B^+)$ 满足

$$
\Phi(Z)=P Z P'+Y ,
\tag{1}
$$

则 $Z\in M_{d,e}(B^+)$。这个结论对 $B,B^+$ 同时沿 $\mathbb Z_\ell$ 扩张到任意有限自由 $\mathbb Z_\ell$-代数 $O$ 后亦成立，其中 $\Phi$ 作用在 Witt 因子且固定 $O$。

项目取 $k=\mathbb C_\ell^\flat$，即 $\ell$-进复数域的倾斜，$R=\mathcal O_{\mathbb C_\ell^\flat}$。这段在 Wach 格的反演比较中用来检查一个周期坐标和逆矩阵的坐标是否属于整周期环 $A_{\inf}$。

## 证明

先把 (1) 模 $\ell$ 约化，记小写字母为像。取乘法赋值 $|\cdot|$ 使 $R=\{x:|x|\le1\}$。若 $z$ 有一项的绝对值大于 $1$，取绝对值最大的一项，设其值为 $M>1$。在该位置，左侧的绝对值为 $M^\ell$。右侧的每个乘积只出现一次 $z$，其余来自 $P,P'$ 的因子绝对值至多 $1$，而 $y$ 也有绝对值至多 $1$。超度量不等式给出右侧至多 $M$，与 $M^\ell>M$ 矛盾。所以 $z$ 每项都在 $R$。

下面逐层增加 $\ell$ 的精度。取 $z$ 各项的 Teichmüller 提升，得 $Z_0\in M_{d,e}(B^+)$，写 $Z=Z_0+\ell Z_1$。这一步用 $W(k)/\ell W(k)=k$。因为 $k$ 完美，$R$ 也完美：元素若在 $R$，其唯一的 $\ell$ 次根的绝对值仍至多一。故有 $W(R)/\ell W(R)=R$，而且 $W(R)/\ell W(R)\to W(k)/\ell W(k)$ 单射。代回 (1) 得

$$
\ell\big(\Phi(Z_1)-PZ_1P'\big)
       =PZ_0P'+Y-\Phi(Z_0).
$$

等式右侧既在 $M_{d,e}(B^+)$ 内，在大环中又被 $\ell$ 整除。因此利用模 $\ell$ 的单射，它在小环中也被 $\ell$ 整除。消去大环中无挠的 $\ell$，得到 $\Phi(Z_1)=PZ_1P'+Y_1$，其中 $Y_1\in M_{d,e}(B^+)$。对 $Z_1$ 重复这一论证，于是 $Z$ 在任意模 $\ell^n$ 的截断中等于某个小环元素。这意味着其每个 Witt 坐标都在 $R$，即 $Z\in M_{d,e}(B^+)$。矩阵若无条目，结论直接成立。

现在扩张系数到 $O$。给 $O$ 取一个有限 $\mathbb Z_\ell$-基。每个扩张后的环元素 $b$ 都在自由模 $O\otimes_{\mathbb Z_\ell}B$ 上定义乘法矩阵 $L_b$。把 $Z,P,P',Y$ 每个元素替换成对应的乘法块矩阵，可保持加法、乘法与 $\Phi$。原结论说明 $Z$ 的每个块只有小环系数。将块矩阵作用到单位元 $1$ 的坐标向量，得到 $b=L_b(1)$，于是 $b\in O\otimes_{\mathbb Z_\ell}B^+$。这个步骤使先前的绝对值论证只需在真正的赋值域里用一次。

## Lean 对照

- `residue_integral` 取赋值最大项。`step` 减去第一位的整提升后用模 $\ell$ 单射消去一份 $\ell$。`integral_of_frobenius` 让截断阶数趋向无穷，逐坐标回到小环。倾斜整数环为赋值环的构造见 `valuationRing_tilt`，其域和完美性由工程的倾斜模型提供。[FrobeniusIntegralityWittTiltAinf.lean:102](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/FrobeniusIntegralityWittTiltAinf.lean#L102) · [同文件:144](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/FrobeniusIntegralityWittTiltAinf.lean#L144) · [同文件:239](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/FrobeniusIntegralityWittTiltAinf.lean#L239) · [同文件:92](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/FrobeniusIntegralityWittTiltAinf.lean#L92)
- `eq_sum_regRep` 是作用到单位元的坐标重构。`integrality_baseChange` 使用乘法块矩阵，最后的系数域整数环版本是 `frobenius_integrality_coeff`。[扩张系数的源码](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/FrobeniusIntegralityTensorAinfCoefficients.lean)

状态为源码级推导。另行未重新编译。底层 Witt 环性质及域的倾斜构造作为输入。
