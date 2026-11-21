# Commutators and finite quotients transport local reciprocity

[Chinese proof](../zh/%E4%BA%A4%E6%8D%A2%E5%AD%90%E5%92%8C%E6%9C%89%E9%99%90%E5%95%86%E6%80%8E%E6%A0%B7%E6%8A%8A%E6%9D%AF%E7%A7%AF%E7%BB%93%E8%AE%BA%E7%94%A8%E4%BA%8E%E6%89%AD%E7%BB%93%E5%80%BC.md)

Let $\ell$ be an odd prime, $O$ a DVR finite over $\mathbb Z_\ell$, $W=\operatorname{Frac}(O)/O$, $G=G_{\mathbb Q}$, and $F=N_0\ell^m$ for $m\ge1$, $N_0\ge1$ prime to $\ell$. Write $U=G_{\mathbb Q(\mu_F)}$, $\alpha:G\to O^\times$ a character trivial modulo $\ell^m$ on $U$, and $\beta=\varepsilon_\ell\alpha^{-1}$. Assume $\alpha-\varepsilon_\ell$ is a unit at some group element. Fix $n\ge1$, prime $q\equiv1\bmod F$, and $a_0\mid A\mid\ell^m$ in $O$. Let $w_A\in W$ have annihilator $(A)$. Assume $\nu:G\to W$ restricts to a locally constant additive homomorphism on $U$ killed by $A$, obeys $\nu(gug^{-1})=\beta(g)\nu(u)$ for $g\in G,u\in U$, and vanishes on inertia outside $Fnq$. Let $c:G\to W$ be a continuous $\alpha$-cocycle killed by $a_0$, vanishing on inertia outside $F$. On each decomposition group over $F$ let $c(g)=(\alpha(g)-1)m_v$, $m_v\in W[a_0]$, and on decomposition groups above $n$ outside $Fq$ let $c=0$. Under the duality assumptions of [local cup-product reciprocity](local-cup-products-force-inertia-value-products-to-vanish.md), at any one place over $q$,
$$
\nu(\tau)=y w_A\quad\Longrightarrow\quad y\,c(g)=0
\qquad(\tau\in I_q,\ g\in D_q,\ y\in O).
$$
[`step`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/ChiDvd.lean#L37)

**Proof.** Since $G/U$ is abelian, commutators belong to $U$. Choose $\delta'$ with $\beta(\delta')-1$ a unit, using $\beta(\delta')-1=-\alpha(\delta')^{-1}(\alpha(\delta')-\varepsilon_\ell(\delta'))$. Set
$$
b(g)=-(\beta(\delta')-1)^{-1}\nu([g,\delta']),\qquad [g,\delta']=g\delta'g^{-1}\delta'^{-1}.
$$
It is locally constant since the commutator map is continuous into $U$. The identity $[gh,\delta']=g[h,\delta']g^{-1}[g,\delta']$ and equivariance give the $\beta$-cocycle rule. On $U$, $[u,\delta']=u(\delta'u^{-1}\delta'^{-1})$, so $\nu([u,\delta'])=(1-\beta(\delta'))\nu(u)$ and $b|_U=\nu|_U$. All values of $b$ are killed by $A$.

The assertion is immediate for a unit $A$; otherwise identify $O/(A)=B$ with $W[A]$ by $x\mapsto xw_A$. The functions $b,c$ become locally constant $\bar b,\bar c$ over the finite $\mathbb Z/\ell^m\mathbb Z$-algebra $B$, with residual twists $\bar\beta,\bar\alpha$. The latter is locally constant because it factors through $G/U$. Outside $Fnq$, inertia lies in $U$, $\bar\alpha=1$, and $\bar c=\bar b=0$. Above $Fn$ away from $q$, $\bar c$ is a coboundary, using $m_v$ above $F$ and zero otherwise. At $q$, complete cyclotomic splitting implies $D_q\subset U$, so $\bar\alpha=\bar\beta=1$ and $\bar c|_{I_q}=0$. Apply the cup-product theorem with $N=Fn$ to obtain $\lambda(\bar b(\tau)\bar c(g))=0$ for every $\mathbb Z/\ell^m\mathbb Z$-linear $\lambda:B\to\mathbb Z/\ell^m\mathbb Z$.

Such functionals separate points. Decompose the additive group of $B$ into cyclic groups of orders $\ell^j$, $j\le m$. Project a nonzero component to its summand and inject it via $1\mapsto\ell^{m-j}$. Thus $\bar b(\tau)\bar c(g)=0$. Since $b(\tau)=\nu(\tau)=yw_A$, $\bar b(\tau)=y\bmod A$; return to $W[A]$ to get the conclusion.

`ext` supplies the commutator extension, `chi_dvd` gives the cyclotomic congruence, and `recip` uses the module dual to obtain the torsion form `Rec`. This note states the local assumptions used in the auxiliary-prime iteration; the source permits a general ramification modulus divisible by $F$. [Extension](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/ImportsAlt.lean#L7) · [Congruence](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/ChiDvd.lean#L11) · [Finite reciprocity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/OverIff.lean#L297) · [`Rec`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PrimitiveFrobeniusFixed/IsAdmissiblePrimeListNil.lean#L141)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
