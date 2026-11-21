# How quotient-lattice slopes bound the count discrepancy

[Chinese proof](../zh/%E5%95%86%E6%A0%BC%E6%96%9C%E7%8E%87%E5%A6%82%E4%BD%95%E6%8E%A7%E5%88%B6%E8%AE%A1%E6%95%B0%E5%B7%AE.md) · [Reading and review status](../../STATUS.md)

The [translation-average estimate](translation-averaging.md) takes a common upper bound on the count discrepancies as input. This note proves that bound from the slope, divisibility and scale conditions in `Deduction.ch_top`. The proof compares an average slope with the largest slope and tracks the constants in the resulting error.

## Identifying the count and its main term

Use $H,D,\ell,N,T,T_2,a(t),w_{h,j}$ and $\mathrm{gap}(h)$ from the translation-average estimate. Set $n=|H|$, $n_T=|T|$, $n_2=|T_2|$ and $f=|\Phi|=2n$. Additional data include a finite set $U$ of indices with a translation map $\mathrm{tr}:U\to H$, and for each $u\in U$ a nonempty finite set $W(u)$. Each $v\in W(u)$ provides the slopes $\mu_M(v),\mu_M^{\max}(v),\mu_N(v),\mu_N^{\max}(v)$ and the other real numbers specified below. At this stage only the relations between these numbers are used.

The numerical data have integer parameters $m,f$, real parameters $x,\varepsilon,a_E,b,b',k,L,L_a,B_0,N_c$, and real $v_0,\ell_g,\gamma,\lambda_L$. The coefficients are $c_{\rm div},e_{\rm div},c_E,c_H,c_{\rm count},c_{\rm slope},c_1,c_{\rm loss},e_{\rm loss},c_{HH}$. Other bounds use $X'',e_K,K$. Under the given bijections we can index the size and weight data by $t\in T$ and $\rho\in\Phi$. The identification condition, `IdentU`, gives $a_t=a(t)$, $w_{u,j,\rho}=w_{\mathrm{tr}(u),j}(\rho)$, $\gamma=\gamma_E$, and $\lambda_L=\operatorname{Re}\ell(c)$ for $c(i,j,h)=(-1)^i$. It also identifies $\mathrm{ASK}(u)$ as the sum of the counts in $\mathrm{gap}(\mathrm{tr}(u))$. Put $S_a=\sum_{t\in T}a_t$ and

$$
\begin{aligned}
W_{\log}(u)&=\sum_{j=1}^m \frac1f\sum_{\rho\in\Phi}\log w_{u,j,\rho},\\
\mathrm{Main}(u)&=m\sum_{t\in T}a_t(\log a_t-1-\gamma+\lambda_L)-S_aW_{\log}(u).
\end{aligned}
$$

Use $a_t\log a_t=0$ when $a_t=0$. By the main-term formula in the [Fourier identity](finite-fourier-balance.md), $\mathrm{Main}(u)$ is the sum of the real parts of the main terms. Hence

$$
\mathrm{gap}(\mathrm{tr}(u))=\mathrm{ASK}(u)-\mathrm{Main}(u). \tag{1}
$$

**Claim.** Under the local, slope and scale hypotheses below, all $u\in U$ satisfy

$$
\mathrm{gap}(\mathrm{tr}(u))\le x^{(e_{\rm div}+e_{\rm loss}+3)\varepsilon}B_E,
\qquad
B_E=n_Ta_E(1+m^2/k)+m\left[2nmbx^\varepsilon+
\frac{n_2 kbx^\varepsilon}{n^2 x^{-\varepsilon}}\right].
$$

## Local and slope hypotheses

Fix $u\in U$ and suppress $u$ in most subscripts. Use the positive weights $d_v$ to write $\langle Z\rangle=(\sum_{v\in W(u)} d_v Z(v))/\sum_{v\in W(u)}d_v$. The setup `HidaSetting` requires $x,b,k,v_0,f>0$, $a_E,b'\ge0$, $a_t\ge0$, $w_{u,j,\rho}>0$, $d_v,T_v>0$, and $\mu_N(v)\le\mu_N^{\max}(v)$. It also requires $c_1\ge0$, $\bar\delta<1$, $\bar\eta\ge0$ and $0\le\bar e\le1/4$. Let $E_v$ be the sum of the $m$ index-comparison terms $E_{v,j}$. Define

