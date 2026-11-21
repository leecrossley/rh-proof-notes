# 怎样用有限差分控制 $L$ 函数的增长

目标是在 $\Re s\ge-7/4$ 内控制 $L(s,\chi)$ 和去极点后的 $(s-1)\zeta(s)$。这一范围正好覆盖[局部零点计数](%E5%9C%86%E7%9B%98%E9%87%8C%E7%9A%84%E9%9B%B6%E7%82%B9%E6%80%8E%E6%A0%B7%E6%8E%A7%E5%88%B6%E5%AF%B9%E6%95%B0%E5%AF%BC%E6%95%B0.md)所需的圆盘。两份 Lean 证明都把级数换成收敛更快的余项，再用恒等定理延拓。

## 一、非主特征的级数可以分部求和三次

**命题（[`norm_LFunction_le_poly_left`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SummableNinePowMulInvSqSucc.lean#L269)）。** 存在绝对常数 $C>0$，使任意正整数 $q$、模 $q$ 非主狄利克雷特征 $\chi$ 及复数 $s$ 满足 $\Re s\ge-7/4$ 时，有

$$
|L(s,\chi)|\le Cq^4(|s|+2)^4 .
\tag{1}
$$

**分部求和的一步。** 设 $(a_n)_{n\ge0}$ 是周期 $q$ 的复序列，一整周期的和为零，且 $|a_n|\le M$。令 $T(n)=\sum_{j=0}^{n-1}a_j$，则 $T(n)$ 也有周期 $q$，且 $|T(n)|\le qM$。记 $\mu=q^{-1}\sum_{n=0}^{q-1} T(n+1)$，以及 $b_n=T(n+1)-\mu$。于是 $b_n$ 仍以 $q$ 为周期、周期和仍为零，且

$$
|\mu|\le qM,\qquad |b_n|\le2qM .
\tag{2}
$$

若 $\sum_{n\ge0}|u_n|<\infty$，将 $a_n=T(n+1)-T(n)$ 代入，有限求和后令截断点趋于无穷。边界项趋于零，因为 $T$ 有界且 $u_n\to0$。再用 $\sum(u_n-u_{n+1})=u_0$，得到

$$
\sum_{n\ge0}a_n u_n
=\sum_{n\ge0}T(n+1)(u_n-u_{n+1})
=\mu u_0+\sum_{n\ge0}b_n(u_n-u_{n+1}).
\tag{3}
$$

减去平均值 $\mu$ 的目的，是让新系数列仍可重复使用同一个分部求和步骤。

**有限差分的估计。** 对 $x>0$ 写 $\Delta^0_s(x)=x^{-s}$，$\Delta_s^{k+1}(x)=\Delta_s^k(x)-\Delta_s^k(x+1)$。对任意 $k\ge1$，反复用 $u(x)-u(x+1)=-\int_0^1u'(x+t)\,dt$，得到

$$
\Delta_s^k(x)=s(s+1)\cdots(s+k-1)\int_{[0,1]^k}
(x+t_1+\cdots+t_k)^{-s-k}\,dt_1\cdots dt_k .
$$

因此在 $\Re s+k\ge0$ 时，

$$
|\Delta_s^k(x)|\le (|s|+k)^k\,x^{-\Re s-k}.
\tag{4}
$$

也可以直接对 $x$ 求导并归纳得到这条界，这是 Lean 的路线。对固定 $k,x$，$\Delta_s^k(x)$ 作为 $s$ 的函数是全纯的，因为它就是有限个正实数的 $-s$ 次幂的线性组合。

**实际延拓。** 非主特征的周期和为零，证明见[尾项估计](M%C3%B6bius%E6%88%AA%E6%96%AD%E6%80%8E%E6%A0%B7%E6%A3%80%E6%B5%8B%E9%9D%A0%E8%BF%91%E4%B8%80%E7%9A%84%E9%9B%B6%E7%82%B9.md)第三节。在 $\Re s>1$ 中以 $a_n=\chi(n+1)$ 和 $u_n=\Delta_s^0(n+1)$ 开始，将 (3) 连续应用三次。每一次用的新 $u_n$ 是前一次的差分序列，由 (4) 在该半平面绝对可和。得到

$$
L(s,\chi)=
\mu_1\Delta_s^0(1)+\mu_2\Delta_s^1(1)+\mu_3\Delta_s^2(1)
+\sum_{n\ge0} b_n\Delta_s^3(n+1),
\tag{5}
$$

其中三次依次取 $M=1,2q,4q^2$，所以
$|\mu_1|\le q,\ |\mu_2|\le2q^2,\ |\mu_3|\le4q^3,\ |b_n|\le8q^3$。

在 $\Re s\ge-15/8$ 时，$\Re s+3\ge9/8$。因此只要再限制 $|s|\le A$，(4) 就给出统一比较 $|b_n\Delta_s^3(n+1)|\le8q^3(A+3)^3(n+1)^{-9/8}$。故 (5) 右侧在 $\Re s>-15/8$ 局部一致收敛、全纯，与 $L$ 的解析延拓在绝对收敛区一致。由恒等定理，(5) 在这个更大的半平面都成立。

最后在 $\Re s\ge-7/4$ 使用 (5)。令 $Z=\sum_{n\ge1}n^{-9/8}<\infty$。有 $|\Delta_s^0(1)|=1,\ |\Delta_s^1(1)|=|1-2^{-s}|\le5,\ |\Delta_s^2(1)|\le(|s|+2)^2$。余项至多为 $8q^3(|s|+3)^3 Z$。用 $q\ge1,\ |s|+3\le2(|s|+2)$ 合并，可取 $C=15+64Z$。这与源码的常数形式一致。

## 二、去极点的 ζ 用相邻差分作抵消

**命题（[`norm_sub_one_mul_riemannZeta_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/NormSubOneMulRiemannZetaLe.lean#L188)）。** 存在绝对常数 $C'>0$，对所有 $\Re s\ge-7/4$ 且 $s\ne1$，

$$
|(s-1)\zeta(s)|\le C'(|s|+2)^5.
\tag{6}
$$

**构造差分。** 令 $w=1-s$，对 $x\ge1$ 设

$$
T(x,s)=x^w-\frac{w}{2}x^{w-1}+\frac{w(w-1)}{12}x^{w-2},
\quad
E(x,s)=T(x+1,s)-T(x,s)-w x^{w-1}.
\tag{7}
$$

$T$ 的后二项补偿了 $x^w$ 的有限差分与导数之间的偏差。为了看出余项降到了哪个次数，固定 $x,s$，记 $u(t)=(x+t)^w$，并取

$$
\begin{aligned}
B_1(t)&=t-\tfrac12,\\
B_2(t)&=(t^2-t+1/6)/2,\\
B_3(t)&=(t^3-\tfrac32 t^2+\tfrac12t)/6.
\end{aligned}
$$

有 $B_1'=1,\ B_2'=B_1,\ B_3'=B_2$。对 $G(t)=u(t)-B_1(t)u'(t)+B_2(t)u''(t)-B_3(t)u'''(t)$ 求导，各低阶项依次抵消，剩下 $G'(t)=-B_3(t)u^{(4)}(t)$。又 $B_3(0)=B_3(1)=0$，$B_2(0)=B_2(1)=1/12$，故 $G(1)=T(x+1,s)$，$G(0)=T(x,s)+w x^{w-1}$。因此

$$
E(x,s)=G(1)-G(0)
=-\int_0^1 B_3(t)w(w-1)(w-2)(w-3)(x+t)^{w-4}\,dt .
\tag{8}
$$

在 $0\le t\le1$ 时，$|B_3(t)|\le1$。还因 $w=1-s$，有 $|w|,|w-1|,|w-2|,|w-3|\le|s|+2$。若 $\Re s\ge-15/8$，则 $\Re(w-4)=-3-\Re s\le-9/8$。故

$$
|E(x,s)|\le(|s|+2)^4 x^{-9/8}.
\tag{9}
$$

**应用望远镜求和。** 当 $\Re s>1$ 时，$T(N+1,s)\to0$。将 (7) 在 $x=1,\ldots,N$ 求和，有

$$
\sum_{n=1}^N E(n,s)= T(N+1,s)-T(1,s)+(s-1)\sum_{n=1}^N n^{-s}.
$$

令 $N\to\infty$，得到 $(s-1)\zeta(s)=T(1,s)+\sum_{n\ge1}E(n,s)$。每个 $E(n,\cdot)$ 全纯，(9) 保证级数在 $\Re s>-15/8$ 局部一致收敛，所以用恒等定理将等式延拓到该半平面，并且当 $s=1$ 时这个右侧正好取值 $1$。最后 $|T(1,s)|\le1+(|s|+2)/2+(|s|+2)^2/12$，级数模至多 $(|s|+2)^4 Z$。合并可取 $C'=3+Z$，给出 (6)。

## 源码对照

- (3) 是 `abel_step`，三次所得 (5) 在 `abel_three` 和 `LFunction_eq`。差分是 `diffPow`，(4) 对应 `norm_diffPow_le`，最终是 [`norm_LFunction_le_poly_left`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SummableNinePowMulInvSqSucc.lean#L269)。[第 37、83、158、205、269 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SummableNinePowMulInvSqSucc.lean#L37)
- (7) 对应 `emT` 和 `emE`，余项界是 `norm_emE_le`。在绝对收敛区的望远镜式与延拓由 `eq_of_one_lt`、`eq_of_lt` 给出，最后得到 [`norm_sub_one_mul_riemannZeta_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/NormSubOneMulRiemannZetaLe.lean#L188)。[第 7、21、136、168、188 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/NormSubOneMulRiemannZetaLe.lean#L7)
- 两条上界与 $\Re s=2$ 的圆心下界配合，使圆盘定理右侧只依赖模数、高度的对数。[圆盘译稿](%E5%9C%86%E7%9B%98%E9%87%8C%E7%9A%84%E9%9B%B6%E7%82%B9%E6%80%8E%E6%A0%B7%E6%8E%A7%E5%88%B6%E5%AF%B9%E6%95%B0%E5%AF%BC%E6%95%B0.md)
