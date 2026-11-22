# A self-dual Hermitian trace basis for odd orbits

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $p\ge5$, let $i$ be a positive odd integer, and take $K_0$ to be the completed maximal unramified extension of $\mathbb Q_p$ with arithmetic Frobenius $\sigma$. Write $O$ for the ring of integers of the unramified quadratic subfield, with conjugation $\bar a=\sigma(a)$, and $O_i$ for the integral ring in the fixed field of $\sigma^{2i}$. These are the unramified extensions of degrees $2$ and $2i$, respectively. The relative trace $T$ from the larger field to the quadratic field is $\sum_{m=0}^{i-1}\sigma^{2m}$.

**Claim.** There are $\omega_1,\ldots,\omega_i\in O_i$ with
$$
T(\omega_j\,\sigma^i\omega_k)=\delta_{jk}.
$$
In the terminology of the even-degree construction, $(\omega_j)$ and $(\sigma^i\omega_j)$ are integral Frobenius trace-dual lists of length $i$ for period $2i$.

Start with the [trace-dual lists](constructing-the-integral-frobenius-dual-lists.md) $u_j,v_j\in O_i$, so $T(u_jv_k)=\delta_{jk}$. They come from a root of order $p^{2i}-1$. Let $V_{mj}=\sigma^{2m}u_j$ and $Q_{km}=\sigma^{2m}v_k$, so $QV=I$. Define the $i$-by-$i$ Gram matrix
$$
H_{jk}=T(u_j\,\sigma^i u_k),\qquad H=V^t\,\sigma^i(V).
$$
Its inverse is $\sigma^i(Q)Q^t$, by matrix multiplication. The entries of each matrix belong to $O$, since each is a sum of integral products over the relative Frobenius cycle. Thus $H$ has unit determinant over $O$. Also $\sigma^i$ restricts to $\sigma$ on $O$, since $i$ is odd. It commutes with $T$, and $\sigma^{2i}=1$ on $O_i$. It follows that $\overline{H_{jk}}=H_{kj}$. This is the odd-degree use in forming the Hermitian Gram matrix.

We spell out the integral orthonormalization. The reduction of $H$ is nondegenerate over $\mathbb F_{p^2}$. It has a vector of nonzero length: if all lengths vanished, evaluating on $x+c y$ for every $c\in\mathbb F_{p^2}$ would give vanishing of the relative trace of $c$ times each pairing. The trace pairing on $\mathbb F_{p^2}$ is nondegenerate, as for a nonzero $a$ one can take $c=a^{-1}$ and obtain trace $2\ne0$. Thus some lifted vector has unit length. Its Hermitian orthogonal projection divides by that unit, giving a direct sum of its line and a free integral orthogonal complement. In particular, extend the lift to a basis using a unit coordinate, and subtract the line projection from all the other basis vectors. The complement Gram matrix again has unit determinant. Induction yields an orthogonal integral basis with unit lengths fixed by $\sigma$.

Every such length $h$ is a norm $a\bar a$ of a unit of $O$. Over the residue field the norm $x\mapsto x^{p+1}$ is onto $\mathbb F_p^\times$, by cyclicity. Lift the chosen residue by a power of the primitive $(p^2-1)$-st root to a unit $a_0$. Then $h/(a_0\bar a_0)$ is fixed by $\sigma$ and congruent to $1\bmod p$. The equation $b^2=h/(a_0\bar a_0)$ has a unique solution congruent to $1\bmod p$, by a simple-root lift with derivative $2$. The uniqueness implies $\sigma(b)=b$. Now $a=a_0 b$ has norm $h$. Divide each basis vector by the indicated $a$, giving a change of basis $P$ over $O$ with $P H\overline P^{\,t}=I$, in the row convention. Put $\omega_j=\sum_k P_{jk}u_k$. They remain integral and fixed by $\sigma^{2i}$, and the trace Gram matrix of $(\omega_j)$ against $(\sigma^i\omega_j)$ is the identity because $\sigma^i(P)=\overline P$.

**Lean correspondence.** [`norm_onto`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/OrbitLabellings/ExistsUnitQuotientOfNormOneUnramifiedUltrametric.lean#L87) uses the prime-to-(p) roots of unity and a square root near (1). [`congr_one`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/OrbitLabellings/ExistsUnitQuotientOfNormOneUnramifiedUltrametric.lean#L172) gives the integral Hermitian change of basis, [`main`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/OrbitLabellings/ExistsUnitQuotientOfNormOneUnramifiedUltrametric.lean#L273) computes the Gram matrix and its inverse, and [`exists_unit_quotient_of_normOne_unramified_ultrametric`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/OrbitLabellings/ExistsUnitQuotientOfNormOneUnramifiedUltrametric.lean#L355) supplies the two lists used below.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
