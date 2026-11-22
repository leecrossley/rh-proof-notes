# Trace-dual coordinates give the hyperbolic frame

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Let $K_0,\sigma$ be as in the [unramified coefficient field](assembling-the-inert-cm-curve-data.md#the-coefficient-field-and-the-frobenius-lift) for a prime $p\ge5$. Let $\mathcal P$ be a finite set with a permutation $z\mapsto z^+$ of uniform positive even orbit length $d$, and let $R$ contain one representative per orbit. Identify places with pairs $(r,s)$ for $s\in\mathbb Z/d\mathbb Z$, where the permutation adds $1$ to $s$. Let $A$ be a finite set of matrix-entry indices, and $I$ a finite coordinate index set. Suppose that $g_{z,j},h_{z,j}\in K_0^I$ for $z\in\mathcal P,\ j\in A$ satisfy
$$
\begin{gathered}
g_{z,j}\text{ and }h_{z,j}\text{ have integral entries},\\
\sigma(g_{z,j})=h_{z^+,j},\qquad
\sigma(h_{z,j})=g_{z^+,j},\\
\sum_{i\in I} h_{w,k,i}g_{z,j,i}=\delta_{wz}\delta_{kj},
\end{gathered}
$$
with Frobenius acting entry by entry. Let $\omega_\ell,\omega_\ell^*$ be the [integral trace-dual lists](constructing-the-integral-frobenius-dual-lists.md) of length $d/2$. For every $e=(r,\ell,j)$ define two vectors
$$
f_e=\sum_{s\ \mathrm{even}}\sigma^s(\omega_\ell)\,g_{r,s,j},
\qquad
f'_e=\sum_{s\ \mathrm{odd}}\sigma^s(\omega_\ell^*)\,g_{r,s,j}.
$$
These are `fOf` and `fOf'`. Their entries are integral and fixed by $\sigma^2$, and they satisfy the hyperbolic Gram identities for $\langle u,v\rangle=\sum_i \sigma(u_i)v_i$:
$$
\langle f_e,f_{e'}\rangle=\langle f'_e,f'_{e'}\rangle=0,\qquad
\langle f_e,f'_{e'}\rangle=\delta_{ee'}.
$$
Moreover the corresponding linear forms in the orbit variables $Z_{r,s,j}$ recover the original coefficients $g$:
$$
\sum_{e=(r,\ell,j)} \bigl(f_e E_{\omega_\ell^*}(Z_{r,j})
       +f'_e O_{\omega_\ell}(Z_{r,j})\bigr)
=\sum_{r,s,j}g_{r,s,j}Z_{r,s,j}.
$$
Here $E_c,O_c$ are the parity forms from the [biextension construction](why-root-of-unity-averaging-preserves-the-biextension.md). The identity is vector-valued in $K_0^I$; its $i$-th component is the substitution `hypZ` of the theta expansion. [The hyperbolic coordinate vectors](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsRingHomRhoK.lean#L42)

## The Gram matrix

Integrality of the two sums follows from integrality of their entries and preservation of the unit ball by $\sigma$. Their invariance under $\sigma^2$ follows by moving $s$ by two in each sum, since $\sigma^2(g_{r,s,j})=g_{r,s+2,j}$ and the lists $\omega_\ell,\omega_\ell^*$ are fixed by $\sigma^d$. Thus wrapping at the end of the orbit gives the same coefficients. [Integrality and invariance under the square of Frobenius](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/HyperbolicCoordinatesIntegralSigmaSqFixed.lean#L1)

In $\langle f_e,f_{e'}\rangle$, expand both sums. Every term is a multiple of $\sum_i h_{r,s+1,j,i}g_{r',t,j',i}$ with $s,t$ even. The first place has odd index and the second even. If $r\ne r'$ they are on different orbits, and if $r=r'$ they are distinct by parity. Duality of $h,g$ therefore makes every term zero. In $\langle f'_e,f'_{e'}\rangle$ the same argument uses the even index $s+1$ and the odd index $t$. In the mixed case, only terms with equal $r,j$ and $t=s+1$ survive. The remaining sum is
$$
\sum_{s\ \mathrm{even}}\sigma^{s+1}(\omega_\ell\omega_{\ell'}^*)
=\sigma(\delta_{\ell\ell'})=\delta_{\ell\ell'}.
$$
This proves the three Gram identities. [Same-parity sums are isotropic](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/HyperbolicCoordinatesIsotropic.lean#L1) · [Opposite-parity duality](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/HyperbolicCoordinatesDual.lean#L30)

## Recover each coefficient of the substitution

For the even slots the trace-duality identity gives an inverse pair of square matrices with entries $\sigma^s(\omega_\ell)$ and $\sigma^s(\omega_\ell^*)$, as in the [trace-dual expansion proof](why-root-of-unity-averaging-preserves-the-biextension.md#trace-dual-expansions). Multiplying in the opposite order gives
$$
\sum_\ell \sigma^s(\omega_\ell)\sigma^t(\omega_\ell^*)=\delta_{st}
$$
for all even $s,t$. Apply $\sigma$ to get the formula for all odd $s,t$, since each odd slot is the successor of an even slot. Fix $r,j$ and an even $t$. The coefficient of $Z_{r,t,j}$ on the left of the claimed substitution identity is
$\sum_{s\ \mathrm{even}}g_{r,s,j}\sum_\ell\sigma^s(\omega_\ell)\sigma^t(\omega_\ell^*)$, which is $g_{r,t,j}$. For odd $t$ use the odd formula with the two lists in the opposite order. The orbit labeling is bijective, so these equalities prove the full linear substitution identity. [Recover each parity coefficient by the inverse trace matrices](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/LinearFormsHyperbolicCoordinatesEqTarget.lean#L12)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
