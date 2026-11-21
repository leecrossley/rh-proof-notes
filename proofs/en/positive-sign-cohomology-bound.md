# Summing the positive-sign cohomology bounds over primes

[Chinese proof](../zh/%E6%AD%A3%E5%8F%B7%E4%B8%8A%E5%90%8C%E8%B0%83%E9%95%BF%E5%BA%A6%E6%80%8E%E6%A0%B7%E6%8C%89%E7%B4%A0%E6%95%B0%E5%90%88%E5%B9%B6.md) · [Reading and review status](../../STATUS.md)

## Host conditions and conclusion

Let $\chi$ be a primitive Dirichlet character of conductor $Q\ge1$. Take integers $u,t\ge2$ and primes $q,d$ with $q\equiv3\pmod8$, $d\equiv7\pmod{16}$, and $\gcd(qd,Q)=1$. Put $N=\operatorname{lcm}(2^{u+2},Q)qd$. Let $E$ be the corresponding CM field in $\mathbb Q(\zeta_N)$, fixed by the units that lie in $\ker\chi$, are $\pm1$ modulo $2^{u+2}$, and are squares modulo $q$ and modulo $d$.

Write $p_K$ for the least prime at least seven, congruent to three modulo four and not dividing $Q$, and $h_*$ for the class number of $\mathbb Q(\sqrt{-p_K})$. Write $p_1$ for the least prime congruent to one modulo the odd part of $\operatorname{ord}(\chi)$ and not dividing $2Qp_K$. Require $q,d$ to exceed $2t+1,Q,\operatorname{ord}(\chi),p_K,h_*,p_1$. Define the finite set

$$
B_\chi=\{3\}\cup\{\ell:\ell\text{ odd prime},\ \ell\mid Q\,\operatorname{ord}(\chi)\,p_K h_*p_1\}.
$$

For odd $\ell$ and $1\le a<t$, let $L^+_{\ell,a}$ denote the $\mathbb Z_\ell$-length of the $(-1)^a$ eigenspace in the localization kernel with twist $-a$ on $E$, allowing ramification only at the finite places over $\ell$. This is the positive-sign part, with the sign depending on $a$.

Fix nonnegative integers $j_\ell$ and $B\ge0$. Assume that for every $\ell\in B_\chi$ and every $\ell$-power cyclotomic extension of $\mathbb Q(\zeta_{\ell Q})$ of degree $\ell^{j_\ell}$, the corresponding localization-kernel lengths for $1\le a<t$ are finite and have sum at most $B$. With the counting inputs below, there are $C$ and primes $r_1,r_2$, depending only on $\chi$ and the layer indices, such that for $q,d>r_1,r_2$, every $L^+_{\ell,a}$ in this range is finite and, for every finite set $S$ of odd primes,

$$
\sum_{\ell\in S}\log\ell\sum_{1\le a<t}L^+_{\ell,a}\le (Nt)^C+CB. \tag{1}
$$

All length statements quantify over the allowed algebraic closures and local data. This is the assembly in `PointHV`.

## Comparison with individual characters

Write $H$ for the subgroup defining $E$ and $T_{\ell,a}$ for the characters modulo $N$ trivial on $H$ with $\psi(-1)=(-1)^a$. Use a finite $\ell$-adic coefficient ring $O$ containing the needed roots of unity. Let $V(\ell,a,\psi)$ be the normalized length of the corresponding localization kernel: divide its $O$-length by the ramification index of $O$. It uses the coefficient character $\psi^{-1}\chi_{\rm cyc}^{-a}$, with local conditions at $\ell N$ and at infinity.

If $\ell\nmid[(\mathbb Z/N\mathbb Z)^\times:H]$, `redPrime` gives $L^+_{\ell,a}\le\sum_{\psi\in T_{\ell,a}}V(\ell,a,\psi)$. In general `redAll` adds $|T_{\ell,a}|\operatorname{lossAll}(\ell,N,[(\mathbb Z/N\mathbb Z)^\times:H],a)$ to this bound, and `lossLe` gives $\operatorname{lossAll}\le (Na)^6$. These comparisons first hold for extended lengths. Finiteness of the right side allows their use with finite real quantities. The number of characters satisfies $|T_{\ell,a}|\le N$.

