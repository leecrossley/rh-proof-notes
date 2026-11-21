# 为什么大的二进导子能分开辅助 Frobenius 值

**命题。** 设 $O$ 为任意整环，$n,a$ 为非负整数，$\xi$ 为模 $2^n$ 的本原 $O$-值 Dirichlet 特征。对任意奇整数 $v>1$ 及任意正奇整数 $u$，有

$$
\xi(v)^{2^a u}=1\quad\Longrightarrow\quad 2^n< v^2\,2^a .
$$

这个初等界用于 [秩四数据的 Frobenius 分离](%E6%80%8E%E6%A0%B7%E4%B8%BAII%E7%B1%BB%E5%92%8CIII%E7%B1%BB%E6%9E%84%E9%80%A0%E7%A7%A9%E5%9B%9B%E5%8F%82%E8%80%83%E6%95%B0%E6%8D%AE.md)。若要在 $v$ 处保证一个乘积特征不等于 $1$，先取共同幂消去其他因子，再用 $v^2 2^a\le2^n$ 排除此等式。

## 证明

若 $n\le1$，则 $2^n\le2< v^2 2^a$。设 $n\ge2$。模 $2^n$ 换模至 $2^{n-1}$ 的单位群同态，其核为 $1$ 与 $1+2^{n-1}$。若 $\xi(1+2^{n-1})=1$，则 $\xi$ 经过更小的模数，与本原性矛盾。

令 $s=v_2(v^2-1)\ge3$。用两个简单事实。若 $z\equiv1\pmod4$ 且 $z>1$，则平方让 $v_2(z-1)$ 增加 $1$，因为 $z^2-1=(z-1)(z+1)$ 且 $v_2(z+1)=1$。若 $u$ 为正奇数，则取 $u$ 次幂保持这个赋值，因为 $(z^u-1)/(z-1)$ 是 $u$ 个奇数之和。于是

$$
v_2\big((v^2)^{2^a u}-1\big)=s+a .
$$

若 $s+a<n$，对 $z=(v^2)^{2^a u}$ 再平方 $n-1-s-a$ 次，就得到一个与 $1+2^{n-1}$ 模 $2^n$ 合同的数。另一方面 $z$ 是 $v^{2^a u}$ 的平方，假设 $\xi(v)^{2^a u}=1$，所以 $\xi$ 在这个数上等于 $1$。这与本原性矛盾。因此 $n\le s+a$，且 $2^s\le v^2-1<v^2$，推出所求。

## 本原奇特征及低导子扭曲

若 $n\ge3$、$O$ 含有一个本原 $2^{n-2}$ 次单位根 $\zeta$，便可以构造模 $2^n$ 的本原奇特征。事实上，$5$ 在模 $2^n$ 中的阶是 $2^{n-2}$，由上面平方的赋值公式用于 $5$ 得到。它的幂均为 $1\bmod4$，恰好遍历全部这样的单位；乘 $-1$ 得到另一类单位。因此每个单位可唯一写成 $(-1)^\epsilon 5^j$，取值设为 $(-1)^\epsilon\zeta^j$。当 $n=3$ 时论证仍适用。若 $O$ 特征为 $2$，给定的本原 $2^{n-2}$ 次单位根假设无法满足。因 $5^{2^{n-3}}$ 是 $1+2^{n-1}$ 模 $2^n$ 的类，所得特征在核上非平凡，故本原；在 $-1$ 上为 $-1$。

再取任一导子为 $2^c$ 且 $c<n$ 的特征 $\eta$。它的本原特征可拉回模 $2^n$。它在上面换模的核上平凡，故与本原 $\xi$ 的乘积在核上仍非平凡，导子仍是 $2^n$。因此乘低导子二进特征可以修改奇偶性且不会降低实际导子。

## Lean 对照

- [`two_pow_lt_sq_mul_of_primitive_char_pow_eq_one`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/TwoPowLtSqMulOfPrimitiveCharPowEqOne.lean#L61)。源码把平方和奇数幂的赋值直接写成 $1+2^s$ 乘奇因子的表达式。
- [`exists_primitive_odd_dirichletCharacter_two_pow`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/ExistsPrimitiveOddDirichletCharacterTwoPow.lean#L16) 的接口假设存在全部所需的 $2^n$ 次单位根，取到的根的实际阶为 $2^{n-2}$。
- [`exists_primitive_two_pow_twist_mul`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/ExistsPrimitiveTwoPowTwistMul.lean#L3)。允许 $\eta$ 最初给在任意模数 $N$ 上，结论的取值等式对与 $2N$ 互素的整数成立。本篇为发布版源码对照。
