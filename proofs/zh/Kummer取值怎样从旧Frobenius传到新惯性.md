# Kummer 取值怎样从旧 Frobenius 传到新惯性

长度估计逐个加入辅助素数 $q$。加入前用 Frobenius $\Phi_q$ 检测旧的特征 $\nu_L$，加入后要在同一个素处的惯性群中找到元素 $t_q$ 继续迭代。本篇证明这两个取值相差一个单位，并计算从空列表开始时的取值。

## 命题与记号

记 $\Omega=\overline{\mathbb Q}$、$G=\operatorname{Gal}(\Omega/\mathbb Q)$、$K_N=\mathbb Q(\mu_N)$。给定正整数 $M\mid F$、$M$ 次本原单位根 $\zeta$ 和 $\delta\in G$，设 $\delta$ 在 $\mu_M$ 上作用为 $x\mapsto x^a$，其中 $a$ 是非负整数。写 $P(x)=\delta(x)/x^a$（$x\ne0$），$U=\operatorname{Gal}(\Omega/K_F)$。所有 Frobenius 均取算术 Frobenius，即在剩余域中作用为 $x\mapsto x^q$。

给定素数 $r$ 和整数 $\ell$。一个辅助素数 $p$ 必须满足

$$
p\equiv1\pmod F,\qquad p\ne r,\qquad
\ell\nmid\operatorname{ord}_{(\mathbb Z/p\mathbb Z)^\times}(r).
$$

称正平方自由整数 $d$ 可用，若它的每个素因子都满足这些条件。对每个可用的 $d$，给定 $x_d\in K_{Fd}^\times$，且它在 $r$ 以外的所有素处均为单位。对每个素数 $q$ 和可用的 $qd$，还给定 $s=s(d,q)\ge0$ 且 $\ell\nmid s$。让 $\tau_p\in G$ 在所有阶与 $p$ 互素的单位根上作用平凡，并在 $\mu_p$ 上生成 $\operatorname{Gal}(K_p/\mathbb Q)$。

以下是项目的范数与同余条件（$\texttt{Sys}$）。对每个上述 $d,q$、每个固定 $K_{Fd}$ 并在 $\mu_q$ 上给出生成元的 $\tau$，以及每个在 $\mu_{Fd}$ 上作用为 $q$ 次幂的 $\Phi$，有

$$
\prod_{i=0}^{q-2}\tau^i(x_{qd})
=\left(\frac{x_d}{\Phi^{-1}(x_d)}\right)^s,\qquad
x_{qd}\equiv\bigl(\Phi^{-1}(x_d)\bigr)^s
\quad\text{在每个 }q\text{ 上方的素处}.
\tag{1}
$$

定义 $D_p(v)=\prod_{i=0}^{p-2}\tau_p^i(v)^i$，令 $D_L$ 为列表 $L$ 中这些算子的复合，空列表时为恒等算子。取互异辅助素数的列表 $q::L$，其中 $q$ 是新加入的一项，$d=\prod_{p\in L}p$。设

$$
y=D_L(x_d),\qquad w=D_L(x_{qd}),\qquad v=D_q(w).
$$

对 $y$ 和 $v$ 都假设满足根条件：对每个 $g\in U$，$g(y)/y$ 在 $K_{Fd}$ 内有 $M$ 次根，$g(v)/v$ 在 $K_{Fqd}$ 内有 $M$ 次根。相应的 Kummer 特征记为 $\kappa_L,\kappa_{q::L}$。它们由下式唯一确定，式中 $Y_y^M=y,\ z_g^M=g(y)/y$，在 $v$ 上使用同一公式。[根公式与连续加法性](%E6%80%8E%E6%A0%B7%E4%BB%8EKummer%E6%A0%B9%E7%9A%84%E6%AF%94%E5%80%BC%E6%9E%84%E9%80%A0%E5%8F%AF%E7%94%A8%E7%9A%84%E5%8A%A0%E6%B3%95%E7%89%B9%E5%BE%81.md)

$$
\zeta^{\kappa_L(g)}
=\frac{g(P(Y_y))}{P(Y_y)P(z_g)}.
\tag{2}
$$

任取 $q$ 上方的绝对素处、该处的算术 Frobenius 提升 $\Phi$ 和一个在 $\mu_q$ 上与 $\tau_q$ 作用相同的惯性元素 $t_q$。后者存在，因为 $\mathbb Q_q(\mu_q)/\mathbb Q_q$ 完全分歧，惯性群在其 Galois 群上满射。则在 $\mathbb Z/M\mathbb Z$ 中有

$$
\kappa_{q::L}(t_q)=-s(d,q)\,\kappa_L(\Phi).
\tag{3}
$$

## 由范数关系求一个确切的根

