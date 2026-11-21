# Dwork's integrality test for the formal exponential

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $K$ be a characteristic-zero ultrametric normed field, $p$ a prime, and $\mathcal O=\{a:\lVert a\rVert\le1\}$. Assume $\lVert p\rVert=p^{-1}$ and a field endomorphism $\sigma$ with $\sigma(a)\equiv a^p\bmod p\mathcal O$ for $a\in\mathcal O$. In finitely many variables $X$, put $Tf=\sigma(f)(X^p)$. If $\Psi(X)\in K[[X]]$ has zero constant term, then
$$
\exp\Psi\in\mathcal O[[X]]
\quad\Longleftrightarrow\quad T\Psi-p\Psi\in p\mathcal O[[X]] .
$$
This is `DworkMv`, which does not require a discrete norm. [DworkMv and the integral exponential equivalence](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/CyclicPowerClassOfExpEquiv.lean#L13)

First consider a series $F$ of constant term $1$. If $F$ is integral, then $TF\equiv F^p\bmod p$ by reducing mod $p$ and using the Frobenius congruence. Its integral power $F^p$ has integral inverse, so $G=TF/F^p$ belongs to $1+p\mathcal O[[X]]$. Conversely suppose $G$ belongs to this set. Induct on total degree $n\ge1$, knowing that the coefficients of $F$ below $n$ are integral. Let $P=F_{<n}$. Since $T$ multiplies degrees by $p$, $TF$ and $TP$ agree in degrees through $n$. Meanwhile the degree-$n$ part of $F^p-P^p$ is $pF_n$, because $P(0)=1$ and a product involving two terms of degree at least $n$ has degree at least $2n>n$. Thus the degree-$n$ part of
$$
TP-GP^p
$$
is $pF_n$, using $TF=GF^p$ and $G(0)=1$. The entire displayed difference is divisible by $p$ since $P$ is integral and $TP\equiv P^p\bmod p$. Dividing the degree-$n$ part by $p$ proves $F_n$ integral. The constant term supplies the base case, so this proves the inverse criterion. [Multivariable Dwork proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/LocalComponentGL.lean#L448)

If $H$ has zero constant term, the condition $H\in p\mathcal O[[X]]$ is equivalent to $\exp(H)-1\in p\mathcal O[[X]]$. For the forward direction the coefficients of $H^k/k!$ are multiples of $p$ for $k\ge1$, since $v_p(k!)=\sum_{j\ge1}\lfloor k/p^j\rfloor\le k-1$, and integers prime to $p$ have norm $1$. For the reverse use the formal logarithm of $1+J=\exp H$. The coefficients of $J^k/k$ are multiples of $p$ when $J$ belongs to $p\mathcal O[[X]]$, since $v_p(k)\le k-1$. In either direction all calculations in a fixed degree are finite. Now set $F=\exp\Psi$, so $TF/F^p=\exp(T\Psi-p\Psi)$, because $T$ is a ring map fixing rational coefficients. The two equivalences prove the claimed test.

Finally, if $P\sim Q$ and $m$ is a positive integer prime to $p$, the Frobenius defect of $(P-Q)/m$ is the original defect divided by $m$, a unit in $\mathcal O$. Hence $(P-Q)/m\sim0$. This is the instance of `LamModule` used to divide the sum of torus translates by $p^d-1$. The integral-unit root recursion in the [averaging proof](why-root-of-unity-averaging-preserves-the-biextension.md) proves the same closure for this integer denominator. The Frobenius test will also be used where the coefficients of the defect itself have to be bounded. [Module rule for the logarithmic classes](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaLogCoordinates/UniformThetaSubstitution/FrobeniusLiftNorms/ScalingSwapLemmas.lean#L314)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
