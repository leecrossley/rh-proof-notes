# Second cohomology bounds the remaining small weights

[Chinese proof](../zh/%E7%AA%97%E5%8F%A3%E9%87%8C%E5%89%A9%E4%B8%8B%E7%9A%84%E5%B0%8F%E6%8C%87%E6%A0%87%E6%80%8E%E6%A0%B7%E7%94%A8%E4%BA%8C%E9%98%B6%E4%B8%8A%E5%90%8C%E8%B0%83%E4%BC%B0%E8%AE%A1.md)

## Statement

Let $\ell$ be prime, $L_0$ contain $\mu_\ell$ or $\mu_4$ at two, and $R,c,Z,n_0\ge0$ be integers. Put $j_0=\lfloor\log_\ell R\rfloor+3$, using integer logarithm zero at $R=0$. Take cyclotomic $\ell$-power layers $L_2/L_0$ of degree $\ell^{j_0}$ and $L_1/L_0$ of degree $\ell^m$. Put $n_2=[L_2:\mathbb Q]\le n_0$ and $\Delta_2=|\operatorname{disc}L_2|$. For $C_K,\varepsilon>0$, $c_0,C_t\ge0$, and $x\ge1$ suppose $\log(2\Delta_2)\le c_0 x^{\varepsilon/4}$. Assume the `FirstBound`, `SecondBound` and `LemmaK` comparisons below, and that every $a$ in the exception set $E$ with $a\le x^{C_t}$ has $a\le x^{\varepsilon/(2C_K)}$. For each $1\le a\le Z$ with $a\le x^{C_t}$, the localization-kernel length $\mathrm{shaInv}(L_1,\ell,a)$ is finite and at most
$$
R(m+j_0+c+\lfloor\log_\ell Z\rfloor)+
2\exp\big((2n_0)^{C_K}c_0 x^{3\varepsilon/4}\big).
$$

## The two cases

Outside $E$, `FirstBound` gives the smaller linear bound with $\max(m,j_0)$ instead of $m+j_0$. Inside $E$, `SecondBound` gives at most $\operatorname{length}_{\mathbb Z_\ell} V+R\max(m-j_0,0)$ for $V=H^2(G_{L_2,S},\mathbb Z_\ell(a+1))$, where ramification is allowed at the places $S$ over $\ell$. [`LemmaK`](assembling-the-small-index-second-cohomology-bound.md) asserts finiteness over every totally imaginary $L$ with the prescribed roots and all allowed local models and $a\ge1$, and $\log|V|\le\exp((2a[L:\mathbb Q])^{C_K}\log(2|\operatorname{disc}L|))$. Here $L_2$ has the prescribed roots and is totally imaginary. Length is log cardinality divided by $\log\ell$, at most twice log cardinality. By exception smallness, $(2an_2)^{C_K}\le(2n_0)^{C_K}x^{\varepsilon/2}$. Multiply by the discriminant bound and substitute. This gives the stated inequality.

## Summing in the window

The window uses $Z=\lfloor X^{C_t}\rfloor$, $X^{1/J}\le x\le X$, hence $\log X\le J\log x$. For $m\le A(1+\log x)$ the linear term has the same logarithmic bound up to a fixed constant. Including an extra unit in the two-primary comparison, the per-weight cost is at most $C(1+\log x)+2e^{Cx^{3\varepsilon/4}}$. Summing over $1\le a<t(x)\le x^{C_t}$ multiplies by at most $x^{C_t}$. Both $C_t\log x$ and $Cx^{3\varepsilon/4}$ are eventually absorbed in $x^{4\varepsilon/5}$, giving total at most $\exp(x^{4\varepsilon/5})$. For the fixed odd-prime case, $L_2$ and its discriminant are fixed and $m=j_0$. At two, `layerdisc` controls the degree and discriminant using $\log(qd)\le X^{\varepsilon/(4J)}\le x^{\varepsilon/4}$, while $m\le e(x)+2$ and $2^{e(x)}\le x^{A_1}$ give the required logarithmic growth. These are the two uses in `ThmBab` and the [common window](exceptional-twist-window.md).

## Lean correspondence

- [`point`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LayeredIsomorphisms/ImportsAlt.lean) uses [the two tower comparisons](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LayeredIsomorphisms/SecondBound.lean). [`klen`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LayeredIsomorphisms/Klen.lean) and [`kexp`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LayeredIsomorphisms/Kexp.lean) handle log cardinality and the exponent.
- [`point2`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LayeredIsomorphisms/Point2.lean), [`final`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LayeredIsomorphisms/Final.lean) and [`vvat`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LayeredIsomorphisms/Vvat.lean) absorb and sum. [`partA`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LayeredIsomorphisms/PartA.lean#L24) and [`partB`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LayeredIsomorphisms/PartB.lean#L50) apply this within the window.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