因为 $q\nmid Fd$，$\Phi$ 在 $\mu_{Fd}$ 上取 $q$ 次幂。又因 $q\equiv1\bmod F$，有 $\Phi\in U$。惯性元素 $t_q$ 固定 $K_{Fd}$，在 $K_{Fqd}$ 上和 $\tau_q$ 作用相同。

在分圆域上各个 Galois 元素交换。把 $D_L$ 作用在 (1) 上，得到

$$
\prod_{i=0}^{q-2}\tau_q^i(w)
=\left(\frac{y}{\Phi^{-1}y}\right)^s,\qquad
w/(\Phi^{-1}y)^s\equiv1
\quad\text{在所有 }q\text{ 上方的素处}.
\tag{4}
$$

第二个式子在应用 $D_L$ 后仍成立，因为每一步的 $\tau_p$ 只会置换 $q$ 上方的素处。各元素在这些处均为单位，这允许取商和乘方。

把 $\tau_q$ 作用在 $D_q(w)$ 上，再与 $D_q(w)$ 相除。对于 $\tau_q^i(w)$，当 $1\le i\le q-2$ 时指数差为 $-1$，而首尾项利用 $\tau_q^{q-1}(w)=w$ 合并。由此得到

$$
\frac{t_q(v)}{v}=\frac{w^{q-1}}{\prod_{i=0}^{q-2}\tau_q^i(w)}
=w^{q-1}\left(\frac{\Phi^{-1}y}{y}\right)^s.
$$

设 $k=(q-1)/M$，并从 $y$ 的根条件取 $Z^M=\Phi^{-1}y/y$ 且 $Z\in K_{Fd}$。于是可以在 $v$ 对应的式 (2) 中直接取 $z_{t_q}=w^k Z^s$。

## 约化到剩余域并取得符号

设 $Y_v^M=v$。对 $t_q$ 和 $\Phi^{-1}$ 分别应用式 (2)，把第一个结果除以第二个结果的 $s$ 次幂，得到下式。用到的代数关系是 $P$ 保持乘积，以及

$$
\bigl(\Phi^{-1}P(Y_y)\bigr)^M=P(\Phi^{-1}y),
$$

其中后一等式用 $\delta,\Phi$ 在 $K_{Fd}$ 上交换。因为 $q=1+Mk$，整理后

$$
\frac{\zeta^{\kappa_{q::L}(t_q)}}{\zeta^{s\kappa_L(\Phi^{-1})}}
= \frac{t_q(P(Y_v))}{P(Y_v)}
   \left(\frac{P(Y_y)}{\bigl(\Phi^{-1}P(Y_y)\bigr)^q}\right)^s
   \frac{1}{P\bigl(w/(\Phi^{-1}y)^s\bigr)^k}.
\tag{5}
$$

右端每个因子在所取素处都约化为 $1$。第一个因 $t_q$ 属于惯性群，而 $P(Y_v)$ 是单位。第二个由算术 Frobenius 的定义，取该处的局部单位 $B=\Phi^{-1}P(Y_y)$，便有 $\Phi(B)\equiv B^q$。第三个由 (4)，其同余对所有 $q$ 上方的素处成立，施加 $\delta$ 后仍成立。根 $Y_y,Y_v$ 局部为单位，用的是它们的 $M$ 次幂在所有这些素处为单位。

等式左端是一个 $M$ 次单位根。因 $q\nmid M$，约化在 $\mu_M$ 上单射。于是左端为 $1$。由 $\zeta$ 本原，$\kappa_{q::L}(t_q)=s\kappa_L(\Phi^{-1})$。式 (2) 所定义的特征在 $U$ 上为加法，给出 $\kappa_L(\Phi^{-1})=-\kappa_L(\Phi)$。这证明 (3)。

## 初始素数的取值

设 $r\nmid F$、$y\in K_F^\times$ 满足 (2) 的根条件，固定 $r$ 上方的绝对素处，记其加法赋值为 $v_r$ 并归一化成 $v_r(r)=1$。给定整数值函数 $h(t)$（$t\in(\mathbb Z/F\mathbb Z)^\times$），假设每个在 $\mu_F$ 上指数为 $t$ 的提升 $\sigma_t$ 都满足

$$
v_r(\sigma_t P(y))=h(t).
$$

选 $\rho^M=r$ 及该处的惯性元素 $t_r$ 使 $t_r(\rho)=\zeta\rho$。这样的元素存在：$X^M-r$ 在 $\mathbb Q_r(\mu_M)$ 上为 Eisenstein 多项式，因为 $r\nmid M$ 且添入 $\mu_M$ 时不分歧。添入 $\rho$ 随后给出完全分歧的 Galois 扩张，$\rho\mapsto\zeta\rho$ 来自惯性。

