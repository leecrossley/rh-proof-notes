# A cyclotomic localization kernel bounds each higher block

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E9%AB%98%E6%AC%A1%E5%9D%97%E7%9A%84%E5%85%A8%E5%B1%80%E9%95%BF%E5%BA%A6%E7%94%B1%E5%88%86%E5%9C%86%E5%B1%80%E9%83%A8%E5%8C%96%E6%A0%B8%E6%8E%A7%E5%88%B6.md)

Let $E$ be a number field, $G=G_E$, $\ell$ prime, and $S_\ell$ the finite places over $\ell$. Let $G_{E,S_\ell}=G/N$ where $N$ is generated as a closed normal subgroup by inertia at all other finite places. The cyclotomic character $\epsilon$ factors through this quotient. Fix $a\ge1$, a DVR $\mathcal O$ finite over $\mathbb Z_\ell$, its fraction field $K$, and $e=\operatorname{ord}_{\mathcal O}(\ell)$. Set $A_0=(\mathbb Q_\ell/\mathbb Z_\ell)(\epsilon^{-a})$, $A=(K/\mathcal O)(\epsilon^{-a})$, with action by multiplication by $\epsilon(g)^{-a}$.

**Proposition.** Let $\mathcal S$ be the submodule of continuous $H^1(G,A)$ with zero restriction to inertia at every finite place outside $S_\ell$ and zero restriction to the whole decomposition group at each $w\in S_\ell$. Write
$$
\Sha_a=\ker\left(H^1(G_{E,S_\ell},A_0)\longrightarrow
\prod_{w\in S_\ell}H^1(G_{E_w},A_0)\right).
$$
Then $\operatorname{length}_{\mathcal O}\mathcal S\le e\,\operatorname{length}_{\mathbb Z_\ell}\Sha_a$. This uses a first cohomology kernel. The project relates it to a second cohomology kernel elsewhere using Poitou–Tate duality.

First use coefficients $A_0$. On inertia outside $S_\ell$ the action is trivial, so a cocycle with zero restricted class vanishes pointwise there. On $N$, the action is also trivial, hence the restricted cocycle is an additive homomorphism. For $n\in N$ we have $z(gng^{-1})=gz(n)$ from the cocycle identity and $z(g)+gz(g^{-1})=0$. The kernel in $N$ is therefore closed and normal in $G$ and contains the generating inertia groups. Thus $z$ vanishes on $N$ and factors continuously through $G/N$. At $w\in S_\ell$ an original coboundary remains one, using its same vector. If the decomposition group is conjugated, $z(k)=km-m$ gives $z(gkg^{-1})=(gkg^{-1}-1)(gm-z(g))$. Hence the descended class belongs to $\Sha_a$ and the original is its inflation.

Now choose a $\mathbb Z_\ell$-basis of the finite free module $\mathcal O$ of rank $n$. Since $K=\mathcal O[1/\ell]$, it identifies $K/\mathcal O$ with $(\mathbb Q_\ell/\mathbb Z_\ell)^n$. The twist is scalar over $\mathbb Z_\ell$, so the coordinates preserve continuous cohomology, localization and coboundaries. The $\mathbb Z_\ell$-length of $\mathcal S$ is at most $n\operatorname{length}_{\mathbb Z_\ell}\Sha_a$ by the previous paragraph. Put $f=[k_{\mathcal O}:\mathbb F_\ell]$. Restriction of scalars multiplies finite lengths by $f$, since the simple factors are copies of $k_{\mathcal O}$, and extends to infinite lengths by unbounded finite chain lengths. Comparing $\mathcal O/\ell\mathcal O$ in the two units gives $n=ef$. Canceling $f$ proves the proposition.

For block $c\ge2$ use $a=c-1$. Rows and columns above $\ell$ require zero local cohomology class. Outside them the strict conditions require unramified classes, including the designated places in $Q$. Thus summing the bound over $1\le c-1<t$ gives the global higher-block term.

## Lean correspondence

- `coc_ine`, `coc_NS`, `coc_loc` and `selZ_le_map` give the descent. [Inertia](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/AdmissibleDesigns/CocZeroOfUnr.lean#L65) · [Inflation image](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/AdmissibleDesigns/CocZeroOfUnr.lean#L293)
- `coefChange` and `tieSel2_full` change the length units and transfer the result to the block. [Coefficient basis](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/AdmissibleDesigns/H1MapMemLocallyConstant.lean#L326) · [Application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/AdmissibleDesigns/CoefChangeRec.lean#L23)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
