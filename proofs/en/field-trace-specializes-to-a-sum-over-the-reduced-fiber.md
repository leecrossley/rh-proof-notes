# Field trace specializes to a sum over the reduced fiber

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E7%BA%A6%E5%8C%96%E7%BA%A4%E7%BB%B4%E4%B8%8A%E7%9A%84%E5%9F%9F%E8%BF%B9%E7%AD%89%E4%BA%8E%E9%80%90%E7%82%B9%E5%8F%96%E5%80%BC%E5%92%8C.md)

## Statement

Let $k$ be algebraically closed of characteristic zero, $A$ an integrally closed domain over $k$ with fraction field $F$, $L/F$ finite, and $B$ the integral closure of $A$ in $L$, finite projective over $A$. Let $e_0:A\to k$ be a $k$-point with kernel $\mathfrak p$, and assume $\bar B=B/\mathfrak p B$ reduced. For every $h\in B$ the field trace lies in $A$ and
$$
e_0(\operatorname{Tr}_{L/F}h)=\sum_{e:B\to k,\ e|_A=e_0}e(h).
$$
In the Lefschetz comparison $A=k[t_1,\ldots,t_d]$, the point is the origin, and $B$ comes from the [finite affine cover](prescribed-points-in-one-reduced-projective-fiber.md) on that chart.

## Proof

Over the local ring $A_{\mathfrak p}$ the finite projective $B_{\mathfrak p}$ is free. Multiplication by $h$ has a matrix $M_h$ whose scalar extension to $F$ computes the field trace. The trace lies in $A$ since it is a sum of integral conjugates in $F$ and $A$ is integrally closed. Reducing $M_h$ at $e_0$ gives the multiplication matrix of $\bar h$ on $\bar B$ and trace commutes with reduction.

The reduced finite-dimensional $\bar B$ is a product of its fields at the maximal ideals. Each is $k$ by algebraic closure, indexed by an extension $e$ of $e_0$. In this product multiplication is diagonal by the values $e(h)$. This proves the formula. Also any specified values in the product lift to $B$ by the quotient map. In the fixed-point comparison take the desired values on coincidences and zero elsewhere. If $b(y)=0$, lift the idempotent of the one factor for $y$ to $c$ with $c(y)=1$. Then $cb\in(t_1,\ldots,t_d)$, so $b$ at $y$ is a local combination of these parameters with denominators invertible there.

The top Čech expression is $h\,d\log t_1\wedge\cdots\wedge d\log t_d$. The coefficient map takes the displayed volume form to one and then takes the field trace of $h$. For the resulting bottom-ring polynomial the Laurent constant term is evaluation at the origin. Thus this local Čech contribution is the pointwise sum above.

## Lean correspondence

- [`trace_quotient_eq_of_projective`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/TraceQuotientEqOfProjective.lean#L9) specializes the trace. [`ev_eq_trace_quot`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/TraceEvalOriginEqFibreTrace.lean) applies it at the origin.
- [`exists_regular_parameters_of_reduced_quotient`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CommutativeAlgebra/ExistsRegularParametersOfReducedQuotient.lean) gives the local decomposition in parameters.
- [`trF_locCoch_eq_finsum_fib`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/TraceCechCochainFractionEqSumFibre.lean) uses the Laurent constant term.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
