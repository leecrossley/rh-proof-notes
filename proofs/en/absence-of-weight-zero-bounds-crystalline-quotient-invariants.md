# Absence of weight zero bounds crystalline quotient invariants

[Chinese proof](../zh/%E9%9B%B6%E6%9D%83%E7%BC%BA%E5%A4%B1%E6%80%8E%E6%A0%B7%E7%BB%99%E5%87%BA%E6%99%B6%E4%BD%93%E5%95%86%E6%A0%BC%E7%9A%84%E4%B8%8D%E5%8F%98%E9%87%8F%E9%95%BF%E5%BA%A6.md)

## Statement

Let $\ell$ be prime, $N>0$, with $4\mid N$ at two. Let $K,L$ be finite over $\mathbb Q_\ell$ with $K\subseteq \mathbb Q_\ell(\mu_{\operatorname{lcm}(\ell,N)})$ and $L$ containing these roots. Let $V$ be a continuous crystalline $L$-representation of rank $r$, with full stable $\mathcal O_L$-lattice $T$. Suppose all filtration jumps across embeddings $K\hookrightarrow L$ belong to one set $U\subseteq[-h,h]$ of at most $n$ integers, with no zero jump. Use the crystalline restriction, Fontaine and Wach inputs of the source. Put
$$
s=\max(1,v_\ell(N)),\quad \lambda=s+\lfloor\log_\ell(2h)\rfloor+\lfloor\log_\ell N\rfloor+1,\quad
c_0=20(n+1)\lambda.
$$
At zero use integer logarithm zero. Then $(V/T)^{G_K}$ is killed by $\ell^{c_0}$ and its length in units of $\operatorname{length}_{\mathcal O_L}(\mathcal O_L/\ell)$ is at most $rc_0$. This enters the [small-prime split bound](explicit-split-estimate-constants-at-two-and-three.md).

## An embedding direction

In the admissible cyclotomic field with `HypW`, take $M=2s+1+\min\{j\ge0:2h\le\ell^j(\ell-1)\}$. A vector $v$ fixed modulo $T$ has coordinates $y\in\mathbb Q_\ell^d$ on a $\mathbb Z_\ell$-basis of $T$ with integral differences under all $G_K$. On the level-$M$ cyclotomic group, the [embedding comparison](../zh/%E6%80%8E%E6%A0%B7%E7%94%A8%E5%8F%AF%E5%88%86%E5%B9%82%E7%AD%89%E5%85%83%E6%8A%BD%E5%87%BA%E4%B8%80%E4%B8%AA%E5%B5%8C%E5%85%A5%E7%9A%84%E6%99%B6%E4%BD%93%E6%AF%94%E8%BE%83%E6%A1%86%E6%9E%B6.md) `exists_tau_component_frame_of_lattice` gives an intertwining matrix $P$ to the $\tau$ component over $\mathbb C_\ell$. For source and target balls $B_d,B_a$ it gives
$$
B_a\subseteq P(B_d),\qquad \ell P(B_d)\subseteq B_a,\qquad
y'\in\mathbb Q_\ell^d,\ Py'\in P(B_d)\ \Longrightarrow\ y'\in\mathbb Z_\ell^d.
$$
It also gives the small-norm frame and a Hodge–Tate basis with weights $J$ among the jumps at $\tau$. Therefore $Py$ is an approximate invariant modulo $P(B_d)$ and zero is missing. If $J$ is nonempty, the [missing-weight bound](missing-hodge-tate-weights-control-approximate-invariants.md) gives integrality of its image after multiplication by $\ell^{2+\sum_{u\in J}(M+v_\ell(u))}$. The comparison reflects this integrality to $y$. If $J$ is empty, the target is zero and integrality already follows from the same comparison. We can enlarge the exponent to
$$
c_\tau=2+\sum_{u\text{ a jump at }\tau}(M+v_\ell(u)),
$$
summing distinct jumps. It kills the original class.

## Passing to a single uniform bound

Let $K'=\mathbb Q_\ell(\mu_{\operatorname{lcm}(\ell,N)})$. It equals its own level-$s$ cyclotomic extension over its unramified part, is contained in $L$, and satisfies the input domain conditions by `exists_up`. Restrict $V,T$ there. Crystallinity and the filtration jumps are preserved under restriction along every embedding of $K'$ into $L$. A $G_K$-fixed class is still fixed on $G_{K'}$ in the same quotient. The source permits the larger comparison exponent
$$
c_{\rm int}=v_{\deg}+2+\max\left(1,\sum_{u\in U'\setminus\{0\}}(M+v_\ell(u))\right),
$$
where $U'\subseteq U$ is the union of jumps and $v_{\deg}$ is the degree valuation difference from level $s$ to $M$. The cyclotomic degrees give $0\le v_{\deg}\le M$. If $a=\lfloor\log_\ell(2h)\rfloor$, minimality gives $M\le2s+a+2$ and $M+a\le2\lambda$. Every nonzero $u$ has $v_\ell(u)\le a$. Hence the sum is at most $2n\lambda$, and $c_{\rm int}\le2\lambda+3(n+1)\lambda\le c_0$. If jump sets are originally given separately with size $\le r$ at each of $a_0$ embeddings, take their union of size at most $a_0r$. The row uses $a_0\le4 n_{\rm row}$ and $r\le n_V$.

Finally the $\ell^{c_0}$-torsion of $V/T$ is $\ell^{-c_0}T/T\simeq T/\ell^{c_0}T$. Since $T$ is free of rank $r$, its normalized length is $rc_0$, bounding the invariant submodule.

## Lean correspondence

- [`invariants_killed`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/InvariantsVanishAtPrimeOfAdmissible.lean#L29), [`killed_of_coordinates`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/InvariantsVanishAtPrimeOfAdmissible.lean#L156), and [the component frame](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsTauComponentFrameOfLatticeStatement.lean#L9) give the integral comparison.
- [`torsion_exponent_kills_invariants_no_jump_zero`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TorsionExponentKillsInvariantsNoJumpZero.lean#L53), [cyclotomic restriction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ResidueCharacters/InvariantsKilledOverCyclotomic.lean#L14) and [the exponent bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ResidueCharacters/LocNum.lean#L71) give the uniform bound.
- [`kill_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ResidueCharacters/InvariantsLengthAdmissibleOfNonzeroJumps.lean#L30) and [`length_invariants_Wprime_divisible_le_of_nonzero_jumps`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ResidueCharacters/InvariantsLengthAdmissibleOfNonzeroJumps.lean#L74) combine the jumps and convert the annihilation to length.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
