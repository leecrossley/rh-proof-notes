# RH Proof Notes

[中文首页](README.zh-CN.md) · [English proof catalogue](PROOFS.en.md) · [Chinese proof catalogue](PROOFS.zh-CN.md) · [Reading and review status](STATUS.md) · [Contributing](CONTRIBUTING.md)

A bilingual reading project for the Lean proof of RH and Dirichlet GRH released by Levent Alpöge, working with Claude. The notes state the assumptions, work through the mathematical deductions, and link to the Lean declarations at a fixed revision. They are written for readers who want to follow the arguments without opening a Lean environment. [Original announcement](https://alpo.ge/remark.pdf) · [Sources and attribution](SOURCES.md)

## Where to start

1. [From window estimates to RH](proofs/en/from-windows-to-rh.md) gives the main route and shows how the analytic conclusion follows from the window estimate.
2. [The Landau window lemma](proofs/en/landau-window.md) proves the analytic step. [The residue calculation](proofs/en/pole-data.md) explains why every zero supplies a pole and why these residues cannot cancel.
3. [One window for two estimates](proofs/en/common-window.md) works through the choice of scale and the change of cutoff from 401 to 400.
4. [From period valuations to an integral lattice map](proofs/en/integral-lattice-map.md) shows how local divisibility becomes integrality of a global pairing.
5. [From Dirichlet nonvanishing to RH](proofs/en/from-dirichlet-nonvanishing.md) and [RH from the right half-plane](proofs/en/rh-from-right-half-plane.md) are short English proofs adapted from Tam Nguyen Duc's project under CC BY 4.0.

The English notes on the [finite Fourier identity](proofs/en/finite-fourier-balance.md), [translation averaging](proofs/en/translation-averaging.md), and [primitive characters](proofs/en/primitive-characters-from-inertia.md) explain the passage from an arithmetic count-discrepancy bound to the pointwise estimate on a weighted prime sum.

The [English proof catalogue](PROOFS.en.md) covers all 340 notes in the [Chinese proof catalogue](PROOFS.zh-CN.md), with both catalogues arranged by topic. Additional English reconstructions follow the local theta expansion and the determinant estimates that give the odd prime-power terms in the arithmetic count. The [status page](STATUS.md) records the scope, remaining dependencies and review state of the exposition, and links to the Lean verification report.

For the origin of the weights, start with [Prime powers in the jet coefficient bound](proofs/en/prime-powers-in-the-jet-coefficient-bound.md) and follow the chain through [top-row capacities](proofs/en/top-row-capacities-and-prime-power-ramps.md) to [the prime-power count](proofs/en/from-orbit-valuations-to-the-prime-power-count.md).

For the theta expansion used as input there, start with [From host integrality to the all-place theta expansion](proofs/en/from-host-integrality-to-the-all-place-theta-expansion.md). It links to the proofs of the hyperbolic sum, the integral logarithmic coordinates, and root-of-unity averaging.

For the curve underlying that expansion, [Assembling the inert CM curve data](proofs/en/assembling-the-inert-cm-curve-data.md) leads to the good-model, torsion and isogeny arguments for the formal exponent.

Contributions in **English or Chinese** are welcome. [How to contribute](CONTRIBUTING.md) · [CC BY 4.0 and attribution](LICENSE.md)