$$
\begin{aligned}
D_0&=m\sum_t a_t[\log a_t-1-\gamma-\log(\pi/v_0)+\lambda_L],\\
D_1&=c_{\rm div}[n_Ta_E L_a+m(B_0+N_c)x^{e_{\rm div}\varepsilon}],\\
S_0&=c_{\rm slope}n_Ta_E L_a,\qquad q=m/k,\qquad J_0=c_{\rm count}L_a(1+m^2/k),\\
\Lambda_5&=W_{\log}(u)+m\log(v_0/\pi)+m\ell_g-J_0.
\end{aligned}
$$

For every $v,v'\in W(u)$ the divisibility, index, height, size and base-slope hypotheses require

$$
\begin{aligned}
\mu_{CC}+h_v-F_o&\le D_0-S_a\log T_v+D_1,\\
|E_v-mS_a\ell_g|&\le mc_E B_0,\\
|(h_v+S_a\log T_v)-(h_{v'}+S_a\log T_{v'})|
&\le c_H(n_Ta_E L_a+mB_0),\\
\Lambda_5\le\log T_v&\le c_{\rm count}mL,\qquad
|\log T_v-\log T_{v'}|\le c_{\rm count}\log k,\\
\mu_M(v)&\ge-S_0(1+q),\qquad \mu_M^{\max}(v)\le S_0 .
\end{aligned}
$$

They are `DIV`, `EComp5`, `HComp`, `Count5` and `Slopes` in Lean. Write $L_5(v)=c_1 I_O+c_1 n_Tm(a_E/k+b')\log T_v+c_1X''+1$. The quotient slopes satisfy

$$
\begin{aligned}
\mu_N^{\max}(v)&\le\mu_M^{\max}(v)+G_a+F_o-E_v+c_1 mB_0,\\
\mu_N(v)&\ge \mu_M(v)+G_a+F_o-E_v-L_5(v).
\end{aligned}
$$

Let $s=\langle\mu_N(v)-h_v\rangle$ and $r=\max_v[\mu_N^{\max}(v)-h_v]-s$. We have $r\ge0$. Put $P_0=c_{\rm loss}n_Tmbx^{e_{\rm loss}\varepsilon}$ and assume $\mathrm{ASK}(u)-G_a\le P_0$ and $I_O\le P_0$. The height and variation data satisfy

$$
s-\mu_{CC}^{\min}\le H_*,\quad 0<H_*\le x^{c_{HH}}b,\quad
0\le\delta_u\le\bar\delta,\quad 0\le\eta_u\le\bar\eta,\quad 0\le e_u\le\bar e.
$$

The final slope comparison, `SlopeIneq`, applies with these bounds on $H_*,\delta_u,\eta_u,e_u$. Its conclusion is

$$
s-\log|W(u)|-
\frac{4r\log(1+H_*/r)+(\eta_u+4\sqrt{e_u})H_*}{1-\delta_u}\le\mu_{CC}. \tag{2}
$$

At $r=0$ the logarithmic product is interpreted as zero. Together these are the conditions of `LChain.SizeData₂`.

## From the slopes to an explicit discrepancy

In the lower bound for $\mu_N(v)-h_v$, use divisibility to bound $F_o-h_v$ below. Then use $S_a\ge0$, $\log T_v\ge\Lambda_5$, $E_v\le m(S_a\ell_g+c_E B_0)$ and $\mu_M(v)\ge-S_0(1+q)$. Taking the positive-weight average gives $s\ge G_a+\mu_{CC}-K_5-\langle L_5\rangle$, with

$$
K_5=S_0(1+q)+m(S_a\ell_g+c_E B_0)+D_0-S_a\Lambda_5+D_1.
$$

On expanding $\Lambda_5$, the $mS_a\ell_g$ term cancels, and the two logarithms of the reciprocal factors $\pi/v_0$ and $v_0/\pi$ cancel. The result is

$$
K_5=\mathrm{Main}(u)+K_0,\qquad
K_0=S_a J_0+D_1+mc_E B_0+S_0(1+q). \tag{3}
$$

The index comparison gives $|E_v-E_{v'}|\le2mc_E B_0$. The height comparison and the variation in $\log T_v$ bound the differences of $h_v$. Thus

$$
(-E_v-h_v)-(-E_{v'}-h_{v'})\le
V_0=2mc_E B_0+c_H(n_Ta_E L_a+mB_0)+S_a c_{\rm count}\log k.
$$

Apply the upper quotient-slope bound at $v$ and the lower bound at $v'$. Their common term $G_a+F_o$ cancels. The two base-slope bounds give a difference at most $S_0(2+q)$. Consequently

$$
(\mu_N^{\max}(v)-h_v)-(\mu_N(v')-h_{v'})
\le K_3+L_5(v'),\qquad K_3=S_0(2+q)+V_0+c_1mB_0.
$$

Average over $v'$ and then maximize over $v$ to get $r\le K_3+\langle L_5\rangle$. The loss bound for $I_O$ and the upper bound for $\log T_v$ give

$$
\langle L_5\rangle\le M_5
=c_1P_0+c_1n_Tm(a_E/k+b')c_{\rm count}mL+c_1X''+1.
$$

For $0\le r\le U_*$ and $0<H_*\le Xb$ with $X,b>0$, we have
$r\log(1+H_*/r)\le \log(1+X)(U_*+b)$. At $r=0$ this follows from the convention. For $r>0$ apply $\log v\le v-1$ to $(1+H_*/r)/(1+X)$ and multiply by $r$. The resulting upper bound is $r\log(1+X)+(H_*-rX)/(1+X)$. Use $H_*\le Xb$ and $X/(1+X)\le\log(1+X)$, the latter by applying $\log v\le v-1$ to $v=1/(1+X)$.

Apply this estimate with $U_*=K_3+M_5$ and $X=x^{c_{HH}}$. Bound the variation parameters in (2) by $\bar\delta,\bar\eta,\bar e$. Substitute the lower bound for $s$ using (3), and use $\mathrm{ASK}(u)\le G_a+P_0$. We obtain

$$
\begin{aligned}
\mathrm{ASK}(u)-\mathrm{Main}(u)\le{}&
K_0+\log|W(u)|+P_0+M_5\\
&+\frac{4\log(1+x^{c_{HH}})(K_3+M_5+b)
+(\bar\eta+4\sqrt{\bar e})x^{c_{HH}}b}{1-\bar\delta}.
\end{aligned} \tag{4}
$$

This is the estimate `each_unit_bound_statement`, with right-hand side `ErrX5at`.

## Scale hypotheses and comparison of errors

Write $y=x^\varepsilon$, $y_D=x^{e_{\rm div}\varepsilon}$ and $y_L=x^{e_{\rm loss}\varepsilon}$. The condition `ErrWindows` requires:

- $x\ge1$, $0<\varepsilon\le1$, $b\ge1$, $a_E\ge xb$, $n_T\ge1$, $m\le x^{1/2+\varepsilon/2}$, and $xm\le k$.
- $e_K\ge0$, $1\le k\le x^{e_K}$, $k\le a_E$, $0\le L,L_a\le2y$, $b'\ge0$, $kb'\le a_E$, and $0\le X''\le a_E$.
- $0\le a_t\le2a_E$ for all $t$, $B_0,N_c\ge0$, and $\log|W(u)|\le(k-3)\log2$ for all $u$.
- $\bar\delta\le1/2$, $\bar\eta,\bar e\ge0$, and $E_*=(\bar\eta+4\sqrt{\bar e})x^{c_{HH}}b\le Ky n_Ta_E$.
- The seven coefficients $c_{\rm div},c_E,c_H,c_{\rm count},c_{\rm slope},c_1,c_{\rm loss}$ belong to $[0,K]$, and $e_{\rm div},e_{\rm loss},c_{HH}\ge0$.

The condition `LargeX` gives $\log x\le y$ and $200(1+K)^2(1+c_{HH})(1+e_K)\le y$. Finally `BNBoundsU` gives $B_0\le2nmby$ and $N_c\le n_2kby/(n^2x^{-\varepsilon})$.

These assumptions give $m\le x$, $mb\le a_E$, $q\le1$, $a_E\ge1$, $b'\le a_E/k$, $S_a\le2n_Ta_E$, and $\log|W(u)|\le k\le a_E$. Put $h=1+c_{HH}$ and $g=1+e_K$. Then $\log(1+x^{c_{HH}})\le hy$, $\log k\le gy$ and $(1-\bar\delta)^{-1}\le2$. Define

$$
E_0=n_Ta_E(1+m^2/k)+m(B_0+N_c),\qquad P=y_D y_L y E_0.
$$

Here $E_0\ge1$ and $y,y_D,y_L\ge1$, so $P$ dominates each of $E_0,yE_0,y_DE_0,y_LE_0$. Bound the terms of (4) as follows:

- $S_a J_0\le4KP$ and $D_1\le3KP$. The two terms of $D_1$ are bounded by $2KP$ and $KP$.
- $mc_E B_0\le KP$ and $S_0(1+q)\le4KP$, giving $K_0\le12KP$. Also $P_0\le KP$ since $mb\le a_E$.
- In $M_5$ the first term is at most $K^2P$. By $n_Tm^2(a_E/k+b')\le2n_Ta_E m^2/k\le2E_0$ and $L\le2y$, the second is at most $4K^2P$. The remaining terms are at most $(K+1)P$. Thus $M_5\le(5K^2+K+1)P$.
- In $K_3$, the base-slope contribution is at most $6KP$. The three terms of $V_0$ are bounded by $2KP,3KP,2KgP$, and $c_1mB_0\le KP$. Since $b\le P$, $K_3+M_5+b\le U'P$ with $U'=5K^2+13K+2Kg+2$.

The first four terms of (4) are at most $(5K^2+14K+2)P$. For the fractional term use $E_*\le KP$, $\log(1+x^{c_{HH}})\le hy$ and the bound of two on the reciprocal denominator. The total is at most

$$
[(5K^2+16K+2)+8hU']\,yP
\le 200(1+K)^2hg\,yP\le y^2P.
$$

For the first inequality use $U'\le(5K^2+15K+2)g$ and $h,g\ge1$, bounding the bracket by $(45K^2+136K+18)hg$. The final inequality is `LargeX`. We have $y^2P=x^{(e_{\rm div}+e_{\rm loss}+3)\varepsilon}E_0$, and `BNBoundsU` implies $E_0\le B_E$. Equation (1) proves the claim.

## How the result enters the main route

The application `core_gm` supplies, for each $h\in H_0$, a point $u$ with $\mathrm{tr}(u)=h$. It uses $e_{\rm div}\le e_D$ and $e_{\rm loss}\le e_L$ to take $C=e_D+e_L+3$ in the translation-average estimate. Once the positive $\varepsilon$ and the constants are fixed, the conditions of `LargeX` follow at sufficiently large $x$ from $\log x=o(x^\varepsilon)$ and $x^\varepsilon\to\infty$. The pointwise construction needed on an entire window is upstream of this numerical deduction.

- The entry is [`Deduction.ch_top`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/ChTop.lean#L37), with `ch_top_main_eq` in the same file. The data identifications are in [`SplitInertia.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/SplitInertia.lean).
- The hypotheses are collected in [`SizeData₂`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/SChain.lean#L16), with the two quotient-slope estimates in [`QuotientSlopeBoundsWith.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/QuotientSlopeBoundsWith.lean) and the explicit formula in [`MeanBoundSecondForm.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/RankGapBounds/MeanBoundSecondForm.lean).
- The slope comparisons leading to (4) are in [`LevelOfCongruence.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ChainSlopeWindows/LevelOfCongruence.lean) and [`WeightedMeanData.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/RankGapBounds/RankGapProofs/WeightedMeanData.lean).
- The size assumptions and final bounds use [`ErrorFormsWeakWindowsFalse.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ErrorFormsWeakWindowsFalse.lean), [`errX5at_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ChainSlopeWindows/PChain.lean#L613), and [`core_ineq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ChainSlopeWindows/SubThreeMulLogTwoLe.lean#L13).

English translation draft. The divisibility and slope comparisons are assumptions here. For their inputs see the Chinese notes on the [local quotient slopes](quotient-slope-bounds.md) and the [cohomological divisibility loss](cohomology-and-divisibility-loss.md).
