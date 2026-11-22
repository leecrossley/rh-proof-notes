# Character orthogonality explains the selected moment denominator

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $p=\pi\bar\pi$ be a split word prime, $f=\#\{P:P\mid\pi\}$, and $a$ the source rank. For the standard word-prime pair let $M$ and $M''$ be the period lattices for the original and companion targets. Put $F=fa$. Let $\omega$ be the integral alternating period pairing, under which both period lattices are self-dual and $\omega(rx,y)=\omega(x,\bar r y)$. Use the intermediate half-lattice $B$ of the induced theta, with $g(\pi/\bar\pi)M\subseteq B$ and $g(\bar\pi/\pi)B\subseteq M$ for an integer $g$ prime to $p$. The pairing and the translation cocycle are integral on $B\times B$. With $c$ the prime-to-$p$ box denominator, set $C=cg\bar\pi(M\cap M'')$. Let $Z$ be the box congruence lattice and $J$ represent $C/(C\cap Z)$. Assume the box relation $cg\bar\pi y\in Z$ for $y\in M$ holds exactly for $y\in\pi M$. Use the induced theta formula for $x+j$, $j\in J$,
$$
\Theta_{x+j}
=\frac1n W(-t_0)W(-j)\sum_{y\in R}W(y)e ,
\qquad 0<n\mid[M:M\cap B],\quad R\text{ represents }B/(B\cap M),\quad n>0 .
$$
Here $W$ is the normalized Weil translation, $e$ the original normalized theta and $t_0$ a chosen lift of $x$. Under the move and rational-translate hypotheses specified below, the jet table of $\sum_{j\in J}\Theta_{x+j}$ has integral closure in the tables $p^{-F}\operatorname{ptTab}(t,m)$ for $t\in M''$. The support in the operator theorem follows because an element of $M''$ has its adjoint integral on the companion target, which agrees locally with the intended hyperplane at $P\mid\pi$.

### The character filter and the surviving translations

The vacuum $e$ is fixed by $W(M)$, and $C\subseteq M$. Commuting $W(-j)$ past $W(y)$ therefore leaves just the phase $\exp(\pm2\pi i\omega(j,y))$. This is a character on $C/(C\cap Z)$, because $C\cap Z\subseteq B$ and $\omega$ is integral on $B$. Its sum is $|J|$ when the character is trivial and zero otherwise. In the latter case multiplication by an element with character different from one multiplies the sum by that value and permutes its terms. The surviving lattice is
$$
B'=\{y\in B:\omega(C,y)\subseteq\mathbb Z\}.
$$
It contains $B\cap M$, since $C\subseteq M$. Let $B_1=B\cap M''$ and $B_2=pB$. Both are contained in $B'$. For $B_1$ use $C\subseteq M''$ and self-duality. For $pB$ move $p$ to the first argument of the pairing, and use $pC\subseteq g(\pi/\bar\pi)M\subseteq B$. The latter inclusion follows by comparing the scalar multiples, since $p=\pi\bar\pi$.

If $y\in B'$, for $m\in M''$ we have $\bar\pi m\in M\cap M''$. Pairing $y$ with $cg\bar\pi^2m$ and transferring the scalar gives $\pi^2cg\,y\in M''$ by self-duality. Also $\bar\pi cg\,y\in M''$ by $g(\bar\pi/\pi)y\in M$ and $\pi M\subseteq M''$. Bézout for $\pi^2,\bar\pi$ gives $cg\,y\in M''$. Bézout for $cg,p$ then writes $y$ as a sum of an element of $B_1$ and an element of $pB$. For $y_2\in pB$ one has $gy_2\in M$ by $g(\bar\pi/\pi)B\subseteq M$. If $y_1\in B_1$ and $y_1+y_2\in M$, then $gy_1\in M$ and also $\bar\pi y_1\in M$, so $y_1\in M$. Thus the surviving cosets decompose as a product of the two coset sets.

