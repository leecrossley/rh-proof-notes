# 为什么固定周期商里的 Frobenius 减一可逆

## 命题

先给出工程使用的矩阵形式。令 $B$ 为交换环，含子环 $B^+$ 与 $E$，设 $\varphi$ 为保持两子环的环自同态，且固定整数。给定素数 $\ell$，取 $t\in B^+$，定义加法子群

$$
\mathcal F_j=t^jB^++\ell B\qquad(j\ge0).
$$

取 $\varphi$-稳定的子环 $S\subset B$ 含 $E$。假设：

- $\varphi(t)\in\mathcal F_2$。对每个 $q\in E$，某个 $t^c q\in\mathcal F_0$。
- $S,E$ 都在 $B$ 中对 $\ell$ 饱和。对每个 $k\ge0$ 及每列 $f_i\in S\cap\mathcal F_{i+k}$，可在 $S$ 内取和 $s$，满足 $s-\sum_{i<j}f_i\in\mathcal F_{j+k}$ 对每个 $j\ge0$ 成立。
- $\bigcap_j(E+\mathcal F_j)\subset E+\ell B$。任意 $y\in S$ 与 $k\ge0$ 都有 $y_0\in B$ 及 $r\ge0$ 使 $y-y_0\in\mathcal F_k$、$\varphi^r(y_0)\in E+\ell B$。
- $S$ 可容纳任意 $s_i\in S$ 的 $\sum_i\ell^is_i$，意义为每个前 $j$ 项与和的差属于 $\ell^jB$。并且 $\bigcap_j(E+\ell^jB)=E$。

对每个 $d\ge0$ 和 $P\in M_d(E)$，在 $S^d/E^d$ 上令 $\Phi$ 由 $x\mapsto P\varphi(x)$ 给出，$\varphi$ 逐分量作用。则 $\Phi-1$ 双射。工程取 $B=O\otimes_{\mathbb Z_\ell}W(\mathbb C_\ell^\flat)$，$B^+=O\otimes_{\mathbb Z_\ell}W(\mathcal O_{\mathbb C_\ell^\flat})$，$E$ 为 étale 系数环，$S=B^H$，$H$ 是到分圆群的限制映射的核。$t$ 是其中代表 $U$ 的分圆周期。这个具体选择的环条件在正文末尾列出 Lean 接口。

## 证明

在 $\mathcal F_j$ 中，等式 $x=t^j a+\ell b$ 等价于 $x$ 模 $\ell$ 是 $t^j$ 乘整环元素。因为 $\varphi(B^+)\subset B^+$、$\varphi(t)\in\mathcal F_2$，有

$$
\varphi(\mathcal F_j)\subset\mathcal F_{2j}.
$$

同样，若 $t^c q\in\mathcal F_0$，则 $q\mathcal F_{j+c}\subset\mathcal F_j$。取一个共同 $c$ 适用于 $P$ 的所有系数。对 $m\ge0$，设 $F_m=(\mathcal F_{m+c+1})^d$。因为

$$
2(m+c+1)-c\ \ge\ m+c+2,
$$

所以 $\Phi$ 将 $F_m$ 送到 $F_{m+1}$。$S^d,E^d$ 都被 $\Phi$ 保持。

要用[两层完备性的抽象引理](%E6%80%8E%E6%A0%B7%E7%94%A8%E4%B8%A4%E5%B1%82%E5%AE%8C%E5%A4%87%E6%80%A7%E8%A7%A3%E5%95%86%E6%A8%A1%E4%B8%8A%E7%9A%84Frobenius%E5%B7%AE%E6%96%B9%E7%A8%8B.md)，还需证明任意 $y\in S^d$ 的某个迭代 $\Phi^r y$ 可落到 $E^d+F_0$。对 $y$ 各坐标分别选逼近 $y_{0,i}$，在 $\mathcal F_{c+1}$ 中逼近，并各选 $r_i$ 使 $\varphi^{r_i}(y_{0,i})\in E+\ell B$。由于 $\varphi$ 保持 $E+\ell B$，可把 $r_i$ 换成同一个 $r=\max_i r_i$。现在

