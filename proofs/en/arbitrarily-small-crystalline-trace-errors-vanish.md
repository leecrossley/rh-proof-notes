# Arbitrarily small crystalline trace errors vanish

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E4%BB%BB%E6%84%8F%E7%B2%BE%E5%BA%A6%E7%9A%84%E6%99%B6%E4%BD%93%E8%BF%B9%E8%AF%AF%E5%B7%AE%E5%BF%85%E9%A1%BB%E4%B8%BA%E9%9B%B6.md)

## Statement

Let $K=\overline{\mathbb Q}_\ell$ and $F$ its maximal unramified subfield. Use the injection $A_{\rm cris}\hookrightarrow B_{\rm cris}$ of integral and rational period rings and a coefficient embedding $u:F\hookrightarrow B_{\rm cris}$ taking norm-$\le1$ elements into the integral ring. Assume $A_{\rm cris}$ is $\ell$-torsion-free and $\bigcap_M\ell^M A_{\rm cris}=0$. Fix $s\in A_{\rm cris}$ invertible in $B_{\rm cris}$, a matrix $V$ over $A_{\rm cris}$ and vector $e$ over $\mathbb Z_\ell$. Let $t\in K^d$ collect target matrix traces and $p\in K$ be the target Weil–Deligne trace. Assume for every $F$-linear $\lambda:K\to F$ that
$$
u(\lambda(t))(Ve)=s u(\lambda(p)). \tag{1}
$$
Each layer analogously has $V',e',t'_k,p_k$ with $u(\lambda(t'_k))(V'e')=s u(\lambda(p_k))$ for all seeds and functionals, the same $s$ throughout.

Suppose for each $M\ge0$ some layer has integer $P$ and coefficients $c_k\in K$ with $VP-PV'\in\ell^M A_{\rm cris}$ and $Pe'-e\in\ell^M\mathbb Z_\ell$ entrywise, and
$$
\delta=tP-\sum_k c_k t'_k,\qquad
\eta=\theta-\sum_k c_k p_k,\qquad
|\delta_j|_\ell,|\eta|_\ell\le\ell^{-M}.
$$
Then $p=\theta$. This is the algebra in `TrLim`.

## Proof

If $p\ne\theta$, fix $c_1\ge0$ with $z=\ell^{c_1}(p-\theta)$ and all $\ell^{c_1}t_i$ of norm at most one. Take $c_2\ge0$ with $\ell^{-c_2}\le |z|_\ell$. For each $M$ choose the indicated layer and apply the [coordinate lemma](an-integral-coordinate-detects-a-nonzero-period-trace-error.md) to $\ell^{c_1}t_i,\ell^{-M}\delta_j,\ell^{-M}\eta,z$. Their images are integral, and $q=\lambda(z)$ has $\ell^{-c_2}\le|q|_\ell\le1$.

Apply each seed equality with the $F$-linear functional $x\mapsto\lambda(c_kx)$, so no $F$-rationality of $c_k$ is needed. Subtract these from (1) and insert the errors to get
$$
\begin{aligned}
s u(\lambda(p-\theta))
={}&u(\lambda(t))\big((VP-PV')e'-V(Pe'-e)\big)\\
&+u(\lambda(\delta))V'e'-s u(\lambda(\eta)).
\end{aligned}
$$
After multiplying by $\ell^{c_1}$ every term is in $\ell^M A_{\rm cris}$. The first line uses the two matrix congruences and integrality of $\lambda(\ell^{c_1}t_i)$. The second uses integrality of the scaled small errors. Thus $s u(q)\in\ell^M A_{\rm cris}$. Multiply by $u(\ell^{c_2}/q)$, which is integral, giving $\ell^{c_2}s\in\ell^M A_{\rm cris}$. The exponents $c_1,c_2$ were fixed, so all $M$ give $\ell^{c_2}s=0$ by separatedness. Torsion-freeness gives $s=0$, contrary to invertibility in the period ring. Hence $p=\theta$.

For a local Weil element, `Tie2` gives (1) from period bases, `OpEx2` gives the [integral operator comparison](compatible-period-bases-give-compatible-integral-frobenius-operators.md), and [joint approximation](one-set-of-coefficients-approximates-global-and-local-traces.md) supplies $\delta,\eta$. Applying this at the powers of Frobenius gives all power sums, which determine the characteristic polynomial by Newton identities.

## Lean correspondence

- [`IsTr`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/JointApproxOfMem.lean#L85) and [`TrStep` and `TrLim`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/IntBasisAlt.lean#L139) give the conditions.
- [`trStep_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/TrStep.lean#L83), [`trLim_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/TrLimHolds.lean#L8) and [`closedTr_of` and `congPhi_of_closedTr`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/ClosedPhiOfClosedTr.lean) give divisibility, separatedness and the Frobenius application.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
