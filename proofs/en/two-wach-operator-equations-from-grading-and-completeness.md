# Two Wach operator equations from grading and completeness

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E4%BB%8EWach%E6%A8%A1%E7%9A%84%E5%88%86%E6%AC%A1%E4%B8%8E%E5%AE%8C%E5%A4%87%E6%80%A7%E5%8F%96%E5%BE%97%E4%B8%A4%E4%B8%AA%E7%AE%97%E5%AD%90%E6%96%B9%E7%A8%8B.md)

Let $\mathcal O$ be commutative, $A$ a commutative $\mathcal O$-algebra, $N$ an $A$-module, $X,Q\in A$, and $a,k,M\ge0$ integers.

**Graded equation.** Suppose $\gamma$ is $\mathcal O$-linear on $N$, with $(\gamma-u^i)X^i n\in X^{i+1}N$ for every $n\in N$ and $1\le i\le a$, for some $u\in\mathcal O$. Then for every $n$ there exist $x,z\in N$ with
$$
C_\gamma Xn=(\gamma-1)Xx+X^{a+1}z,\qquad C_\gamma=\prod_{i=1}^a(1-u^i).
$$
The hypothesis follows for semilinear $\gamma$ if $\gamma_A(X)\equiv uX\bmod X^2$ and $(\gamma-1)N\subset XN$: expand $\gamma_A(X)^i\gamma(n)$ in degree $i$.

In fact, put $C_j=\prod_{i=1}^j(1-u^i)$ and start with $C_0Xn=Xn$. If $C_jXn=(\gamma-1)Xx+X^{j+1}m$, multiply by $1-u^{j+1}$. In degree $j+1$ the last term becomes $-(\gamma-1)X^{j+1}m$ modulo $X^{j+2}N$. Replacing $x$ by $(1-u^{j+1})x-X^jm$ gives the next step. Iterate to $j=a$.

**Complete equation.** Suppose $\varphi$ acts on an $A$-module $D\supseteq N$, semilinearly for an $\mathcal O$-endomorphism $\varphi_A$, with $Q^M\varphi(N)\subset N$ and $\varphi_A(X)=XQ^kv$ for $v\in A$. Let $N$ be complete and separated for the $I$-adic topology, with $Q\in I$ and $\varphi_A(I)\subset I$. If $k(a+1)\ge M+1$, then $\varphi$ preserves $X^{a+1}N$ and every $X^{a+1}n$ equals $(1-\varphi)X^{a+1}z$ for some $z\in N$.

Put $b=a+1$, $d=kb-M-1\ge0$ and $G(n)=Q^{1+d}v^b(Q^M\varphi(n))$. Then $\varphi(X^bn)=X^bG(n)$. Semilinearity and the extra factor $Q$ imply $G(I^jN)\subseteq I^{j+1}N$. Thus the series $z=\sum_{j\ge0}G^j(n)$ converges in $N$ and $(1-G)z=n$ by continuity. Multiplying by $X^b$ gives the assertion. These two equations are used together to remove the second Herr obstruction.

## Lean correspondence

- `gammaGradedStep_holds` and `gammaImageProduct_holds` give the graded equation. [Grade](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CoboundaryTransfers/GammaStableTransfers/TorsionKilledCriterionHolds.lean#L7) · [Product](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CoboundaryTransfers/GammaStableTransfers/TorsionKilledCriterionHolds.lean#L28)
- `phi_map_surjective` gives the complete equation by contraction. [Contraction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/LagrangeExtensionCocycles/ExtensionCocycleProofs/PhiOnto.lean#L10)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
