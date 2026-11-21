# CM conjugation reflects Hodge–Tate weights with a common weight

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88CM%E5%85%B1%E8%BD%AD%E6%8A%8AHodge%E2%80%93Tate%E6%9D%83%E5%8F%8D%E5%B0%84%E5%88%B0%E5%90%8C%E4%B8%80%E4%B8%AA%E6%95%B4%E6%95%B0.md)

## Statement

Let $E/F$ be a CM extension with involution $c$, $a\ge1$, and $\pi$ a cuspidal automorphic representation of $\mathrm{GL}_a(\mathbb A_E)$. Take a continuous Hecke character $\chi$ of $F$ and $\psi=\chi\circ N_{E/F}$. Assume regular algebraicity, so each normalized infinitesimal multiset $\Lambda_\tau$ for $\tau:E\to\mathbb C$ has $a$ distinct elements in $(a-1)/2+\mathbb Z$. Assume `PolarizedPair`, specifically the nondegenerate conjugate equivariant dual pairing of $\pi\otimes(\psi^{-1}\circ\det)$ with $\pi$. Then some integer $w$ works for all $\tau$:
$$
\Lambda_{\tau c}=\{a-1-w-z:z\in\Lambda_\tau\}.
$$
For $\iota:\overline{\mathbb Q}_\ell\simeq\mathbb C$ and $H_\sigma=\{(a-1)/2-z:z\in\Lambda_{\iota\sigma}\}$, this gives $H_{\sigma c}=\{w-h:h\in H_\sigma\}$. When geometric comparison identifies these multisets with filtration jumps, it gives the Hodge–Tate formula.

## Proof

Let $b_\tau$ be the infinitesimal exponent of $\psi$ at the embedding. Twisting by $\psi^{-1}$ subtracts $b_\tau$, and the dual pairing negates the shifted parameters at the conjugate embedding. Thus $\Lambda_{\tau c}=\{b_\tau-z:z\in\Lambda_\tau\}$. Adding a parameter $z$ and its conjugate partner shows $b_\tau\in\mathbb Z$ by regular algebraicity and $a\ge1$. Since the norm at a complex place is $z\bar z$, $b_{\tau c}=b_\tau$. Write $b_\phi$ for this common exponent over each real embedding $\phi$ of $F$. For totally positive $x\in F^\times$, lift $\phi(x)$ to $\sqrt{\phi(x)}$ at the complex place. The character then has
$$
\chi_\infty(x)=\prod_\phi \phi(x)^{b_\phi}.
$$

For $u\in O_F^\times$, its finite unit idèle belongs to a compact group, so the absolute value of the finite character there is one. The diagonal principal idèle value is one too, giving $|\chi_\infty(u)|=1$. Apply the formula to $u^2$ and take logarithms to get $\sum_\phi b_\phi\log|\phi(u)|=0$. Dirichlet's unit theorem says those logarithms span the hyperplane $\sum_\phi x_\phi=0$, so all $b_\phi$ equal. Equivalently, choose an embedding with least exponent and a unit whose logarithms are negative at all other embeddings. Such a unit exists because the log lattice is full in the hyperplane, by following that direction arbitrarily far and moving to a nearby lattice point. Subtract the least exponent times the norm relation to force each remaining exponent equal. This includes the one-embedding case. Write the common exponent $b$ and take $w=a-1-b$. Substituting a paired pair $z,b-z$ into $(a-1)/2-z$ gives the reflection formula. The [local power sum comparison](operator-power-sums-pass-along-the-lattice-tower.md) enters the identification with filtration weights.

## Lean correspondence

- [`exists_isWeight`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsIsWeight.lean#L25) obtains integrality and uses positive square roots of idèles. [The dual-pairing identity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/InfCharConjEmbeddingNegOfInvariantPairingStatement.lean#L15) supplies the parameter relation.
- [`heckeChar_parallel_weight`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/BuildingsResidueChars/HeckeCharParallelWeight.lean#L178) uses the units. [`IsWeight`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GaloisGeometry/IsWeight.lean#L21) and [`PropsB.weights_conj`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/TypeConditions/WeightsConjBis.lean#L62) give the two normalizations.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
