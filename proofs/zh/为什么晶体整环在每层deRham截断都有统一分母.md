# 为什么晶体整环在每层 de Rham 截断都有统一分母

## 命题

设 $\ell$ 为素数，$A=A_{\inf}=W(\mathcal O_{\mathbb C_\ell^\flat})$，$P=A[1/\ell]$。Fontaine 特化 $\theta:A\to\mathcal O_{\mathbb C_\ell}$ 的核由一个非零元 $\xi$ 生成。设 $A_{\rm cris}^0\subset P$ 是在 $A$ 上添入所有 $\xi^j/j!$ 得到的分幂包络，$A_{\rm cris}$ 是它的 $\ell$-进完备化，$B_{\rm dR}^+=\varprojlim_m P/(\xi^m)$。则有一个延伸原映射的比较

$$
j:A_{\rm cris}\longrightarrow B_{\rm dR}^+.
$$

它满足，对每个 $m\ge0$ 和每个 $x\in A_{\rm cris}$，存在 $a\in A$ 使得

$$
\ell^m j(x)\equiv a\pmod{{\rm Fil}^m}.
\tag{1}
$$

这里 ${\rm Fil}^m$ 是 $B_{\rm dR}^+$ 到 $P/(\xi^m)$ 的映射核。统一指数 $m$ 与 $x$ 无关。另有 $A/(\xi^m)$ 在 $\ell$-进意义下分离且完备，且映射到 $P/(\xi^m)$ 单射。这些结论使用[Fontaine 特化核的生成元](%E4%B8%BA%E4%BB%80%E4%B9%88%E5%88%86%E5%9C%86%E5%85%83%E7%94%9F%E6%88%90Fontaine%E7%89%B9%E5%8C%96%E7%9A%84%E6%A0%B8.md)、$A$ 的 $\ell$-进完备性及分幂包络的生成方式。[ExistsCanonicalAcrisToBdRPlus.lean:210](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/ExistsCanonicalAcrisToBdRPlus.lean#L210) · [FontaineXiPowSaturatedQuotientComplete.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/FontaineXiPowSaturatedQuotientComplete.lean)

分幂包络与 de Rham 完备化采用 Bhatt、Morrow、Scholze 导论中的定义。[Integral p-adic Hodge theory，导论](https://www.math.uni-bonn.de/people/scholze/integralpadicHodge.pdf#page=4)

## 为什么整数环的各层商分离且完备

先证 $A/(\xi)$ 没有 $\ell$-挠，因为它嵌入特征零整域 $\mathcal O_{\mathbb C_\ell}$。于是从 $\xi^m\mid \ell a$ 可先推出 $\xi\mid a$，写 $a=\xi a_1$，约去 $\xi$ 后，再用归纳得 $\xi^m\mid a$。反复应用这个过程，也能从 $\xi^m\mid \ell^k a$ 消去所有 $\ell$。这就是整商 $B_m=A/(\xi^m)$ 到 $P/(\xi^m)$ 单射的原因。

固定 $m>0$，令 $\eta=\xi^m$。如果 $a$ 在 $B_m$ 的像属于每个 $\ell^nB_m$，可写 $a=\eta b_n+\ell^n c_n$。对 $k\ge n$ 比较两式，有 $\eta(b_n-b_k)\in\ell^n A$。利用刚证的消去性质，可将等式右侧的 $\ell^n$ 系数写成 $\eta$ 乘另一元素；在 $A$ 中约去 $\eta$，得 $b_n-b_k\in\ell^n A$。所以 $b_n$ 在 $A$ 中有极限 $b$，且 $a=\eta b$。这证明分离性。

再取 $B_m$ 中的一条相容逼近列，使第 $n+1$ 项与第 $n$ 项的差属于 $\ell^nB_m$。选代表 $u_n\in A$。从 $u_0$ 开始逐项调整下一个代表，减去它和上一个代表相差的 $\eta$ 倍数，使新代表的相邻差直接属于 $\ell^n A$。这样在 $A$ 取极限，再降到 $B_m$，即得原逼近列的极限。$m=0$ 时商环为零。[FontaineXiPowSaturatedQuotientComplete.lean:20](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/FontaineXiPowSaturatedQuotientComplete.lean#L20) · [同文件:58](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/FontaineXiPowSaturatedQuotientComplete.lean#L58)

## 找到能接收完备化的像

令 $R_m$ 为 $A_{\rm cris}^0$ 在 $P/(\xi^m)$ 中的像。已知 $B_m\subseteq R_m$。分幂乘积满足

$$
\frac{\xi^i}{i!}\frac{\xi^j}{j!}
=\binom{i+j}{i}\frac{\xi^{i+j}}{(i+j)!},
$$

故 $A_{\rm cris}^0$ 是这些分幂的 $A$-线性张成。第 $j\ge m$ 项在 $P/(\xi^m)$ 中为零。对 $j<m$，由 $v_\ell(j!)\le j$ 可知 $\ell^m/j!\in\mathbb Z_\ell$。所以 $\ell^m R_m\subseteq B_m$。统一分母来自截断后只留下有限次数。[ExistsCanonicalAcrisToBdRPlus.lean:125](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/ExistsCanonicalAcrisToBdRPlus.lean#L125)

这一夹逼还说明 $R_m$ 本身是 $\ell$-进完备分离的。若 $b\in B_m\cap\ell^{n+m}R_m$，则 $b=\ell^n(\ell^m r)$ 对某个 $r\in R_m$ 成立，故 $b\in\ell^n B_m$。因此 $B_m$ 的自然 $\ell$-进拓扑与从 $R_m$ 诱导的拓扑一致，且 $B_m$ 包含开子群 $\ell^mR_m$。任一 $R_m$ 的 Cauchy 列，减去一个足够晚的固定项后，尾部就落在 $B_m$，可以在 $B_m$ 中取极限。若一个元素属于每个 $\ell^nR_m$，它已经在 $B_m$，并由相同的比较属于每个 $\ell^nB_m$，故为零。[ExistsCanonicalAcrisToBdRPlus.lean:22](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/ExistsCanonicalAcrisToBdRPlus.lean#L22) · [同文件:185](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/ExistsCanonicalAcrisToBdRPlus.lean#L185)

因为 $R_m$ 完备分离，从 $A_{\rm cris}^0$ 到 $R_m$ 的映射可延至 $A_{\rm cris}$，做法是取任意整逼近序列在 $R_m$ 中的极限。对不同 $m$，延伸映射在稠密子环 $A_{\rm cris}^0$ 上与原投影相容，由分离性在全部 $A_{\rm cris}$ 上相容。取逆极限得到 $j$。而每个截断的值仍在 $R_m$，乘上 $\ell^m$ 后就进入 $B_m$，即 (1)。这一结果和整商的分离性正好给出[开圆盘取值时所用的闭性](%E6%80%8E%E6%A0%B7%E7%94%A8%E6%99%B6%E4%BD%93%E6%95%B4%E7%8E%AF%E6%9E%84%E9%80%A0%E5%8F%AF%E6%B1%82%E5%92%8C%E7%9A%84%E8%B5%8B%E8%8C%83%E5%91%A8%E6%9C%9F%E7%8E%AF.md)。

## Lean 对照

- `sat_pow`、`complete_quot`、`xi_sat` 消去 $\ell$ 并构造整商的极限。[FontaineXiPowSaturatedQuotientComplete.lean:20](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/FontaineXiPowSaturatedQuotientComplete.lean#L20) · [同文件:58](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/FontaineXiPowSaturatedQuotientComplete.lean#L58) · [同文件:108](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/FontaineXiPowSaturatedQuotientComplete.lean#L108)
- `bound` 给出截断层的统一指数，`range_complete` 将完备性传到分幂包络在各截断层的像，`exists_isCrisP` 从这些像取逆极限。[ExistsCanonicalAcrisToBdRPlus.lean:125](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/ExistsCanonicalAcrisToBdRPlus.lean#L125) · [同文件:185](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/ExistsCanonicalAcrisToBdRPlus.lean#L185) · [同文件:210](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/ExistsCanonicalAcrisToBdRPlus.lean#L210)

状态为源码对读。另行未重新编译。
