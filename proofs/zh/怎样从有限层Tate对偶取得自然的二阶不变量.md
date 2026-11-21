# 怎样从有限层 Tate 对偶取得自然的二阶不变量

## 命题

设 $p$ 是素数，$K/\mathbb Q_p$ 与 $L/\mathbb Q_p$ 为有限扩张。令 $G=G_K$，$O=\mathcal O_L$，$\varpi$ 为 $O$ 的统一化元。对每个有限生成的 $O$-模 $M$ 赋予其 $\varpi$-进拓扑，令 $G$ 在 $M$ 上作用平凡。用 $M(1)=M\otimes_{\mathbb Z_p}\mathbb Z_p(1)$ 表示分圆扭曲，就是让 $G$ 按 $p$-进分圆特征乘在 $M$ 上。取连续余链定义的连续上同调。使用有限系数的局部 Tate 对偶及其有限性，则存在自然的 $O$-线性同构

$$
H^2(G,M(1))\simeq M .
$$

这里自然性指，对任何 $O$-线性连续映射 $M\to M'$，两边的同构与它诱导的映射交换。

## 证明

先处理有限模 $A$。局部 Tate 对偶把 $H^2(G,A(1))$ 与

$$
H^0\bigl(G,\operatorname{Hom}(A(1),\mathbb Q_p/\mathbb Z_p(1))\bigr)
$$

配成完美对偶，值在 $\mathbb Q_p/\mathbb Z_p$。两个 $(1)$ 抵消，里面就是 $\operatorname{Hom}(A,\mathbb Q_p/\mathbb Z_p)$，作用平凡。有限阿贝尔 $p$-群到其双对偶的评价映射是同构，可在循环群上逐项验证。故 $H^2(G,A(1))\simeq A$，对 $A$ 是自然的。$O$-线性随自然性而来，因为 $O$ 的每个元素给 $A$ 一个系数自同态。[Milne，Arithmetic Duality Theorems，I.2，Theorem 2.8](https://www.jmilne.org/math/Books/ADT.pdf#page=39)

令 $A_n=M/\varpi^nM$，$n\ge1$。每个 $A_n$ 有限，且 $M\simeq\varprojlim_n A_n$。下面证明自然映射

$$
H^2(G,M(1))\longrightarrow\varprojlim_n H^2(G,A_n(1))
\tag{1}
$$

是同构。一个连续余链到 $M(1)$ 等价于一列相容的有限层连续余链。有限层的系数商映射有集合截面，截面连续，故每个有限层余链都能连续地提升到下一层作为余链。微分与系数约化交换。

对 (1) 的满射性，给定相容的一列二阶类。依次选代表二次余闭链 $z_n$。若已选第 $n$ 层代表，下一层任一代表约化后与它相差一个一次余链的微分。把该一次余链提升到下一层并减掉其微分，便使两层代表精确相容。递推后相容的 $z_n$ 构成到 $M(1)$ 的连续二次余闭链。

对单射性，设 $z$ 的每个 $z_n$ 都是余边界。令 $B_n$ 为满足 $db=z_n$ 的一次余链集合，再将相差一次余边界的 $b$ 视为同一个元素。所得集合非空，任两元素之差是 $H^1(G,A_n(1))$ 的元素。因此它是这个有限群上的平移空间，特别是有限集合。约化给出这些集合的转移映射。一列有限非空集合的逆极限非空。事实上在乘积的每个有限层限制中可从最高一层倒推，得到有限交性质，再用紧致性。取一列相容的余链类，依次选实际代表。下一层代表约化后与已选代表相差一个零次余链的微分。提升该零次余链并减掉其微分即可。相容的一次余链给出 $z$ 的原像，所以原类为零。

把第一段的有限层自然同构取逆极限，再用 (1)，得到 $H^2(G,M(1))\simeq\varprojlim_n A_n=M$。每个箭头都是自然的。特别地，若 $M\hookrightarrow M'$ 单射，$H^2(G,M(1))\to H^2(G,M'(1))$ 也单射。

## Lean 对照

- `GlobalTheory.FreeTwistH2.exists_free_H2_twist` 从模 $p^n$ 的相容基本余闭链构造 $H^2(G,O(1))$ 的生成元。`bijective_phi_quot_pow` 验证模 $\varpi^k$ 情形。[ExistsGeneratorH2Twist.lean:40](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsGeneratorH2Twist.lean#L40) · [EveryGeneratorH2Twist.lean:14](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/EveryGeneratorH2Twist.lean#L14)
- `natInvIso_of_localTateDuality` 将有限生成 $O$-模分成自由部分及循环扭结部分，由各项的一致生成元给自然性。正文把同一有限层到整模的过渡直接写成逆极限的余链论证。[NatInvIsoOfLocalTateDualityCyclotomicTwist.lean:15](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/NatInvIsoOfLocalTateDualityCyclotomicTwist.lean#L15)
- `h2Map_injective_statement` 在[杯积从大模回到小模](%E6%9D%AF%E7%A7%AF%E5%9C%A8%E5%A4%A7%E6%A8%A1%E4%B8%AD%E6%B6%88%E5%A4%B1%E5%90%8E%E6%80%8E%E6%A0%B7%E5%9B%9E%E5%88%B0%E5%B0%8F%E6%A8%A1.md)时使用单射结论。[H2MapInjectiveStatement.lean:14](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/CupProductVanishing/CupProductProofs/H2MapInjectiveStatement.lean#L14)

状态为源码级推导。另行未重新编译。外部输入是有限系数局部 Tate 对偶和 $H^1$ 的有限性。
