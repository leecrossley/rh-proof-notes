# The alternating Hecke coefficients are integral

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

At a fixed served component let its length be $2\nu$. Suppose $1\le r\le k/2$ and $1\le j\le m$. At each slot $s$, assume the initial weight coordinates satisfy $\lambda_s(1)\ge\cdots\ge\lambda_s(k)$ and $\lambda_s(k)+w_1(s)\ge0$. Assume $w_1(s)\le\cdots\le w_m(s)$. Put $N_j=k+j(t+1)$ for $t\ge0$, and set $a_s=\lambda_s(1)-\lambda_s(2)$ on the given top set, $a_s=0$ elsewhere. Let $A=\sum_{s\text{ even}}a_s$. In the [alternating operator](a-symmetric-polynomial-inverse-removes-the-added-hecke-parameters.md), assume the scalars $m_a$ satisfy
$$
v_p(m_a)=\sum_{s\text{ even}}w_a(s)-\sum_{s\text{ odd}}w_a(s).
$$
The unit corrections leave these valuations unchanged. Then the coefficients $c_l$ of that operator satisfy $v_p(c_l)\ge0$ for $0\le l\le r$ and $v_p(c_r)\ge A$. These are the bounds `Cii`. [Weight and monotonicity conditions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/TheoremOfAlternateForm.lean#L366) · [`Cii`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/TheoremOfAlternateForm.lean#L538)

Each entry $\widehat m_a p^{\nu(t-2b)}$ of $X_j$, $1\le a\le j$, $0\le b\le t$, has valuation at least
$$
M=\sum_{s\text{ even}}w_1(s)-\sum_{s\text{ odd}}w_j(s)-\nu t.
$$
Use the increasing weights in both sums and $t-2b\ge -t$. The homogeneous polynomial $h_l(X_j)$ is a sum of products of $l$ entries, each of valuation at least $lM$. Its valuation is at least $lM$ as well. Insert this in the formula for $c_l$. The odd-slot weight terms of $D_j(r)-D_j(r-l)$ cancel the odd-slot term of $lM$. The resulting lower bound is
$$
\sum_{s\text{ even}}\sum_{a=r-l+1}^r \bigl(\lambda_s(a)+w_1(s)\bigr)
+\nu l(N_j-2r+l-t).
$$
[Cancellation in the exponent](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/TheoremOfAlternateForm.lean#L416) · [The shared valuation floor](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/TheoremOfAlternateForm.lean#L470) · [The homogeneous symmetric sum](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/TheoremOfAlternateForm.lean#L508)

Every summand of the double sum is nonnegative by the smallest-weight bound. Also $N_j-2r+l-t\ge j(t+1)-t\ge1$. At $l=r$ the double sum contains the first weight at every even slot. At a top slot its contribution $\lambda_s(1)+w_1(s)$ is at least $\lambda_s(1)-\lambda_s(2)=a_s$, since $\lambda_s(2)+w_1(s)\ge0$. This gives the claimed extra gain $A$, exactly the compensation needed for [the zero Hecke term](the-zero-hecke-term-pays-for-its-own-valuation-loss.md). [The top gap in the first weight](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/TheoremOfAlternateForm.lean#L395) · [Nonnegative tail and extra top gain](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/TheoremOfAlternateForm.lean#L426)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