Representatives $R_1$ of $B_1/(B_1\cap M)$ also represent $M''/(M''\cap M)$. To see surjectivity, for $m\in M''$ one has $g\pi m\in B_1$, since $\bar\pi m\in M$ and $g(\pi/\bar\pi)M\subseteq B$. Also $\bar\pi m\in M$. A Bézout relation for $g\pi,\bar\pi$ puts $m$ in $B_1$ modulo $M$. Put $k=|R_1|$. Self-duality gives equality of the two relative indices of $M$ and $M''$, since $\omega\bmod\mathbb Z$ pairs the two finite quotients with zero kernel in each argument. Consequently $k=[M:M\cap M'']$ divides $p^F$ by [the companion index bound](a-hyperplane-companion-pays-one-residue-factor-per-source-column.md).

### The size of the coefficient

On $B$ the integral cocycle means the translate of a sum of directions is the composition of translates. Write $R_2$ for representatives of $B_2/(B_2\cap M)$. Use the normalized theta move law $\sum_{y_1\in R_1}W(y_1)e=\sqrt{k}\,\kappa e''$, with $e''$ the companion theta and $\kappa$ algebraic. The surviving sum is then a sum of translates $W(y_2-t_0)e''$ for $y_2\in R_2$, each with coefficient
$$
A_{y_2}=\frac{|J|}{n}\sqrt{k}\,\kappa\,\zeta_{y_2}.
$$
Here $\zeta_{y_2}$ is a cocycle phase with rational argument modulo $1$, hence a root of unity. The move character comes from the relative determinant ideal $(\pi/\bar\pi)$. Its exponent in the move formula is $a/2$: the character on this principal norm-one ideal is the inverse product of its CM images. Each inverse image has $p$-adic norm at most $p$, since $\pi\bar\pi=p$ and each conjugate of $\bar\pi$ is integral. Thus $|\kappa|_p^2\le p^F$.

Since $g\pi M\subseteq B\cap M$, $n$ divides $[M:g\pi M]$. By the assumed box relation, $|J|=[M\cap M'':\pi M]$. Hence
$$
[M:g\pi M]=k\,|J|\,[\pi M:g\pi M],
$$
where the last factor is prime to $p$. It follows that $|\,|J|/n\,|_p\cdot |k|_p\le1$, and $k\mid p^F$ gives $|\,|J|/n\,|_p\le p^F$. Using $|\sqrt{k}|_p^2=|k|_p$, the square of the norm of $A_{y_2}$ is at most $p^F\cdot1\cdot p^F=p^{2F}$. Thus $A_{y_2}$ is an integral multiple of $p^{-F}$ after embedding.

Finally the chosen lift obeys $cgt_0\in M$ in this branch, and $gy_2\in M$. The resulting $cg(y_2-t_0)\in M$ gives $cg\pi(y_2-t_0)\in M''$. [The rational-translate moment theorem](bezout-separates-the-two-parts-of-a-split-theta-translate.md) for the companion gives integral closure in its unscaled point tables for every translate of this kind, since $cg$ is prime to $p$. Multiply these closures by the bounded coefficients and add the finite sum. That proves the claimed normalization and support. The formula for the induced vector comes from [the indicator transform](the-induced-theta-is-a-finite-period-translate-sum.md). The normalized theta move is the remaining input to the change of target.

### Lean correspondence

- [`lat`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MomentsCosetSum.lean#L36) proves the lattice product decomposition.
- [`charsum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MomentsCosetSum.lean#L301), [`prodsum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MomentsCosetSum.lean#L329), [`idx`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MomentsCosetSum.lean#L243) and [`size`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MomentsCosetSum.lean#L168) give the filter, sum, index divisibility and coefficient bound.
- [`moments_coset_sum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MomentsCosetSum.lean#L363) combines them, with [`type_p`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MemSuppBarOfNe.lean#L267) identifying the operator support.
- [`chi_move`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/RelDetCompanion.lean#L258) and [`move`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/NegOneZpowRound.lean#L100) compute the character and power in the move.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
