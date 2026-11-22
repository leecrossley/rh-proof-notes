# Finitely many congruences detect powers of S-units

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let \(F\) be a number field, \(S\) a finite set of finite places, and \(m\ge1\). There is a finite set \(B\) of finite places disjoint from \(S\) such that an \(S\)-unit \(x\in F^\times\) with
\[
x\equiv1\bmod\mathfrak p_b\quad\text{for every }b\in B
\]
is an \(m\)-th power in \(F^\times\). Here an \(S\)-unit has valuation zero at all finite places outside \(S\), and the displayed congruences use the first power of the local maximal ideals. The set \(B\) depends on \(F,S,m\) and works for every \(S\)-unit. This supplies the compatibility condition for [prescribing finite-order local characters](finite-order-local-characters-globalize-with-trivial-infinite-components.md). [Exact statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsKummerField.lean#L252)

## Descending a sufficiently high power from a cyclotomic field

We first prove the input for \(m=\lambda^r\), where \(\lambda\) is prime and \(r\ge0\). Set \(D=[F:\mathbb Q]\), \(t=(1+\lambda^2)^{D!}\), and write \(t-1=\lambda^s e\) with \(\lambda\nmid e\). Put \(M=\lambda^{r+s}\). If \(x\in F^\times\) has an \(M\)-th root \(y\) in \(K=F(\mu_M)\), then \(x\) is a \(\lambda^r\)-th power in \(F^\times\). [Descent theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsPowDescentCyclotomic.lean#L141)

Choose a primitive \(M\)-th root of unity \(\zeta\). The image \(H\) of \(\operatorname{Gal}(K/F)\) in \((\mathbb Z/M\mathbb Z)^\times\) has index at most \(D\). Indeed \([\mathbb Q(\mu_M):\mathbb Q]=\varphi(M)\le [K:\mathbb Q]=D|H|\). Thus \(H\) contains the \(D!\)-th power of every unit modulo \(M\), since the index divides \(D!\). Some \(\tau\in\operatorname{Gal}(K/F)\) consequently acts on \(\mu_M\) by the \(t\)-th power. [Cyclotomic automorphism](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsPowDescentCyclotomic.lean#L38)

Let \(N=\lambda^r\) and \(A_N=1+t+\cdots+t^{N-1}\). The valuation formula \(v_\lambda(t^N-1)=v_\lambda(t-1)+r\), since \(t\equiv1\bmod\lambda^2\), gives \(v_\lambda(A_N)=r\). It follows by iterating the binomial expansion for a \(\lambda\)-th power. If \(u=1+b\) with \(v_\lambda(b)\ge2\), the term \(\lambda b\) in \(u^\lambda-1\) has valuation \(1+v_\lambda(b)\) and every later term has larger valuation. Hence each iteration adds \(1\). So \(t^N\equiv1\bmod M\), and \(\tau^N=1\). [Geometric sum valuation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsPowDescentCyclotomic.lean#L8)

For any \(\sigma\in\operatorname{Gal}(K/F)\) the quotient \(\sigma(y)/y\) belongs to \(\mu_M\), because \(y^M=x\). Write \(\alpha=\tau(y)/y\) and \(\beta=\sigma(y)/y\). By iteration
\[
\tau^N(y)=\alpha^{A_N}y.
\]
As \(\tau^N=1\), the order of \(\alpha\) divides both \(M\) and \(A_N\), so \(\alpha^N=1\). The group \(\operatorname{Gal}(K/F)\) is abelian. Commuting \(\sigma\) and \(\tau\) on \(y\) gives
\[
\sigma(\alpha)\,\beta y=\tau(\beta)\,\alpha y
=\beta^t\alpha y,
\qquad
\sigma(\alpha)=\beta^{t-1}\alpha.
\]
Thus \(v=y^{t-1}/\alpha\) is fixed by every \(\sigma\), so \(v\in F^\times\). Since \(\alpha^N=1\) and \(N(t-1)=Me\), it satisfies \(v^N=x^e\). Choose integers \(a,b\) with \(ae+bN=1\). Then \((v^a x^b)^N=x\), giving the required root in \(F\). [Cyclotomic descent calculation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsPowDescentCyclotomic.lean#L70)

## Using one congruence for each Frobenius action

The \(S\)-unit group is finitely generated. For example, the valuations at \(S\) map it into \(\mathbb Z^S\), and the kernel is the finitely generated ordinary unit group by Dirichlet's unit theorem. For each member of a finite generating set, adjoin an \(M\)-th root to \(K\). Since \(K\) already contains \(\mu_M\), this gives a finite Galois extension \(L/K\) containing all \(M\)-th roots of every \(S\)-unit. Indeed products of roots of the generators, with integer exponents, give one root of each \(S\)-unit and multiplication by \(\mu_M\) gives the others. [The Kummer field](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsKummerField.lean#L14)

For each \(\sigma\in\operatorname{Gal}(L/K)\), Čebotarev supplies a prime of \(K\) away from \(M\) and the primes over \(S\), and a prolongation to \(L\) at which the Frobenius is \(\sigma\). Let \(B\) be the set of their contractions to \(F\). The selected primes are finite in number and independent of \(x\). If \(x\equiv1\) at all the contracted primes, take \(y\in L\) with \(y^M=x\). At each selected prime of \(L\) above a prime of \(K\), \(y\) is a unit and its reduction is an \(M\)-th root of unity. The residue characteristic does not divide \(M\), so the reductions of the \(M\) roots of unity in \(K\) are distinct. Consequently the reduction of \(y\) is the reduction of some \(M\)-th root of unity in \(K\). Frobenius over \(K\) fixes that reduction. The reductions of \(y\) and \(\sigma y\) are therefore equal. Their quotient is an \(M\)-th root of unity with reduction \(1\), so \(\sigma y=y\). Every element of \(\operatorname{Gal}(L/K)\) fixes \(y\), hence \(y\in K\). The cyclotomic descent just proved gives a \(\lambda^r\)-th root of \(x\) in \(F\). [Uniform Frobenius tests](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsKummerField.lean#L116)

For general \(m\), take the union of the testing sets for its prime-power factors. If \(u^h=x\), \(v^k=x\) with \(h,k\) coprime and \(Ah+Bk=1\), then \((u^Bv^A)^{hk}=x\). Iterate to get an \(m\)-th root. For \(m=1\), use the empty set. [Combining coprime exponents](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsKummerField.lean#L219)


Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
