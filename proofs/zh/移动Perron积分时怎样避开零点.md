# 移动Perron积分时怎样避开零点

**命题。** 存在绝对常数 $C>0$，使对每个正整数 $q$、模 $q$ 的本原狄利克雷特征 $\chi$ 和实数 $2\le T\le u$，可以选取 $T'\in[T,T+1]$，满足下式。记 $c=1+1/\log u$、$m_\chi(\rho)=\operatorname{ord}_{\rho}L(s,\chi)$，并令
$Z(Y)=\{\rho:\ L(\rho,\chi)=0,\ 0<\Re\rho<1,\ |\Im\rho|<Y\}$。则

$$
\left|
 \frac1{2\pi}\int_{-T'}^{T'}
 -\frac{L'}{L}(c+it,\chi)\frac{u^{c+it}}{c+it}\,dt
 -\mathbf1_{q=1}u
 +\sum_{\rho\in Z(T')}m_\chi(\rho)\frac{u^\rho}{\rho}
 \right|
 \le
 C\left(\frac{u\log^2(quT)}{T}+\log(qu)+
            \sum_{\rho\in Z(1)}\frac{m_\chi(\rho)}{|\rho|}\right).
 \tag{1}
$$

左端积分沿复平面右侧竖线。证明将它移到 $\Re s=-1/2$。穿过的各个零点以留数形式给出显式公式，横边和左边竖线成为误差。

## 一、在两条横边同时避开邻近零点

沿用[条带里的对数导数公式](%E5%9C%86%E7%9B%98%E9%87%8C%E7%9A%84%E9%9B%B6%E7%82%B9%E6%80%8E%E6%A0%B7%E6%8E%A7%E5%88%B6%E5%AF%B9%E6%95%B0%E5%AF%BC%E6%95%B0.md)。设 $v\in\mathbb R$，以 $2+iv$ 为中心、半径 $7/2$ 的圆盘内零点总重数 $\ll\log(q(|v|+2))$。对 $-1\le\Re s\le2,\ \Im s=v$，若 $s$ 非零点且 $s\ne1$，扣去这些零点的分式，对数导数余项也有此上界。$q=1$ 时有额外的极点修正 $1/(s-1)$。在 $|v|\ge2$ 时其模至多 $1/2$。

对于 $t\in[T,T+1]$，若一个 $\Re w\in[-1,1)$ 的零点在以 $2+it$ 为中心的这个圆盘里，那么它也在以 $2+iT$ 或 $2+i(T+1)$ 为中心的圆盘里。若 $\Im w$ 在 $[T,T+1]$ 外，选离 $\Im w$ 较近的端点，这不会增加距离。若 $\Im w$ 在区间内，用更近的端点，虚部差最多 $1/2$，而实部差最多 $3$，故距离最多 $\sqrt{9+1/4}<7/2$。对 $-t$ 同样可用 $-T,-T-1$。

把前两个端点圆盘中零点的虚部，以及后两个圆盘中零点虚部的相反数，合成有限集合 $F\subset\mathbb R$。其大小 $J\ll\log(qT)$，因为每个零点至少一重。设 $d=1/(2(J+1))$。从 $[T,T+1]$ 中删去每个 $y\in F$ 周围半径 $d$ 的开区间，总删去长度至多 $2dJ<1$。选剩下的一个 $T'$。对任意 $-1/2\le\Re s\le2,\ \Im s=\pm T'$，其局部零点 $w$ 满足 $|s-w|\ge d$。确实，$\Re w\ge-1$ 时由所选高度排除，$\Re w<-1$ 时实部差已大于 $1/2$。由 $d>0$ 也知横边这一段没有零点。把总重数和每项的倒数界代回局部公式，得

$$
|L'/L(s,\chi)|\ll\log^2(qT).
 \tag{2}
$$

在 $2\le\Re s\le3$ 可直接用 $\sum_{n\ge1}\Lambda(n)n^{-2}<\infty$ 界对数导数。无零点性来自 Euler 乘积。因此 (2) 和无零点性覆盖整条所需横边。

## 二、左竖线和原点附近的对数导数

本原特征的函数方程给出非正实部的零点性质。若 $\Re w\le0$，则 $L(w,\chi)$ 的零点只可能是非正整数，且为简单零点。理由是完成函数在 $w$ 的值等于一个非零常数乘反射点 $1-w$ 的完成函数值，反射点实部至少 $1$，那里 $L$ 函数非零且 Gamma 因子有限非零。左边 $L$ 的零点只可来自 Gamma 倒数的简单零点。具体地，$\chi(-1)=(-1)^a$ 时 Gamma 因子含 $\Gamma((w+a)/2)$，其倒数在 $(w+a)/2=0,-1,\ldots$ 处有单零点。$q=1,w=0$ 是完成函数有极点的特殊点，直接用 $\zeta(0)=-1/2$。这些断言的 Lean 证明也用 Gamma 的递推式推出倒数在负偶数处的导数非零。

因此左边 $\Re s=-1/2$ 每点都离任何 $L$ 零点至少 $1/2$。若零点在右半平面，实部差至少 $1/2$，其余零点由整数位置得出同样的界。局部公式给

$$
|L'/L(-1/2+it,\chi)|\ll\log(q(|t|+2)).
 \tag{3}
$$

如果 $\chi$ 是本原主特征，则 $q=1$，且应加回 ζ 的极点修正，其模至多 $2/3$，已吸收到 (3)。

在 $s=0$ 附近，写 $m=\operatorname{ord}_{0}L(s,\chi)\in\{0,1\}$。由局部因式分解，

$$
L'/L(s,\chi)=m/s+h(s),
$$

其中 $h$ 在 $0$ 全纯。为估计 $h(0)$，令 $s=x>0$ 沿实轴趋于零，在同一个以 $2$ 为中心的圆盘公式中扣掉 $m/s$。剩余零点分式趋于 $m_\chi(w)/(-w)$，因为列表有限且 $w\ne0$。所以 $|h(0)|$ 至多 $O(\log(2q))$ 加这些倒数模的和。非正实部时 $w\ne0$ 是非零整数，故 $|w|\ge1$。正实部而 $|\Im w|\ge1$ 时也一样。这两部分用圆盘总重数 $\ll\log(2q)$ 控制。其余零点 $w\in Z(1)$。ζ 的极点项在 $0$ 有界，亦可吸收。因此

$$
|h(0)|\ll\log(2q)+\sum_{\rho\in Z(1)}m_\chi(\rho)/|\rho|.
 \tag{4}
$$

## 三、逐个计算矩形中的留数

令 $G(s)=-\frac{L'}{L}(s,\chi)\frac{u^s}{s}$。取矩形 $-1/2\le\Re s\le c,\ |\Im s|\le T'$。由 (2)–(3) 和右边的 Euler 乘积，边界没有零点或极点。内部的非平凡零点恰是 $Z(T')$，因 $L$ 在 $\Re s\ge1$ 无零点，且 $-1/2<\Re s\le0$ 的唯一可能零点为 $0$。因子分解给每个 $\rho\in Z(T')$ 处留数 $-m_\chi(\rho)u^\rho/\rho$。当 $q=1$，在 $1$ 处由 ζ 的简单极点得 $-L'/L(s)=1/(s-1)+O(1)$，故留数为 $u$。当 $q>1$，本原 $\chi$ 非主， $1$ 处正则。

在 $0$ 处展开 $u^s=1+s\log u+O(s^2)$，由 $L'/L=m/s+h(s)$ 得

$$
G(s)=-m/s^2-(m\log u+h(0))/s+O(1).
$$

因此原点的留数模至多 $\log u+|h(0)|$，由 (4) 控制。

现在用逆时针矩形留数公式。右竖边向上，除以 $2\pi i$ 后正是 (1) 的积分。其他三边均可用绝对值估计。横边长度 $c+1/2\le3$，$|s|\ge T,\ |u^s|\le u^c=eu$。由 (2)，两边一共 $\ll (u/T)\log^2(quT)$。左边则由 (3) 得到

$$
\ll \frac1{\sqrt u}\log(q(T'+2))
       \int_{-T'}^{T'}\frac{dt}{\sqrt{1/4+t^2}}
 \ll \frac1{\sqrt u}\log(q(T'+2))\log(2T'+1).
$$

积分可将 $|t|\le1$ 与 $|t|>1$ 分开，分别用 $2$ 与 $1/|t|$。因 $T'\le T+1$ 且 $u/T\ge1$，左边也 $\ll (u/T)\log^2(quT)$。将原点留数和三条边的界合并，得到 (1)。

## Lean 对照

- 好高度的选择和局部对数导数组合在 `GlobalTheory.GoodHeight.exists_far`、`local_formula`、`exists_height`。本原特征在 $\Re s\le0$ 的零点和重数是 `GlobalTheory.LFunction_zero_of_re_nonpos`。[好高度第 8、93、150 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsBoundRight.lean) · [非正实部零点源码](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/CompletedLFunctionNeZeroOfReNonpos.lean)
- (4) 是 `GlobalTheory.LAtZero.logDeriv_LFunction_near_zero`。`GlobalTheory.ExplicitRect.residue_identity` 是第三节的矩形等式。[原点第 104 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LogDerivLFunctionNearZero.lean) · [留数第 189 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/AnalyticAtDslope.lean)
- (1) 是 `GlobalTheory.PerronShift.perron_shift`，左竖线的两级估计见同文件第 47、143 行。此稿为源码对读，使用的宽条带公式已有局部核验。[主证明第 227 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/PerronIntegralShiftPrimitiveLFunction.lean) · [转发第 6 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/PerronIntegralShiftPrimitiveLFunctionStatement.lean)
