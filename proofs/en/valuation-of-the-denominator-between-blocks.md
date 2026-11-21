# Valuing the denominator between blocks

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E5%9D%97%E9%97%B4%E5%88%86%E6%AF%8D%E7%9A%84%E8%B5%8B%E5%80%BC%E6%98%AF%E5%88%86%E5%9C%86%E5%B1%82%E6%95%B0%E5%8A%A0%E9%98%B6%E4%B9%98%E8%B5%8B%E5%80%BC.md)

**Proposition.** Let $\mathcal O$ be a characteristic-zero DVR in which $\ell$ is a nonunit prime integer, and set $e_{\mathcal O}=\operatorname{ord}_{\mathcal O}(\ell)>0$. Take $s\ge1$, with $s\ge2$ when $\ell=2$, units $u,u_1\in\mathcal O^\times$, and integer $t\ge0$. Put $x=1+\ell^s u$ and $\Delta=\prod_{1\le j<t}u_1(1-x^{-j})$, with the empty product $1$. Then $x$ is a unit, $\Delta\ne0$, and
$$
\operatorname{ord}_{\mathcal O}(\Delta)
=e_{\mathcal O}\sum_{1\le j<t}(s+v_\ell(j)).
\tag{1}
$$
For $t\ge1$ the sum equals $(t-1)s+v_\ell((t-1)!)$. For all $t\ge0$ it is at most $ts+v_\ell(t!)$.

Modulo the maximal ideal $x=1$. If $n\ge1$ is coprime to $\ell$, then $(x^n-1)/(x-1)=1+x+\cdots+x^{n-1}$ is a unit since it reduces to $n$ in residue characteristic $\ell$. Next suppose $y=1+\ell^m a$ with $m\ge s$ and $a$ a unit. In $y^\ell-1$, the linear term is $\ell^{m+1}a$. For $2\le j<\ell$, the coefficient $\binom{\ell}j$ is divisible by $\ell$, so the corresponding terms are divisible by $\ell^{m+2}$. The last term is also divisible by $\ell^{m+2}$, by $m\ell\ge m+2$, which uses $m\ge2$ when $\ell=2$. Thus $y^\ell-1$ equals $\ell^{m+1}$ times a unit. Write $n=\ell^b n_0$ with $(n_0,\ell)=1$, apply the first argument to $x^{n_0}$, and iterate the second $b$ times. This gives $x^n-1=\ell^{s+v_\ell(n)}u_n$ for a unit $u_n$.

Since $u_1(1-x^{-j})=u_1 x^{-j}(x^j-1)$, each factor is nonzero and has valuation $e_{\mathcal O}(s+v_\ell(j))$. Add the valuations to get (1), and use multiplicativity on the positive integers for the factorial form. The normalized block ring uses values given by a common unit times the indicated cyclotomic powers, so differences supply these factors. The product clears denominators for comparisons of integral lattices. Its cost in length units divided by $e_{\mathcal O}$ is the sum in (1).

## Lean correspondence

- `DeltaValuation.step`, `iter`, `pow_sub_one` and `powSubOneO` give the unit and valuation formula. [Power step](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/CoprimeLiftBounds/CoprimeLiftProofs/TheoremNFiveDeltaClause.lean#L54) · [Valuation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/CoprimeLiftBounds/CoprimeLiftProofs/TheoremNFiveDeltaClause.lean#L118)
- `theorem_n_five_delta_sum` and `theorem_n_five_delta_clause` give the sum and bound. `realDisplayAllK_of` applies it with the block cohomology estimates. [Sum](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/CoprimeLiftBounds/CoprimeLiftProofs/TheoremNFiveDeltaClause.lean#L123) · [Application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/AdmissibleDesigns/RealDisplayAllKOf.lean#L150)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
