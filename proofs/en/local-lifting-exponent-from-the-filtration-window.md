# The local lifting exponent depends on the filtration width

[Chinese proof](../zh/%E5%B1%80%E9%83%A8%E6%8F%90%E5%8D%87%E6%8C%87%E6%95%B0%E4%B8%BA%E4%BB%80%E4%B9%88%E5%8F%AA%E4%BE%9D%E8%B5%96%E8%BF%87%E6%BB%A4%E7%AA%97%E5%8F%A3%E7%9A%84%E5%AE%BD%E5%BA%A6.md)

Let $\ell\ge3$ be prime, $K_w/\mathbb Q_\ell$ finite unramified, and $L/\mathbb Q_\ell$ finite containing all images of $K_w(\mu_\ell)$, with integers $\mathcal O$. Let $(V_x)$ be continuous finite-dimensional crystalline $L$-representations of $G_{K_w}$ whose de Rham filtration jumps at each embedding belong to $[-M,h]$ for integers $M,h\ge0$. Let $U_1,U_2$ be subquotients of finite direct sums of the $V_x$, with stable full lattices $T_1,T_2$. Let $F:U_1\to U_2$ be equivariant and linear with $F(T_1)=T_2$. Here $H^1_f(G,T)$ is the submodule of integral cohomology whose classes become coboundaries after adjoining $B_{\rm cris}$ to the rational representation.

**Proposition.** Under the project period comparison and the Case A crystalline lifting theorem, every integer
$$
e'\ge 23\left(2+\frac{M+h}{\ell}+\log_\ell(M+h+1)\right)
$$
satisfies $\ell^{e'}H^1_f(G_{K_w},T_2)\subseteq F_*H^1_f(G_{K_w},T_1)$. This is the column `LiftAt` condition. On a representative $c_2$ it gives $\ell^{e'}c_2(g)=F(c_1(g))+gv-v$ for all $g$, with $c_1$ a finite cocycle and $v\in T_2$.

Crystalline representations are closed under finite sums, subobjects and quotients, and the de Rham filtration is strictly exact in these sequences. Thus $U_1,U_2$ are crystalline with the same jump window. Put $H=M+h$ and let $S$ be the set of all source jumps over all embeddings. Case A, at the first cyclotomic layer for the unramified base and odd prime, gives the inclusion with exact exponent $e_A=2e_W+e_U$ from the [Wach lifting argument](crystalline-lifting-cost-of-two-wach-exponents.md), where
$$
\begin{aligned}
J&=\{a+j:a\in S,\ 1\le j\le M,\ a+j\ne0\}\cup\{1,\ldots,M\},\\
a_0&=\left\lfloor M/(\ell-1)\right\rfloor+1,\quad
e_W=\left\lfloor H\ell/(\ell-1)^2+3+\log_\ell(H+1)\right\rfloor,\\
e_U&=\sum_{j\in J}v_\ell(j)+a_0+v_\ell(a_0!).
\end{aligned}
$$
The embedding hypothesis allows the first cyclotomic layer in the comparison.

If $M=0$ then $J$ is empty. Otherwise $J\subseteq[-(M-1),H]\setminus\{0\}$, so its total valuation is at most $v_\ell((M-1)!)+v_\ell(H!)\le2H/(\ell-1)$ by the Legendre formula $v_\ell(n!)=\sum_{b\ge1}\lfloor n/\ell^b\rfloor\le n/(\ell-1)$. This last bound for the total holds also when $M=0$. Using $a_0\le H/(\ell-1)+1$ gives
$$
e_A\le \frac{2H\ell}{(\ell-1)^2}+6+2\log_\ell(H+1)
+\frac{2H}{\ell-1}+\left(1+\frac1{\ell-1}\right)\left(\frac{H}{\ell-1}+1\right)
\le\frac{39H}{4\ell}+\frac{15}2+2\log_\ell(H+1).
$$
The last estimate uses $\ell/(\ell-1)\le3/2$. This is below the stated bound. Multiplying the inclusion for $e_A$ by $\ell^{e'-e_A}$ keeps the image in the source image submodule. For split primes the project applies the same argument to the original twist and the dual twist with jumps in $[-h_N,h_N]$, taking $H=2h_N$ and rounding the bound up for the common exponent.

## Lean correspondence

- `LiftAt` and `LatHom.LiftF` state the integral lifting quantified over the lattices. `subquot_crys` transfers crystallinity and `coreLiftA` is the case-specific input. [Statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/QuotientHomNonvanishingBound.lean#L148) · [Case A](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/LiftingTheory.lean#L219)
- `arith_sizeA` bounds the exact exponents. `lift_of_window` and `shape_le_eA` apply the uniform bound on both sides. [Arithmetic](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/FrobeniusPowUniformizerFactorisation.lean#L1799) · [Window](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/LiftColumnRowSetup.lean#L31) · [Split-prime application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/ImportsFurtherMore.lean#L22)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