Most counting inputs give a bound of the form $\log\ell\cdot V(\ell,a,\psi)\le(\ell Na)^{C_0}$, including finiteness, with a uniform exponent within each case. A layer input for $\ell\in B_\chi$ gives $\sum_{1\le a<t}V(\ell,a,\psi)\le B+(Nt)^{C_4}$ for characters trivial on $H$ whose `chiP ℓ ψ` has odd order. This operation first removes the part of order an $\ell$-power, then takes the component at modulus prime to $\ell$ by the Chinese remainder decomposition. The layer bound gives finiteness for all $a$ in the sum.

## Primes outside the fixed set

Put $M=Nt$. For odd $\ell\notin B_\chi$, the host structure gives $\ell\nmid[(\mathbb Z/N\mathbb Z)^\times:H]$. Use `redPrime`. Fix $1\le a<t$. Among these primes, `CountI` gives

$$
\sum_{\ell-1\nmid 2a}\log\ell \sum_{\psi\in T_{\ell,a}}V(\ell,a,\psi)\le M^{C_1}
$$

on every finite set of such primes, for $q,d>r_1,r_2$ with the constants depending only on $\chi$.

For $\ell-1\mid2a$, the classification `cases` puts each $\psi$ into at least one of the following cases:

- `CountZ` when $\psi=1$.
- `CountII` when $a\ge2$ and `chiP ℓ ψ` has even order.
- `CountIII` for nontrivial $\psi$ with odd-order `chiP ℓ ψ`.

Take $K$ to be the largest of their pointwise exponents. Here $\ell\le2a+1\le 2t$, so $\ell Na\le M^3$. Each weighted character term is at most $M^{3K}$. There are at most $2t$ such primes and at most $N$ characters each, so this part is at most $2M\cdot M^{3K}$. Summing both parts for $1\le a<t$ gives at most $t(M^{C_1}+2M\cdot M^{3K})\le M^{C_1+3K+4}$, using $M\ge2$ and $t\le M$. This is `SumOut`.

## Primes in the fixed set

Now fix $\ell\in B_\chi$. For $a\ge2$, use `CountII` for even-order `chiP ℓ ψ` and the layer bound `CountIV` for odd order. At $a=1$, the pointwise estimates `CountV` and `CountVs` apply on the two sides of $R_1(\ell,\psi)\le2^{c_2(\psi)}$. Here $c_2(\psi)$ is the dyadic conductor exponent of $\psi$, and $R_1=16\operatorname{ord}(\chi)(\ell Q)^2 4^{n_0}$. In this expression $n_0=v_2(\ell^{f_0}-1)$ and $f_0$ is the order of $\ell$ modulo $\operatorname{lcm}(4,\operatorname{ord}(\theta))$, where $\theta$ is obtained by deleting the $\ell$-power order part and the dyadic modulus component of $\psi$.

Collect in $O_\ell$ all characters occurring in some $T_{\ell,a}$ for which `chiP ℓ ψ` has odd order. The assertion `hostOdd` implies that their conductors divide $Q$. Indeed removing the modulus component at $\ell$ leaves those at $2,q,d$, and removing the $\ell$-power order part leaves the parity of their orders unchanged. The dyadic component has order a power of two, and the components at $q,d$ are trivial on squares, so have order at most two. Oddness of the resulting order forces these added components to be trivial. Thus $|O_\ell|\le\varphi(Q)\le Q$.

For each character in $O_\ell$, sum first over all $1\le a<t$ in the layer estimate. This gives total at most $(\log\ell)Q(B+M^{C_4})$. Outside $O_\ell$, use the pointwise estimates with the maximum of their exponents $K'$. Since $\ell\le N$ and $Na\le M$, we have $\ell Na\le M^2$. There are at most $tN=M$ terms, so the total is at most $M^{2K'+1}$. The comparison error in `redAll` is at most $(\log\ell)NM^6$ for each $a$, and contributes at most $M^8$ in all.

Using $\log\ell\le\ell\le M$ and $Q\le M$, take $C_\ell=C_4+2K'+9+\ell Q$. The coefficient of $B$ is at most $C_\ell$, and each of the three polynomial contributions is at most $M^{C_\ell-1}$. As $M\ge3$, this gives

$$
(\log\ell)\sum_{1\le a<t}L^+_{\ell,a}\le M^{C_\ell}+C_\ell B.
$$

