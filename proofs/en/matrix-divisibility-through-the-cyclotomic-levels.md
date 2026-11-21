# Matrix divisibility through the cyclotomic levels

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E6%B2%BF%E5%88%86%E5%9C%86%E5%B1%82%E9%80%90%E6%A0%B9%E6%B6%88%E5%8E%BB%E7%9F%A9%E9%98%B5%E4%B8%AD%E7%9A%84%E5%88%86%E6%AF%8D.md)

Let $\ell$ be prime and $L/\mathbb Q_\ell$ finite containing the $\ell^s$-th roots of unity, $s\ge1$. Put $A=\prod_{i\in\mathbb Z/n\mathbb Z}\mathcal O_L[[U]]$, $n\ge1$, $X=(1+U)^{\ell^{s-1}}-1$, and $Q=\Phi_{\ell^s}(1+U)$. The map $\gamma$ substitutes $1+U\mapsto(1+U)^u$ componentwise, with $u\in\mathbb Z_\ell^\times$ of infinite order. The map $\varphi$ sends component $i-1$ to $i$ and substitutes $1+U\mapsto(1+U)^\ell$. Both act entrywise on matrices. For nonnegative integers $r,a,m,m'$, suppose $r$-square matrices $B,G,G_1,F,P,P'$ over $A$ satisfy
$$
G\equiv G_1\equiv I\bmod U,\quad
X^aG\gamma(B)=\gamma(X)^aBG_1,\quad
PP'=Q^{m'}I,\quad F\varphi(B)=Q^m BP .
$$
Then $X^a$ divides every entry of $B$. The project's chosen $u\in1+\ell^s\mathbb Z_\ell$ has infinite order by the valuation of powers of principal units, with $s\ge2$ when $\ell=2$.

**Proof.** Write $E_{i,\zeta}$ for expansion at $1+U=\zeta\exp(t)$ in component $i$. At $1$, suppress $i$ and write $E(X)=tw(t)$, $w(0)=\ell^{s-1}\ne0$, and $E(\gamma f)(t)=E(f)(ut)$. If $E(B)=t^k C(t)$ for $0\le k<a$, the $\gamma$-relation, after cancellation, reads
$$
w(t)^a u^k E(G)(t)C(ut)=u^a w(ut)^a C(t)E(G_1)(t).
$$
The constant matrices $E(G)(0),E(G_1)(0)$ are both $I$. Thus $w(0)^a(u^k-u^a)C(0)=0$ and $C(0)=0$. Starting at $k=0$, this proves divisibility by $t^a$ at $1$.

Multiplying the Frobenius relation on the right by $P'$ gives $Q^{m+m'}B=F\varphi(B)P'$. At $\zeta^{\ell^j}=1$, $1\le j\le s-1$, the expansion of $\varphi(B)$ comes from component $i-1$ at $\zeta^\ell$, with $t$ replaced by $\ell t$. If it is divisible by $t^a$ at the preceding level, the right-hand side is also divisible by $t^a$. Since $Q(\zeta-1)=\ell$, its expansion is a unit over $L$, giving $t^a\mid E_{i,\zeta}(B)$. Induction over $j$ and the [integral root test for $X^a$](testing-integral-power-series-at-cyclotomic-roots.md) finish the proof.

`X_pow_dvd_of_rescale` handles the constant matrix comparison, `pow_smul_eq` the second relation, and `X_pow_dvd_entry` the induction, using `levLaws` for expansions. [Rescaling](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/MapConstantCoeffEqOne.lean#L36) · [Frobenius identity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/MapConstantCoeffEqOne.lean#L84) · [Root induction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/MapConstantCoeffEqOne.lean#L103) · [Expansion rules](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLevelExpansionLawsOfRootsOfUnity.lean#L72)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
