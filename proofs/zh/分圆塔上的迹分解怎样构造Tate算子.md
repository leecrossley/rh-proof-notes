# 分圆塔上的迹分解怎样构造 Tate 算子

## 命题

设 $\ell$ 为素数，$K_0/\mathbb Q_\ell$ 为有限无分歧扩张。对 $j\ge1$ 记 $K_j=K_0(\mu_{\ell^j})$，其整数环记作 $O_j$。令 $O_\infty$ 为 $\bigcup_j O_j$ 在 $\mathbb C_\ell$ 中的闭包。对 $j\ge1$，令 $X_j$ 为所有 $i>j$ 的分量

$$
X^{(i)}=\sum_{a=1}^{\ell-1}\zeta_i^a O_{i-1},\qquad
\zeta_i\text{ 是本原 }\ell^i\text{ 次单位根}
$$

的有限和在 $\mathbb C_\ell$ 中的闭包。换一个本原根不改变这个模，因为其幂可按指数模 $\ell$ 分组，$\zeta_i^\ell$ 属于 $O_{i-1}^\times$。

首先有整数分解 $O_\infty=O_j\oplus X_j$，且 $X_j\cap K_j=0$。第二，给定 $g$ 固定 $K_j$ 且满足 $v_\ell(\chi(g)-1)=j$。若 $\ell=2$，另要求 $j\ge2$。取任意本原 $\ell$ 次单位根 $\zeta$，置 $\pi=\zeta-1$。则存在 $O_j$-线性的 $S:X_j\to X_j$，使对每个 $x\in X_j$

$$
(g-1)Sx=S(g-1)x=\pi x,\qquad
|Sx|_\ell\le\ell |x|_\ell .
\tag{1}
$$

绝对值取 $|\ell|_\ell=\ell^{-1}$ 的归一化。这是[生成元高层扰动](%E5%88%86%E5%9C%86%E7%94%9F%E6%88%90%E5%85%83%E7%9A%84%E4%BD%99%E4%B8%8D%E5%8F%98%E9%87%8F%E4%B8%BA%E4%BB%80%E4%B9%88%E7%94%B1%E6%9D%83%E5%B7%AE%E4%B9%98%E7%A7%AF%E6%B6%88%E5%8E%BB.md)所用的算子。

## 从有限层的整数基到闭补空间

取相容的本原根 $\zeta_i$，满足 $\zeta_i^\ell=\zeta_{i-1}$。每层 $K_i/K_0$ 全分歧，$\zeta_i-1$ 为素元。理由是 $\Phi_{\ell^i}(1+X)$ 是以 $\ell$ 为素元的 Eisenstein 多项式，首一，常数为 $\ell$，模 $\ell$ 为 $X^{\ell^{i-1}(\ell-1)}$。对 $i\ge2$ 的相邻两层，$(1+X)^\ell-\zeta_{i-1}$ 在 $O_{i-1}$ 上又为 Eisenstein。因而 $\zeta_i-1$ 的前 $\ell$ 个幂为 $O_i$ 的 $O_{i-1}$ 基。可直接看其张成性：在这组域基下，$\ell$ 个项的赋值若有限，模相对分歧指数 $\ell$ 各异，故和的最低赋值由其中一项唯一实现。和为整数便迫使每个系数为整数。

用二项式作三角换基，$1,\zeta_i,\ldots,\zeta_i^{\ell-1}$ 也是这组整数基。对此基取 $K_i/K_{i-1}$ 的归一化迹，即 $\ell^{-1}\operatorname{Tr}$。$\zeta_i^a$ 的各共轭是 $\zeta_i^a$ 乘上全体 $\ell$ 次单位根的 $a$ 次幂，所以对 $1\le a<\ell$ 迹为零，而归一化迹在 $O_{i-1}$ 上为恒等。于是 $O_i=O_{i-1}\oplus X^{(i)}$，且归一化迹保持整数。

对任意 $m\ge j$，依次下取归一化迹，得投影 $P_j:O_m\to O_j$。这些投影在 $m$ 的共同部分一致，核是 $X^{(j+1)}\oplus\cdots\oplus X^{(m)}$。它们与以后要用的 $g$ 相交换，因为塔上各层稳定且域迹与自同构相容。

