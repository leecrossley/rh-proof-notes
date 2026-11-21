# Assembling the small-index second cohomology bound

[Chinese proof](../zh/%E5%B0%8F%E6%8C%87%E6%A0%87%E7%9A%84%E4%BA%8C%E9%98%B6%E4%B8%8A%E5%90%8C%E8%B0%83%E7%95%8C%E6%80%8E%E6%A0%B7%E7%94%B1%E8%AE%A1%E6%95%B0%E5%90%88%E6%88%90.md)

## Statement

Let $L$ be totally imaginary of degree $n$ and absolute discriminant $D$, containing $\mu_\ell$ for a prime $\ell$ or $\mu_4$ when $\ell=2$. For $e\ge1$ write $s=s(L,\ell,e)$ for the length of the localization kernel for $(\mathbb Q_\ell/\mathbb Z_\ell)(-e)$ over $G_{L,S}$, $S$ the places above $\ell$. Define $B_C(e,n,D)=\exp((2en)^C\log(2D))$. Assume Poitou–Tate, local finiteness and Tate duality. If $s$ is finite and $s\log\ell\le B_C$ uniformly for these data, then with $C_K=\max(C,0)+9$,
$$
H^2(G_{L,S},\mathbb Z_\ell(e+1))\text{ is finite},\qquad
\log\#H^2(G_{L,S},\mathbb Z_\ell(e+1))\le B_{C_K}(e,n,D).
$$
This is `ZK.sFinal`. The following argument also explains how `sNum` supplies the premise in the [window route](second-cohomology-bounds-the-remaining-small-weights.md).

## The local contributions

By [length duality](first-localization-kernels-control-second-cohomology-length.md), the second cohomology length is at most $s+\sum_{v\mid\ell}h_v$, where $h_v$ is the length of the local invariants of $(\mathbb Q_\ell/\mathbb Z_\ell)(-e)$. The local cyclotomic image has index $m_v\le[L_v:\mathbb Q_\ell]\le n$ in $\mathbb Z_\ell^\times$, since the unrestricted local cyclotomic image is the whole group. Thus $(1+\ell^2)^{m_v}$ belongs to it. The binomial valuation formula gives
$$
v_\ell((1+\ell^2)^{m_v e}-1)=2+v_\ell(m_v)+v_\ell(e).
$$
Indeed taking powers prime to $\ell$ preserves the valuation of the difference from one, and each $\ell$th power increases it by one from initial valuation at least two. This difference kills the local invariants, so $h_v\le2+\lfloor\log_\ell n\rfloor+e$. With at most $n$ places the length bound is finite. Multiply by $\log\ell$ for log cardinality. Since $\ell\le n+1$, the extra term is at most $n(3+e)\log(n+1)$ and hence at most
$$
P=4n\log(2D)(2e)(2e+3)\log(n+1).
$$
Write $x=2en$, $Y=\log(2D)$ and $p=x^{\max(C,0)}$. Using $\log(n+1)\le n$ and $2e+3\le5e$, one gets $P\le10x^2Y\le(x^9-1)pY$. The log cardinality is at most $e^{pY}+(x^9-1)pY\le e^{px^9Y}$ by $e^u\ge1+u$.

## The three counts supplying the premise

Pass to a [large cyclotomic layer](choosing-the-cyclotomic-layer-for-small-index-counting.md) $L'$ of degree $n'$ and discriminant $D'$, with maximal $\ell$-power roots of order $\ell^c$. It satisfies $2e+1<\min(\ell^c,r_2(L'))$ and $s(L,\ell,e)\le s(L',\ell,e)$. On each higher layer $F/L'$ with a primitive $\ell^\nu$th root take $\gamma$ acting on it by $1+\ell^c$, and set $q=\ell^\nu$, $a=(1+\ell^c)^e$. The group $E_{\gamma,a,q}$ consists of class group homomorphisms into $\mathbb Z/q\mathbb Z$ with the covariance rule of the [class-group count](counting-twisted-characters-with-class-groups-and-units.md). Put $T(L',N,i)=\# H_i(\mathrm{GL}_N(O_{L'}),\mathbb Z)_{\mathrm{tors}}$ and
$$
\begin{gathered}
T_1=T(L',4e+6,2e+1),\quad T_2=T(L',4e+6,2e),\\
b=2e+(2e+1)(c+2e+1),\qquad
g=2n'+\lfloor\log_2 h_{L'}\rfloor+2,\quad v=v_\ell(e),\quad X=(b+v)g+c+v.
\end{gathered}
$$
1. `SFew` bounds the number of representatives satisfying the indicated principal-divisor condition and having distinct weighted norm power classes by $q^{r_2(L')}T_1T_2$. This is the [map from weighted norms to matrix group homology](weighted-norm-power-classes-in-matrix-group-homology.md).
2. `SCount` transfers this to $E_{\gamma,a,q}$, canceling $q^{r_2(L')}$ and obtaining $\# E_{\gamma,a,q}\le T_1T_2\ell^X$.
3. `SSha` takes a bound uniform over the layers to a bound on $\ell^{s(L',\ell,e)}$, including finiteness of the length. See the [finite-layer comparison](finite-layer-class-group-counts-control-the-localization-kernel.md).

Hence $s(L,\ell,e)\log\ell\le \log T_1+\log T_2+X\log\ell$. The [quantitative torsion bound](hermitian-forms-bound-matrix-group-torsion.md) `STors` gives $\log T_i\le B_{C_0}(e,n',D')$ with $C_0=24$ available.

## Absorbing the constants

Write $u=2en'$, $Y'=\log(2D')$. The class-number bound in `sNum` gives $g\le u+2uY'+2$. With $c,\log\ell\le u$, $v\le e\le u$ and $2e+1\le n'$, one has $b\le u+2u^2$, $b+v\le3u^2$, $g\le6uY'$ and $c+v\le4uY'$. Thus $X\log\ell\le19u^4Y'\le u^9Y'$. For $A=u^{\max(C_0,9)}Y'\ge1$ the sum is at most $2e^A+A\le e^{4A}$. Since $u^2\ge4$, use $C'=\max(C_0,9)+2$ as the exponent at $L'$.

For $x=2en$, the layer estimates give $d\le8x$, $n'\le4x^2$, $2en'\le x^5$ and $\ell^c\le2n'$. The discriminant comparison yields
$$
\log(2D')\le\log2+d\log D+n'\log(2n')
\le73x^4\log(2D)\le x^{11}\log(2D).
$$
Here $\log(2n')\le2n'\le8x^2$ and $x^7\ge128$. Hence $B_{C'}(e,n',D')\le B_{5C'+11}(e,n,D)$. This gives $C=5(\max(C_0,9)+2)+11$ for the first kernel, and the first section's comparison completes `LemmaK`.

## Lean correspondence

- [`LemmaK`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GeneratorCountTuples/LemmaK.lean#L13), [`lemmaK_litN_alt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/KFinal.lean#L11) and [`lemmaK_of_litN_alt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/LemmaKOfLitN.lean#L12) give the bound and actual window entry point.
- [`lemmaK_of_steps`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/LemmaKOfSteps.lean#L170) and [`ZK.lemmaK`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/LemmaKOfLitN.lean#L28) assemble the inputs.
- [`sFinal`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/SFinal.lean#L100) treats the local terms and [`numFin`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GeneratorCountTuples/NumFin.lean#L5) relates length and cardinality.
- [`sNum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/NumThree.lean#L211) uses `num_three`, `num_poly` and `num_down` for the constants. [`sTors`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/ExponentLe.lean#L122) supplies the matrix group torsion bound.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
