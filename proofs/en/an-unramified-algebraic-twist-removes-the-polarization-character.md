# An unramified algebraic twist removes the polarization character

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Let $E/F$ be a CM number field, $F=E^+$, $\ell$ a prime, and $a\ge1$. Let $\pi$ be a regular algebraic cuspidal representation of $\mathrm{GL}_a(\mathbb A_E)$, polarized by a Hecke character $\chi$ of $F$. Thus at every real place $\chi_v(-1)=(-1)^a$ and
$$
\pi^c\simeq \pi^\vee\otimes((\chi\circ N_{E/F})\circ\det).
$$
Suppose $\pi$ is good in the following sense. The field $E$ contains a square root of a negative rational integer and $[F:\mathbb Q]$ is even. At every nonsplit finite place $w$ of $E/F$, $\pi_w$ is spherical, $w\nmid\ell$, and $E/F$ is unramified there. Fix any split place $w_0$ of $E$. Then there is an algebraic Hecke character $\kappa$ of $E$, unramified at $w_0$ and at every nonsplit place, such that $\pi'=\pi\otimes(\kappa\circ\det)$ is a good, regular algebraic, conjugate-self-dual cuspidal representation. Its canonical polarization is $\eta_{E/F}^a$, for the quadratic norm character $\eta_{E/F}$. [Exact twisting theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsGoodConjSelfDualTwistSplitUnramified.lean#L65)

## The required real character

The [parallel weight calculation](cm-conjugation-reflects-hodge-tate-weights-about-a-common-integer.md) gives an integer $b$ such that on positive real ideles the character $\chi$ has local exponent $b$ at every real place. Its sign at negative arguments is fixed by $\chi_v(-1)=(-1)^a$. Since $\eta_{E/F,v}$ is sign at each real place, the real Hecke character
$$
\psi=\chi^{-1}\eta_{E/F}^{\,a+|b|}
$$
has exponent $-b$ on positive arguments and sign $(-1)^{-b}$ at $-1$. Thus its complete real character at every place is $x\mapsto x^{-b}$ for $x\in\mathbb R^\times$. This is the role of the auxiliary quadratic factor. Its pullback along $N_{E/F}$ is trivial, so $\psi\circ N_{E/F}=(\chi\circ N_{E/F})^{-1}$. [Parallel exponent and sign correction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsGoodConjSelfDualTwistSplitUnramified.lean#L69)

At a nonsplit place $w$, the conjugation fixes the place. Both $\pi_w^c$ and $\pi_w^\vee$ are spherical. By the polarization, the latter is still spherical after twisting by $(\chi\circ N_{E/F})\circ\det$. A spherical representation is a constituent of an unramified principal series with unramified support. If a character twist of it is spherical, each character in that twisted support must be unramified. Therefore the twisting character is itself unramified. Since $E_w/F_v$ at the lower place $v$ is unramified quadratic, the norm maps local units onto local units by the residue and principal-unit calculation in the [angular character proof](prescribing-a-unitary-hecke-characters-angular-exponents.md#making-the-prescriptions-agree). Thus $\chi_v$ is unramified. The quadratic norm character is also unramified there, so $\psi_v$ is unramified. [Sphericity detects unramifiedness of the twist](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/HeckeCharUnrAtOfSphericalAndTwistSpherical.lean#L43) · [Passing from the norm pullback to the real character](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/HeckeCharUnrAtUnderOfCompNormUnramified.lean#L64)

Apply the [real character extension proof](extending-a-real-hecke-character-while-preserving-the-required-unramified-places.md) to $\psi$ with exponent $-b$. It gives an algebraic $\kappa$ restricting to $\psi$, unramified at $w_0$ and at every nonsplit place. The required hypotheses are exactly the preceding exponent and local unramifiedness conclusions. [Choosing the extension](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsGoodConjSelfDualTwistSplitUnramified.lean#L101)

## The twist is conjugate self-dual

On ideles of $E$, the product $\kappa\kappa^c$ equals the norm pullback of the real restriction of $\kappa$, because multiplication by the conjugate idèle is the norm embedded back into $E$. Thus
$$
\kappa\kappa^c=\psi\circ N_{E/F}=(\chi\circ N_{E/F})^{-1}.
$$
Using the polarization of $\pi$, we obtain
$$
(\pi')^c\simeq
\pi^\vee\otimes((\chi\circ N_{E/F})\kappa^c)\circ\det
\simeq \pi^\vee\otimes(\kappa^{-1}\circ\det)=(\pi')^\vee .
$$
The canonical polarization $\eta_{E/F}^a$ has the required signs and trivial norm pullback. A determinant character twist preserves cuspidality. At each complex embedding its algebraic exponent translates the infinitesimal multiset by an integer, preserving regular algebraicity. At a nonsplit place the twist is unramified, so it preserves sphericality and multiplies the Satake multiset by its local value on a uniformizer. The field and place conditions therefore still hold for $\pi'$. This proves the asserted twist with both local unramifiedness requirements. [Verifying the new polarization and the same good scope](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsGoodConjSelfDualTwistSplitUnramified.lean#L102)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
