# A prime polynomial second moment at fixed modulus

[Chinese proof](../zh/%E5%9B%BA%E5%AE%9A%E6%A8%A1%E6%95%B0%E7%9A%84%E7%B4%A0%E6%95%B0%E5%A4%9A%E9%A1%B9%E5%BC%8F%E4%BA%8C%E9%98%B6%E7%9F%A9.md)

**Proposition.** There is an absolute $C>0$ such that for any integer $q\ge1$, any real $T\ge1$, $N\ge(2qT)^2$, $y\in\mathbb R$, and complex coefficients $a_p$,
$$
\sum_{\chi\bmod q}\int_{-T}^T\left|\sum_{N<p\le y}a_p\chi(p)p^{-it}\right|^2dt
\le C\sum_{N<p\le y}\frac{p|a_p|^2}{\log p}.
\tag{1}
$$
The inner sums range over primes, the outer sum over all characters. The set $P=\{p:N<p\le y\}$ is the project `primesIoc N y`, with the natural-number floors used by Lean. When $P$ is empty both sides vanish.

## Gallagher's short windows

For finitely many real frequencies $\lambda_j$ and complex coefficients $b_j$, put $h=1/T$, $D(t)=\sum_j b_j e^{-it\lambda_j}$ and $f(v)=\sum_j b_j\mathbf1_{[\lambda_j-h,\lambda_j)}(v)$. Using the Fourier transform $\widehat f(w)=\int f(v)e^{-2\pi iwv}dv$, integrate each interval to get $\widehat f(w)=D(2\pi w)\int_0^h e^{2\pi iwu}du$. At $|t|\le T$, the kernel has real part at least $h/2$ because $\cos(tu)\ge1-(tu)^2/2\ge1/2$ on $[0,h]$. By change of variables and Plancherel, $\int_{-T}^T|D(t)|^2dt\le8\pi T^2\int|f|^2$. For $\lambda_p=\log p$ and $b_p=a_p\chi(p)$, set $x=e^v$. This yields
$$
\int_{-T}^T\left|\sum_{p\in P}a_p\chi(p)p^{-it}\right|^2dt
\le 8\pi T^2\int_0^\infty\left|\sum_{p\in P_x}a_p\chi(p)\right|^2dx/x,
\quad P_x=\{p\in P:x<p\le xe^{1/T}\}.
\tag{2}
$$

## Orthogonality and Brun–Titchmarsh

Since $p>N>q$ for $p\in P$, the primes are units modulo $q$. Orthogonality on the finite abelian unit group follows by geometric sums over characters of each cyclic factor. Thus summing the square in (2) over characters gives $\varphi(q)\sum_{r\in(\mathbb Z/q\mathbb Z)^\times}|\sum_{p\in P_x,\ p\equiv r}a_p|^2$. By Cauchy–Schwarz this is at most $\sum_{p\in P_x}\varphi(q)|P_{x,[p]}||a_p|^2$, with $P_{x,[p]}$ the subset of $P_x$ congruent to $p$.

From $e^{1/T}-1\le2/T$, the window is contained in $(x,x+Y]$ for $Y=2x/T$ and each $p\le3x$. As $4(qT)^2\le N<p$, nonempty windows satisfy $x\ge4(qT)^2/3\ge qT$, so $Y\ge2q$. Also $p(qT)^2\le(3x)(3x/4)\le(2x)^2$, hence $\log(Y/q)\ge\frac12\log p$. The [Brun–Titchmarsh bound](brun-titchmarsh-from-missing-residue-classes.md) with $B=48$ gives
$$
\varphi(q)|P_{x,[p]}|\le B(2x/T)/\log(Y/q)\le4B p/(T\log p).
$$
Each $p$ occurs for $pe^{-1/T}\le x<p$, of $dx/x$ measure $1/T$. Insert the last bound in (2) and integrate termwise to get (1) with $C=32\pi B$. When $N\asymp q^{2+\varepsilon}$ and $T=(\log q)^A\ge1$, the size condition holds for sufficiently large $q$, since $(2qT)^2/N=O(q^{-\varepsilon}(\log q)^{2A})$. The [log-free zero density argument](log-free-zero-density-fixed-modulus.md) uses this second moment.

## Plancherel for the step functions here

The transform of $e^{-\pi v^2}$ is $G(w)=e^{-\pi w^2}$. Indeed differentiate under the absolutely convergent integral and integrate by parts in $v$ to get $G'=-2\pi wG$. Polar coordinates in the square of the integral give $G(0)=1$. Thus for $\rho_\varepsilon(t)=\varepsilon^{-1}e^{-\pi(t/\varepsilon)^2}$ and our compactly supported bounded step function $f$,
$$
\int e^{-\pi\varepsilon^2 w^2}|\widehat f(w)|^2 dw
=\int\!\!\int f(v)\overline{f(u)}\rho_\varepsilon(v-u)\,du\,dv .
$$
The interchange follows from $f\in L^1$ and the integrable Gaussian weight. The $\rho_\varepsilon$ have integral one and their mass outside any fixed neighborhood of zero tends to zero. At each non-jump point $v$, the convolution with $f$ tends to $f(v)$ because $f$ is locally constant. The outer integral is dominated by $|f(v)|\|f\|_\infty$. Letting $\varepsilon$ decrease to zero, dominated convergence on the right and monotone convergence on the left give $\int|\widehat f|^2=\int|f|^2$.

The Lean `plancherel` proves the result for $L^1\cap L^2$. It identifies the integral Fourier transform with the $L^2$ transform almost everywhere by pairing both with smooth compactly supported functions, then uses Mathlib's Fourier isometry. [Integral transform](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/IntegralNormSqLp.lean#L10) · [Mathlib isometry](https://github.com/leanprover-community/mathlib4/blob/0df444a360eaa60ab8c11dca51a86af692955474/Mathlib/Analysis/Fourier/LpSpace.lean#L89)

## Lean correspondence

- `GlobalTheory.GallagherLemma.exp_sum` and `gallagher` give (2) using `plancherel`. [Fourier step](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/IntegralNormSqLp.lean#L99) · [Multiplicative windows](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/IntegralNormSqLp.lean#L163)
- `GlobalTheory.PrimeMeanValue.orth` and `window` use orthogonality and Brun–Titchmarsh. `kernel_integral` gives the $1/T$ factor and `prime_mean_value` gives (1). [Orthogonality](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/PrimeMeanValueCharactersTwistIntegralLe.lean#L29) · [Window](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/PrimeMeanValueCharactersTwistIntegralLe.lean#L59) · [Conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/PrimeMeanValueCharactersTwistIntegralLe.lean#L179)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
