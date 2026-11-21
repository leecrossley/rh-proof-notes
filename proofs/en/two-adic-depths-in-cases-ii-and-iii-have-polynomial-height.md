# Two-adic depths in Cases II and III have polynomial height

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88II%E7%B1%BB%E5%92%8CIII%E7%B1%BB%E4%BD%BF%E7%94%A8%E7%9A%84%E4%BA%8C%E8%BF%9B%E5%B1%82%E6%95%B0%E6%9C%89%E5%A4%9A%E9%A1%B9%E5%BC%8F%E9%AB%98%E5%BA%A6.md)

Fix $\chi,Q,o$ and the [host data](choosing-among-seven-positive-sign-length-estimates.md) with $N,p_1$. For odd prime $\ell$, allowed coefficients $O$, $e\ge2$, and host character $\psi$ of sign $(-1)^e$, let $c=c_2(\psi)$ be the two-component conductor exponent. Form $\theta$ by removing the $\ell$-power-order part and then the two-component, $f_0=\operatorname{ord}_{(\mathbb Z/\operatorname{lcm}(4,\operatorname{ord}\theta)\mathbb Z)^\times}(\ell)$, $n_0=v_2(\ell^{f_0}-1)$. Define
$$
\begin{aligned}
n_2&=\left\lceil\log_2\max(\ell N4^{n_0},2^{c+6}o\ell^3Q^2)\right\rceil,\\
n_3&=\left\lceil\log_2\max(\ell Qp_1 4^{n_0},8\ell^2)\right\rceil .
\end{aligned}
$$
For nonnegative integers $C_0,A$, some $C_\chi$ depending only on $\chi,C_0,A$ satisfies for either $(n',P)=(n_2,1),(n_3,p_1)$,
$$
2C_0(\ell-1)2^{n'}(2o)[\ell 2^{n'} NP(e+1)]^A\log p_0(\ell NP)
\le(\ell Ne)^{C_\chi},
$$
where $p_0(m)$ is the least prime $\ge5$ not dividing $m$. [Depth definitions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/DirichletPrimeToLPartMulLPowerPart.lean#L221) · [`arith`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/TwoPowClogLe.lean#L172)

**Proof.** On units with two-component identity, the host quotient injects into the character image for $\chi$ and the two square quotients, so its exponent divides $2o$. Thus $\operatorname{ord}\theta\mid2o$ and is prime to $\ell$. The modulus for $f_0$ divides $4o$, and reduction on units is surjective, so $f_0\mid f=\varphi(4o)$. By definition $\ell^{f_0}\equiv1\bmod4$, giving $2\le n_0$ and $2^{n_0}\le\ell^{f_0}-1<\ell^f$. [Order bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/OrdProjNDvd.lean#L37) · [Two-adic growth](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/CmDatumCharTwoAdicOrderBounds.lean#L61)

Write $X=\ell Ne\ge16$, since $16\mid N$. Also $Q\le N,\ o\le Q,\ 2^c\mid N$. Rounding a positive input up to the next power of two costs at most a factor two. Thus
$$
2^{n_2}\le2\max(\ell N\ell^{2f},64\,2^co\ell^3Q^2)\le X^{2f+10},
\qquad
2^{n_3}\le2\max(\ell Qp_1\ell^{2f},8\ell^2)\le X^{11+Q+p_1+2f}.
$$
The bounds use $128\le X^2,\ Q\le X^Q,\ p_1\le X^{p_1}$. Either is $\le X^a$ for $a=2f+10+11+Q+p_1+2f$. Also the first maximum shows $c\le n_2$, and in III $c=0$ by odd order.

Bertrand gives a prime between $m+5$ and $2(m+5)$, eligible for $p_0(m)$, so $p_0(m)\le2m+10$. Put $B=1+p_1$, so $P\le B\le X^B$. We have $2C_0\le X^{2C_0}$, $(\ell-1)2^{n'}(2o)\le X^{1+a+2o}$, $\ell\,2^{n'} NP(e+1)\le X^{1+a+1+B+2}$, and $\log p_0(\ell NP)\le2\ell NP+10\le X^{2+(1+1+B)+10+1}$. Multiply with the third exponent scaled by $A$. This gives the asserted $C_\chi$ in the [Case II and III estimate](cases-ii-and-iii-share-the-rank-four-length-method.md). [Auxiliary prime bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/PZeroLe.lean#L6)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
