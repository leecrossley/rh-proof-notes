# How cohomological length bounds the local divisibility loss

[Chinese proof](../zh/%E4%B8%8A%E5%90%8C%E8%B0%83%E9%95%BF%E5%BA%A6%E6%80%8E%E6%A0%B7%E6%8E%A7%E5%88%B6%E5%B1%80%E9%83%A8%E6%95%B4%E9%99%A4%E6%8D%9F%E5%A4%B1.md) · [Reading and review status](../../STATUS.md)

A cohomological length bound becomes useful to the prime-sum argument only after it enters an inequality for the period data. The theorem `divinN_of_hypV` converts the length bound and a local comparison into the uniform estimate for divisibility used in family selection.

## Data and statement

Fix $\varepsilon>0$ and a family $F$ satisfying the scale conditions of `FamP ε`. At each real scale $x$ there is a set of indices $I(x)$. Each $i\in I(x)$ specifies the local field and rank data $D(x,i)$ and the size and count data $L(x,i)$. For sufficiently large $x$ these records use the parameters $x,\varepsilon$. All quantities below may depend on $(x,i)$ except the common constants and thresholds.

The data give a host number field $E$, a twist cutoff $t$, an integer $f\ge1$, the number $m\ge0$ of lift indices, a target rank $D_0\ge0$, and ranks $d(j)\ge0$ for $1\le j\le m$. Write $y=x^\varepsilon$, $b=\exp y$, $B_0=fmby$. Let $N_c$ be the associated nonnegative size budget. Define

$$
A(j)=\sum_{\substack{w\in S\\\mu(w)\ne\mu_0}}\lambda(w)e(w)\eta(j,w).
$$

Here $S$ is the finite set of places supplied by the data, $\mu(w)$ is the local label with reference value $\mu_0$, $\lambda(w)$ is the weight, $e(w)$ the ramification index, and $\eta(j,w)$ the local index for the $j$th lift. This is `etaSum`.

Let $l(E,p,e)$ be the localization-kernel length for the $-e$th cyclotomic twist, as defined in [the window argument](main-theorem-and-window.md#what-the-basic-window-supply-requires). Use the local data specified by $D$. Its table records lengths $\lambda_{p,e}$ that agree with the actual lengths when the latter are finite. Put $v(p)=(\log p)\sum_{1\le e<t}\lambda_{p,e}$ for primes $p$, with zero values at nonprimes. Assume the following.

1. **Length bound.** Beyond a common threshold $x_V$, every candidate satisfies $\mathrm{VVle}(E,t,\sqrt b)$. This means finite lengths for each prime and $1\le e<t$ with every allowed localization choice, and the bound $\sqrt b$ on the weighted sum over every finite prime set.
2. **Local comparison.** There are a real $C$ and a threshold $x_N$ such that for every candidate with $x\ge x_N$ whose lengths are finite for the designated local data at every prime and $1\le e<t$, summability of $v$ implies
   $$
   A(j)\le d(j)\left[C\big(fmby^2+(\log x)^2N_c\big)+\sum_p v(p)\right]
   \quad(1\le j\le m). \tag{1}
   $$
   The finiteness condition `ShaFinOdd` quantifies over all primes. The comparison (1) is the quantitative input `LinkN`.
3. **Rank equality.** Beyond a common threshold $x_R$, every candidate and every $1\le j\le m$ has $d(j)=D_0$.

Then some common constant $C'$ and threshold $x_0$ give

$$
A(j)\le D_0 C'x^\varepsilon(B_0+N_c)
$$

for all $x\ge x_0$, $i\in I(x)$, and $1\le j\le m$.

## Proof

Take $x$ above the required thresholds and at least $1$, and fix $i\in I(x)$. Apply the length bound to the designated localization choices. By finiteness the recorded and actual lengths agree, so

$$
v(p)=(\log p)\sum_{1\le e<t}l(E,p,e)\ge0.
$$

Every finite sum of these terms is at most $\sqrt b$. In order of increasing prime the partial sums form a nondecreasing bounded sequence. Therefore the series converges and its sum $V$ is at most $\sqrt b$. This supplies the two prerequisites of (1).

If there is a $j$ in the range, $m\ge1$. As $f,y\ge1$ and $b\ge1$, we have

$$
V\le\sqrt b\le b\le B_0\le y(B_0+N_c).
$$

The estimate $\log x=o(x^{\varepsilon/2})$ gives $(\log x)^2\le y$ beyond a threshold depending only on $\varepsilon$. Indeed with $x=e^u$ the ratio is $u/e^{\varepsilon u/2}\to0$. Also $fmby^2=yB_0$. Since these budgets and $d(j)$ are nonnegative, replacing $C$ by $|C|$ in (1) gives

$$
A(j)\le d(j)\bigl[|C|y(B_0+N_c)+V\bigr]
\le D_0(|C|+1)y(B_0+N_c).
$$

The last step uses the rank equality. Take $C'=|C|+1$ and take the maximum of the three hypothesis thresholds, the scale agreement threshold, and the logarithmic threshold. None depends on $i$ or $j$.

The [family selection theorem](joint-family-selection.md) applies this once the comparison and the rank equality are available on the chosen family. It combines the resulting `DIVinN` with localization coverage and size estimates to obtain `LinkDIV`, one of the inputs to the final assembly of the [count discrepancy bound](quotient-slopes-and-count-discrepancy.md).

## Lean references and review

- [`HypV`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/DivinNOfHypV.lean#L10), [`VVle`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/ExistsPageN.lean#L12) and [`vvRecord`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/DivinNOfHypV.lean#L17) give the length bound and the passage to a summable series.
- [`LinkN_at`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalTheoremInputs.lean#L40), [`LinkN`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalTheoremInputs.lean#L45), [`SmallLevelRankEq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalTheoremInputs.lean#L52), and [`DIVinN`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalTheoremInputs.lean#L62) state the comparison, the rank equality and the uniform output.
- [`log_sq_le_rpow`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/DivinNOfHypV.lean#L59), [`divinN_at`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/DivinNOfHypV.lean#L76) and [`divinN_of_hypV`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/DivinNOfHypV.lean#L117) give the numerical deduction and uniform threshold. The caller is [`topDesWin`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/DesWin.lean#L11).

English translation draft checked against the source argument. The local comparison (1) and the rank equality are inputs to this note.
