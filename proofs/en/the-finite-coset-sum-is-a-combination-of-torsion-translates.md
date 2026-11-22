# The finite coset sum is a combination of torsion translates

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E$ be the column number field, let $\mathcal N,\mathcal N'$ be the two $\mathcal O_E$-lattices, and let $\mathfrak a$ be the module of period scalars. Put $M=\mathfrak a\operatorname{Hom}_{\mathcal O_E}(\mathcal N,\mathcal N')$ inside the $E$-space of matrices. Use the chosen complex embeddings and common factor $\delta$ to map a matrix to $j(X)=(\delta\sigma_\tau(X))_\tau$ in a complex vector space $V$. Set $\Lambda=j(M)$. On $V$ use the Hermitian form $H$ of the column construction, a real common multiple of the sum of entrywise Hermitian products. Set
$$
B(x,y)=\operatorname{Im} H(x,y),\qquad
q(x)=\tfrac{\sqrt d}{2}\operatorname{Re}H(x,x),\qquad
\alpha(x)=e^{\pi i q(x)}.
$$
Assume $B(\Lambda,\Lambda)\subset\mathbb Z$ and $q(\Lambda)\subset\mathbb Z$. For $x\in V$ and a function $f$, define the Heisenberg translation
$$
U(x)f(z)=f(z+x)\exp\!\left[-\pi\left(H(z,x)+\tfrac12 H(x,x)\right)\right].
$$
In particular $U(x)U(y)=e^{-\pi i B(x,y)}U(x+y)$, by expanding the exponent and using $H(y,x)=\overline{H(x,y)}$.

Let $\mathcal S$ be the selected set of primes of $E$ in the column level. At a prime $\mathfrak q$ put $e_{\mathfrak q}=1$ if $\mathfrak q\in\mathcal S$, $-1$ if $\mathfrak q\notin\mathcal S$ but $\overline{\mathfrak q}\in\mathcal S$, and $0$ otherwise. Fix an integer $c>0$ all of whose rational prime divisors lie in a finite set $S$. Let $A$ and $D$ be the images under $j$ of the global modules defined by belonging locally to $c^{-e_{\mathfrak q}}M_{\mathfrak q}$ and $c^{e_{\mathfrak q}}M_{\mathfrak q}$, respectively. These are `AC` and `BC`. Assume that the three quotients
$$
A/(A\cap\Lambda),\qquad
(\Lambda\cap A)/(\Lambda\cap A\cap D),\qquad
D/(D\cap\Lambda)
$$
are finite. Choose sets of representatives $X,J,Y$, respectively. Let $\Xi$ be any function of $E$-matrices with algebraic values that are integral under all $p$-adic embeddings for every $p\notin S$. Define $\Phi(v)$ to be $\Xi$ on a selected preimage when $v\in j(\operatorname{Mat}(E))$, and $0$ elsewhere. Let $\theta$ be the input theta function. The column kernel `thC` has the following formula, with volume parameter $1$:
$$
\begin{aligned}
\widehat\Phi_x(y)&=|J|^{-1}\sum_{s\in J}\Phi(s-x)e^{2\pi i B(s,y)},\\
\Theta(z)&=\sum_{x\in X}\alpha(x)U(x)
 \left(\sum_{y\in Y}\widehat\Phi_x(y)\alpha(y)U(y)\theta\right)(z).
\end{aligned}
$$
It is a finite linear combination of $U(t)\theta$, with each $ct\in\Lambda$ and each coefficient algebraic and integral at every $p\notin S$. This conclusion uses only the stated hypotheses about $\theta$.

**Proof.** For any of the two modules defining $A,D$, multiplication by $c$ sends it into $M$. Indeed, at every prime the new exponent of $c$ is $1\pm e_{\mathfrak q}\ge0$. Conversely the same exponent test gives $cM$ contained in each module. Global membership in $M$ follows from membership at every prime. Thus $cA,cD\subset\Lambda$, and $c\Lambda\subset A\cap D$. All representatives in $X,J,Y$ are killed by $c$ modulo $\Lambda$. Moreover the finite group represented by $J$ is killed by $c$. If a prime divides its cardinality, Cauchy's theorem gives an element of that order, so it divides $c$. Therefore $1/|J|$ is integral at $p\notin S$.

Expand the Heisenberg product in the definition. The translate indexed by $(x,y)$ is $t=x+y$, with $ct\in\Lambda$, and its coefficient is
$$
\alpha(x)\widehat\Phi_x(y)\alpha(y)e^{-\pi i B(x,y)}.
$$
The relations $c^2 q(x)=q(cx)\in\mathbb Z$ and $c^2 B(s,y)=B(cs,cy)\in\mathbb Z$, with the same statements for $y$ and $(x,y)$, show that every exponential factor is a root of unity. Such a factor is algebraic and has norm one at every $p$-adic embedding. Each $\Phi(s-x)$ is integral outside $S$ by construction. The sum defining $\widehat\Phi_x(y)$ and then the displayed product preserve integrality outside $S$. These coefficients and translates establish the assertion.

**Lean correspondence.** [`expS` and `twist₂`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/XiIndCClass.lean#L177) define the two local twists. [`onV`, `LamC`, `AC` and `BC`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/XiIndCClass.lean#L210) give the embedding and lattices. [`xiV` and `thC`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/XiIndCClass.lean#L224) give the coset formula. [`half_periods_torsion`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/KernelLocalFactors/PeriodLatticeFinitelyGenerated.lean#L248) proves the multiplication-by-level inclusions, [`snum_relIdx`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/KernelLocalFactors/PeriodLatticeFinitelyGenerated.lean#L260) controls the representative cardinality, and [`theta_coset_kernel`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/KernelLocalFactors/PeriodLatticeFinitelyGenerated.lean#L276) applies [`twist_lattice_kernel`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/KernelLocalFactors/PeriodLatticeFinitelyGenerated.lean#L179) to the three sets of representatives.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
