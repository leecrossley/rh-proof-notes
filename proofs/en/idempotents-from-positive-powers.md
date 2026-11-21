# An idempotent limit preserves relations of all positive powers

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E4%BB%8E%E6%AD%A3%E6%95%B4%E6%95%B0%E5%B9%82%E4%B8%AD%E5%8F%96%E5%BE%97%E4%BF%9D%E6%8C%81%E5%8E%9F%E6%9C%89%E5%85%B3%E7%B3%BB%E7%9A%84%E5%B9%82%E7%AD%89%E5%85%83.md)

**Proposition.** Let $\ell$ be prime, $R$ a unital $\mathbb Z_\ell$-algebra finite as a module, and $b\in R$. There is an idempotent $E\in R$ such that for every $\mathbb Z_\ell$-submodule $M\subseteq R$ and $c\in R$, if $b^n-c\in M$ for every integer $n\ge1$, then $E-c\in M$. Multiplication in $R$ may be noncommutative.

With the $\ell$-adic topology the finite module $R$ is compact, complete and separated by the structure theorem over $\mathbb Z_\ell$. Every submodule $M$ is finitely generated and is the continuous image of a finite power of $\mathbb Z_\ell$ by a spanning map. Thus $c+M$ is closed. In the finite ring $R/\ell^j R$, the positive powers of $\bar b$ eventually repeat with some period $d\ge1$ starting at exponent $s$. For large $k$, $k!\ge s$ and $d\mid k!$. Hence $\bar b^{k!}$ stabilizes as $k\to\infty$ and equals $\bar b^{2k!}$. This holds for every $j$, so $b^{k!}$ converges to $E\in R$. The stabilized reductions are idempotent and $R$ is separated, so $E^2=E$. If all positive powers lie in $c+M$, closedness puts $E$ there as well.

For matrix functions, an already idempotent evaluation at $\pi$ stays fixed on all positive powers. Take $M$ to be the kernel of evaluation to preserve that value. A subalgebra containing $b$ contains its powers and the limit. For $Qb=0$ or $bQ=0$, take the respective multiplication kernel to obtain $QE=0$ or $EQ=0$. These facts give the [two orthogonal projections](orthogonal-projections-from-an-integral-representation.md).

## Lean correspondence

- `exists_idempotent_sub_mem_of_pow_sub_mem` uses compactness of the closure of the positive powers. The factorial sequence above explicitly realizes an idempotent there. [Limit](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsIdempotentSubMemOfPowSubMem.lean#L25)
- `GlobalTheory.SpanIdem.exists_idem` applies the result to the subalgebra, evaluation and multiplication kernels. [Application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsOrthogonalIdempotentsHeckeSpanRep.lean#L84)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
