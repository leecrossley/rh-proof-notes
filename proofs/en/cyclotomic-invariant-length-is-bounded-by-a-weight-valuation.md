# Cyclotomic invariant length is bounded by a weight valuation

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E5%88%86%E5%9C%86%E6%89%AD%E6%9B%B2%E4%B8%8D%E5%8F%98%E9%87%8F%E7%9A%84%E9%95%BF%E5%BA%A6%E5%8F%AA%E5%A4%9A%E4%B8%80%E4%B8%AA%E6%8C%87%E6%95%B0%E8%B5%8B%E5%80%BC.md)

## Statement

Let $\ell$ be prime, $K/\mathbb Q_\ell$ finite with integers $\mathcal O$, and $\epsilon:G\to\mathcal O^\times$ a continuous character of a local Galois group. Suppose $\epsilon(g)=1+\ell^s$ for some $g$, $s\ge1$, with $s\ge2$ at two. For $n>0$ let $M_n$ be the invariants in $(K/\mathcal O)(\epsilon^{-n})$. Write $e=v_\mathcal O(\ell)$ for the valuation normalized on a uniformizer, and $\operatorname{len}_\ell=\operatorname{length}_\mathcal O/e$. Then
$$
\operatorname{len}_\ell M_n\le s+v_\ell(n).
$$
In the row, `EpsInertia.epsAll` supplies $g$ in inertia for the image of the cyclotomic character at every $w\mid\ell$. The maximum $h_0$ over $w$ and $1\le n<t$ is at most $s+\lfloor\log_\ell t\rfloor$, with empty maximum zero. This enters the [split bound](explicit-split-estimate-constants-at-two-and-three.md).

## Proof

Write $n=u\ell^a$ with $\ell\nmid u$. The first binomial term of $(1+\ell^s)^u-1$ has valuation $s$, and all higher terms have valuation at least $2s>s$. Write $(1+\ell^s)^u=1+b$ with $v_\ell(b)=s$. If $v_\ell(b)=S\ge s$, the first term of $(1+b)^\ell-1$ has valuation $S+1$. The intermediate terms have valuation at least $1+2S$, and the final term has valuation $\ell S>S+1$ under the stated hypotheses. Thus taking an $\ell$th power increases the valuation by one. Iteration gives $v_\ell((1+\ell^s)^n-1)=s+v_\ell(n)$.

Every invariant is killed by $\alpha=\epsilon(g)^n-1$, by multiplying its fixed-point equality by $\epsilon(g)^n$. Since $\alpha\ne0$, the entire annihilator is $\alpha^{-1}\mathcal O/\mathcal O\simeq\mathcal O/\alpha\mathcal O$ of length $e\,v_\ell(\alpha)$. Taking the length of its submodule of invariants and dividing by $e$ proves the bound. Finally $\ell^{v_\ell(n)}\le n\le t$, giving the maximum estimate.

For example, $\ell=3,s=1,n=6$ gives $4^2-1=15$ with valuation one and $4^6-1=9\cdot455$ with valuation two. Over $\mathbb Q_3$ the annihilator then has length two. If $g$ topologically generates $G$, continuity identifies this annihilator with the invariant submodule.

## Lean correspondence

- [`lenUnit_invariants_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ResidueCharacters/LenUnitInvariantsLe.lean#L9) uses the inertia element, power-difference valuation, and annihilator.
- [`h0_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ResidueCharacters/LenUnitInvariantsLe.lean#L55) takes the maximum over the places and weights.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
