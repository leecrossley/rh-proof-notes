# Finding integral points from formal logarithms

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

An orbit calculation first produces coordinates in the additive variables of a formal logarithm. The biextension identities are available on integral points of the formal group. The following argument passes from the additive variables to those points.

## The inverse functional equation

Let $K$ be a characteristic-zero ultrametric normed field, $\mathcal O=\{x\in K:\lVert x\rVert\le1\}$, $p$ a prime with $\lVert p\rVert<1$, and $q=p^h$ for an integer $h\ge1$. Let $\rho:K\to K$ be a field endomorphism with $\rho(a)\equiv a^q\bmod p\mathcal O$ for every $a\in\mathcal O$. For any finite set of variables write $Tg=\rho(g)(X^q)$, where $\rho$ acts on coefficients and $X^q$ raises every variable to the power $q$. For an integral matrix $M=(M_{ij})$ of size $m$, define
$$
Dg=g-p^{-1}MTg
$$
on $m$-tuples of series, with $T$ acting separately on each component. In Lean, $Dg$ integral is `IsFunEqTypeV`.

Suppose $f$ is an $m$-tuple of series in $m$ variables with zero constant term, linear part the identity and $Df$ integral. For every $m$-tuple $g$ with zero constant term in any finite set of variables, $Dg$ is integral if and only if there is a zero-constant integral tuple $H$ such that $f(H)=g$. The tuple is unique. The existence implication is `FunEqHomV`. The reverse implication is `FunEqSubstV`. [Definitions and statements](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/FormalGroupWitt/Statement.lean#L83)

First observe that if the entries of $f$ have coefficients $f_{i,n}$ at a nonconstant monomial of exponent $n$, and $k$ is the largest integer such that $q^k$ divides every coordinate of $n$, then
$$
p^k f_{i,n}\in\mathcal O .
$$
There is at least one positive entry of $n$, so $k$ is finite. For $k=0$ the term $p^{-1}MTf$ has zero coefficient at $n$, proving the claim. When $k\ge1$, the coefficient in it comes from $n/q$. By induction $p^{k-1}f_{j,n/q}$ is integral and $\rho$ preserves $\mathcal O$ and fixes $p$. Multiplying the equation for the coefficient at $n$ by $p^k$ therefore gives an integral coefficient. [Coefficient bounds from the functional equation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/FormalGroupWitt/FormalGroupWittProofs/CoeffV.lean#L144)

Now let $H$ be integral with no constant term. Put $A_i=H_i^q$ and $B_i=TH_i$. In characteristic $p$, taking the $q$-th power of a series raises its coefficients and its variables to the $q$-th power, so $A_i\equiv B_i\bmod p$. We use the following amplification. If $x,y$ are integral and $x-y\in p^a\mathcal O[[X]]$ with $a\ge1$, the binomial expansion of $x^p-y^p$ has all coefficients in $p^{a+1}\mathcal O[[X]]$. The intermediate terms have a factor $p$ and the last term is divisible by $p^{ap}$. Iterating gives $A_i^{q^k}\equiv B_i^{q^k}\bmod p^{1+hk}$, including $k=0$. It follows for the above monomial $n$ that $A^n-B^n$ is divisible by $p^{1+k}$, by taking additional nonnegative integer powers and subtracting the products one factor at a time. The coefficient $\rho(f_{i,n})$ is integral after multiplication by $p^k$; hence each term $\rho(f_{i,n})(A^n-B^n)$ is divisible by $p$. This proves that $\rho(f)(A)-\rho(f)(B)$ is divisible by $p$. In every fixed degree the sum has only finitely many terms because the inputs have zero constant term.

We can now compare the two substitutions in the functional equation:
$$
D(f(H))=(Df)(H)+p^{-1}M\bigl(\rho(f)(A)-\rho(f)(B)\bigr).
$$
The first term is integral by integral substitution and the second by the preceding congruence. This establishes the reverse implication. [Functional equation after integral substitution](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/FormalGroupWitt/FormalGroupWittProofs/FunctionalEquationSubstVector.lean#L101)

For the direct implication, solve $f(H)=g$ by increasing total degree. At degree $n\ge1$ the nonlinear terms of $f$ depend only on degrees below $n$ of $H$, so the identity linear part determines $H_n$ uniquely. Suppose the degrees below $n$ have integral coefficients. The truncation $P=H_{<n}$ is integral. By the reverse implication and linearity, $D(g-f(P))$ is integral. The difference $g-f(P)$ begins at degree $n$, with degree-$n$ component $H_n$. Its image under $T$ has order at least $qn>n$. Thus the degree-$n$ coefficients of $D(g-f(P))$ are the coefficients of $H_n$, which are integral. This starts at $n=1$ with $P=0$ and proves the claim. [Degree induction for the inverse](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/FormalGroupWitt/FormalGroupWittProofs/FunctionalEquationHomVector.lean#L36)

## The one-dimensional height-two logarithm

In the application $p>2$, $\lVert p\rVert=p^{-1}$, the norm of every nonzero element is a power of $p$, and $\sigma:K\to K$ satisfies $\sigma(a)\equiv a^p\bmod p$ on $\mathcal O$. This is `UnrOK`. In particular $\sigma(\mathcal O)\subseteq\mathcal O$, and applying the congruence twice gives $\sigma^2(a)\equiv a^{p^2}\bmod p$. Use $q=p^2$, $\rho=\sigma^2$, $M=(1)$, and
$$
\lambda(t)=\sum_{j\ge0}p^{-j}t^{p^{2j}} .
$$
Its coefficients are rational and $\lambda(t)-p^{-1}\lambda(t^{p^2})=t$ by dropping the initial term. Thus $\lambda$ has identity linear term and integral defect $D\lambda$. The condition `IP` on $g$ is precisely $g(0)=0$ and $Dg$ integral. Under it $\lambda^{-1}(g)$ is a zero-constant integral series. These $g$'s are closed under addition and under multiplication by any $c\in\mathcal O$ with $\sigma^2(c)=c$, because $D(cg)=cDg$ for such $c$. [Integral part lemma](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussSumParity/KummerThetaLogarithms/IpNormPowSubPowLe.lean#L141) · [Closure of IP](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussSumParity/KummerThetaLogarithms/IpNormPowSubPowLe.lean#L89)

In particular $g=\lambda(x)+\lambda(y)$ has integral defect, so $F(x,y)=\lambda^{-1}(g)$ is integral. Its group law identities follow by applying the invertible $\lambda$ and using ordinary addition. Also, for $c$ as above, $[c]x=\lambda^{-1}(c\lambda(x))$ is integral. These observations give the formal coordinates used in the parity calculation.

## The cyclic shift

Let $d$ be positive and even. For a family of zero-constant series $L_s$, indexed by $s\in\mathbb Z/d\mathbb Z$, assume
$$
L_s-p^{-1}TL_{s-2}\in\mathcal O[[X]]
\quad(s\in\mathbb Z/d\mathbb Z).
$$
Lean calls this `ShiftType`. If $L_s=\sum_{j\ge0}p^{-j}X_{s-2j}^{p^{2j}}$ then $L_s-p^{-1}TL_{s-2}=X_s$, by cancellation of consecutive terms. The calculation works for any assignment of the $X_s$ to variables. It applies to one letter of a pair of letter families and to a fixed matrix entry of the orbit. It also applies to sums of two such log families by linearity.

Take $c\in\mathcal O$ with $\sigma^d(c)=c$. In each parity class $J$ put $G_J=\sum_{s\in J}\sigma^s(c)L_s$, with representatives $0\le s<d$. Moving the summation index by two preserves $J$, and $\sigma^d(c)=c$ makes the coefficient unaffected by wrapping. Therefore
$$
DG_J=\sum_{s\in J}\sigma^s(c)\bigl(L_s-p^{-1}TL_{s-2}\bigr).
$$
Every term is integral. As $G_J(0)=0$, the one-dimensional result gives the integral point $\lambda^{-1}(G_J)$ for each parity. In the orbit construction these are the points passed to the two arguments of the biextension series. [Shift type and parity forms](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussSumParity/LetterShift.lean#L15) · [Cyclic logarithms and the parity calculation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussSumParity/KummerThetaLogarithms/EqZeroOfPowEqOne.lean#L259)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
