# Turán幂和怎样推出带对数损失的零点排斥

**命题（[`deuring_heilbronn_lossy`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHB.lean#L13)）。** 存在绝对常数 $c_0,c_1,c_2>0$，使对每个整数 $M\ge3$、每个实数 $T\ge2$，记 $L=\log(MT)$，有下列结论。设 $\chi_1$ 是模 $M$ 的非主实特征，$\beta$ 是它的实零点且 $1-c_1/L<\beta<1$。设 $\chi$ 是模 $M$ 的任意特征，$\rho$ 是其 $L$ 函数的零点，满足 $\Re\rho\ge1-c_0$、$|\Im\rho|\le T$ 且 $(\chi,\rho)\ne(\chi_1,\beta)$。主特征的 $1$ 是极点，不计入零点。则

$$
(1-\Re\rho)L\ \ge\
 c_2\log\frac{c_1}{(1-\beta)L^3}.
 \tag{1}
$$

Lean 的陈述 `DeuringHeilbronnMB` 只要求存在某个自然数作为 $L$ 的幂指数，证明取 $3$。筛选所用的相对素数定理将它代入加权零点和，以便从误差里提出 $1-\beta$ 的因子。[加权零点和怎样使用排斥](%E9%9B%B6%E7%82%B9%E5%AF%86%E5%BA%A6%E5%B8%A6%E5%AF%B9%E6%95%B0%E6%8D%9F%E5%A4%B1%E6%97%B6%E6%80%8E%E6%A0%B7%E4%BF%9D%E4%BD%8F%E7%9B%B8%E5%AF%B9%E8%AF%AF%E5%B7%AE.md)

## 一、把两个移高的对数导数变为倒数幂和

记 $\lambda=1-\beta$、$t=\Im\rho$、$\ell=\log(3M)$，取 $0<h\le2/25$，并记 $s_0=1+h,s_1=1+h+it$。对每个整数 $j\ge1$，定义

$$
D_j(\psi;s)=\frac1{(j-1)!}\sum_{n\ge1}
  \frac{\Lambda(n)\psi(n)(\log n)^{j-1}}{n^s},
 \qquad
 A_j=D_j(\chi_0;s_0)+D_j(\chi_1;s_0).
$$

$\Lambda$ 是 von Mangoldt 函数。绝对收敛允许逐项计算。因为 $\chi_1^2=\chi_0$，在单位上 $1+\chi_1(n)\ge0$，在非单位上两特征都为零。因此 $A_j$ 为非负实数，且

$$
|D_j(\chi;s_1)+D_j(\chi\chi_1;s_1)|\le A_j .
 \tag{2}
$$

四个对数导数的实部总和也非负。后两项用同一高度 $t$，所以其项与前两项合并后是非负权乘以 $1+\Re(\chi(n)n^{-it})$。

本节用如下局部估计。对任意模 $M$ 特征 $\psi$ 与实数 $v$，在闭盘 $|\rho'-(26/25+iv)|\le4/25$ 取其所有零点 $\rho'$ 及各自的正整数权 $m_{\rho'}$。这些零点的实部小于 $1$，权重总和 $O(\log(M(|v|+2)))$。对 $\Re s>1$、$|s-(26/25+iv)|\le1/25$ 和每个 $j\ge1$，有

$$
D_j(\psi;s)=\frac{\mathbf1_{\psi=\chi_0}}{(s-1)^j}
             -\sum_{\rho'}\frac{m_{\rho'}}{(s-\rho')^j}
             +O(\log(M(|v|+2))25^{j-1}).
 \tag{3}
$$

这是 `DHLocal`，下面展开它。它来自半径 $12/25$ 的对数导数圆盘估计，对去掉主特征极点后的解析余项作 Cauchy 导数估计。对非主特征用 $f(s)=L(s,\psi)$。对主特征用去极点的 $f(s)=(s-1)L(s,\chi_0)$，在 $1$ 的定义取极限。后者在 $1$ 的值为 $\prod_{p\mid M}(1-1/p)\ne0$，所以去极点前后计数相同。在中心 $z_0=26/25+iv$，Euler 乘积给 $|L(z_0,\psi)|^{-1}\le\zeta(26/25)\le26$。去极点的情形还用 $|z_0-1|\ge1/25$。外盘半径 $r=12/25$，其左端 $14/25>1/2$。非主特征由周期和得多项式增长。对主特征用 $(s-1)\zeta(s)$ 的增长界，乘上有限 Euler 乘积。在该盘内每个 Euler 因子模至多 $2$，其乘积至多 $2^{\omega(M)}\le M$。因此外盘上的相对增长 $|f(z)|/|f(z_0)|$ 由 $M(|v|+2)$ 的固定次幂及常数控制。

圆盘引理在半径 $r/3=4/25$ 内找零点，并从 $f'/f$ 扣掉各零点的 $m_{\rho'}/(s-\rho')$。剩下的函数在半径 $r/6$ 的盘内有界，界为 $O(\log(M(|v|+2)))$，由可去奇点定理延拓到盘内全部点。对离 $z_0$ 不超过 $r/12=1/25$ 的 $s$，以 $s$ 为心用半径 $r/12$ 的 Cauchy 界（可取稍小半径后令半径增加）。归一化的第 $j-1$ 阶导数至多把界乘 $25^{j-1}$。主特征在 $f'/f$ 中多了一项 $1/(s-1)$，从它换回 $D_j(\chi_0;s)$ 时产生 (3) 的极点项。[圆盘引理](%E5%9C%86%E7%9B%98%E9%87%8C%E7%9A%84%E9%9B%B6%E7%82%B9%E6%80%8E%E6%A0%B7%E6%8E%A7%E5%88%B6%E5%AF%B9%E6%95%B0%E5%AF%BC%E6%95%B0.md) · [增长界](%E6%80%8E%E6%A0%B7%E7%94%A8%E6%9C%89%E9%99%90%E5%B7%AE%E5%88%86%E6%8E%A7%E5%88%B6L%E5%87%BD%E6%95%B0%E7%9A%84%E5%A2%9E%E9%95%BF.md)

取 $c_1\le1/20,\ c_0\le2/25$。前两项在 $v=0$ 用 (3)，$\beta\ge19/20$ 落在 $\chi_1$ 的盘中，从零点表中删掉它的一份。后两项在 $v=t$ 用 (3)，若某一项的特征为 $\chi_1$ 且该盘含 $\beta$，也删掉它的一份。前两项恰有一个主特征极点，后两项至多有一个。后一对若有主特征，另一特征就是 $\chi_1$。凡能配对的极点与删去的零点，其差满足

$$
|(s-1)^{-j}-(s-\beta)^{-j}|
 \le j\lambda h^{-j-1}
$$

，因为沿 $1$ 到 $\beta$ 的线段上 $|s-x|\ge h$。若后一对存在极点而其 $\beta$ 在盘外，由 $26/25-\beta\le9/100$ 与盘半径 $4/25$ 可知 $|t|>1/8$，未配对极点项的模至多 $8^j$。四个局部误差均为 $O(L25^{j-1})$。

令 $w_i$ 枚举后两项剩余的 $s_1-\rho'$，按权重复。因为没有零点在 $\Re s\ge1$，$\Re w_i\ge h$。目标零点在第三项的盘内，因为 $\Re\rho\ge22/25$ 且 $\Im\rho=t$，条件 $(\chi,\rho)\ne(\chi_1,\beta)$ 保证它未被删掉。因而有一项 $w_i=h+(1-\Re\rho)$。由 (2) 和后两项的 (3)，取绝对值得

$$
\left|\sum_i w_i^{-j}\right|\le A_j+2j\lambda h^{-j-1}+25^j C_F L.
 \tag{4}
$$

还可从四个 (3) 之和的实部取 $j=1$。四个对数导数总和的实部非负，每个倒数 $(s-\rho')^{-1}$ 的实部也非负。丢去前两张零点表的倒数和，留下

$$
\Re\sum_i w_i^{-1}\le 2\lambda h^{-2}+25C_F L.
 \tag{5}
$$

同一个绝对常数 $C_F>0$ 适用于 (4)、(5)。这里分别使用两种估计的原因在于，一阶实部总量将控制参与 Turán 的项数，高阶的复模上界将与 Turán 的大值相冲突。

## 二、正系数素数和的上界

当 $0<h\le1$、$\beta\ge1-1/\ell$ 时，源码的 `DHPrime` 给出绝对常数 $C_P>0$，对所有 $j\ge1$，

$$
A_j\le C_P\lambda\ell^2(j+1)^2h^{-j-1}
      +\frac{(C_P\ell)^j}{(j-1)!}
      +\frac{C_P(j+1)\ell^2}{Mh^j}.
 \tag{6}
$$

这是对两个实轴对数导数的估计，权为 $1+\chi_1(n)$（只考虑与 $M$ 互素的 $n$）。正系数和的证明可继续读双曲线分割和分段求和。[素数侧估计](%E5%8F%8C%E6%9B%B2%E7%BA%BF%E5%88%86%E5%89%B2%E6%80%8E%E6%A0%B7%E6%8E%A7%E5%88%B6%E5%B8%A6%E6%AD%A3%E7%B3%BB%E6%95%B0%E7%9A%84%E7%B4%A0%E6%95%B0%E5%B9%82%E5%92%8C.md)

这里 $\ell\le2L$，所以 $c_1\le1/20$ 已保证 $\beta\ge1-1/\ell$。还用 Siegel 间隙的特例 $\lambda\ge c_S M^{-1/2}$（$c_S>0$ 为绝对常数）。由 $\ell^2\ll\sqrt M$，得到 $\ell^2/M\ll\lambda$。[Siegel 间隙的证明](%E6%80%8E%E6%A0%B7%E7%94%B1%E9%9D%9E%E8%B4%9FDirichlet%E7%B3%BB%E6%95%B0%E5%BE%97%E5%88%B0Siegel%E9%97%B4%E9%9A%99.md)

## 三、选阶数与排斥距离

通常的零点区域给定一个绝对常数 $c_Z>0$，区域中至多一个零点。选 $c_1\le c_Z/4$，于是 $\beta$ 在该区域内。由 $\log(M(|t|+2))\le2L$，另一零点满足 $L(1-\Re\rho)\ge c_Z/2$。以下令 $h=1-\Re\rho$，则 $h>0$，前面构造的 $w_i$ 有一个等于 $2h$。[零点区域里的唯一性](%E4%B8%BA%E4%BB%80%E4%B9%88%E9%9D%A0%E8%BF%91%E4%B8%80%E7%9A%84%E5%AE%9E%E4%BE%8B%E5%A4%96%E9%9B%B6%E7%82%B9%E5%94%AF%E4%B8%80%E4%B8%94%E7%AE%80%E5%8D%95.md)

反设 $hL<c_2K$，其中 $K=\log(c_1/(\lambda L^3))$。由于 $hL\ge c_Z/2$，$K>c_Z/(2c_2)$，故可用预先选小 $c_2$ 使本证明中的 $K$ 超过任何固定阈值。令 $u_i=h/w_i$。$\Re w_i\ge h$ 推出 $|u_i|^2\le\Re u_i$，且其中一项为 $1/2$。由 (5)，

$$
S:=\sum_i\Re u_i\le 2\lambda/h+25C_F hL.
 \tag{7}
$$

因为 $\lambda L^3=c_1e^{-K}$、$L\ge1$ 和 $hL\ge c_Z/2$，第一项至多 $4c_1/c_Z\le1$。

可直接用 $A=1,C_T=1600$ 的 [Turán 界](%E6%9C%89%E7%90%86%E5%87%BD%E6%95%B0%E5%92%8C%E5%8D%95%E4%BD%8D%E6%A0%B9%E6%80%8E%E6%A0%B7%E7%BB%99%E5%87%BATur%C3%A1n%E7%9A%84%E8%BF%9E%E7%BB%AD%E5%B9%82%E5%92%8C%E7%95%8C.md)。保留源码的写法，令 $A\ge1,C_T>0$ 是一般 Turán 界里的常数，即阶数区间 $[m+1,m+An]$ 中有一个幂和模至少 $[n/(C_T(m+n))]^{An}$。取

$$
R=16e^{A+1},\qquad \epsilon=R^{-1},\qquad
 \theta=(2\log R)^{-1},\qquad D=\log\max(C_T,1),
 \qquad \kappa=\frac{\theta\epsilon^2}{A(D+1)}.
$$

选 $c_0\le1/(25R)$，$25C_F c_2\le\kappa$，$2eC_P c_2R\le\theta$。由 (7) 得 $S\le1+\kappa K$。只对 $|u_i|\ge\epsilon$ 的 $n$ 项用 Turán，$1\le n\le S/\epsilon^2$，因为每项的实部至少 $\epsilon^2$。除以这些项中最大的模（至少 $1/2$）再用 Turán，取 $m=\lceil\theta K\rceil$。得到 $m+1\le j\le m+An$，并有

$$
2^{-j}\left(\frac{n}{C_T(m+n)}\right)^{An}
 \le\left|\sum_i u_i^j\right|+\epsilon^{j-2}S.
 \tag{8}
$$

这里较小的项用 $|u_i|^j\le\epsilon^{j-2}\Re u_i$ 控制，且 $j\ge2$。又由 $n\epsilon^2\le1+\kappa K$，得

$$
\theta K<j\le2\theta K+J,\qquad AnD\le AD/\epsilon^2+j,
 \qquad J=1+A/\epsilon^2 .
$$

用 $\log(1+m/n)\le m/n$ 和 $m\le j$，(8) 的左端至少为 $E^{-1}(8/R)^j$，其中 $E=e^{AD/\epsilon^2}$。

最后以 $h^j$ 乘 (4) 和 (6)。含 $\lambda/h$ 的项由 $\lambda/h\le 2\lambda L/c_Z$ 及 $\ell\le2L$ 控制。末项 $(j+1)\ell^2/M\ll (j+1)\lambda$ 也可合并，合计 $O((j+1)^2\lambda L^3)$。阶乘项满足

$$
\frac{(C_P\ell h)^j}{(j-1)!}\le j(e C_P\ell h/j)^j\le jR^{-j}.
$$

后一界用 $\ell h\le2c_2K$ 和 $j>\theta K$。圆盘误差 $C_F L(25h)^j\le jR^{-(j-1)}$，用 $25h\le R^{-1}$ 与 $25C_F hL\le\kappa K\le\theta K<j$。尾项 $\epsilon^{j-2}S$ 也由 $R^2(1+j)R^{-j}$ 控制。又 $j\le K/\log R+J$ 给 $\lambda L^3=c_1e^{-K}\le c_1 R^{J-j}$。所以 (8) 迫使 $8^j\le C(j+1)^2$，其中 $C$ 独立于 $c_2,M,T$ 和特征。初始把 $c_2$ 选到使 $\theta c_Z/(2c_2)$ 超过该不等式允许的最大阶数即可。由此反设不能成立，得 (1)。

其中 $\ell^2$ 来自 (6) 的正系数和，$1/h\ll L$ 来自通常零点区域。合并组装上界时，两者产生 $\lambda L^3$，这就是本证明的对数幂来源。

## Lean 对照

- [`deuring_heilbronn_lossy`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHB.lean#L13) `deuring_heilbronn_lossy`、[`deuring_heilbronn_finish_turan`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/DeuringHeilbronnFinishTuran.lean#L14) `deuring_heilbronn_finish_turan` 给 (1)，[`region_gap`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHFinish.lean#L22) `region_gap` 给通常区域的间隙。[结论第 13 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHB.lean) · [合成第 14 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/DeuringHeilbronnFinishTuran.lean) · [间隙第 22 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHFinish.lean)
- [`deuring_heilbronn_dominant`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHDom.lean#L108) `deuring_heilbronn_dominant`、[`deuring_heilbronn_local`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHLocal.lean#L167) `deuring_heilbronn_local`、[`deuring_heilbronn_inequality`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHIneqF.lean#L12) `deuring_heilbronn_inequality` 给 (2)–(5)。取模只用移高的两张表。$\Re$ 一阶和才用四张表。[对数导数比较第 108 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHDom.lean) · [局部第 167 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHLocal.lean) · [Cauchy 第 84 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHCauchy.lean) · [两种和第 12 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHIneqF.lean)
- [`deuring_heilbronn_prime_sum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHPrime.lean#L151) `deuring_heilbronn_prime_sum` 给 (6)。[`exists_power_sum_lower_bound`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/ExistsPowerSumLowerBound.lean#L9) `exists_power_sum_lower_bound` 给 (8)，[`ub_terms`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/UbTerms.lean#L84) `ub_terms` 与 [`core2`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/NormUSum.lean#L20) `core2` 比较上下界。[正系数和第 151 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTDHPrime.lean) · [下界第 9 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/ExistsPowerSumLowerBound.lean) · [上界第 84 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/UbTerms.lean) · [比较第 20 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/NormUSum.lean)

本篇按源码对读。在给定例外零点的前提下推出排斥，证明的定量输入逐项列在正文。其中 Turán 幂和和 [`exists_power_sum_lower_bound`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/ExistsPowerSumLowerBound.lean#L9) 的筛项下界已在 Lean 4.33.1 中重放。完整的排斥定理及其传递公理为源码对读。