$$
\Phi^r y_0=P\varphi(P)\cdots\varphi^{r-1}(P)\,\varphi^r(y_0)
       \in E^d+\ell B^d.
$$

另一方面 $y-y_0\in F_0$，所以 $\Phi^r(y-y_0)\in F_0$。相加即得 $\Phi^r y\in E^d+F_0$。当 $d=0$ 结论直接成立。滤过完备、交集闭性和 $\ell$-进拼接都可逐坐标应用。所有抽象引理的条件得证，于是 $\Phi-1$ 双射。

最后说明此矩阵形式怎样进入工程的 `DecW`。对 Galois 格 $T$，比较 $J:D(T)\to B\otimes_O T$ 把任一 $E$-基送到一个 $B$-基。这个基被 $H$ 逐向量固定，因为 $H$ 在分圆群的像为 $1$。因此 $(B\otimes T)^H$ 对应 $S^d$，$J(D(T))$ 对应 $E^d$。半线性的周期 Frobenius 在此基下恰为 $P\varphi$，其中 $P$ 由 $D(T)$ 的 Frobenius 给出。故在 $(B\otimes T)^H/J(D(T))$ 上，Frobenius 减一为双射。这说明周期层中的两类多余解都可控制。给定同余类能求出原像，两个原像的差若落在核中就来自 $D(T)$。

## Lean 对照

- `near_frob` 和 `near_mul_of_bound` 给出过滤翻倍和乘一个有分母系数时损失的 $c$ 阶。`semi_iterate` 展开矩阵迭代，`matrix_frob_sub_one_bijective` 套用抽象引理。[MatrixFrobeniusSubOneBijectiveModSubring.lean:24](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/MatrixFrobeniusSubOneBijectiveModSubring.lean#L24) · [同文件:31](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/MatrixFrobeniusSubOneBijectiveModSubring.lean#L31) · [同文件:67](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/MatrixFrobeniusSubOneBijectiveModSubring.lean#L67) · [同文件:97](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/MatrixFrobeniusSubOneBijectiveModSubring.lean#L97)
- `decompletion_matrix` 在实际周期环上验证这些输入，具体使用固定环的完备性、étale 像的闭性、从固定域对 Frobenius 完美化的逼近。`decW_of_matrix` 用周期基识别固定向量和模 $E$ 的关系。[DecompletionPhiSubOneBijective.lean:25](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/DecompletionPhiSubOneBijective.lean#L25) · [固定环完备性](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/GaloisFixedTensorWittCompletePiAdicModEll.lean#L50) · [系数像闭性](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/EtaleRingImageAddEllPiAdicClosed.lean#L111) · [Frobenius 完美化逼近](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/GaloisFixedTensorWittApproxFrobeniusPerfection.lean#L210) · [DecWOfMatrix.lean:40](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/DecWOfMatrix.lean#L40)

状态为源码级推导。另行未重新编译。抽象引理和矩阵步骤已展开。具体模型的[两种闭性](%E4%B8%BA%E4%BB%80%E4%B9%88%E5%9B%BA%E5%AE%9A%E5%91%A8%E6%9C%9F%E7%8E%AF%E5%92%8C%C3%A9tale%E5%83%8F%E5%9C%A8%E4%B8%A4%E7%A7%8D%E7%B2%BE%E5%BA%A6%E4%B8%8B%E9%83%BD%E9%97%AD%E5%90%88.md)和[固定域逼近](%E4%B8%BA%E4%BB%80%E4%B9%88%E5%88%86%E5%9C%86%E5%A1%94%E7%9A%84%E5%9B%BA%E5%AE%9A%E5%80%BE%E6%96%9C%E5%85%83%E7%B4%A0%E5%8F%AF%E7%94%A8%E6%A0%B9%E7%9A%84%E5%A4%9A%E9%A1%B9%E5%BC%8F%E9%80%BC%E8%BF%91.md)另有证明。
