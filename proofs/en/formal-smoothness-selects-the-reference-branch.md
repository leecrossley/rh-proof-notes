# Formal smoothness selects the reference branch

[Chinese proof](../zh/%E5%BD%A2%E5%BC%8F%E5%85%89%E6%BB%91%E6%80%8E%E6%A0%B7%E9%80%89%E5%87%BA%E7%BB%8F%E8%BF%87%E5%8F%82%E8%80%83%E7%82%B9%E7%9A%84%E5%94%AF%E4%B8%80%E5%88%86%E6%94%AF.md)

## Statement

Let $O$ be a complete DVR finite over $\mathbb Z_\ell$, $E=\operatorname{Frac}O$, and $R$ a complete Noetherian local $O$-algebra with the same residue field. Take an $O$-algebra retraction $x:R\to O$, put $\mathfrak p=\ker x$, and let $I\subseteq\mathfrak p$. Assume that for all finite-dimensional augmented $E$-algebras $B,B'$ with nilpotent augmentation ideals, across an augmented surjection $B\to B'$ every map $R\to B'$ killing $I$ with reference augmentation $x$ lifts to such a map to $B$.

Then $I$ has a unique minimal prime $P$ contained in $\mathfrak p$. There is $y$ with $x(y)\ne0$ and $yP\subseteq I$. Set
$$
n=\dim_E\big((\mathfrak p/(\mathfrak p^2+I))\otimes_O E\big).
$$
Then $\dim R/P=n+1$, and there is $\phi:R\to E[[T_1,\ldots,T_n]]$ with kernel $P$ and constant term $x$. For any $N\ge0$, every $f$ in the power series ring is, after multiplication by $c\in O\setminus\{0\}$, congruent to some $\phi(a)$ modulo $(T)^N$. Conversely $\phi(a)\in(T)^N$ implies $ca\in\mathfrak p^N+P$ for some such $c$. These conditions give `IsCompl`. For the [ordinary local chart](the-weight-distribution-in-the-local-smooth-chart.md), $I=I_Y$ and $n=12$.

## Proof

Let $A=(R/I)_{\mathfrak p}$ with residue field $E$. Modulo $\mathfrak p^N$ every $s\notin\mathfrak p$ becomes invertible once $O\setminus\{0\}$ is inverted: $s=x(s)+(s-x(s))$ is a unit plus a nilpotent. Thus
$$
A/\mathfrak m_A^N\simeq(R/(\mathfrak p^N+I))\otimes_O E.
$$
Choose $t_i$ lifting a basis of $\mathfrak m_A/\mathfrak m_A^2$, so they generate $\mathfrak m_A$. Over $E$, send this basis to $T_i$ modulo $(T)^2$ and keep the residue constants. This defines a point of $R$ killing $I$. The lifting hypothesis extends it successively modulo $(T)^N$ and gives $\phi$ into $E[[T]]$ in the limit. It keeps augmentation $x$, hence extends to $A$ and continuously to its completion.

Sending $T_i$ to $t_i$ gives a surjection $E[[T]]\to\widehat A$ by successively matching coefficients in each maximal ideal power. Composing with the completed $\phi$ gives a power series endomorphism that is the identity to first order. Such a substitution has an inverse obtained by recursively correcting the lowest remaining degree of the error. Thus the surjection is an isomorphism and so is the completed $\phi$.

Completion preserves the truncated quotients and $A$ injects into $\widehat A$ by Krull intersection. In particular $A$ is a domain and $P=\ker\phi$ is the kernel of $R\to A$. For any prime $Q$ between $I$ and $\mathfrak p$, if $a\in P$ then $sa\in I$ for some $s\notin\mathfrak p$, so $a\in Q$. This proves uniqueness of the minimal prime. Taking the product of suitable $s$ for finitely many generators of $P$ gives $yP\subseteq I$ and $x(y)\ne0$.

The isomorphic truncated quotients and the localization formula give both stated comparisons by clearing denominators. In the reverse direction one even has $ca\in\mathfrak p^N+I$. The localization of $R/P$ at the section kernel has completion of dimension $n$, so the section kernel has height $n$. Its quotient is the one-dimensional ring $O$. The dimension formula in the complete Noetherian local domain $R/P$ gives dimension $n+1$.

## Lean correspondence

- [`smoothCompl`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/SmoothCompl.lean#L136) uses `sc_tower` to lift and `sc_inj` for the injectivity comparison. The proof above expresses these steps with localization and completion.
- [`IsCompl`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/IsInertiaInfiniteCyclotomic.lean#L155) packages the properties.
- [`saturatedOrdinaryIdeal_smooth_at_residualRep`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/CrystallineOrdinaryIdeals/OrdinaryLocusIdealLeKerOfIsBasePoint.lean#L102) supplies the lifting premise via the two crystalline criteria and crystalline lifting.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