取 $Y^M=y$ 并写 $A=\sigma_tP(Y)$。有 $A^M=\sigma_tP(y)$ 且 $v_r(A)=h(t)/M$。所以 $B=A/\rho^{h(t)}$ 为单位，并且 $B^M\in K_F$。惯性元素 $t_r$ 固定 $K_F$，故 $t_r(B)/B$ 是 $M$ 次单位根。它约化为 $1$，由 $r\nmid M$ 得 $t_r(B)=B$。因此 $t_r(A)/A=\zeta^{h(t)}$。又因为 $\sigma_t^{-1}t_r\sigma_t\in U$ 固定 $y$，式 (2) 可取 $z_g=1$。对该式施加 $\sigma_t$，用 $\sigma_t(\zeta)=\zeta^{[t]}$（$[t]$ 是任一整数代表）得

$$
[t]\,\kappa_{\varnothing}(\sigma_t^{-1}t_r\sigma_t)=h(t)\pmod M.
\tag{6}
$$

## 项目怎样同时得到一套 $\nu_L$

项目使用的参数还满足 $\ell$ 是奇素数，$m\ge1$，$M=\ell^m$，$F=N_0M$ 且 $(N_0,\ell)=1$，$r\equiv1\bmod F$ 为素数，$0\le b<F$。取 $O$ 为有限扩张的 $\ell$ 进整数环，$W=\operatorname{Frac}(O)/O$，$w_0\in W[M]$。特征 $\alpha:G\to O^\times$ 满足 $\alpha|_U\equiv1\bmod MO$，在复共轭上取 $-1$，并且对某个 $\delta$ 有 $\alpha(\delta)-\varepsilon_\ell(\delta)\in O^\times$。这里 $\varepsilon_\ell$ 是 $\ell$ 进分圆特征。沿用前面的 $P$，取 $a$ 为 $\varepsilon_\ell(\delta)\bmod M$ 的最小非负代表，设 $\beta=\varepsilon_\ell\alpha^{-1}$，记 $d_0$ 为 $\delta$ 在 $\mu_F$ 上的指数。把 $\theta_b(t)$ 定义为

$$
\theta_b(t)=\left\lfloor\frac{b[t]}{F}\right\rfloor-
\left\lfloor\frac{b[-t]}{F}\right\rfloor
\quad (0\le[t],[-t]<F),\qquad
z=\sum_{t\in(\mathbb Z/F\mathbb Z)^\times}\theta_b(t)\alpha(\sigma_t)^{-1}.
$$

存在性论证先用 $\texttt{laxEx}$ 给出 $X_d\in K_{Fd}^\times$ 及整数指数 $s_0(d,q)\ge0$。其陈述同 (1) 及前面的单位条件，且 $\ell\nmid s_0(d,q)$，但范数等式及同余右端各可乘一个阶整除 $2Fqd$ 的单位根。同余中的根对所有 $q$ 上方的素处一致。它还给出 $v_r(\sigma_tX_1)=\theta_b(t)$ 对所有提升成立。范数和同余的单位根由 $P$ 及幂次消去：取

$$
x_d=P(X_d)^{2N_0d}.
$$

因为 $P$ 在所有这些分圆域上和 Galois 作用交换，范数等式可直接施加 $P$ 再取 $2N_0qd$ 次幂。在同余中也可以逐素处做相同操作，因为同余在所有 $q$ 上方的处成立。每个额外单位根的 $2N_0qd$ 次幂属于 $\mu_M$，而 $P|_{\mu_M}=1$。比较 $x_d$ 与 $x_{qd}$ 的指数，得到 (1) 中的 $s(d,q)=q s_0(d,q)$，仍与 $\ell$ 互素。所用的另一个项目输入 $\texttt{derInv}$ 断言：对每个互异辅助素数列表 $L$，令 $d=\prod_{p\in L}p$ 及 $y_L=D_L(x_d)$，则每个 $g\in U$ 都满足 $g(y_L)/y_L\in(K_{Fd}^\times)^M$。这恰好给出 (2) 所需的根。

形成 Kummer 特征后，定义

$$
\nu_L(g)=\sum_{t\in(\mathbb Z/F\mathbb Z)^\times}
\kappa_L(\sigma_t^{-1}g\sigma_t)\,\beta(\sigma_t)w_0.
$$

该式在 $U$ 上是连续加法映射，按 $\beta$ 共轭等变，被 $M$ 消去，并在 $Frd$ 以外的惯性群上为零。这里使用了 $\beta|_U\equiv1\bmod MO$ 和 $Mw_0=0$。把 (3) 应用于共轭的素处、$\sigma_t^{-1}\Phi\sigma_t$ 与 $\sigma_t^{-1}t_q\sigma_t$。后者在 $\mu_q$ 上与 $t_q$ 作用相同，因为 $K_q/\mathbb Q$ 是阿贝尔扩张。故每个和项都乘同一个 $-q s_0(d,q)$，即

