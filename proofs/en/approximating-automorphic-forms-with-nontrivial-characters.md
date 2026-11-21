# Approximating automorphic forms with nontrivial characters

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E7%94%A8%E9%9D%9E%E5%B9%B3%E5%87%A1%E8%A7%92%E8%89%B2%E9%80%BC%E8%BF%91%E5%8E%9F%E8%87%AA%E5%AE%88%E5%BD%A2%E5%BC%8F.md)

## Statement

Let $\Gamma,C\le G$ be groups and $\lambda:C\to\mathbb Z/\ell^m\mathbb Z$ a homomorphism for prime $\ell$, $m\ge0$. Assume that $\gamma g=gc$ for $\gamma\in\Gamma,c\in C$ implies $\lambda(c)=0$ for every $g\in G$. Then there is $\mathcal L:G\to\mathbb Z/\ell^m\mathbb Z$ with $\mathcal L(\gamma g)=\mathcal L(g)$ and $\mathcal L(gc)=\mathcal L(g)+\lambda(c)$. For $f:G\to\mathbb C$ put $f_\chi(g)=\chi(\mathcal L(g))f(g)$ for each nontrivial complex character. Use the $\ell$-adic norm transported by a given $\iota:\overline{\mathbb Q}_\ell\simeq\mathbb C$. Then
$$
\left|f(g)+\sum_{\chi\ne1}f_\chi(g)\right|_\ell\le \ell^{-m}|f(g)|_\ell.
$$
If $f$ is right $C$-invariant, $f_\chi$ transforms by $\chi\circ\lambda$. In the project, $G$ is a definite unitary adelic group, $\Gamma$ its rational points and $C$ the new level including a small compact group at one $\ell$-adic place. Right multiplication at infinity preserves the multiplier so the algebraic weight is retained.

## Proof

For a chosen representative $b$ of each double coset $\Gamma\backslash G/C$, put $\mathcal L(\gamma bc)=\lambda(c)$. If $\gamma bc=\gamma'bc'$ then $(\gamma')^{-1}\gamma b=bc'c^{-1}$, so the stabilizer hypothesis gives $\lambda(c')=\lambda(c)$. This proves well-definedness and the transformation rules. To preserve the infinity action, include the infinity group on the right with $\lambda$ zero there, using the enlarged stabilizer condition in `Ell`.

For $M=\ell^m$ and a primitive $M$th root $\zeta$, the characters are $\chi_j(b)=\zeta^{jb}$, $0\le j<M$. Their sum is $M$ at zero and otherwise zero by the geometric series. Thus $f+\sum_{\chi\ne1}f_\chi=M\mathbf1_{\mathcal L=0} f$, and the norm of $M$ gives the estimate. The right character rule follows directly from that for $\mathcal L$.

In the application, the place $w_0\mid\ell$ uses a torsion-free compact open $J$ and a surjection $\lambda_J$ to the cyclic group. Rational stabilizers at the finite level with the compact infinity group are finite, so the projection to $J$ is trivial. This verifies the required stabilizer condition. The local type input says that any irreducible smooth representation with a nonzero vector of $J$-character $\chi\circ\lambda_J$ for $\chi\ne1$ is supercuspidal. This gives the needed type on each automorphic constituent of $f_\chi$. Choosing the depth for arbitrarily large $m$ gives arbitrary precision.

## Lean correspondence

- [`EllGrp` and `Ell`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/StGlob.lean), [`charSum_pf`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/CharSum.lean#L9) and [`tyStep_pf`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/TyStep.lean#L9) give the setup, character sums and approximation.
- [`exists_ellType`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/IntegralStructures/CongruenceOddLevel/ExistsEllType.lean#L15) supplies $J$ and its local type property.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
