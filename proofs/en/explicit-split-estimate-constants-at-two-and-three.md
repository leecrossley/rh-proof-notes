# Explicit split estimate constants at two and three

[Chinese proof](../zh/%E4%BA%8C%E5%92%8C%E4%B8%89%E5%A4%84%E7%9A%84%E5%88%86%E8%A3%82%E4%BC%B0%E8%AE%A1%E6%80%8E%E6%A0%B7%E7%BB%99%E5%87%BA%E4%B8%A4%E4%B8%AA%E6%98%BE%E5%BC%8F%E5%B8%B8%E6%95%B0.md)

## Statement

Fix an admitted row and size parameters, local twist record $i$ at prime $\ell$, and good Hecke point $\pi$. Let $f=[E:\mathbb Q]/2$, $m$ the layer count, $r,t,V=n_V$ the ranks, with $1\le m\le f$, $0\le r\le t$, $t,V\ge1$. Let $N=\mathrm{condN}$, $s=\max(1,v_\ell(N))$ the bottom exponent, $H=b+\mathrm{Sc}+\eta_{\rm size}+t+2$ with nonnegative size terms, and $\Lambda=s+\log_\ell(2H)+1$. Assume $H\ge1$ and $N,t\le H$. The split comparison uses finite sets $C_{\rm col},C_{\rm row}$ of places of $E$ above $\ell$, and $h_1,h_2,h_3\in\mathbb N$ at most $4H$. Define
$$
\begin{aligned}
L_h&=s+\lfloor\log_\ell(2h)\rfloor+\lfloor\log_\ell N\rfloor+1,\\
e'&=32(2h_1s+1)+L_{h_1},\\
c_0&=20(2fV+1)L_{h_2},\qquad c_B=40(t+1)(2fV+1)L_{h_3}.
\end{aligned}
$$
Integer logarithm at zero is zero. Assume $h_W(u)\le rc_0$ for the column quotient invariants and [rank-one invariant bound](cyclotomic-invariant-length-is-bounded-by-a-weight-valuation.md) $h_0\le s+\lfloor\log_\ell t\rfloor$. Set $v_\Delta=\sum_{1\le k<t}(s+v_\ell(k))$. Assume finite cohomology lengths, `KillAt` making $s_\pi$ finite and all the residual unit differences nonzero, and their cost $Z=t\sum_v\operatorname{len}_\ell(\mathcal O/(\zeta_v-1))\le\ell^{-2}$. With $d_w=[E_w:\mathbb Q_\ell]$, $\mathrm{VV}(\ell)=\sum_{1\le k<t}\mathrm{shaLen}(\ell,k)$ and class number $h_E$, the assumed `ShaBoundTheoremB` is
$$
\begin{aligned}
v_\pi\le{}&s_\pi+\mathrm{VV}(\ell)+v_\ell(h_E)+Z\\
&+\sum_{u\in C_{\rm col}}\big(e'+d_um(2e'+v_\Delta)+2v_\Delta+h_W(u)+rc_0\big)\\
&+t\sum_{w\in C_{\rm row}}(d_w+2)c_B+4V(|C_{\rm col}|+1)v_\Delta+t|C_{\rm col}|h_0.
\end{aligned}
\tag{1}
$$
The [row and column costs](../zh/%E8%B4%9F%E8%BF%87%E6%BB%A4%E8%B7%B3%E7%82%B9%E6%80%8E%E6%A0%B7%E5%8F%98%E6%88%90%E5%88%86%E8%A3%82%E5%A4%84%E6%A0%BC%E6%8C%87%E6%95%B0%E7%9A%84%E8%A1%8C%E5%88%97%E4%BB%A3%E4%BB%B7.md) and [descent of the lifting exponent](descending-a-crystalline-lift-costs-the-degree-valuation.md) give the inputs. Then
$$
v_\pi\le s_\pi+\mathrm{VV}(\ell)+v_\ell(h_E)+\ell^{-2}
+6000\,fmHs+30000\,f^2t^2V\Lambda .
\tag{2}
$$

## Bounding the terms

Every integer $n\le8H$ has integer logarithm at most $\log_\ell(2H)+2\le\Lambda$. With $s+1\le\Lambda$ this gives $L_{h_j}\le3\Lambda$. Also $\log\ell>2/3$ and $\log(2H)\le2H-1$ give $\Lambda\le s+3H+1\le6Hs$. Hence $e'\le32(8Hs+1)+18Hs\le1000Hs$. Since $2fV+1\le3fV$ and $t+1\le2t$, we get $c_0\le1000 fV\Lambda$, $c_B\le1000 tfV\Lambda$ and thus $h_W(u)\le1000r fV\Lambda$. Also $h_0\le2\Lambda\le1000\Lambda$. Counting multiples of each $\ell^j$ gives $\sum_{k<t}v_\ell(k)\le\sum_{j\ge1}\lfloor t/\ell^j\rfloor\le t$, so $v_\Delta\le t(s+1)\le t\Lambda$.

Every set of places above $\ell$ has size and sum of degrees at most $2f$, by $\sum_{w\mid\ell}d_w=2f$. Take $c=1000$, $X=c fmHs$, and $Y=cf^2t^2V\Lambda$. In (1), the two column contributions in $e'$ are at most $2X$ and $4X$. The two in $v_\Delta$ are at most $2Y$ and $4Y$, using $m\le f$. The column invariants and $rc_0$ contribute at most $4Y$ since $r\le t$. The row term is at most $6Y$ because $\sum_{C_{\rm row}}(d_w+2)\le6f$. Since $|C_{\rm col}|+1\le3f$, the next term is at most $12Y$, and the final term at most $2Y$. Thus the total cost is at most $6X+30Y$, giving (2).

## Applying at two and three

At $\ell=2$, the tower conductor $\mathrm{QS}$ is divisible by four. The bottom exponent is $v_2(\mathrm{QS})=v_2(N)$, since $N=\mathrm{QS}\,q\,d$ and two is distinct from $q,d$. At three outside the specified small-prime set, three is distinct from $q,d$ and both generator primes. It lies in the split interval, does not divide $N$, and has bottom exponent one. In both decompositions $h_1,h_2,h_3$ are the source's $\lfloor H\rfloor,\mathrm{hOf},\lfloor2b\rfloor$, all at most $4H$ by the size and rounding bounds. The same explicit costs follow.

## Lean correspondence

- [`boundSplit` and `ShaBoundTheoremB`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/EmbeddingTypes.lean#L293) and [`conclusion_split_alt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/ConclusionSplitOfHub.lean#L21) supply (1).
- [`lamN_le`, `eL_le` and the cyclotomic weight bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ResidueCharacters/CyclotomicWeightExponentLe.lean#L10), [`split_arith`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ResidueCharacters/NumSplit.lean#L120), and [`boundSplit_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ResidueCharacters/NumSplit.lean#L170) give the numerical estimates.
- [The explicit bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ResidueCharacters/NumRow.lean#L70), [the row at two](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/NRowTwo.lean#L11) and [the row at three](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/NRowThree.lean#L12) give the applications.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
