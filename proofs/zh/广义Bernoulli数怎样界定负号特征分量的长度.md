# 广义Bernoulli数怎样界定负号特征分量的长度

**命题（[`psiOf`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/PsiOf.lean#L12)，`UpperTheory.V.ML.psiOf`）。** 设 $E/\mathbb Q$ 为有限阿贝尔 Galois 扩张，$E$ 为 CM 数域，即全实数域的全虚二次扩张。固定代数闭包 $\Omega$ 同时包含 $\mathbb Q$ 和 $E$。给定正整数 $N$ 以及群同态
$\varrho:(\mathbb Z/N\mathbb Z)^\times\to\mathrm{Gal}(E/\mathbb Q)$，要求当 $g\in G_{\mathbb Q}=\mathrm{Gal}(\Omega/\mathbb Q)$ 在 $\mu_N$ 上作用为取 $t$ 次幂时，$g|_E=\varrho(t)$。这是源码的 `IsCycAct`。取奇素数 $\ell\nmid[E:\mathbb Q]$，取 $O\subseteq\overline{\mathbb Q}_\ell$ 为有限于 $\mathbb Z_\ell$ 的离散赋值环。设 $e\ge1,\ k=e+1$，取任意群特征 $\psi:\mathrm{Gal}(E/\mathbb Q)\to O^\times$。在模 $N$ 的单位上定义 $\chi=\psi\circ\varrho$，延为狄利克雷特征，要求 $\chi(-1)=(-1)^k$。令 $\chi^*$ 为诱导 $\chi$ 的本原特征，取任意 $a\in O$ 满足

$$
a=N\Bigl(\prod_{p\le k+1}p\Bigr) B_{k,\chi^*}.
$$

若局部相互律 `Rec` 成立，则

$$
\operatorname{length}_O H_E(\varepsilon_\ell^{-e})[\psi]\le v_O(a).
 \tag{1}
$$

这里 $H_E(\varepsilon_\ell^{-e})$ 表示以 $W=\operatorname{Frac}(O)/O$ 为系数、作用为 $\varepsilon_\ell^{-e}$ 的连续一阶上同调，再取所有有限惯性群与 $\ell$ 上方分解群的局部化核。方括号表示 Galois 共轭作用按 $\psi$ 取值的特征空间，具体作用见第三节。在 Lean 中，这个长度叫 `psiLen`，命题对这些参数的全称量化叫 `PsiBound`。这一条是负号长度证明中，对不整除 $[E:\mathbb Q]$ 的奇素数使用的分量估计。[负号长度怎样对所有特征求和](%E8%B4%9F%E5%8F%B7%E4%B8%8A%E5%90%8C%E8%B0%83%E9%95%BF%E5%BA%A6%E6%80%8E%E6%A0%B7%E7%94%B1%E8%B5%8B%E5%80%BC%E5%92%8C%E6%B6%88%E5%8E%BB%E5%85%83%E6%8E%A7%E5%88%B6.md)

## 一、本原特征的有理数域估计

设 $\phi$ 是系数在 $O$ 中的本原狄利克雷特征，导子 $f\ge1$，且 $\ell\nmid\operatorname{ord}(\phi)$、$\phi(-1)=(-1)^k$。写 $\phi_G$ 为 $\phi$ 通过 $\mu_f$ 在 $G_{\mathbb Q}$ 上取得的特征。我们先证明

$$
\operatorname{length}_O H_{\mathbb Q}(\alpha)\le v_O(a_f),\qquad
  \alpha=\varepsilon_\ell^{-e}\phi_G^{-1},\qquad
  a_f=f\Bigl(\prod_{p\le k+1}p\Bigr)B_{k,\phi}.
 \tag{2}
$$

这里的局部化核按开头相同的惯性、分解群条件定义。式 (2) 是源码 `prim_case`，右端 $a_f$ 的整性来自清 Bernoulli 分母。

先辨明本原性提供的局部条件。对任何有理素数 $p$，$\mathbb Q(\mu_f)/\mathbb Q$ 在 $p$ 处的惯性像是模 $f$ 的单位群到模 $f/p^{v_p(f)}$ 单位群映射的核。当 $p\mid f$，这一事实可在 $\mathbb Q_p$ 上看出。令 $f=p^a f'$ 且 $p\nmid f'$。$\mu_{f'}$ 生成不分歧扩张，$\mu_{p^a}$ 生成全分歧扩张，二者交为基域。因此惯性恰在 $p^a$ 的分量上给出全部单位。当 $p\nmid f$，惯性像为平凡群。若 $\phi$ 在 $p\mid f$ 的惯性像上平凡，就经模 $f/p^{v_p(f)}$ 分解，违反本原性。因此对 $p\mid f$ 可取 $u\in I_p$ 使 $\phi_G(u)\ne1$。

每个 $\phi_G(g)$ 是阶整除 $\operatorname{ord}(\phi)$ 的单位根。若其中一个 $x\ne1$ 且阶整除与 $\ell$ 互素的 $d$，则 $x-1$ 为单位。否则 $x$ 在剩余域等于 $1$，而 $(x-1)(1+x+\cdots+x^{d-1})=0$ 给 $1+x+\cdots+x^{d-1}=0$，约化后便得 $d=0$，与 $\ell\nmid d$ 矛盾。所以在 $p\mid f,p\ne\ell$ 的惯性上，可取 $\alpha(u)-1$ 为单位，因为 $\varepsilon_\ell$ 在这里平凡。在 $p\nmid f\ell$ 的惯性上，$\alpha$ 平凡。[本原性、惯性与单位第 93 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/PrimRam.lean)

现在分两种情况。

- 若对每个 $g$，$\alpha(g)-\varepsilon_\ell(g)$ 都在 $O$ 的极大理想中，则 $\alpha\equiv\varepsilon_\ell$ 模该理想。在任意 $p\ne\ell$ 的惯性上，$\varepsilon_\ell=1$，故 $\phi_G^{-1}\equiv1$。由上面的单位根性质，$\phi_G^{-1}=1$，所以 $\alpha$ 在这些惯性群上都平凡。用 `exc` 得 $H_{\mathbb Q}(\alpha)=0$，从而 (2) 成立。[`exc` 的证明](%E6%80%8E%E6%A0%B7%E7%BB%99%E5%B1%80%E9%83%A8%E9%9B%B6%E4%B8%8A%E5%90%8C%E8%B0%83%E7%B1%BB%E9%80%89%E4%BB%A3%E8%A1%A8%E5%85%83%E5%B9%B6%E6%8E%A7%E5%88%B6%E9%95%BF%E5%BA%A6.md)
- 若存在 $g$ 使差为单位，对每个非零 $a_0\in O$ 用 `zEval`。它给 $F=(f/\ell^{v_\ell(f)})\ell^m$ 和 $z$ 满足 $a_0z\mid\ell^m,\ z\mid a_f$，并给辅助素数长度估计要求的两项同余。对复共轭 $\delta$，$\alpha(\delta)=(-1)^{e+k}=-1$，故 $\alpha(\delta)-1=-2$ 为单位。源码从某个 $F$ 的取逆提升得到同一单位条件。将 $z$ 代入 `count`，得 $T(a_0)$ 的长度至多 $v_O(z)\le v_O(a_f)$。因为 $F$ 与 $f\ell$ 有相同的素因子，定义 $T(a_0)$ 的分歧条件与局部条件都可用固定的 $f\ell$。因此对所有 $a_0$ 得同一个界，应用 `shaToShT` 得 (2)。 [下取整和 Bernoulli 赋值](%E4%B8%8B%E5%8F%96%E6%95%B4%E7%B3%BB%E6%95%B0%E6%80%8E%E6%A0%B7%E7%BB%99%E5%87%BA%E5%B9%BF%E4%B9%89Bernoulli%E6%95%B0%E7%9A%84%E8%B5%8B%E5%80%BC.md) · [加辅助素数的长度估计](%E9%80%90%E4%B8%AA%E5%8A%A0%E5%85%A5%E8%BE%85%E5%8A%A9%E7%B4%A0%E6%95%B0%E6%80%8E%E6%A0%B7%E6%8A%8A%E5%90%8C%E8%B0%83%E9%95%BF%E5%BA%A6%E5%8E%8B%E5%88%B0%E4%B8%80%E4%B8%AA%E8%B5%8B%E5%80%BC.md) · [局部零上同调的代表元](%E6%80%8E%E6%A0%B7%E7%BB%99%E5%B1%80%E9%83%A8%E9%9B%B6%E4%B8%8A%E5%90%8C%E8%B0%83%E7%B1%BB%E9%80%89%E4%BB%A3%E8%A1%A8%E5%85%83%E5%B9%B6%E6%8E%A7%E5%88%B6%E9%95%BF%E5%BA%A6.md)

## 二、把本原估计传到任意模数

设 $\chi$ 为模 $N$ 特征，$\ell\nmid\operatorname{ord}(\chi)$，满足 $\chi(-1)=(-1)^k$。取 $\phi=\chi^*$、$f=\operatorname{cond}(\chi)$。升模 $f\to N$ 在单位群层面是通过一个满射拉回，故特征阶及 $-1$ 处的值保持。它也保持从绝对 Galois 群定义的特征，因为 $g$ 在 $\mu_f$ 上的指数是其在 $\mu_N$ 上的指数模 $f$ 的约化。因此 $\chi_G=\phi_G$，(2) 左边的局部化核无须改变。

右边的 $a_f$ 与 (1) 中的 $a$ 用的是同一个本原 Bernoulli 数，且 $a=(N/f)a_f$。故 $v_O(a_f)\le v_O(a)$。这样便得到 `vChar` 对任意模数所需的有理数域估计。这里用的是本原 Bernoulli 数的定义，升模没有额外的 Euler 因子加在 $a$ 上。[本原下降第 165 行、任意模数第 201 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/PrimCase.lean) · [本原值升模不变第 15 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/Primeq.lean)

## 三、可逆指数怎样识别特征分量

令 $G=G_{\mathbb Q}$，$U=G_E$。它是开正规子群，$G/U=\mathrm{Gal}(E/\mathbb Q)$。写 $\widetilde\psi:G\to O^\times$ 为 $\psi$ 经该商得到的特征，它在 $U$ 上平凡。考虑 $W$ 上的两种 $G$ 作用，

$$
\rho=\varepsilon_\ell^{-e},\qquad
                    \rho'=\varepsilon_\ell^{-e}\widetilde\psi^{-1}.
$$

它们在 $U$ 上相同，所以 $H^1(U,W)$ 的余闭链、余边界和局部限制可以取为同一个模。$G$ 在 $U$ 的余闭链上通过 $z(u)\mapsto\rho(g)z(g^{-1}ug)$ 作用。在两种系数下，这两个作用只相差标量 $\widetilde\psi(g)$。于是，$\rho$ 作用下属于 $\widetilde\psi$ 的特征类，恰对应 $\rho'$ 作用下的 $G/U$ 不变类。这就是 `selTwist` 的作用。

还需把 $U$ 上的不变类送回 $G$。下面给出 `selUnit` 使用的限制与转移。设 $d=[G:U]$，因为 $\ell\nmid d$，$d$ 在 $O$ 可逆。

**限制是单射。** 若 $G$ 上的一阶类在 $U$ 上为零，可减去一个处处定义的余边界，使其代表元 $z$ 在 $U$ 上为零。于是 $z(gu)=z(g)$ 且 $z(ug)=\rho'(u)z(g)$。因 $U$ 正规，$z$ 成为 $G/U$ 上取 $W^U$ 值的余闭链。对任意 $g$ 平均 $z(gq)=z(g)+\rho'(g)z(q)$（$q$ 遍历商群），得 $z(g)=(1-\rho'(g))d^{-1}\sum_q z(q)$，故为余边界。

**每个不变类都可限制得到。** 取商群各元素 $i$ 的代表元 $x_i$，写 $g x_i=x_{\bar g i}u_{g,i}$，其中 $u_{g,i}\in U$。对 $U$ 上的余闭链 $z$，定义

$$
Cz(g)=\sum_i\rho'(x_{\bar g i})z(u_{g,i}).
$$

因为 $u_{gh,i}=u_{g,\bar h i}\,u_{h,i}$，代入 $z$ 的余闭链恒等式得 $Cz(gh)=Cz(g)+\rho'(g)Cz(h)$。选定代表元后，每个陪集在 $G$ 中开闭，所以 $Cz$ 连续。对 $u\in U$，限制后的 $Cz(u)$ 是 $\sum_i\rho'(x_i)z(x_i^{-1}u x_i)$。在 $U$ 的上同调中，它的类是所有共轭类之和。若原类不变，此和恰为 $d[z]$，故 $d^{-1}[Cz]$ 是所需的原像。

上述同构也保留局部化核。对任意要加局部条件的惯性群或分解群 $D\subseteq G$，$U\cap D$ 是 $D$ 的开正规子群，其指数整除 $d$（看 $D$ 在 $G/U$ 中的像）。刚证明的限制单射可用于这对群。所以一个 $G$ 上的类若限制到 $U\cap D$ 已经为零，则它在 $D$ 上也为零。反向由限制的复合立即成立。这里的 $U\cap I_v$ 及 $U\cap D_v$ 正是 $E$ 的相应惯性与分解群。于是得到长度等式

$$
\operatorname{length}_O H_E(\varepsilon_\ell^{-e})[\psi]
      =\operatorname{length}_O H_{\mathbb Q}
                       (\varepsilon_\ell^{-e}\widetilde\psi^{-1}) .
 \tag{3}
$$

[改变系数特征第 60 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/SelmerTransport/SelTwist.lean) · [限制到不变类第 26 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/SelmerTransport/SelUnit.lean) · [合成等式第 9 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CharacterLevelBounds/EigV.lean)

## 四、把同一个 $\psi$ 代入

按开头的单位根作用条件，$g|_E=\varrho(t)$ 时，$\widetilde\psi(g)=\psi(\varrho(t))=\chi(t)$，所以 $\widetilde\psi=\chi_G$。此外 $\chi$ 的阶整除 $|\mathrm{Gal}(E/\mathbb Q)|=[E:\mathbb Q]$，因为 $\chi$ 通过该有限群取值。这给第二节所需的 $\ell\nmid\operatorname{ord}(\chi)$。用 (3) 后，以该 $\chi$ 代入第二节的有理数域界，得到 (1)。

因此 $\ell\nmid[E:\mathbb Q]$ 在两处使用。一处使上同调限制可用 $d^{-1}$ 求逆，另一处让本原特征的非平凡值和 $1$ 的差为单位。这样就能把估计送入负号长度的不整除域次数分支。

## Lean 对照与证明范围

- [`primRam`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/PrimRam.lean#L93) `primRam` 给本原特征的惯性条件。[`prim_case`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/PrimCase.lean#L89) `prim_case` 合并 `exc`、`zEval`、`count`、`shaToShT`。[`lev_case`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/PrimCase.lean#L165) `lev_case`、[`vChar`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/PrimCase.lean#L201) `vChar` 传到任意模数。[本原情形第 89 行、升模第 165 行、整条有理数域估计第 201 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/PrimCase.lean)
- [`selTwist`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/SelmerTransport/SelTwist.lean#L60) `selTwist`、[`selUnit`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/SelmerTransport/SelUnit.lean#L26) `selUnit`、[`selEigBase`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/SelmerTransport/SelEigBase.lean#L7) `selEigBase` 给同一个模上的特征比较与局部限制同构，[`eigV`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CharacterLevelBounds/EigV.lean#L9) `eigV` 专门化为 (3)。[一般长度等式第 7 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/SelmerTransport/SelEigBase.lean)
- [`psiOf`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/PsiOf.lean#L12) `psiOf` 第 12 行用切出的狄利克雷特征验证第四节。`iv` 用传入的 Poitou–Tate 全局对偶和局部不分歧正交提供 `Rec`。两项输入怎样给出局部相互律，见杯积证明。[合成](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/PsiOf.lean) · [相互律输入，第 4 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/Iv.lean) · [局部杯积](%E5%B1%80%E9%83%A8%E6%9D%AF%E7%A7%AF%E6%80%8E%E6%A0%B7%E8%BF%AB%E4%BD%BF%E6%83%AF%E6%80%A7%E4%B8%8A%E7%9A%84%E5%8F%96%E5%80%BC%E4%B9%98%E7%A7%AF%E6%B6%88%E5%A4%B1.md)

窗口估计在 `of_four_alt` 处把 `ML.iv` 得到的分量界传给 `Odd.thmBcFree_of`，再用于负号长度总和。它从 `LitCoh` 取出归一化的 Poitou–Tate 对偶和局部不分歧正交。上游这两项有各自的定理证明体，分别从全局九项正合列，以及局部有限性、Tate 对偶和 Euler 特征公式组装。这里已定位调用，两个上游对偶证明仍作为经典输入。[窗口调用，第 18–22 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/HVCore.lean) · [组装两项输入，第 301、323、331 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/TemperedProductOfSquareIntegrable.lean) · [全局对偶，第 18 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/WeilBound/CoreStatements/PublishedTheorems/PoitouTateDuality/PoitouTateNineTerm/PoitouTateNormalisedHolds.lean) · [局部正交，第 10 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicSpectrum/Proofs/GlobalProofs/UnramifiedOrthogonality.lean)

本篇为源码对读。`psiOf` 是带 `Rec` 输入的推论，最终给出的长度上界有限，因为奇偶性相容的本原 Bernoulli 数非零。右端 Bernoulli 数的非零性和赋值比较见 [Bernoulli 同余](%E4%B8%8B%E5%8F%96%E6%95%B4%E7%B3%BB%E6%95%B0%E6%80%8E%E6%A0%B7%E7%BB%99%E5%87%BA%E5%B9%BF%E4%B9%89Bernoulli%E6%95%B0%E7%9A%84%E8%B5%8B%E5%80%BC.md)。上述声明的内核重放及传递公理状态未查。
