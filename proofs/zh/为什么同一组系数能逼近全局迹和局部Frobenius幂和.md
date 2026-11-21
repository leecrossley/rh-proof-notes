# 为什么同一组系数能逼近全局迹和局部 Frobenius 幂和

## 命题

设 $K$ 为带非阿基米德绝对值的域，$\Gamma$ 为群，$r,\rho_i:\Gamma\to\mathrm{GL}_a(K)$ 为表示，其中 $i\in A$。给定两组坐标 $\theta:J\to K$、$\theta':J'\to K$ 和每个种子的坐标 $\eta_i:J\to K,\eta_i':J'\to K$。假定在不交并 $J\sqcup J'$ 上，$(\theta,\theta')$ 可由 $(\eta_i,\eta_i')$ 作 [多项式逼近](%E6%80%8E%E6%A0%B7%E4%BB%8E%E7%A8%A0%E5%AF%86Frobenius%E5%8F%96%E5%80%BC%E6%9E%84%E9%80%A0%E6%9E%81%E9%99%90%E8%BF%B9.md)。假定对每个有限的 $F\subseteq A$、系数 $c_i$ 和误差 $\varepsilon$，只要 $J$ 上所有整系数多项式上的逼近误差都至多 $\varepsilon$，同一组合在所有 $\operatorname{tr}r(g)$ 上的误差也至多 $\varepsilon$。

给定序列 $S_n,s(\rho)_n$，其中 $n\in\mathbb N$，以及 $p:\mathbb N\to J'$ 和公用缩放 $u_n\in K$，使 $S_n=u_n\theta'_{p(n)}$、$s(\rho_i)_n=u_n\eta'_{i,p(n)}$。则任意给定 $N\ge0,\varepsilon>0$，可选一组有限系数 $c_i$，使同时对所有 $g\in\Gamma$ 有

$$
\left|\operatorname{tr}r(g)-\sum_i c_i\operatorname{tr}\rho_i(g)\right|\le\varepsilon,
$$

且同时对全部 $0\le n\le N$ 有 $|S_n-\sum_i c_i s(\rho_i)_n|\le\varepsilon$。

## 证明

取 $M=\max(1,|u_0|,\ldots,|u_N|)$，用两组坐标共同的逼近假设选一组系数，误差至多 $\varepsilon/M$。对只用 $J$ 的多项式，第二组坐标不起作用。于是由题设的误差传递，同一系数在每个群元素的迹上都至多有 $\varepsilon/M\le\varepsilon$ 的误差。

对 $n\le N$，用仅含一个变量的多项式 $X_{p(n)}$，得 $\left|\theta'_{p(n)}-\sum_i c_i\eta'_{i,p(n)}\right|\le\varepsilon/M$。乘以 $u_n$ 后误差至多 $|u_n|\varepsilon/M\le\varepsilon$。两项只用了同一次逼近。若多个指标给同一个 $\rho$，可合并其系数，因为在两处求和的被乘函数都只依赖表示 $\rho$。

## 在局部相容性中的用途

主线对每个指定的 $w\mid\ell$ 都选择一组在 $w$ 晶体、具有同一 Hodge–Tate 权的种子。第一组坐标是球形 Hecke 本征值。其误差传递由 [极限迹构造](%E6%80%8E%E6%A0%B7%E4%BB%8E%E7%A8%A0%E5%AF%86Frobenius%E5%8F%96%E5%80%BC%E6%9E%84%E9%80%A0%E6%9E%81%E9%99%90%E8%BF%B9.md) 的第一项给出。第二组坐标是 $w$ 处 Satake 参数的幂和，先乘使 Hecke 算子整的非零常数，再纳入总逼近。若 $\sigma$ 是局部 Weil 群元素，第二组坐标选指数 $-n\deg\sigma$，因为项目的代数归一化下 Weil–Deligne 参数在 $\sigma$ 上的本征值为其 Satake 归一化参数的 $-\deg\sigma$ 次幂。$u_n$ 是相应整化常数的逆。得到的正是 `JointApprox`。将它交给晶体 Frobenius 的闭性定理，才能认出目标表示在这个地方的 Frobenius 多项式。

## Lean 对照

- [`joint`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/TraceLimits/SlopeTestRemainingChoices.lean#L50) 给误差同时成立。[同文件的 `phiSum_satWD`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/TraceLimits/SlopeTestRemainingChoices.lean#L91) 计算幂和指数。
- [`limWU4_of` 的末段](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/TraceLimits/LimFinOddOf.lean#L172) 令 $J'$ 含 $w$ 的缩放幂和并应用该引理。本篇按源码对读，闭性定理在上游另证。
