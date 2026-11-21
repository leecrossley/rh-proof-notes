# From period valuations to an integral lattice map

[中文](../zh/integral-lattice-map.md) · [Reading and review status](../../STATUS.md)

The input in the Lean proof is a valuation bound for certain periods at each finite place. The slope argument needs an integral map between lattices over a number field. This note proves the transfer between those statements and specifies the hypotheses used in it.

## 1. Test vectors with integral coefficients

Let $K$ be a number field, $R=\mathcal O_K$, and $\iota:K\hookrightarrow\mathbb C$ an embedding. Let $O$ be a Dedekind domain embedded in $R$, let $W$ be a complex vector space, and let $M\subset W$ be a finitely generated $O$-module. Suppose the natural map $\mathbb C\otimes_O M\to W$ is injective. Let $e:W\to W$ be a complex-linear idempotent and assume $be(M)\subset M$ for some integer $b>0$. Then

$$
RM\cap\operatorname{im}e=R(M\cap\operatorname{im}e),
$$

where $RM$ denotes the $R$-span inside $W$.

Indeed $p=b(1-e)$ preserves $M$ and $\ker p=\operatorname{im}e$. Set $M_0=\ker(p|_M)$. The kernel sequence $0\to M_0\to M\xrightarrow{p}M$ stays exact at the first two terms after tensoring with $R$. Here $R$ is torsion-free over the Dedekind domain $O$ and therefore flat. For the same reason $M$ is flat over $O$, so $R\otimes_O M$ embeds in $\mathbb C\otimes_O M$ and then in $W$. Its image is $RM$ and the extended map is $p|_{RM}$. Its kernel is the image of $R\otimes_O M_0$, which is $RM_0$. This gives the identity.

