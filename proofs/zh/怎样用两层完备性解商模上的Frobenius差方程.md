# 怎样用两层完备性解商模上的 Frobenius 差方程

## 命题

设 $V$ 是加法群，$\ell$ 是素数。设 $D\subset M\subset V$ 为子群，要求 $M,D$ 都在 $V$ 中对 $\ell$ 饱和，即 $\ell x$ 落在该子群时 $x$ 也落在其中。令 $\Phi:V\to V$ 为加法自同态，保持 $M,D$，并有一列递减子群 $F_0\supset F_1\supset\cdots$，满足 $\Phi(F_j)\subset F_{j+1}$。再假定：

1. 对每个 $y\in M$，存在 $n\ge0$、$d\in D$，使 $\Phi^n y-d\in F_0$。
2. 对每列 $f_i\in M\cap F_i$，存在 $s\in M$ 使每个 $k\ge0$ 均有 $s-\sum_{i<k}f_i\in F_k$。
3. 若 $x\in\bigcap_k(D+F_k)$，则 $x\in D+\ell V$。
4. 对每列 $x_i\in M$，存在 $w\in M$ 使 $w-\sum_{i<k}\ell^i x_i\in\ell^k V$ 对每个 $k\ge0$ 成立。若 $x\in\bigcap_k(D+\ell^k V)$，则 $x\in D$。

则 $\Phi-1:M/D\to M/D$ 是双射。前三级条件负责解决模 $\ell$ 的方程，最后一级负责把这些解组成一个整方程的解。

## 证明

先证单射。设 $z\in M$ 且 $(\Phi-1)z\in D$。因此 $\Phi^n z-z\in D$ 对所有 $n$ 成立。由条件 1，选 $d$ 使 $\Phi^n z-d\in F_0$。将这个差写成 $z$ 减去 $D$ 的某个元素，可知 $z\in D+F_0$。若 $z-d_k\in F_k$，则

$$
z-\big(\Phi d_k-(\Phi-1)z\big)=\Phi(z-d_k)\in F_{k+1},
$$

而括号内仍在 $D$，故 $z\in D+F_{k+1}$。归纳后由条件 3，得到 $z=d+\ell r$，$d\in D$。饱和性给出 $r\in M$ 与 $(\Phi-1)r\in D$，因为

$$
\ell(\Phi-1)r=(\Phi-1)z-(\Phi-1)d\in D.
$$

对 $r$ 重复，可以在任意模 $\ell^k$ 下用 $D$ 近似 $z$，最后由条件 4 得 $z\in D$。

再证满射。给定 $y\in M$，取 $n,d$ 使 $e=\Phi^n y-d\in F_0$。因 $\Phi$ 使过滤升一级，$\Phi^i e\in F_i$ 对每个 $i$ 成立，且皆在 $M$。用条件 2 取 $s\in M$，它模 $F_k$ 同于前 $k$ 项的和。记该部分和为 $s_k$，则

$$
(\Phi-1)s_k=\Phi^k e-e.
$$

所以 $(\Phi-1)s+e\in F_k$ 对所有 $k$ 成立。由条件 3，存在 $d'\in D,r\in V$ 使 $(\Phi-1)s+e=d'+\ell r$。

令 $t=\sum_{i<n}\Phi^i y$，则 $(\Phi-1)t=\Phi^n y-y$。取 $z_0=-t-s$，得到

$$
y-(\Phi-1)z_0=d+d'+\ell r .
\tag{1}
$$

左侧与 $d+d'$ 都在 $M$，故饱和性给出 $r\in M$。这就得到模 $\ell$ 的一步解。

依次对 $y$ 和每一步新出现的 $r$ 应用 (1)。会得到 $z_i\in M,\ d_i\in D$，使

$$
y-(\Phi-1)\sum_{i<k}\ell^iz_i
      -\sum_{i<k}\ell^i d_i \ \in\ell^k V
$$

对每个 $k$ 成立。用条件 4 取 $w\in M$ 与各个 $\sum_{i<k}\ell^iz_i$ 在模 $\ell^k V$ 下相等。因为 $\Phi-1$ 是加法映射，改用 $w$ 后上式仍成立，于是 $y-(\Phi-1)w\in D+\ell^k V$ 对每个 $k$ 成立。再次用条件 4 得到 $y-(\Phi-1)w\in D$。这就是满射。

在工程中，第一层过滤在模 $\ell$ 的环上按分圆参数幂取近似。实际使用的 $\Phi$ 是一个矩阵乘逐项 Frobenius 的算子。[从标量到 étale 模的对应](%E4%B8%BA%E4%BB%80%E4%B9%88%E5%9B%BA%E5%AE%9A%E5%91%A8%E6%9C%9F%E5%95%86%E9%87%8C%E7%9A%84Frobenius%E5%87%8F%E4%B8%80%E5%8F%AF%E9%80%86.md)另篇说明怎样验证其收缩条件。

## Lean 对照

- `sub_one_bijective_quotient_of_topNilpotent` 用 `step` 对固定类逐个除以 $\ell$，`step1` 对任意元素先用几何级数解模 $\ell$ 的方程，再拼成完整解。[SubOneBijectiveQuotientOfTopNilpotent.lean:5](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/SubOneBijectiveQuotientOfTopNilpotent.lean#L5)

状态为源码级推导。另行未重新编译。
