# 怎样排序各点的根并把函数下降到原 Hecke 环

## 命题

设 $\mathcal O$ 为整环，分式域为 $K$。设 $X$ 为非空有限集、$\mathbb T\subseteq\mathcal O^X$ 为子代数。取首一 $P(T)\in\mathbb T[T]$，次数 $t\ge0$。假设每个 $x\in X$ 的评价 $P_x(T)\in\mathcal O[T]$ 有 $t$ 个互异、都在 $\mathcal O$ 的根。

令 $X'$ 为所有 $(x,\lambda_0,\ldots,\lambda_{t-1})$，其中 $(\lambda_j)$ 是 $P_x$ 的根的一种排序。写 $p:X'\to X$ 为投影，$\lambda_j$ 也表示在 $X'$ 读出第 $j$ 根的函数。令 $\mathbb T'\subseteq\mathcal O^{X'}$ 由拉回的 $\mathbb T$ 及这些根函数生成。则有 $t!$ 个函数 $b_i\in\mathbb T'$，使得

1. $\mathbb T'$ 的每个函数都可写为 $\sum_i(a_i\circ p)b_i$，其中 $a_i\in\mathbb T$。
2. 对任意 $x\in X$，这些 $b_i$ 在纤维 $p^{-1}(x)$ 上的限制线性无关，甚至在 $K$ 上无关。

因此若 $f'\in\mathbb T'$ 在 $Z\subseteq X$ 的逆像以外消失，则表达式中每个 $a_i$ 都在 $Z$ 外消失。对任何 $\pi'\in p^{-1}(\pi)$，$f'(\pi')$ 属于原 Hecke 同余理想 $\mathfrak c_\pi$。

## 逐个添形式根

从一个交换环 $B$ 上的任意首一多项式 $P$ 开始。若次数 $t>0$，先作 $B_1=B[T]/(P)$，以 $u_0$ 表示 $T$ 的像。因为 $P$ 首一，$B_1$ 是秩 $t$ 的自由 $B$-模。于 $B_1[T]$ 中用 $T-u_0$ 除 $P$，余数为 $P(u_0)=0$，得到次数 $t-1$ 的首一商多项式。对商再做同样的步骤，直到次数零。

最终所得分裂代数 $U$ 有 $t$ 个形式根，作为 $B$-模自由且秩 $t(t-1)\cdots 1=t!$。若 $t=0$，取 $U=B$，自由秩为 $1$。这套构造也说明其泛性质：对于任意 $B$-代数中给定的一份有序分解 $P(T)=\prod_j(T-a_j)$，有唯一态射把形式根依次送到 $a_j$。存在性是逐个满足添根的关系。进入下一步时可消去首一因子 $T-a_0$，这个消去在交换环上也成立。唯一性因为这些根和 $B$ 生成 $U$。

现在令 $B=\mathbb T$。每个 $x'\in X'$ 给 $U\to\mathcal O$ 的评价，合在一起给 $U\to\mathcal O^{X'}$，其像恰为 $\mathbb T'$，因为形式根的像就是根函数、$\mathbb T$ 的像就是函数拉回。取自由基 $u_i$ 的像为 $b_i$，得第 1 点。

## 为什么每个纤维都独立

固定 $x\in X$，沿评价 $\mathbb T\to\mathcal O\to K$ 升系数。添根与这个操作可交换，因为每一步都用首一多项式取商及首一除法。第一次添根后，因 $P_x$ 的根互异，由中国剩余定理得到 $K[T]/(P_x)\simeq\prod_{j=0}^{t-1}K$。在一个因子上已选第一个根，剩余商多项式恰由其余根组成。继续做中国剩余分解，最后得到

$$
U\otimes_{\mathbb T}K\simeq \prod_{x'\in p^{-1}(x)} K .
$$

同构的每个坐标，正是按这份根排序作评价。于是自由基 $u_i$ 经此同构得到 $K$-基，意味着 $b_i$ 在该纤维上独立。第 2 点成立。这里无须假设不同 $x$ 的根互不相同。

最后令 $f'$ 在 $p^{-1}(X\setminus Z)$ 上为零。对每个 $x\notin Z$，第 2 点给所有 $a_i(x)=0$。故 $a_i(\pi)\in\mathfrak c_\pi$，从 $f'(\pi')=\sum_i a_i(\pi)b_i(\pi')$ 得结论。这是[同余理想的行列式构造](%E6%80%8E%E6%A0%B7%E7%94%A8%E4%B8%80%E4%B8%AA%E8%A1%8C%E5%88%97%E5%BC%8F%E6%8A%8A%E5%90%8C%E4%BD%99%E7%90%86%E6%83%B3%E7%9A%84%E9%95%BF%E5%BA%A6%E5%88%86%E7%BB%99%E5%90%84%E5%9D%97.md)所需的下降。

## 源码对照

- `splitAlg` 构造自由秩 $t!$ 的分裂代数及泛性质。`splitFibre` 用不同评价同态的线性无关性证明纤维评价矩阵非奇异。正文用逐步中国剩余分解给出同一个纤维事实。[SplitFibre.lean:139](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/SplitFibre.lean#L139) · [第 151 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/SplitFibre.lean#L151)
- `splitPts` 将分裂代数的基作为 $X'$ 上的函数，并核对生成与独立。`descent` 使用了两个性质。[SplitPts.lean:13](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/RamifiedBlockRings/RamifiedBlockProofs/SplitPts.lean#L13) · [VccSpan.lean:7](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/VccSpan.lean#L7)

本篇为源码对读。给定 $P$ 后，从添根到下降已证明。工程中 $P$ 来自互异根的角块矩阵，系数属于 Hecke 环由另一条行列式论证给出。