$$
\nu_{q::L}(t_q)=-q s_0(d,q)\nu_L(\Phi),\qquad -q s_0(d,q)\in O^\times.
\tag{7}
$$

最后，空列表用 $y=x_1=P(X_1)^{2N_0}$。按 $v_r(\sigma_tX_1)=\theta_b(t)$ 计算 $v_r(\sigma_tP(y))$，给出

$$
h(t)=2N_0\bigl(\theta_b(td_0^2)-2a\theta_b(td_0)+a^2\theta_b(t)\bigr).
$$

式 (6) 中的 $[t]$ 也正是 $\varepsilon_\ell(\sigma_t)\bmod M$。因 $Mw_0=0$，在 $\nu_{\varnothing}(t_r)$ 的和式中可将 $\kappa_{\varnothing}(\sigma_t^{-1}t_r\sigma_t)\beta(\sigma_t)w_0$ 改写成 $h(t)\alpha(\sigma_t)^{-1}w_0$。对每个 $j=0,1,2$，把 $\theta_b(td_0^j)$ 的求和指标换为 $td_0^j$。两种提升 $\sigma_{td_0^j}$ 和 $\sigma_t\delta^j$ 在 $\mu_F$ 上一致，$\alpha$ 的取值模 $MO$ 相等。该项的和因而为 $\alpha(\delta)^j z\bmod MO$。合并得

$$
\nu_{\varnothing}(t_r)=2N_0(\alpha(\delta)-a)^2\,z\,w_0.
\tag{8}
$$

因 $m\ge1$，$\alpha(\delta)-a$ 与单位 $\alpha(\delta)-\varepsilon_\ell(\delta)$ 模极大理想相等，加上 $\ell\nmid2N_0$，故 (8) 的系数 $2N_0(\alpha(\delta)-a)^2$ 是单位。(7) 和 (8) 正是长度迭代中需要的两条取值条件。选 $w_0$ 的消去理想后，(8) 让 $z$ 的赋值进入起始长度，(7) 让每轮的 Frobenius 取值成为下一轮的惯性取值。[长度迭代](%E9%80%90%E4%B8%AA%E5%8A%A0%E5%85%A5%E8%BE%85%E5%8A%A9%E7%B4%A0%E6%95%B0%E6%80%8E%E6%A0%B7%E6%8A%8A%E5%90%8C%E8%B0%83%E9%95%BF%E5%BA%A6%E5%8E%8B%E5%88%B0%E4%B8%80%E4%B8%AA%E8%B5%8B%E5%80%BC.md)

## Lean 对照与核验状态

- $\texttt{Sys}$ 的全部条件见源码第 63 行，[`kolStep`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/KolStep.lean#L135) $\texttt{kolStep}$ 第 135 行给出 (3)，其中 $\texttt{hstep}$ 是 $D_q$ 的首尾相消，$\texttt{key}$ 是 (5)。[定义](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/IsAdmissiblePrimeListNil.lean) · [新惯性取值](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/KolStep.lean)
- [`kolInit`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/KolInit.lean#L7) $\texttt{kolInit}$ 第 7 行为 (6)，[`nuSysEx`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/NuSysEx.lean#L79) $\texttt{nuSysEx}$ 第 79 行给出 (7)、(8) 及每个 $\nu_L$ 的性质。[初值](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/KolInit.lean) · [组装](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/NuSysEx.lean)
- 数域元素的存在性见 [`laxEx`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/PlaceEmb.lean#L189) $\texttt{laxEx}$ 第 189 行，去单位根见 [`sysOfLax`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/SysOfLax.lean#L88) $\texttt{sysOfLax}$ 第 88 行，所需的根条件见 [`derInv`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/DerInv.lean#L212) $\texttt{derInv}$ 第 212 行。[元素与范数输入](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/PlaceEmb.lean) · [去单位根](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/SysOfLax.lean) · [根条件](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/DerInv.lean)

以上项目声明为源码对读。$\texttt{laxEx}$ 和 $\texttt{derInv}$ 的证明见相邻译稿。该分支没有单项内核重放或传递公理检查记录。[范数与同余](%E8%BE%85%E5%8A%A9%E5%88%86%E5%9C%86%E5%85%83%E7%B4%A0%E7%9A%84%E8%8C%83%E6%95%B0%E4%B8%8E%E5%90%8C%E4%BD%99%E6%80%8E%E6%A0%B7%E7%9B%B8%E5%AE%B9.md) · [在分圆域内开根](%E4%B8%BA%E4%BB%80%E4%B9%88%E8%BE%85%E5%8A%A9%E6%AF%94%E5%80%BC%E7%9A%84%E6%A0%B9%E5%B7%B2%E7%BB%8F%E5%9C%A8%E5%88%86%E5%9C%86%E5%9F%9F%E9%87%8C.md)
