# 怎样把各处放宽的条件加到 Selmer 长度上

## 命题

设 $\mathcal O$ 是交换环，$G$ 是群，$M$ 是带 $G$ 线性作用的 $\mathcal O$-模。可使用代数或连续余闭链，只要以下 $\mathcal O$-线性限制映射都已定义。令 $H$ 为 $\mathcal O$-模，$\Psi\colon H\to Z^1(G,M)$ 为线性映射，$B^1(G,M)\subseteq Z^1(G,M)$ 为余边界，$H^1=Z^1/B^1$。用 $[\Psi h]$ 表示 $\Psi h$ 的上同调类。给定 $\mathcal O$-子模 $Q\subseteq H^1(G,M)$，以及有限指标集 $I$，每个 $w\in I$ 有子群 $D_w\subseteq G$ 和局部条件 $F_w\subseteq A_w\subseteq H^1(D_w,M)$。设

- 对所有 $h\in H$，$[\Psi h]\in Q$，且 $[\Psi h]|_{D_w}\in A_w$ 对所有 $w\in I$ 成立。
- 满足全部原始局部条件的子模

$$
S_F=\{\xi\in Q:\xi|_{D_w}\in F_w\text{ 对所有 }w\in I\}
$$

  长度至多 $s$。
- $\operatorname{length}_{\mathcal O}(A_w/F_w)\le b_w$。另给出 $\operatorname{length}\ker\Psi\le L$，以及
  $\operatorname{length}(\operatorname{im}\Psi\cap B^1(G,M))\le B$。

则

$$
\operatorname{length}_{\mathcal O} H\le L+B+s+\sum_{w\in I} b_w .
\tag{1}
$$

各长度及上界允许无限值。

## 证明

先用放宽条件定义

$$
S_A=\{\xi\in Q:\xi|_{D_w}\in A_w\text{ 对所有 }w\in I\}.
$$

将 $\xi\in S_A$ 送到各 $\xi|_{D_w}\bmod F_w$，得到映射
$S_A\to\bigoplus_{w\in I}A_w/F_w$。
它的核恰是 $S_F$，所以有单射 $S_A/S_F\hookrightarrow\bigoplus_w A_w/F_w$。由短正合列的长度可加性，

$$
\operatorname{length}S_A
\le \operatorname{length}S_F+\sum_w\operatorname{length}(A_w/F_w)
\le s+\sum_w b_w.
$$

再对 $H\overset{\Psi}{\longrightarrow} Z^1(G,M)\longrightarrow H^1(G,M)$ 使用长度可加性。第一次要分出 $\ker\Psi$，第二次要分出 $\operatorname{im}\Psi\cap B^1$。剩下的最终像包含在 $S_A$，故长度至多 $\operatorname{length}S_A$。将三部分长度相加得 (1)。

## 在整体格指数中的使用

$H$ 取 $\operatorname{Hom}_A(N,M_c)$，其中 $N$ 是列关系模，$M_c$ 是好点处第 $c$ 块的商格。映射 $\Psi$ 将同态在 $y(g)$ 上的值视作同一个群的余闭链。于是三份代价性质不同。

- $L$ 来自同态在 $Y$ 上消失时，列生成元还有多少种选择。各块用对应的列关系估计。
- $B$ 控制余边界。零号块和 $c\ge2$ 用[两份分母的消去式](%E4%B8%BA%E4%BB%80%E4%B9%88%E4%BD%99%E8%BE%B9%E7%95%8C%E6%9C%80%E5%A4%9A%E5%B8%A6%E8%B5%B0%E4%B8%A4%E4%BB%BD%E5%9D%97%E9%97%B4%E5%88%86%E6%AF%8D.md)，分别至多 $2r\operatorname{ord}(\delta_{\mathcal O})$ 和 $2\operatorname{ord}(\delta_{\mathcal O})$。一号块为平凡作用，取 $B=0$。
- $s$ 是严格局部条件下的全局上界。零号块取原表示的 Selmer 长度。一号块通过不分歧的整体特征取得类数赋值。高次块通过分圆负扭曲取得一阶局部化核长度。三者各自需要检验严格条件。列上通常直接用 $F_w$，因此 $b_w=0$。需要放宽的行条件和指定分歧处决定 $\sum b_w$。

这一节解释为什么整体式用相加的方式记录每一处损失。各块的 $L$ 和 $s$ 有另外的数学证明。

## 源码对照

- `selRelax` 先按各局部条件映到商，`blockRhoAbs` 应用这一步并对余闭链、余边界、上同调像分解长度。[LengthEqKerAddRange.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/LengthEqKerAddRange.lean) · [LengthKerSmulLe.lean:147](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/LengthKerSmulLe.lean#L147)
- `blockTrivAbs` 给平凡作用下不计余边界的情形。[BlockChiOneTriv.lean:35](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/BlockChiOneTriv.lean#L35)

本篇为源码对读。正文完整证明抽象的不等式 (1)，此不等式的 $L,B,s,b_w$ 仍需从工程中的逐块论证输入。
