# Factoring a theta series in additive orbit coordinates

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Setting and statement

Let $K_0$ be the characteristic-zero ultrametric field $K$ in [the biextension averaging theorem](why-root-of-unity-averaging-preserves-the-biextension.md). Use all the assumptions there, including `UnrOK` for the prime $p>2$ and endomorphism $\sigma$, the formal logarithm $\lambda$ and its law $F$, `F1` and `F2` for $b_0$, the even integer $d\ge2$, `OwOK` and `TrDual` for the lists $\omega_i,\omega_i^*$, and a primitive root $\zeta$ of order $p^d-1$. Let $j:K_0\to K$ be an isometric embedding into another characteristic-zero ultrametric field. When writing series over $K$, identify the coefficients from $K_0$ with their images under $j$.

For fixed nonnegative integers $N_0,N_1$, let $x_{i,a,b},y_{i,a,b}$ be formal coordinates with $1\le i\le d/2$, $1\le a\le N_0$, $1\le b\le N_1$. Write
$$
S(x,y)=\sum_{i,a,b} b_0(x_{i,a,b},y_{i,a,b}).
$$
Suppose $U_0,\Phi$ are series in these variables over $K$, $U_0$ is integral, $\Phi(0)=0$, and $\Phi\sim S$, meaning $\exp(\Phi-S)$ is integral and the constant terms agree. Set $T(x,y)=\exp(-\Phi(x,y))U_0(x,y)$.

In each matrix entry $(a,b)$ introduce $d$ additive orbit variables $Z_{s,a,b}$, $0\le s<d$. Define $T_Z$ by substituting $\lambda^{-1}(E_{\omega_i^*}(Z_{a,b}))$ for $x_{i,a,b}$ and $\lambda^{-1}(O_{\omega_i}(Z_{a,b}))$ for $y_{i,a,b}$ in $T$. Here $Z_{a,b}$ is the $d$-tuple at the specified matrix entry, and $E_c,O_c$ are the even and odd linear forms in the averaging theorem. Let
$$
\mathcal L_{s,a,b}(Y)=\sum_{e\ge0}p^{-e}Y_{s-2e,a,b}^{p^{2e}}
$$
be the cyclic logarithm, reducing indices modulo $d$. Then there is an integral series $U$ over $K$, in the $Y$ variables, with
$$
T_Z(\mathcal L(Y))=U(Y)\exp\!\left(-\sum_{a,b}\overline b(\mathcal L_{a,b}(Y))\right).
$$
Equivalently for any zero-constant tuple $g$ satisfying $\mathcal L(g(Z))=Z$,
$$
T_Z(Z)=U(g(Z))\exp\!\left(-\sum_{a,b}\overline b(Z_{a,b})\right).
$$
The latter is the form `B0` uses. The series $T_Z$ is `thetaInZ`, and $S$ is `sumE`. [Coordinates, sum of biextensions and statement B0](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussSumParity/StatementB.lean#L20)

## Integral points after cyclic substitution

Use capital letters $X_{i,a,b}(Y)=\lambda^{-1}(E_{\omega_i^*}(\mathcal L_{a,b}(Y)))$ and $V_{i,a,b}(Y)=\lambda^{-1}(O_{\omega_i}(\mathcal L_{a,b}(Y)))$ for the formal points obtained after substitution. Both lie over $K_0$ and are integral, because the cyclic shift makes each input to the inverse logarithm satisfy the integral part condition. These are precisely the points `Xt` in `BiextensionPointsIntegral`. Since $j$ is isometric their images are integral over $K$. Formation of these series commutes with applying $j$ to coefficients, since the logarithm and its inverse have rational coefficients and all formal compositions use zero-constant inputs. [Construction of the integral points](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussSumParity/KummerThetaLogarithms/BiextensionPointsOfExpSpec.lean#L48)

By averaging invariance after $\mathcal L$,
$$
B(Y):=\sum_{a,b}\overline b(\mathcal L_{a,b}(Y))
\ \sim\
\sum_{a,b}\widetilde b(\mathcal L_{a,b}(Y))
=S(X(Y),V(Y)).
$$
The rightmost equality follows from the two definitions of the points. This equivalence is proved over $K_0$ and remains true over $K$, by the isometric embedding. Meanwhile $\Phi\sim S$ and substitution of the integral points give $\Phi(X,V)\sim S(X,V)$. It follows that $B-\Phi(X,V)$ has zero constant term and integral exponential. Thus
$$
U(Y)=\exp\bigl(B(Y)-\Phi(X(Y),V(Y))\bigr)\,U_0(X(Y),V(Y))
$$
is integral. This is the factor in the conclusion. Indeed multiplying it by $\exp(-B)$ gives $T(X,V)=T_Z(\mathcal L(Y))$, by the addition rule for formal exponentials. [Construction and use of the integral factor](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussSumParity/KummerThetaLogarithms/BiextensionOfExpSpec.lean#L81)

The linear part of $\mathcal L$ is the identity. Solving by degree for its inverse, as in the inverse functional equation, gives a unique $g$ with $\mathcal L\circ g$ the identity. The inverse is two-sided, because for two zero-constant inputs giving the same output under $\mathcal L$, equality in every degree follows from the linear part and equality in lower degrees. Substituting $Y=g(Z)$ proves the equivalent identity. The integral factor $U$ is uniform in the displayed formulation with $g$. The proof never requires $g$ itself to have integral coefficients.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
