# Moving a Kummer root forces a large prime-power order modulo a split prime

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let \(E\subset\Omega=\overline{\mathbb Q}\) be a number field, \(\lambda\) a rational prime, \(h\ge0\), and \(q>1\) an integer. Given any bound \(B\), there exists a rational prime \(p>B\) splitting completely in the normal closure of \(E\) for which the reduction of \(q\) is nonzero and
\[
\lambda^h\mid\operatorname{ord}_{\mathbb F_p^\times}(q\bmod p).
\]
The statement in Lean expresses the splitting condition by saying that every valuation-preserving automorphism at every prolongation of \(p\) fixes \(E\). The proof uses degree-one Čebotarev with finite exclusions. [Statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/InertiaQuadraticRamification/UnrCharAtOf.lean#L29) · [Prime selection in Lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/InertiaQuadraticRamification/OrdPrime.lean#L135)

## A root that still moves after a cyclotomic extension

We first prove the auxiliary claim used to prescribe the Frobenius. Let \(U\) be any open subgroup of \(G_{\mathbb Q}\), with fixed field \(K=\Omega^U\). There is an integer \(j\ge0\) such that for every \(J\ge j\), every primitive \(\lambda^J\)-th root of unity \(\zeta\), and every \(y\) with \(y^{\lambda^j}=q\), there exists \(\sigma\in U\) fixing \(\zeta\) and moving \(y\). [Lean statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/InertiaQuadraticRamification/UnrCharAtOf.lean#L24) · [The argument in Lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/InertiaQuadraticRamification/KumMove.lean#L7)

First take \(b\) large enough that \(\varphi(\lambda^b)>[K:\mathbb Q]\). A primitive \(\lambda^b\)-th root cannot belong to \(K\), so some \(\sigma_0\in U\) moves it and therefore moves every primitive \(\lambda^b\)-th root. Choose a prime \(s\mid q\), put \(D=[K:\mathbb Q]v_s(q)>0\), and set \(j=b+v_\lambda(D)\). The integer \(D\) has the following property: for \(z\in K^\times\) and positive \(a\), the identity \(z^a q^c=1\) with \(c\ge0\) implies \(a\mid cD\). Take the norm from \(K\) to \(\mathbb Q\) and the \(s\)-adic valuation to get \(a\,v_s(N_{K/\mathbb Q}z)+cD=0\). [Moving a high-order root of unity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/InertiaQuadraticRamification/MoveRoot.lean#L9) · [Norm and valuation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/InertiaQuadraticRamification/NormVal.lean#L9)

Fix \(J,\zeta,y\) as in the claim, and suppose every element of \(U\) fixing \(\zeta\) fixes \(y\). The action on \(\mu_{\lambda^J}\) has abelian image, so all commutators in \(U\) fix both \(\zeta\) and \(y\). It follows that \(\tau\sigma_0 y=\sigma_0\tau y\) for every \(\tau\in U\). Write \(\sigma_0\zeta=\zeta^a\) with \(a\ge1\). For \(\tau\in U\) we have \(\tau y=y\omega\) with \(\omega\in\mu_{\lambda^j}\subseteq\mu_{\lambda^J}\). Therefore
\[
\tau(\sigma_0 y)=\sigma_0(\tau y)=(\sigma_0 y)\omega^a,
\quad
\tau(y^a)=y^a\omega^a.
\]
The element \(z=\sigma_0 y/y^a\) is fixed by \(U\), hence belongs to \(K\). Also \(z^{\lambda^j}q^{a-1}=1\), so \(\lambda^j\mid(a-1)D\). The choice of \(j\) gives \(\lambda^b\mid a-1\). But then \(\sigma_0\) fixes the primitive \(\lambda^b\)-th root \(\zeta^{\lambda^{J-b}}\), which is a contradiction. This proves the claim.

## Selecting the prime and testing its residue order

Apply the claim with \(U\) the subgroup fixing the normal closure of \(E\), and take \(J=j+h\). Select \(\zeta,y,\sigma\) as above. Choose a finite Galois extension of \(\mathbb Q\) containing the normal closure, \(\zeta\), and all conjugates of \(y\). Čebotarev gives a rational prime \(p>\max(B,q,\lambda^J)\) and a prolongation at which a Frobenius element acts as \(\sigma\) on the chosen finite extension. Since \(\sigma\) fixes the normal closure of \(E\), the prime splits completely there. Its Frobenius fixes \(\zeta\), so \(\lambda^{j+h}\mid p-1\), by reduction of the primitive root at a prime of residue characteristic prime to its order. Write \(p-1=\lambda^{j+h}d\).

Let \(m\) be the order of \(q\bmod p\). If \(\lambda^h\nmid m\), then \(m\mid\lambda^h d\), since \(m\mid p-1\) and the \(\lambda\)-part of \(m\) divides \(\lambda^h\). In the residue field at the chosen prolongation, \(y\) is a unit and
\[
y^p=y(y^{\lambda^j})^{\lambda^h d}
    =y q^{\lambda^h d}=y.
\]
This would make the reductions of \(\sigma y\) and \(y\) equal. Their quotient is a root of unity of order dividing \(\lambda^j\), and reduction is injective on such roots since \(p\ne\lambda\). Thus \(\sigma y=y\), contradicting the choice of \(\sigma\). Hence \(\lambda^h\mid m\), as required. [The residue argument in Lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/InertiaQuadraticRamification/OrdPrime.lean#L200)


Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
