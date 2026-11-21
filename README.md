# Riemann Hypothesis Proof Notes

[简体中文](README.zh-CN.md) · [Proof map](PROOF-MAP.md) · [English catalogue](PROOFS.en.md) · [Review status](STATUS.md)

A bilingual reconstruction of the Lean argument for the **Riemann Hypothesis (RH)** and **Dirichlet Generalized Riemann Hypothesis (GRH)** released by Levent Alpöge and Claude. The notes spell out hypotheses, work through the mathematical deductions, and link to the corresponding Lean declarations at a fixed revision.

## Start reading

1. **[See the proof map](PROOF-MAP.md).** Follow the geometric and arithmetic inputs through the weighted prime sums to the zero-free conclusion. The map identifies the connections still being written.
2. **[Read from window estimates to RH](proofs/en/from-windows-to-rh.md).** Start with an upper bound on arbitrarily late multiplicative windows and follow it to the critical line. The [pole calculation](proofs/en/pole-data.md) and [Landau window lemma](proofs/en/landau-window.md) give the details.
3. **[Trace where the upper bound comes from](proofs/en/assembling-a-window-family.md).** The notes on [local valuations and prime-power weights](proofs/en/from-orbit-valuations-to-the-prime-power-count.md) and [the common window](proofs/en/common-window.md) open two of the upstream branches.

The [English catalogue](PROOFS.en.md) pairs all 340 [Chinese notes](PROOFS.zh-CN.md) with English versions and includes further English reconstructions. The complete prose exposition is still in progress. The [review status](STATUS.md) records the scope of the drafts and the remaining dependencies. Andrew Sutherland's [independent verification report](https://math.mit.edu/~drew/grh/) documents the checks of the formal Lean proof.

## Sources and review

[Original announcement](https://alpo.ge/remark.pdf) · [Pinned Lean source and attribution](SOURCES.md) · [Report a correction or submit a review](CONTRIBUTING.md) · [License](LICENSE.md)
