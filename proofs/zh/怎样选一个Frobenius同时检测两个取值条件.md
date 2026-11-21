# 怎样选一个Frobenius同时检测两个取值条件

**命题（[`pick`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/AddPowNsmul.lean#L175)，`UpperTheory.V.ML.pick`）。** 令 $\ell$ 为奇素数，$O$ 为有限于 $\mathbb Z_\ell$ 的离散赋值整环，$\pi$ 为一致化元，$W=\operatorname{Frac}(O)/O$，$G=G_{\mathbb Q}$。给定整数 $m\ge1$、与 $\ell$ 互素的正整数 $N_0$，令 $F=N_0\ell^m,\ U=G_{\mathbb Q(\mu_F)}$。令 $\varepsilon_\ell:G\to O^\times$ 为分圆特征。取群同态 $\alpha:G\to O^\times$，要求它在 $U$ 上同余于 $1\bmod\ell^m O$，在所有对 $\mu_F$ 取逆的元素上同余于 $-1\bmod\ell^m O$，且对某个 $g$ 有 $\alpha(g)-\varepsilon_\ell(g)$ 为单位。令 $\beta=\varepsilon_\ell\alpha^{-1}$。

取素数 $r$ 与 $F$ 互素，给定非负整数 $n,n'$ 和正整数 $D$。令 $\nu,c:G\to W$ 在 $U$ 上局部常值、加法，且被 $\ell^m$ 消去。要求对 $u\in U,g\in G$ 有

$$
\nu(gug^{-1})=\beta(g)\nu(u),\qquad c(gug^{-1})=\alpha(g)c(u).
$$

还要求 $\nu$ 在所有不在 $n$ 上方的惯性群上为零，$c$ 在所有不在 $n'$ 上方的惯性群上为零。这是 Lean 的两组 `IsNu` 条件。若 $c|_U\ne0$，则存在素数 $q$ 满足

$$
q\nmid D,\qquad q\equiv1\bmod F,\qquad q\ne r,\qquad
     \ell\nmid\operatorname{ord}_{(\mathbb Z/q\mathbb Z)^\times}(r\bmod q)
$$

和一个 $q$ 上方处的算术 Frobenius 提升 $\Phi$，使

$$
c(\Phi)\ne0,\qquad \nu(u)\in O\nu(\Phi)\quad(u\in U).
 \tag{1}
$$

算术 Frobenius 是在剩余域上取 $q$ 次幂的分解群元素。第二个条件的意思是，同一个 $\Phi$ 的 $\nu$ 值生成所有 $\nu(U)$ 张成的 $O$-模。这样，在辅助素数迭代中，新添的惯性值既继承全部消去理想，又能严格推进长度估计。[逐个加入辅助素数的证明](%E9%80%90%E4%B8%AA%E5%8A%A0%E5%85%A5%E8%BE%85%E5%8A%A9%E7%B4%A0%E6%95%B0%E6%80%8E%E6%A0%B7%E6%8A%8A%E5%90%8C%E8%B0%83%E9%95%BF%E5%BA%A6%E5%8E%8B%E5%88%B0%E4%B8%80%E4%B8%AA%E8%B5%8B%E5%80%BC.md)

## 一、固定一个根式会强制怎样的共轭作用

令 $M=\ell^m$，在 $\overline{\mathbb Q}$ 中取 $\rho\ne0$ 使 $\rho^M=r$。令

$$
H=\{u\in U:u(\rho)=\rho\}.
$$

对 $u\in U$，令 $\kappa(u)=u(\rho)/\rho\in\mu_M$。因为 $U$ 固定 $\mu_M$，$\kappa$ 是群同态，核恰为 $H$。对任意 $g\in G$ 有

$$
\kappa(gug^{-1})=g(\kappa(u)).
$$

事实上 $g^{-1}(\rho)/\rho\in\mu_M$，被 $u$ 固定，代入即可。右边等于 $\kappa(u)$ 的 $\varepsilon_\ell(g)\bmod M$ 次幂。特别地，$H$ 正规。作为有限扩张的固定子群，它也是开子群。

由此得到源码的 `radEqv`。若 $f:U\to V$ 是加法同态，值在被 $M$ 消去的 $O$-模中，且 $f(gug^{-1})=\gamma(g)f(u)$，并假设 $f|_H=0$，则

$$
(\gamma(g)-\varepsilon_\ell(g))f(u)=0
                  \quad(g\in G,\ u\in U).
 \tag{2}
$$

因为 $f$ 经 $U/H$ 分解，以上共轭公式说明 $f(gug^{-1})$ 等于 $f(u)$ 乘 $\varepsilon_\ell(g)$ 在 $\mathbb Z/M\mathbb Z$ 中的代表元，这个代表元在 $V$ 上与 $\varepsilon_\ell(g)$ 的作用相同。[共轭引理第 22 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/RadEqv.lean)

## 二、把两个取值条件各写成避开一个开子群

取 $B=\ker(c|_U)$，它是 $G$ 的开子群。若 $H\subseteq B$，就对 $f=c,\gamma=\alpha$ 用 (2)，再用存在一个单位差 $\alpha(g)-\varepsilon_\ell(g)$ 的假设，得到 $c|_U=0$，矛盾。因此 $H$ 不包含在 $B$ 中。

再看 $\nu$。$U$ 紧，$\nu|_U$ 局部常值，故 $\nu(U)$ 有限。$W[A]\cong O/(A)$ 且所有 $W[\pi^j]$ 组成递增链，所以任何两个单元素生成的子模可按包含比较。选 $u_0\in U$ 使 $P=O\nu(u_0)$ 最大，则 $P$ 包含全部 $\nu(u)$。若 $P=0$，条件 (1) 的第二项自动满足，令 $K=B$。

若 $P\ne0$，取开子群 $K=\{u\in U:\nu(u)\in\pi P\}$。对 $\Phi\in U\setminus K$，$\nu(\Phi)=y\nu(u_0)$ 中的 $y$ 必是单位，否则 $\nu(\Phi)\in\pi P$。故 $\nu(\Phi)$ 生成 $P$。还需证明 $H$ 不包含在 $K$ 中。若 $H\subseteq K$，取 $\bar\nu:U\to P/\pi P$，它在 $H$ 上为零，且 $\bar\nu(u_0)\ne0$。对 $\bar\nu$ 用 (2)，其共轭特征是 $\beta$。选一个对 $\mu_F$ 取逆的 $g$，则 $\alpha(g)\equiv-1\bmod\pi$，故

$$
\beta(g)-\varepsilon_\ell(g)=\beta(g)(1-\alpha(g))
$$

是单位，因为 $\ell$ 是奇数。这迫使 $\bar\nu=0$，矛盾。这里对 $c$ 用到 $\alpha-\varepsilon_\ell$ 的单位假设，对 $\nu$ 则用取逆元素上的奇偶条件。两种作用分别保证了两个坏子群不会覆盖 $H$。

## 三、还需要避开更高一层的分圆域

令 $C=G_{\mathbb Q(\mu_{F\ell})}$。我们说明 $H$ 也不包含在 $C$ 中。取 $u\in G$ 在 $\mu_{F\ell}$ 上取 $1+F$ 次幂。由于 $\ell\mid F$，$1+F$ 与 $F\ell$ 互素，故这样的提升存在，且 $u\in U$。取 $g$ 在 $\mu_{F\ell}$ 上作用为取逆。由第一节的共轭公式，

$$
\kappa(gug^{-1}u)=g(\kappa(u))\kappa(u)=1.
$$

所以 $gug^{-1}u\in H$。另一方面，$G$ 在 $\mu_{F\ell}$ 上的作用交换，这个元素的指数是 $(1+F)^2\equiv1+2F\bmod F\ell$，不等于 $1\bmod F\ell$，因为 $\ell\ne2$。于是 $gug^{-1}u\notin C$。

这样得到 $H$ 的三个真子群 $K\cap H,B\cap H,C\cap H$。为什么能同时避开它们？先用两子群事实。若 $H$ 不包含在 $J_1,J_2$ 中，分别拿一个 $H$ 中不在 $J_1$ 或不在 $J_2$ 的元素。若两者都没有同时避开，则分别在 $J_2,J_1$ 中，它们的乘积同时避开，因落入任一个子群都会经消去矛盾。

反设 $H\subseteq K\cup B\cup C$。由两子群事实取 $x\in H\setminus(B\cup C)$ 和 $y\in H\setminus(K\cup C)$，于是 $x\in K,y\in B$。$xy$ 落不到 $K$ 或 $B$，只能在 $C$ 中。考虑 $x^2y$。它若在 $K$ 中则 $y\in K$。它若在 $C$ 中则 $x\in C$，因为 $xy\in C$。它若在 $B$ 中则 $x^2\in B$。然而 $c(x^M)=M c(x)=0$，故 $x^M\in B$，而 $M$ 是奇数。从 $x^2,x^M\in B$ 得 $x\in B$，又矛盾。因此三者不能覆盖 $H$，可以找到

$$
x\in H\setminus(K\cup B\cup C).
 \tag{3}
$$

正是 $c|_U$ 被奇数 $M$ 消去，让三个条件能由同一个元素满足。[两子群、三子群与高一层分圆域第 12、23、70 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/AddPowNsmul.lean)

## 四、从开集里的元素找到素数

使用 Chebotarev 的如下形式。对 $G_{\mathbb Q}$ 的任意非空开集 $V$ 与任意非零整数 $d$，存在素数 $q\nmid d$、一个 $q$ 上方的处和算术 Frobenius 提升 $\Phi\in V$。从有限扩张的通常陈述可以得到它。在 $V$ 中取一个开正规子群的陪集 $xJ\subseteq V$，对有限商 $G/J$ 的 $xJ$ 所在共轭类用 Chebotarev，并避开 $d$ 的有限个素因子。改选素处可把该共轭类代表改为 $xJ$ 本身，故得到落在 $V$ 内的提升。这是项目 `chebQ` 给出的结论，源码从一次素处的密度得到它。[Chebotarev 入口第 8 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/ChebQ.lean)

取 $V=H\setminus(K\cup B\cup C)$，它非空且开，因为各开子群也是闭集。让 Chebotarev 选到 $q\nmid D F\ell r$ 的 $\Phi\in V$。第一、二节的定义已给 (1)。$\Phi|_{\mu_F}=1$ 给 $q\equiv1\bmod F$，而 $\Phi|_{\mu_{F\ell}}\ne1$ 给 $q\not\equiv1\bmod F\ell$。所以写 $q-1=Fh$，有 $\ell\nmid h$。还因 $\Phi(\rho)=\rho$，在 $q$ 上方的剩余域有 $\rho=\rho^q$。$q\nmid r$ 使 $\rho$ 约化后非零，故

$$
1=\rho^{q-1}=(\rho^M)^{N_0h}=r^{N_0h}
               \quad\text{于剩余域内}.
$$

$r$ 的像来自 $\mathbb F_q^\times$，因此它的乘法阶整除 $N_0h$。$\ell\nmid N_0h$，得到所需的阶条件。这样同时得到可用素数和两个取值要求。

## Lean 对照

- `radEqv` 给 (2)。`two_sub`、`three_sub` 给 (3) 的群论，`third` 证明 $H$ 中有元素不固定 $\mu_{F\ell}$。[根式作用第 22 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/RadEqv.lean) · [三个子群第 12、23、70 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/AddPowNsmul.lean)
- `adm` 从根式固定及分圆条件读出模 $q$ 的阶限制，[`pick`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/AddPowNsmul.lean#L175) `pick` 合成。[可用条件第 126 行、选择第 175 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/AddPowNsmul.lean)

本篇为源码对读。Chebotarev 的一次素处结论是本篇使用的数学输入。Lean 声明 `pick` 内部直接调用 `chebQ`，其传递公理依赖与内核重放状态未查。
