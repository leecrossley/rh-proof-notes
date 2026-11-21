# Truncated Perron inversion for the prime-power sum

[Chinese proof](../zh/Perron%E7%A7%AF%E5%88%86%E6%80%8E%E6%A0%B7%E6%88%AA%E5%87%BA%E7%B4%A0%E6%95%B0%E5%B9%82%E5%92%8C.md)

**Proposition.** There is an absolute $C>0$ such that for each integer $q\ge1$, character $\chi\bmod q$, and real $u,T$ with $u\ge2$ and $2\le T\le2u$, putting $c=1+1/\log u$ gives
$$
\left|\sum_{1\le n\le u}\Lambda(n)\chi(n)-
\frac1{2\pi}\int_{-T}^T-\frac{L'}{L}(c+it,\chi)\frac{u^{c+it}}{c+it}\,dt\right|
\le C\left(\frac{u\log^2u}{T}+\log u\right).
\tag{1}
$$
The sum includes $n=u$ when $u$ is an integer.

## The finite-height kernel

For $y>0$, $c>0$, $T\ge1$ write $K_T(y;c)=(2\pi)^{-1}\int_{-T}^T y^{c+it}/(c+it)\,dt$. If $a=\log y<0$, close the vertical line segment to the right at $B>c$. The integrand $e^{as}/s$ has no pole there, and the integral on the added vertical edge tends to zero, with modulus at most $2T e^{aB}/B$. Each horizontal edge costs at most $y^c/(T|a|)$. If $a>0$, close to the left at $-B$. The added vertical edge again vanishes, the same horizontal bound applies, and the pole at $0$ contributes $1$. Thus for $a\ne0$ the error compared to $\mathbf1_{y>1}$ is at most $y^c/(\pi T|a|)$.

For $T|a|\le1$, split $e^{iat}=1+(e^{iat}-1)$ in the kernel. The integral of $1/(c+it)$ is $2\arctan(T/c)$, and $|(e^{iat}-1)/(c+it)|\le |a|$. Therefore $|K_T(y;c)|\le y^c(\pi+2T|a|)/(2\pi)$. As $\mathbf1_{y>1}\le y^c$, this gives
$$
|K_T(y;c)-\mathbf1_{y>1}|\le3y^c\min(1,(T|\log y|)^{-1})\quad(y\ne1).
$$
At $y=1$, $K_T(1;c)=\arctan(T/c)/\pi$, differing from the closed-endpoint value $1$ by at most $1$. Thus the error $E(y)=|K_T(y;c)-\mathbf1_{y\ge1}|$ satisfies $E(y)\le3y^c$ and $T|\log y|E(y)\le3y^c$ for all $y>0$.

## Summing the kernel errors

On $\Re s=c>1$ the log derivative is the absolutely convergent series $\sum_{n\ge1}\Lambda(n)\chi(n)n^{-s}$. Integrate it termwise, which is justified by the uniform majorant $\sum_n(\log n)n^{-c}$. The left side of (1) is at most $\sum_{n\ge1}(\log n) E(u/n)$.

Let $\ell=\log u$. If $n\le u/2$ or $n\ge2u$, then $|\log(u/n)|\ge\log2$ and $u^c=eu$. The total from these terms is $O((u/T)\sum_{n\ge1}(\log n)n^{-1-1/\ell})=O(u\ell^2/T)$. For the sum use $x e^{-x/(2\ell)}\le2\ell$ at $x=\log n$ and $\sum_{n\ge1}n^{-1-1/(2\ell)}\le1+2\ell$.

For $u/2<n<2u$, we have $(u/n)^c\le8$, $\log n\le2\ell$, and $|\log(u/n)|\ge|u-n|/(2u)$ by the derivative of $\log$. Put $N=\lfloor u\rfloor$. The two terms $n=N,N+1$ cost $O(\ell)$ by $E(u/n)\le3(u/n)^c$. For the others $1/|u-n|$ is at most $1/(N-n)$ below $N$ and $1/(n-N-1)$ above $N+1$. The two harmonic sums are $O(\ell)$ and $E(u/n)\ll u/(T|u-n|)$ there. Thus their error is $O(u\ell^2/T)$, proving (1) even when $u$ is arbitrarily close to an integer.

## Lean correspondence

- `far_neg`, `far_pos` and `near` prove the kernel bounds for `truncated_perron_kernel`. [Kernel](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/TruncatedPerronKernel.lean#L346)
- `kernel_bound` includes the endpoint. `interchange`, `far_term`, `near_term` and `sum_w` are used by `truncated_perron_psi`. [Endpoint](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/TruncatedPerronPsi.lean#L7) · [Main estimate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/TruncatedPerronPsi.lean#L436)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