The main call in Lean uses a stronger input. The original test module is already stable under $R$, so $RM=M$. A test vector in the intersection is then its own one-term decomposition. The flatness argument above gives another route to the same decomposition property, called `CutUp`. [Stability argument](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GroupLattices/JointServices/Cut.lean#L33) · [Base-change argument](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Divisibility/TiedLemmas.lean#L168)

## 2. Period bounds on the integral span

Fix a nonzero prime ideal $\mathfrak p\subset R$ and use the integer-valued valuation $v_{\mathfrak p}$ normalized by a uniformizer having value $1$. Let $S\subset K^d$, let $L\subset K^n$ be an $R$-submodule, and let $Q:K^d\times K^n\to K$ be $K$-bilinear. Let $A$ be a complex space, $A^0\subset A$ a complex subspace, $M\subset A$ a set, and $E:K^n\to A$ a map. For each $x\in K^d$ there is a complex-linear function $P_x:A\to\mathbb C$. Assume:

1. Each $E(F)$ with $F\in L$ is a finite $R$-linear combination of elements of $M\cap A^0$, where scalars act through $\iota$.
2. For every $x,F$ we have $\iota(Q(x,F))=P_x(E(F))$.
3. Fix $s\in\mathbb R$. For each $x\in S$ and $H\in M\cap A^0$, the period $P_x(H)$ equals $\iota(a_{x,H})$ for some $a_{x,H}\in K$ with $a_{x,H}=0$ or $v_{\mathfrak p}(a_{x,H})\ge s$.

Then $Q(z,F)$ is zero or has valuation at least $s$ for every $z\in\operatorname{span}_R S$ and $F\in L$.

To prove it, write $E(F)=\sum_i\iota(c_i)H_i$ for $c_i\in R$ and $H_i\in M\cap A^0$. For $x\in S$, linearity and injectivity of $\iota$ give $Q(x,F)=\sum_i c_i a_{x,H_i}$. The set of field elements that are zero or have valuation at least $s$ is an $R$-submodule. This follows from $v_{\mathfrak p}(c)\ge0$ for $c\in R\setminus\{0\}$ and the ultrametric inequality for sums. Thus $Q(x,F)$ is in the submodule. Linearity of $Q(-,F)$ gives the result on the full $R$-span. [Lean transfer lemma](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GroupLattices/ServJointF.lean#L42)

In the application the prime fixes the test type and $s=\lfloor e_{\mathfrak p}g_{\mathfrak p}\rfloor$. Here $e_{\mathfrak p}$ is the ramification index and $g_{\mathfrak p}$ is the local budget assigned to the source lattice. The `adm2` hypothesis supplies condition 3. [Specialization at every place](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GroupLattices/ServJointF.lean#L84)

## 3. Shifting the source lattice

Let $N,N'\subset K^d$, $T\subset K^D$ be $R$-submodules and $B:K^d\times K^D\to K$ a $K$-bilinear pairing. For each nonzero prime ideal $\mathfrak p$ assume the following.

1. For some test module $L_{\mathfrak p}\subset K^{n_{\mathfrak p}}$ and a linear map $A_{\mathfrak p}:K^{n_{\mathfrak p}}\to K^D$, the localization $T_{\mathfrak p}$ equals the localization of $A_{\mathfrak p}(L_{\mathfrak p})$.
2. For a bilinear pairing $Q_{\mathfrak p}$ and a nonzero scalar $\zeta_{\mathfrak p}$ of valuation zero,
   $Q_{\mathfrak p}(z,F)=\zeta_{\mathfrak p}B(z,A_{\mathfrak p}F)$ for all $z,F$. For $z\in N$ and $F\in L_{\mathfrak p}$, this value is zero or has valuation at least $s_{\mathfrak p}$.
3. There exists $a_{\mathfrak p}\in K^\times$ of valuation $-\tau_{\mathfrak p}$ with $N'_{\mathfrak p}=a_{\mathfrak p}N_{\mathfrak p}$, for an integer $\tau_{\mathfrak p}\le\lceil s_{\mathfrak p}\rceil$.

Then $B(N',T)\subset R$. To see this, take $z'\in N'$ and $y\in T$ with $B(z',y)\ne0$. At $\mathfrak p$, write $z'=a_{\mathfrak p}z/c$ and $y=A_{\mathfrak p}F/d_0$ with $z\in N$, $F\in L_{\mathfrak p}$ and $c,d_0\in R\setminus\mathfrak p$. Bilinearity gives

$$
B(z',y)=\frac{a_{\mathfrak p}}{c d_0\zeta_{\mathfrak p}} Q_{\mathfrak p}(z,F).
$$

The denominator has valuation zero. As valuations of nonzero field elements are integers, the right side has valuation at least $-\tau_{\mathfrak p}+\lceil s_{\mathfrak p}\rceil\ge0$. This holds at every finite place. The principal fractional ideal generated by $B(z',y)$ therefore has only nonnegative exponents, so $B(z',y)\in R$. A vanishing value is also in $R$. It follows that $z'\mapsto B(z',-)$ lands in $T^\vee=\{f:f(T)\subset R\}$.

In the application $\tau_{\mathfrak p}=\lfloor e_{\mathfrak p}g_{\mathfrak p}\rfloor$ has finite support. The shift $N'=(\prod_{\mathfrak p}\mathfrak p^{-\tau_{\mathfrak p}})N$ satisfies condition 3. At $\mathfrak p$ only its own ideal factor contributes to the valuation. Thus the bounds from Section 2 give the integral map used in the lattice comparison. [Shift lemma](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/QuotientMetricDivisors/HermitianTwistDivisors/TwistedLatticeNaturality.lean#L720) · [Application to the target lattice](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/IndefiniteForms/PairingConditionOfInverseMatrixIdentity.lean#L393)

The assembly in Andrew O’Desky’s [reading notes, Step 4](https://andrewodesky.com/rh/s/assembly-existence.html) led to these Lean declarations. The actual period estimates and the local identification of the target lattice are upstream inputs. [Period-bound entry](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/ClosedFamilyAdmissibleTwistLink.lean#L12)
