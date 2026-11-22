# The different and Euler factors give the product of local densities

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E/F$ be a CM quadratic extension unramified at every finite place, with $f=[F:\mathbb Q]$, and let $n\ge2$. For each finite place $v$ of $F$, put $q_v=|\mathcal O_F/v|$ and $\eta_v=1$ if $v$ splits, $-1$ if it is inert. Write
$$
\mathcal L_n=\prod_{v<\infty}(1-\eta_v^n q_v^{-n})^{-1}.
$$
Thus $\mathcal L_n=L(n,\eta^n)$ with $\eta$ the quadratic Hecke character, and $\mathcal L_n=\zeta_F(n)$ when $n$ is even. This is `lValEta` in the source.

Use the standard additive character $\psi$ of the adeles of $F$, trivial on $F$ and with real component $e^{-2\pi i x}$ at every real embedding. For each $v$, let $q_v^{c_v}$ be the volume ratio of the annihilator of the local integer ring to that ring, for the multiplication pairing with $\psi_v$. By [the local unit calculation](counting-nonzero-residue-norms-gives-the-local-fibre-density.md), the corresponding finite-place fibre density for a norm $\pm1$ in a self-dual rank-$n$ lattice is
$$
d_v=q_v^{c_v(1/2-n)}(1-\eta_v^n q_v^{-n}).
$$
The product converges absolutely to a positive number and satisfies
$$
\prod_{v<\infty}d_v
=|\operatorname{disc}F|^{1/2-n}\mathcal L_n^{-1}
=(2v_E)^{f(1/2-n)}\mathcal L_n^{-1},
\qquad
v_E=\tfrac12|\operatorname{disc}E|^{1/(2f)} .
\tag{1}
$$
This is the standard-character case of `EulerProductOfDensities` used in the volume formula.

### The standard character gives the inverse different

For the rationals, take the real character $e^{-2\pi i x}$, and at $p$ take $e^{2\pi i\{x\}_p}$, where $\{x\}_p$ is the negative-power part of the $p$-adic expansion in $\mathbb Q/\mathbb Z$. The local character has kernel $\mathbb Z_p$, so the product is defined on the restricted product. For a rational $b$, $b-\sum_p\{b\}_p$ lies in $\mathbb Z_p$ for every $p$ and is rational, hence is an integer. This proves that the product character kills diagonal rationals. Compose with the adelic field trace from $F$ to $\mathbb Q$ to obtain $\psi$. On a finite place $v\mid p$ its component is the character of $\mathbb Q_p$ composed with $\mathrm{Tr}_{F_v/\mathbb Q_p}$. At the real places the components are as stated, since $F$ is totally real.

For $t\in F_v$, $\psi_v(tA_v)=1$ is equivalent to $\mathrm{Tr}_{F_v/\mathbb Q_p}(tA_v)\subseteq\mathbb Z_p$. This is the defining trace condition of the local inverse different $\mathfrak D_{F,v}^{-1}$. The inverse different is the locally free trace dual of the integer ring, so the factor by which its measure exceeds that of $A_v$ is $\mathrm N v^{\operatorname{ord}_v(\mathfrak D_F)}$. Thus $c_v=\operatorname{ord}_v(\mathfrak D_F)$, and
$$
\prod_v q_v^{c_v}=\mathrm N_{F/\mathbb Q}\mathfrak D_F=|\operatorname{disc}F|.
$$
The discriminant identity follows from the determinant of the integral trace pairing, which measures the index of the integer lattice in its trace dual. Since the relative different of $E/F$ is the unit ideal, the tower formula for the different gives $|\operatorname{disc}E|=|\operatorname{disc}F|^2$. Consequently $(2v_E)^f=|\operatorname{disc}F|$.

### Group the Euler factors and take the product

For a split $v$ the two primes $P,\bar P$ of $E$ above it both have norm $q_v$. In `eulerFac` each of them contributes $(1-q_v^{-n})^{-1/2}$; their product is the $v$-factor of $\mathcal L_n$. For inert $v$ the unique prime of $E$ has norm $q_v^2$, so its factor is $(1-(-1)^n q_v^{-n})^{-1}$. This identifies the source product with $\mathcal L_n$.

There are at most $f$ primes of $F$ above each rational prime $p$, each of norm at least $p$. Hence $\sum_v q_v^{-n}\le f\sum_{m\ge2}m^{-n}<\infty$, and all individual factors $1-\eta_v^n q_v^{-n}$ are positive. For $|z|\le1/4$ the power series of the real logarithm gives $|\log(1-z)|\le 2|z|$, so the product of the Euler factors and its reciprocal converge absolutely to positive numbers. The different exponents have finite support. Multiplication of these finite and convergent products proves (1).

For a rational dilation $\psi(a\,\cdot)$, $a\in F^\times$, the annihilator at $v$ is $a^{-1}\mathfrak D_{F,v}^{-1}$. The new volume ratio multiplies $q_v^{c_v}$ by $|a|_v^{-1}$. The product formula gives $\prod_{v<\infty}|a|_v^{-1}=\prod_{v\mid\infty}|a|_v$. Thus the new density product times the real scaling factor $\bigl(\prod_{v\mid\infty}|a|_v\bigr)^{n-1/2}$ equals (1), as in the general density identity. The proof of the volume ratio needs only the constructed standard character.

### Lean correspondence

- [`eulerInv` and `locDens`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/BlockTheory/GlobalSignature/LocalDensityEuler.lean#L92) define the factors. [`eulerFac` and `lValEta`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/HermitianLattices/StatementMass.lean#L30) give the factors indexed by places of $E$.
- [`densityProduct`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/CmLocalDensitiesProductFormula.lean#L12) combines the standard character, inverse different, relative discriminant, and grouped Euler factors. [`density_product`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ProductLocalDensitiesAdeleCharacter.lean#L202) proves the product with the real scaling correction.
- [`eulerProductOfDensities`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/EulerProductOfDensities.lean#L9) transports this identity to the form used by the volume ratio.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
