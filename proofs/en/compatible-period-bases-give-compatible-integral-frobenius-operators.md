# Compatible period bases give compatible integral Frobenius operators

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E4%BB%8E%E7%9B%B8%E5%AE%B9%E5%91%A8%E6%9C%9F%E5%9F%BA%E5%BE%97%E5%88%B0%E7%9B%B8%E5%AE%B9%E7%9A%84%E6%95%B4%E6%95%B0Frobenius%E7%AE%97%E5%AD%90.md)

## Statement

Let $A\hookrightarrow B$ be commutative rings with compatible Frobenius endomorphism $\varphi$ fixing the image of $\mathbb Z_\ell$. Write $\varphi_i=\varphi^{n_i}$ for $n_i\ge0$, and assume $\tau,\varphi_i(\tau)$ and $\ell$ invertible in $B$ for $\tau\in A$. Take $N,k\ge0$, $U\in\mathrm{GL}_d(B)$ and $Z,Z^*\in M_d(A)$ with $Z=\tau^N U$ and $ZZ^*=Z^*Z=cI$, $c=\tau^{2N}\ell^{2k}$. Put
$$
V=\varphi_2(c)\varphi_1(Z)\varphi_2(Z^*),\qquad
s=\varphi_2(\tau)^{3N}\ell^{4k}\varphi_1(\tau)^N .
$$
Then $V$ is integral, $s\in A$ is a unit in $B$, and $V\varphi_2(U)=s\varphi_1(U)$. For another set $Z_1,Z_1^*,U_1$ with matching $N,k,\tau$, form $V_1$. If rectangular $P,R$ have compatible sizes, $P$ has $\mathbb Z_\ell$ entries, $\varphi_i(R)=R$, and $PZ_1-ZR\in\ell^M A$ entrywise, then $VP-PV_1\in\ell^M A$. Thus the denominator $s$ is common to the layers.

## Proof

In $B$ use $Z^*=cZ^{-1}$ to rewrite $V=\varphi_2(c)^2\varphi_1(Z)\varphi_2(Z)^{-1}$. Substitute $Z=\tau^N U$ and multiply by $\varphi_2(U)$. The scalar is $\varphi_2(c)^2\varphi_1(\tau)^N/\varphi_2(\tau)^N=s$ since $\varphi_2(\ell)=\ell$. The original formula for $V$ only multiplies integral matrices. In the source, $Z=YQ$ and $Z^*=Q'Y'$, where $YY'=\tau^{2N}I$ and $QQ'=\ell^{2k}I$. These give the first product relation. The scalar is a unit in $B$, so the reverse product holds there and descends by injectivity.

Put $W=\varphi_1(Z)$, $D=\varphi_2(Z)$, $D^*=\varphi_2(Z^*)$ and similarly for the other layer, and write $b=\varphi_2(c)$. Applying Frobenius to the assumed congruence gives $PD_1-DR$ and $PW_1-WR$ divisible by $\ell^M$. Using $D^*D=DD^*=D_1D_1^*=bI$ gives the identity
$$
VP-PV_1=WD^*(PD_1-DR)D_1^*-b(PW_1-WR)D_1^*.
$$
Both terms lie in $\ell^M A$. In the project, $A=A_{\rm cris}$, $B=B_{\rm cris}$ and the inputs are supplied by crystalline frames with bounded poles and compatible period bases. The two powers describe a Weil Frobenius exponent by their difference. This proves the congruence used in [crystalline trace closedness](arbitrarily-small-crystalline-trace-errors-vanish.md).

## Lean correspondence

- [`OpOne2`, `LinkOp2` and `OpEx2`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/IsOp2One.lean#L23) give the interfaces.
- [`opOne_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/OpOneHolds.lean) gives the denominator and [`linkOp_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/LinkOp.lean#L8) the identity.
- [`opEx_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/OpExHolds.lean#L72) obtains the comparison from the lattice tower and Frobenius-fixed coefficients.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
