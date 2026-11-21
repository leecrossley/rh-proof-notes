# Assembling the pointwise witnesses into one window family

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E6%8A%8A%E9%80%90%E7%82%B9%E6%9E%84%E9%80%A0%E6%8B%BC%E6%88%90%E7%AA%97%E5%8F%A3%E4%B8%8A%E7%9A%84%E5%90%8C%E4%B8%80%E4%B8%AA%E6%95%B0%E6%8D%AE%E6%97%8F.md) · [Reading and review status](../../STATUS.md)

Fix $\lambda>1$ and $0<\varepsilon<1/52$. A scale system `Scales λ` specifies $J\ge1$ and $W\subseteq\mathbb R$ containing arbitrarily late complete intervals $[Y,Y^\lambda]$. For $x>1$, the project's scale $s(x)$ is determined by $x,\varepsilon,J$.

**Claim.** Fix the standard constant table $C$ satisfying `Std C` and $C.\mathrm{GK}\ge0$, real parameters $c_D,c_h$, and a threshold $x_1>1$. Suppose each $x\ge x_1$ in $W$ supplies a `Kit C cD ch (s x)` and a proof `NumAt` of the numerical bounds for each of its rows. Then there is a family `FamP ε` with threshold $x_1$ and scale system $J,W$. At $x>x_1$ every row comes from the kit at $x$. A pointwise property shared by all input rows is therefore valid for every such row in the assembled family, including the numerical conditions on row parameters.

A kit is a nonempty collection of rows at a fixed scale. Its rows give fields, lattices and operators, together with their parameters and arithmetic properties. The kit requires the rows to share the scale, rank, host field, specified auxiliary primes and an identified word set. `NumAt` records the bounds on the row parameters.

## Keeping the rows at the correct scale

Choose $y\in W$ with $y\ge x_1$, which is possible from the window property. For every real $x$ put

$$
a(x)=
\begin{cases}
x,&x>x_1\text{ and }x\in W,\\
y,&\text{otherwise}.
\end{cases}
$$

Thus $a(x)$ is always a scale at which a kit is available. Use the row set of the kit at $a(x)$ when $x\le x_1$ or $x\in W$, and the empty row set otherwise. For $x>x_1$ a nonempty row set then implies $x\in W$ and $a(x)=x$. In particular the physical scale of the row equals its index.

Copy each row's field, lattice, operators and local lengths from that row of the selected kit. The numerical bounds follow from `NumAt` and the shared data from the kit's conditions across rows. Use $W$ as the window set. At its points the row set is nonempty. All the eventual pointwise properties hold because the rows at $x>x_1$ are precisely old rows at $x$. The entries at $x\le x_1$ fill out the definition and do not enter the eventual estimate.

The requirement $J\le C_8$ of the host parameters follows by taking any row at the fallback scale $s(y)$ and applying its host bound: every kit uses the same $J$. This verifies the alignment of the new family constants with the standard table in `exists_famP_of_kits`.

## Choosing one constant table for two requirements

The application must meet the caller's requirement $K$ and the lower requirement $K_0$ of the pointwise construction. Each has an initial scalar lower bound, an intermediate bound depending on the outer table, and a final bound depending on the outer and intermediate tables. The standard table `stdConst` assigns one common number within each of its three variable groups.

Set the first number to $\max(1000,K.\mathrm{pre},K_0.\mathrm{pre})$. This fixes the outer table, so set the second number to the maximum of $1$ and the two intermediate bounds evaluated on that table. Only after both tables are fixed, take the maximum of $1$ and the two final bounds evaluated on them. The resulting constant table meets both requirements. Each comparison uses only the data already chosen at that step.

The parameter $C_{Tu}$ uses its standard value during the row construction, but the final family requires the value $c_T(\varepsilon,9)$. Before choosing the constants, modify the intermediate and final requirement functions to replace this coordinate in their input by its target value before evaluation. Build the family and then set the coordinate to that value. The identity `setTu_large` gives the original requirement $K$ on the final family. The rows themselves are unaffected by this last substitution.

## How the project obtains the kits

The construction `kitS` uses two inputs. The first supplies a common host field, primes, weights and window conditions at every point of the scale system. The second, given that host input, supplies an indexed object for each $0\le i<n$. Take the maximum of the constants required by the two inputs and choose the $n$ objects with the same host and binary word injection. This gives the across-row conditions. See the Chinese proof of the [binary word count](there-are-enough-binary-words-to-index-the-objects.md).

In `designS` one uses $\varepsilon\le1/53$ to satisfy the strict bound $\varepsilon<1/52$. The construction of the rows and the proof of their numerical ranges give two successive parameter thresholds each. Take their maxima in the order of dependence. For $x_1$, take the maximum of $2$ and the two scale thresholds. The preceding claim then gives the family. Each row's word count is $\lceil3\Gamma^2 x^{C_H}\rceil$, which is at least $3\Gamma^2x^{C_H}$ and strictly less than $3\Gamma^2x^{C_H}+1$. The [Minkowski divisibility input](minkowskis-order-bound-and-the-auxiliary-denominator.md) gives the denominator restriction in each row. The host data furnish the rescaling window and the property $G$ for this same family. Along with the rowwise quadratic twist bounds, these are outputs of `DesignChoices`, used in [family selection](joint-family-selection.md).

## Lean references and review

- The scale system is [`Scales.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/PrimeDiscriminants/Scales.lean). The operations `cutScale` and `famOfKits` and the theorem [`exists_famP_of_kits`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsFamPOfKits.lean#L159) transfer the rows to the family.
- Constant choice, the numerical ranges and the final substitution are [`exists_std_large`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsStdLarge.lean#L39), [`szRow_numAt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SzRowNumAt.lean) and [`setTu_large`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/AuxiliaryPrimeMemAvoidedPrimes.lean#L149).
- [`ClassSel.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/ClassSel.lean), via `recS`, calls [`kitS`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/KitS.lean) and [`designS`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/DesignS.lean#L21). The shared hosts come from `hostWW` and the pointwise objects from [`existsObjects_of_admissibleTwistDatum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/ObjCTrue.lean).

English translation draft. The geometric construction of the pointwise witnesses is an input to the assembly.
