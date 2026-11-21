# 怎样把有理的 Herr 提升改成有统一代价的整提升

## 命题

设 $O$ 为交换环，$A$ 为交换 $O$-代数，$p$ 为素数，$X,Q\in A$，$M\ge0$。对 $i=0,1,2$，设 $D_i$ 为 $A$-模，$N_i\subset D_i$ 为子模，$\varphi_i,\gamma_i$ 是交换的半线性算子，所用的两个系数环自同态在 $O$ 上是恒等。假定乘 $X$ 单射，乘 $Q$ 双射，系数环上 $\varphi_A(X)=Xv$，且

$$
Q^M\varphi_i(N_i)\subset N_i,\qquad
(\gamma_i-1)N_i\subset XN_i,\qquad
(\gamma_i-1)U_i\subset XU_i,\quad U_i=\{y:Q^My\in N_i\}.
$$

定义允许的一次项为 $U_i\times XN_i$，二次项为 $XU_i$，微分

$$
d_{0,i}(x)=((\varphi_i-1)x,(\gamma_i-1)x),\qquad
d_{1,i}(y,z)=(\gamma_i-1)y-(\varphi_i-1)z.
$$

设 $\iota:D_0\to D_1,\ F:D_1\to D_2$ 是 $A$-线性映射，保持 $N_i$ 并与两算子相容。再假定 $\iota$ 单射，$\ker F=\operatorname{im}\iota$，而 $\iota^{-1}(N_1)=N_0$。给定整数 $e\ge0$ 和 $c\in O$，假设：

1. $p^eN_2\subset F(N_1)$。
2. 对任意一次余闭链 $h$ 属于 $U_2\times XN_2$，存在 $k\ge0$ 及一次余闭链 $h_1$ 属于 $U_1\times XN_1$，使 $Fh_1=p^kh+d_{0,2}(x)$，其中 $x\in N_2$。这就是工程的 `RatSurj` 条件，含义是允许先乘某次 $p$ 幂再在上同调中提升。
3. 若 $\omega\in XU_0$ 的某个 $p$ 幂倍数是允许的一次项的微分，则 $c\omega$ 也是允许的一次项的微分。

那么对每个 $h$ 如上，存在 $h^\ast\in U_1\times XN_1$，满足 $d_{1,1}(h^\ast)=0$，且 $Fh^\ast=cp^e h$ 逐坐标相等。

## 证明

先说明整性怎样沿 $\iota$ 传回。若 $\iota(w)\in U_1$，则 $\iota(Q^M w)\in N_1$，由饱和性有 $w\in U_0$。若 $\iota(w)=Xt$，则 $XF(t)=0$，所以 $F(t)=0$。写 $t=\iota(t_0)$，利用 $\iota$ 单射便有 $w=Xt_0$。若 $t$ 在 $U_1$ 或 $N_1$ 中，刚才的饱和性保证 $t_0$ 相应在 $U_0$ 或 $N_0$ 中。因此在任何次数上，只要允许的项落入 $\iota(D_0)$，就可以传回为同次数的允许项。

给定 $h=(y,Xn)$，其中 $y\in U_2,n\in N_2$。先提升 $p^eQ^My$ 与 $p^e n$，分别取 $a,b\in N_1$ 作原像。取 $\widetilde y=Q^{-M}a$；这个符号表示乘 $Q^M$ 的逆映射。于是 $\widetilde h=(\widetilde y,Xb)$ 是允许的一次项，$F\widetilde h=p^e h$。它的微分在 $\ker F$ 中，形如 $\iota(\omega)$。而

$$
d_{1,1}(\widetilde y,Xb)
  =X\bigl(u-v\varphi_1(b)+b\bigr),\qquad
Xu=(\gamma_1-1)\widetilde y,\quad u\in U_1.
$$

括号属于 $U_1$，因为 $Q^M\varphi_1(b)\in N_1$。所以上一段保证 $\omega\in XU_0$。这就是任意坐标提升后产生的缺陷。

再用第 2 条取 $k,h_1,x$。第 1 条给出 $m\in N_1$，使 $F(m)=p^ex$。令

$$
h_{\mathrm{cl}}=p^e h_1-d_{0,1}(m).
$$

由于 $\varphi_1,\gamma_1$ 交换，$d_{1,1}d_{0,1}=0$，所以它是允许的一次余闭链。其像为 $p^{k+e}h$。于是 $p^k\widetilde h-h_{\mathrm{cl}}$ 属于 $\ker F$，可写成 $\iota(\alpha)$；逐项应用传回整性的结论，有 $\alpha\in U_0\times XN_0$。求微分得到

$$
d_{1,0}\alpha=p^k\omega.
$$

所以 $\omega$ 确实是被某个 $p$ 幂消去的二次障碍。

第 3 条给出允许的一次项 $\beta$，满足 $d_{1,0}\beta=c\omega$。取

$$
h^\ast=c\widetilde h-\iota(\beta).
$$

它是一次余闭链，且 $\iota(\beta)$ 的像为零，所以 $Fh^\ast=cp^eh$。结论不带第 2 条中随类变化的 $k$。

## Lean 对照

- `CokerKilled`、`RatSurj`、`Lifts` 分别指定格原像代价、有理上同调原像以及带统一次数的精确原像。[Statement.lean:158](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CoboundaryTransfers/Statement.lean#L158)
- `cocycleLiftOfExact_holds` 先构造两个坐标原像，再由 $\ker F$ 上的二次余边界校正。[DiffOneSmulOfTower.lean:83](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CoboundaryTransfers/GammaStableTransfers/DiffOneSmulOfTower.lean#L83)
- `lift_wach` 取[显式的二次障碍消去标量](%E6%80%8E%E6%A0%B7%E7%94%A8%E5%88%86%E6%AC%A1%E4%B8%8E%E5%A4%9A%E9%A1%B9%E5%BC%8F%E6%B6%88%E5%8E%BBHerr%E5%A4%8D%E5%BD%A2%E7%9A%84%E4%BA%8C%E6%AC%A1%E9%9A%9C%E7%A2%8D.md) $c=R(0)C_\gamma$，给出 $Fh^\ast=p^eR(0)C_\gamma h$。[WachBridges.lean:23](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CoboundaryTransfers/WachBridges.lean#L23)

状态为源码级推导。另行未重编译。
