# The determinant in the local fixed-point denominator

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E5%B1%80%E9%83%A8%E5%9B%BA%E5%AE%9A%E7%82%B9%E7%9A%84%E5%88%86%E6%AF%8D%E6%98%AF%E8%A1%8C%E5%88%97%E5%BC%8F.md)

## Statement

Let $Z,Y$ be smooth complex schemes of pure dimension $d$, $c_1,c_2:Y\to Z$ finite étale, and $y$ a common image point over $z$. Choose local parameters $s_i$ at $z$, and in $R=\mathcal O_{Y,y}$ put $t_i=c_1^*s_i$, $u_i=c_2^*s_i$. Define $A$ by $u_i\equiv\sum_j A_{ij}t_j\bmod\mathfrak m^2$, and assume $\det(I-A)\ne0$. Then $r_i=t_i-u_i$ are regular parameters. The change of highest local symbol from $t$ to $r$ contributes $\det(I-A)$ at $y$, and the trace on degree-$a$ cotangent forms is $[T^a]\det(I+TA)$. The local comparison value is their ratio. `FixLoc` and `ValG` give these computations, with `YCmpG` and `YCmpT` needed for the Čech–Koszul comparison giving global trace.

## Proof

The $t_i$ give a cotangent basis by étaleness, hence generate $\mathfrak m$ by Nakayama. Write $u=Gt$ with $G$ over $R$. Modulo $\mathfrak m$ the matrix is $A$, so $r=(I-G)t$ and $I-G$ is invertible by its unit determinant. Thus $r$ too generates $\mathfrak m$ and is a regular parameter sequence in the regular local ring of dimension $d$. The two Koszul complexes are related on degree-one generators by $I-G$, since the differentials are multiplication by the corresponding parameters. In top exterior degree this is multiplication by $\det(I-G)$, specializing at $y$ to $\det(I-A)$. Therefore a representative value $h(y)$ for the same local class has $h(y)\det(I-A)$ equal to the incoming highest coefficient in the comparison.

The matrix of $\bigwedge^a A$ in the exterior basis has entries given by its $a$-minors. The trace is the sum of principal minors of that size, which is $[T^a]\det(I+TA)$ by choosing $a$ columns of $TA$ and the other identity columns. The incoming coefficient computes precisely this trace: express the tensor for the identity as $\sum_k b_k^\vee\otimes b_k$, act by $\bigwedge^a A$ on the second factor and contract. The sum is $\sum_k b_k^\vee((\bigwedge^a A)b_k)$, independent of the expression. Dividing by the nonzero determinant gives
$$
h(y)=\frac{[T^a]\det(I+TA)}{\det(I-A)}.
$$

## Lean correspondence

- [`fixLoc_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/LocalMaximality/PFixLoc.lean#L62) uses the adjugate and unit denominator for the parameter change.
- [`valG_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/LocalMaximality/PullbackKahlerDegree.lean) computes the incoming coefficient and [`minorSum_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/LocalMaximality/PMinorSum.lean) identifies the determinant coefficient.
- [`yMain_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/LocalMaximality/PYMain.lean#L111) assigns this value at fixed points and zero at other fiber points, then uses the two coboundary comparisons.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