为了延拓，若 $x\in O_m$ 且 $|x|_\ell\le\ell^{-k}$，$k\ge0$，则 $\ell^{-k}x\in O_m$，所以 $\ell^{-k}P_jx=P_j(\ell^{-k}x)\in O_j$。因此 $P_j$ 一致连续，延拓到 $O_\infty$，值在完备的 $O_j$ 中。对序列 $x_m\to x$ 取极限可知 $x-P_j x\in X_j$，而 $P_j$ 在 $X_j$ 恒为零，在 $O_j$ 恒为恒等，所以分解唯一。若 $x\in X_j\cap K_j$，由 $X_j$ 在单位球中知 $x\in O_j$，所以 $x=0$。各 $X^{(i)}$ 对乘 $O_j$ 和 $g$ 都稳定，因为 $g(\zeta_i)=\zeta_i^b$ 且指数 $b$ 为单位。因此闭包也稳定。

## 解有限层上的方程

先在有限和的补空间中取一个生成项 $x=\zeta_i^a c$，其中 $i>j$、$1\le a<\ell$、$c\in O_{i-1}$。置 $b=i-j-1$。由幂差赋值，$g^{\ell^{b}}$ 的分圆特征与 $1$ 的差赋值为 $j+b=i-1$。所以它固定 $K_{i-1}$，并将 $\zeta_i^a$ 乘一个本原 $\ell$ 次根 $\eta$。本原 $\ell$ 次根之差 $1-\eta$ 和 $1-\zeta$ 都是 $K_1$ 的素元，故 $\pi/(\eta-1)\in O_1^\times$。令

$$
z=\zeta_i^a\,\frac{\pi}{\eta-1}\,c,\qquad
y=\sum_{k=0}^{\ell^b-1}g^k z .
$$

则 $y\in X^{(i)}$，而

$$
(g-1)y=g^{\ell^b}z-z=(\eta-1)z=\pi x .
$$

因此在代数的有限和补空间上，对每个 $x$ 都能解出 $Sx$。

解在该空间中唯一。若某个有限层的元素被 $g$ 固定，它属于 $K_j$。因为 $g$ 在各有限商 ${\rm Gal}(K_m/K_j)$ 中具有全部群阶 $\ell^{m-j}$，这也是幂差赋值给出的。再与补空间相交就只剩零。因此解的加性和 $O_j$-线性成立，而且 $S(g-1)x=\pi x$，因为两边在施以 $g-1$ 后相等。

## 控制分母并延拓

若代数补空间元素 $x$ 有 $|x|_\ell\le\ell^{-k}$，则 $\ell^{-k}x$ 在同一有限层的整数补空间中。其整数性来自范数，补空间条件来自归一化迹的线性性。将刚才的解施于 $\ell^{-k}x$，再乘 $\ell^k$，由唯一性得 $|Sx|_\ell\le\ell^{-k}$。当 $x\ne0$ 时，取使 $\ell^{-k}$ 刚好不小于 $|x|_\ell$ 的整数幂，可得 $|Sx|_\ell\le\ell |x|_\ell$。$x=0$ 时自然成立。

利用加性得到差值同样有这个范数界。因此 $S$ 从有限和唯一连续延拓到 $X_j$，且其像还在该闭空间。两个算子恒等式和 $O_j$-线性也经极限保留。这便得到 (1)。

## 源码对照

- `Xlev_form`、`Xlev_inter`、`step` 识别一个层差、证明交为零并作单层分解。`tate_decomposition` 将其传到完备环。[TateDecompositionCompletedCyclotomicIntegers.lean 第 184 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TateDecompositionCompletedCyclotomicIntegers.lean#L184) · [第 251 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TateDecompositionCompletedCyclotomicIntegers.lean#L251) · [第 371 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TateDecompositionCompletedCyclotomicIntegers.lean#L371)
- `gen_root`、`solve_alg` 通过本原根和望远镜和解决代数方程。`est_pow`、`exists_tate_operator_bound` 通过整数幂尺度得到范数界并完成延拓。[ExistsTateOperatorLevelComplement.lean 第 185 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsTateOperatorLevelComplement.lean#L185) · [第 216 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsTateOperatorLevelComplement.lean#L216) · [第 296 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsTateOperatorLevelComplement.lean#L296) · [第 405 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsTateOperatorLevelComplement.lean#L405)

本篇为源码对读。用归一化迹统一表示有限层投影，是对源码逐层分解的数学重述。
