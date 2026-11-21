# 为什么 V 类的剩余负二权没有一阶类

**命题。** 给定 [大二进导子分支](%E4%B8%BA%E4%BB%80%E4%B9%88%E5%A4%A7%E4%BA%8C%E8%BF%9B%E5%AF%BC%E5%AD%90%E7%9A%84V%E7%B1%BB%E6%94%B9%E7%94%A8%E9%AB%98%E6%96%AF%E5%9F%9F.md) 的框架，使用其一般权 $e\ge1$ 的接口。记 $k=O/\mathfrak m$，$\eta$ 为模 $4$ 的二次特征，$\bar\Psi$ 为 $\Psi=\varepsilon_\ell^e\psi_G$ 的约化。设 $\gamma=\eta\bar\Psi^{-2}$。对连续余闭链 $z:\Gamma\to k$ 满足

$$
z(gh)=z(g)+\gamma(g)z(h),
$$

假定在 $\ell$ 处分解群上为余边界，在 $S\setminus\{\ell\}$ 的每个 $N_v=I_v\cap\ker\eta\cap\ker\bar\Psi$ 上恒为零。这些是 `Frame.Xpp` 的局部条件。则存在 $b\in k$，使 $z(g)=\gamma(g)b-b$ 对所有 $g$ 成立。

## 二进分量平方后保留低一层的本原性

先证明一个导子事实。设 $c\ge4$，$\theta_2$ 为模 $2^c$ 的本原特征，系数为特征零。其平方在 $1+2^{c-1}$ 上为 $1$，故经模 $2^{c-1}$ 分解。在 $1+2^{c-2}$ 上求平方，有

$$
(1+2^{c-2})^2\equiv1+2^{c-1}\pmod{2^c}.
$$

右边正是 $\theta_2$ 取值 $-1$ 的元素。因此 $\theta_2^2$ 在此处为 $-1$，而模 $4$ 特征 $\eta$ 在此处为 $1$，因为 $c\ge4$。故 $\theta_2^2\eta$ 的导子恰为 $2^{c-1}$。这给 `xiSq`。

现在记 $c=c_2(\psi)$、$n=c-1$，把 $\psi_2$ 的本原模数取为 $2^c$。令 $\xi$ 为 $\psi_2^2\eta$ 所诱导的模 $2^n$ 本原特征。它满足 $\xi(-1)=-1$。设 $\theta$ 是 $\psi$ 去掉 $\ell$-幂阶部分和模二幂分量后的特征，$\omega$ 为模 $\ell$ 圆分的 Teichmüller 提升。把奇数模分量 $\omega^{2e}\theta^2$ 取为导子 $f$ 上的本原特征 $\phi$。它在 $-1$ 上取值 $1$，且 $f\mid\ell\operatorname{cond}(\theta^2)\mid\ell Q$。故 $\phi\xi$ 为奇特征。

设 $d=f_0$，即 $\ell$ 模 $\operatorname{lcm}(4,\operatorname{ord}\theta)$ 的阶。于是 $4,\ell-1,\operatorname{ord}\theta$ 都整除 $\ell^d-1$，故 $\operatorname{ord}\phi\mid\ell^d-1$。另有

$$
f4^{v_2(\ell^d-1)}
\le \ell Q\,4^{n_0}\le 2^{c-1}=2^n
$$

由大导子假设给出。因此 $\phi,\xi$ 满足 [`CorX` 的数值条件](%E5%A4%A7%E7%9A%84%E4%BA%8C%E8%BF%9B%E5%AF%BC%E5%AD%90%E6%80%8E%E6%A0%B7%E4%BD%BF%E5%89%A9%E4%BD%99%E4%BD%99%E9%97%AD%E9%93%BE%E6%88%90%E4%B8%BA%E4%BD%99%E8%BE%B9%E7%95%8C.md)。

## 识别剩余特征和局部条件

$\overline{\omega}=\bar\varepsilon_\ell$，且 $\psi$ 的 $\ell$-幂阶部分约化为 $1$。故 $\phi\xi$ 的约化拉回为 $\bar\Psi^2\eta$，其逆恰为 $\gamma$。把 $z$ 拉回 $G_{\mathbb Q}$。在 $S$ 外，它通过 $\Gamma$，所以在惯性上恒为零。在 $S\setminus\{\ell\}$，局部条件给在 $N_v$ 上恒为零，而 $N_v$ 在 $I_v\cap\ker\gamma$ 中的指数与 $\ell$ 互素，因为它是映到 $\{1,-1\}\times k^\times$ 的核。这条性质在改选共轭素处后仍成立。对 $\ell$ 上方，$z$ 在分解群上为余边界，故在惯性和 $\ker\gamma$ 的交上为零。这样可用 `CorX`，得到拉回的 $z$ 为余边界。由于商映射是满射，$z$ 本身也是余边界。

最后说明这一维计算为何正是次数 $-2$。按 $1,0,-1$ 给矩阵三行赋权，矩阵单位 $E_{20}$（下标从零开始）是唯一权 $-2$ 的单位。由参考表示的对角共轭，它被乘 $\bar\Psi^{-2}$。另一陪集上的李代数对偶作用是 $X\mapsto-JX^{\mathsf T}J$，其中 $J$ 为反序矩阵。对 $E_{20}$ 这给一个负号，恰产生因子 $\eta$。故这个一维伴随表示正是 $\gamma$，其一阶局部商为零。这给出 [大导子 V 类变形估计](%E4%B8%BA%E4%BB%80%E4%B9%88%E5%A4%A7%E4%BA%8C%E8%BF%9B%E5%AF%BC%E5%AD%90%E7%9A%84V%E7%B1%BB%E6%94%B9%E7%94%A8%E9%AB%98%E6%96%AF%E5%9F%9F.md) 的 `HostXpp`。

## Lean 对照

- [`xiSq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/HcXiSq.lean) 证明平方后乘 $\eta$ 的导子。
- [`dirData`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/HcDirData.lean#L28)、[`dir`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/DirGPowOne.lean#L23) 给本原分解和降约等式。
- [`adRep_baseLift_apply`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeGroups/AdRepBaseLiftApply.lean#L16)、[`xppOf`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/HcXppOf.lean#L60)、[`xpp`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/Xpp.lean#L11) 给权与局部条件的传递。本篇为发布版源码对照。
