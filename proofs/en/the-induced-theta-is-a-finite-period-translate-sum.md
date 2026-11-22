# The induced theta is a finite period translate sum

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $M$ be the full period lattice for a self-dual Hermitian lattice pair, with normalized theta $e$ fixed by the normalized translations $W(l)$ for $l\in M$. Let $S$ be a finite set of primes of the CM coefficient field, with $S$ disjoint from its conjugate. Put $\epsilon_Q=1$ on $S$, $-1$ on its conjugate, and $0$ elsewhere. For a positive integer $c$, the first and second half-lattices $A_c,B_c$ are given at $Q$ by $c^{-\epsilon_Q}M_Q,c^{\epsilon_Q}M_Q$, respectively. In the source the alternating pairing and the normalized translation cocycle are obtained from the Hermitian trace pairing. Use its integrality criterion: two directions have integral cocycle if at every $Q$ one can multiply the first direction by a nonzero scalar and the second direction at $\bar Q$ by the inverse conjugate scalar to put both in the localized period lattices.

For a box point $x$, assume an admissible rational lift $t\in A_D$ for some $D>0$ satisfies $t-x\in c\operatorname{Hom}_P$ at every $P\in S$, where the localized period ideal is the unit ideal so $\operatorname{Hom}_P=M_P$. Let $R$ be representatives of $B_c/(B_c\cap M)$, and put
$$
n=[M\cap A_c:M\cap A_c\cap B_c]>0.
$$
Then $n\mid[M:M\cap B_c]$, and the induced theta at $x$ equals
$$
\Theta_x=\frac1n W(-t)\sum_{y\in R}W(y)e.
$$

### The Fourier coefficient and the volume factors

The two half-lattices are commensurable with $M$, so all the indicated quotients are finite. The inclusion $M\cap A_c\subseteq M$ injects its quotient by the intersection with $B_c$ into $M/(M\cap B_c)$, giving the divisibility of $n$. On $B_c\times B_c$, the cocycle is integral: for $y,y'\in B_c$ use $c^{-\epsilon_Q}$ for the scalar in the criterion, whose inverse at $\bar Q$ is $c^{\epsilon_Q}=c^{-\epsilon_{\bar Q}}$. As the alternating form is the skew part of the cocycle, its pairing on $B_c$ is integral too.

By definition the induced theta uses the Fourier transform on the first half-lattice, with input the indicator of $B_c$. At each $y\in R$, the transform is a sum over $n$ representative points in $M\cap A_c$. Only the zero coset of $B_c$ contributes, and its bracket with $y$ is one by integrality on $B_c$. Thus the inner unnormalized sum is $1$. With $v>0$ the volume normalizer, the Fourier coefficient is $v^{-1/2}(v/n)$. The outer induction at the chosen lift supplies a second factor $v^{-1/2}$. These cancel to $1/n$. The remaining factors in each summand are $W(y)e$, followed by $W(-t)$ on the entire sum, which gives the formula.

### Independence of the rational lift

Two lifts $t\in A_D$, $s\in A_{D'}$ need not use the same $D,D'$. They have $t-s\in cM_P$ at $P\in S$. At a conjugate prime their own first-half lattice conditions make both integral, so $t-s\in c^{-1}M_Q$. At all other primes their difference is integral. This proves $t-s\in B_c$. The criterion also makes the cocycle of $t,s$ integral. At $P\in S$ one may put $D't$ in $M_P$ because $D's\in M_P$ and $t-s$ is integral there, and $s/D'\in M_{\bar P}$ by its first-half lattice condition. At the conjugate prime use $t/D\in M_{\bar P}$ and $Ds\in M_P$, since $Dt\in M_P$ and $s-t$ is integral there. At the other primes use scalar $1$. The same criterion makes the cocycle of $t,t$ integral. Bilinearity gives integrality for $(-t,t-s)$.

The sum $\sum_{y\in R}W(y)e$ is independent of representatives, since the cocycle is integral on $B_c$ and $W(M)$ fixes $e$. It is fixed by $W(B_c)$, since translating the representatives by an element of $B_c$ permutes the cosets and inserts no phase. It follows that applying $W(-t)$ or $W(-s)$ to it gives the same result, using the integral cocycle of $(-t,t-s)$. This also verifies the formula with any admissible choice of lift. In the selected-side sum the lifts $t+j$ used for $x+j$ have integral $(t,j)$ cocycle by the same half-lattice criterion on the first half-lattice. Hence their outer factor can be written $W(-t)W(-j)$, as in the finite character filter.

### Lean correspondence

- [`hatS`, `xiS` and `xiInd`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/XiIndCClass.lean#L20) give the finite transform and translation. [`halfAO` and `halfBO`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/XiIndCClass.lean#L187) give the localized half-lattices.
- [`hatS_ind`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ThetaMovedCosetIndicatorVacuumShape.lean#L71) evaluates the indicator transform.
- [`two_lifts`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ThetaMovedCosetIndicatorVacuumShape.lean#L241) compares lifts, and [`thInd_shape`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ThetaMovedCosetIndicatorVacuumShape.lean#L284) proves the finite sum formula.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
