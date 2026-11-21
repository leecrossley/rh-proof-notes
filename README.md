# RH Proof Notes

[中文首页](README.zh-CN.md) · [Chinese proof catalogue](PROOFS.zh-CN.md) · [Reading and review status](STATUS.md) · [Contributing](CONTRIBUTING.md)

A bilingual reading project for the Lean proof of RH and Dirichlet GRH released by Levent Alpöge, working with Claude. The notes state the assumptions, work through the mathematical deductions, and link to the Lean declarations at a fixed revision. They are written for readers who want to follow the arguments without opening a Lean environment. [Original announcement](https://alpo.ge/remark.pdf) · [Sources and attribution](SOURCES.md)

## Where to start

1. [From window estimates to RH](proofs/en/from-windows-to-rh.md) gives the main route and shows how the analytic conclusion follows from the window estimate.
2. [The Landau window lemma](proofs/en/landau-window.md) proves the analytic step. [The residue calculation](proofs/zh/pole-data.md) gives the companion derivation in Chinese.
3. [One window for two estimates](proofs/en/common-window.md) works through the choice of scale and the change of cutoff from 401 to 400.
4. [From period valuations to an integral lattice map](proofs/en/integral-lattice-map.md) shows how local divisibility becomes integrality of a global pairing.
5. [From Dirichlet nonvanishing to RH](proofs/en/from-dirichlet-nonvanishing.md) and [RH from the right half-plane](proofs/en/rh-from-right-half-plane.md) are short English proofs adapted from Tam Nguyen Duc's project under CC BY 4.0.

The [Chinese proof catalogue](PROOFS.zh-CN.md) contains 340 full-length notes, including the arguments behind the window estimate and supporting results on primes in progressions, cohomological lengths, and local Galois representations. Six English notes are linked above. The [status page](STATUS.md) tracks the hypotheses used in the reading path, outstanding links in the exposition, and human review separately from verification of the Lean code.

Contributions in **English or Chinese** are welcome. [How to contribute](CONTRIBUTING.md) · [CC BY 4.0 and attribution](LICENSE.md)
