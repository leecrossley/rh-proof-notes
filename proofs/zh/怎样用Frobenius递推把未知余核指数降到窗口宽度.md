# 怎样用 Frobenius 递推把未知余核指数降到窗口宽度

## 命题

令 $\ell$ 为素数，$O$ 为完备离散赋值环，$0\ne\ell\in\mathfrak m_O=(\varpi)$，$R=O[[U]]$。令 $\phi:R\to R$ 固定 $O$，且 $\phi(U)=(1+U)^\ell-1$。取任意 $s\ge1$，记

$$
X=(1+U)^{\ell^{s-1}}-1,\qquad
Q=\sum_{k=0}^{\ell-1}(1+U)^{k\ell^{s-1}},
$$

故 $\phi(X)=XQ$。取 $n\ge1$，以 $i\in\mathbb Z/n\mathbb Z$ 编号的理想 $\mathfrak a_i\subset R$，以及整数 $H,c\ge0$。假定

$$
U^c\in\mathfrak a_i,\qquad Q^H\mathfrak a_i\subset R\phi(\mathfrak a_{i-1})\qquad\text{对每个 }i .
$$

这里 $R\phi(\mathfrak a)$ 表示由 $\phi(\mathfrak a)$ 生成的 $R$-理想。则 $X^H\in\mathfrak a_i$ 对每个 $i$ 成立。工程中 $\mathfrak a_i$ 是第 $i$ 个 Wach 模余核的零化理想，$c$ 可随格满射变化，$H$ 则只依赖源表示的过滤窗口。

## 证明

设 $B_j=(1+U)^j$，$0\le j<\ell$。由[整幂级数环的 Frobenius 系数展开](%E4%B8%BA%E4%BB%80%E4%B9%88Frobenius%E7%9A%84%E7%B3%BB%E6%95%B0%E5%B1%95%E5%BC%80%E5%8F%AF%E4%BB%A5%E5%9C%A8%E6%95%B4%E5%B9%82%E7%BA%A7%E6%95%B0%E7%8E%AF%E9%87%8C%E5%AE%8C%E6%88%90.md)，每个 $y$ 可唯一写成 $\sum_j B_j\phi(z_j)$。对任意理想 $\mathfrak b$，在这个展开中有

$$
y\in R\phi(\mathfrak b)\quad\Longleftrightarrow\quad z_j\in\mathfrak b\text{ 对所有 }j .
$$

右推左直接成立。对另一方向，把 $y$ 写成 $\sum a_u\phi(b_u)$，其中 $b_u\in\mathfrak b$。把每个 $a_u$ 作上述展开，乘 $\phi(b_u)$ 后，坐标变成 $z_{j,u}b_u$，仍在 $\mathfrak b$。求和并用唯一性即可。

令 $\mathfrak b_i=(\mathfrak a_i:X^H)=\{y:X^Hy\in\mathfrak a_i\}$。若 $y\in\mathfrak b_i$，则

$$
\phi(X^H)y=Q^HX^Hy\in R\phi(\mathfrak a_{i-1}).
$$

写出 $y$ 的坐标 $z_j$。上式的坐标就是 $X^H z_j$。由前一段，这些坐标在 $\mathfrak a_{i-1}$，所以 $z_j\in\mathfrak b_{i-1}$。故

$$
\mathfrak b_i\subset R\phi(\mathfrak b_{i-1}).
\tag{1}
$$

假设某个 $\mathfrak b_{i_0}$ 是真理想。$R$ 是局部环，极大理想是 $(\varpi,U)$，因为幂级数可逆当且仅当其常数项可逆。于是 $\mathfrak b_{i_0}\subset(\varpi,U)$。若 $\mathfrak b_{i_0+m}\subset(\varpi,U^{m+1})$，由 (1) 得

$$
\mathfrak b_{i_0+m+1}\subset(\varpi,\phi(U)^{m+1})
\subset(\varpi,U^{m+2}).
$$

最后一处用掉 $\phi(U)\equiv U^\ell\bmod\varpi$ 和 $\ell(m+1)\ge m+2$。归纳得到 $\mathfrak b_{i_0+c}\subset(\varpi,U^{c+1})$。但 $U^c$ 在所有 $\mathfrak a_i$ 中，所以在所有 $\mathfrak b_i$ 中。它的第 $c$ 次系数为 $1$，不可能属于后一个理想。这与假设矛盾。所有 $\mathfrak b_i$ 都含 $1$，故所求成立。

## Lean 对照

- `exists_coords_mem` 检测 Frobenius 坐标，`colon_le_map` 在消去一个乘子后取得 (1)。`phi_mem_span` 抬升模 $\varpi$ 的消失次数。[XXPowMemOfQQPowMulMemMapPhi.lean:9](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/XXPowMemOfQQPowMulMemMapPhi.lean#L9) · [同文件:35](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/XXPowMemOfQQPowMulMemMapPhi.lean#L35) · [同文件:51](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/XXPowMemOfQQPowMulMemMapPhi.lean#L51)
- `XX_pow_mem_of_QQ_pow_mul_mem_map_phi` 从真理想开始传递纯 $U$ 的阶数，直到第 $c$ 次系数矛盾。[XXPowMemOfQQPowMulMemMapPhi.lean:80](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/XXPowMemOfQQPowMulMemMapPhi.lean#L80)
- `kills_of_cyclotomic` 将本篇理想结论用于 Wach 满射。[CokernelCrystallineSurjectionKilledByXPow.lean:329](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CokernelCrystallineSurjectionKilledByXPow.lean#L329)

状态为源码级推导。另行未重新编译。