This is `SumIn`.

## One exponent for every finite prime set

Put $D=\sum_{\ell\in B_\chi}C_\ell$, $b=|B_\chi|$, and write $C_{\rm out}$ for the exponent in `SumOut`. Split any finite odd prime set $S$ at $B_\chi$. Its total is at most $b(M^D+DB)+M^{C_{\rm out}}$. Using $b+1\le2^b\le M^b$, bound the polynomial terms by $M^{C_{\rm out}+D+b}$. Take $C=C_{\rm out}+D+b+bD$, proving (1). Each length is finite by the same comparisons, which can be applied on a singleton prime set.

The window theorem `thmHV` takes $j_\ell=\lfloor\log_\ell R_\ell\rfloor+3$ using the natural-number logarithm, where $R_\ell$ is the parameter of the cyclotomic-layer window theorem. The full window supplies $B=\exp(x^{4\varepsilon/5})$ with the same $q,d$. Because $x\le X$ and $t(x)\le x^{C_t}$, $q,d>2X^{C_t}+1$ implies the required pointwise prime sizes. The conductor of the given cyclotomic fixed field is $N$, so (1) is the positive-sign term in the [cohomological window](cohomological-window.md).

## Lean references and review

- [`LayerLe.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/LayerLe.lean) states `SumIn`, `SumOut` and `PointHV`. Character comparison and losses use [`RedPrime.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/RedPrime.lean), [`RedAll.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/RedAll.lean) and [`LossLe.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/LossLe.lean). The counting assumptions are in [`Counts.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/Counts.lean).
- [`sumOut`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/SumOut.lean#L50), [`FinalLe.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/FinalLe.lean), and [`point`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/PointArith.lean#L36) give the three sums. [`HostOdd.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/HostOdd.lean) controls the exceptional conductors.
- [`ThmHV.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/ThmHV.lean) applies the estimate pointwise; [`JointWinOfCounts.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/JointWinOfCounts.lean) combines it with the cyclotomic-layer window.

English translation draft. The separate geometric and cohomological estimates are hypotheses here. The Chinese notes give the arguments for [class I](../zh/%E4%B8%80%E4%B8%AA%E7%89%B9%E5%BE%81%E7%9A%84%E9%95%BF%E5%BA%A6%E6%80%8E%E6%A0%B7%E7%94%B1%E6%9C%89%E9%99%90%E4%B8%AA%E8%87%AA%E5%AE%88%E8%BF%B9%E5%B7%AE%E6%8E%A7%E5%88%B6.md), [class Z](../zh/%E5%B9%B3%E5%87%A1%E7%89%B9%E5%BE%81%E7%9A%84Z%E7%B1%BB%E4%B8%8A%E5%90%8C%E8%B0%83%E4%B8%BA%E4%BB%80%E4%B9%88%E6%B6%88%E5%A4%B1.md), [classes II and III](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88II%E7%B1%BB%E5%92%8CIII%E7%B1%BB%E7%9A%84%E9%95%BF%E5%BA%A6%E5%8F%AF%E4%BB%A5%E5%90%88%E7%94%A8%E7%A7%A9%E5%9B%9B%E6%96%B9%E6%B3%95.md), [descent from a cyclotomic layer](../zh/%E9%99%90%E5%88%B6%E5%88%B0%E5%88%86%E5%9C%86%E5%B1%82%E6%97%B6%E4%B8%A2%E5%A4%B1%E7%9A%84%E4%B8%8A%E5%90%8C%E8%B0%83%E6%80%8E%E6%A0%B7%E4%BC%B0%E8%AE%A1.md), and the [large](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E5%A4%A7%E4%BA%8C%E8%BF%9B%E5%AF%BC%E5%AD%90%E7%9A%84V%E7%B1%BB%E6%94%B9%E7%94%A8%E9%AB%98%E6%96%AF%E5%9F%9F.md) and [small](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E5%B0%8F%E4%BA%8C%E8%BF%9B%E5%AF%BC%E5%AD%90%E7%9A%84V%E7%B1%BB%E5%8F%AA%E9%9C%80%E4%B8%8B%E9%99%8D%E5%88%B0%E6%9C%89%E7%95%8C%E6%AC%A1%E6%95%B0%E7%9A%84%E5%9F%9F.md) dyadic conductor cases.
