# Preserving the exceptional zero under a change of modulus

[Chinese proof](../zh/%E6%A8%A1%E6%95%B0%E6%94%B9%E5%8F%98%E6%97%B6%E6%80%8E%E6%A0%B7%E4%BF%9D%E7%95%99%E4%BE%8B%E5%A4%96%E9%9B%B6%E7%82%B9%E7%9A%84%E4%BF%A1%E6%81%AF.md)

For a character $\chi$ modulo $M$, let $\chi^*$ be the inducing primitive character, whose conductor divides $M$. Thus $\chi(n)=\chi^*(n)$ on the units modulo $M$ and is zero elsewhere. For $M\ge3$ and $h>0$, the project predicate `IsExc h χ β` means that the real number $\beta$ satisfies
$$
\chi^2=\chi_0,\qquad 1-h/\log M<\beta<1,\qquad L(\beta,\chi^*)=0.
\tag{1}
$$

**Proposition.** There exists an absolute $h_0>0$ such that for every $0<h\le h_0$ there is $c>0$ with these properties for every integer $M\ge3$.

1. Two pairs $(\chi,\beta)$ modulo $M$ satisfying (1) are equal.
2. Each such pair satisfies $\chi\ne\chi_0$, $\beta\ge7/8$, $L(\beta,\chi)=0$, $\operatorname{ord}_\beta L(s,\chi)=1$, and $1-\beta\ge c/(M^2\log M)$.
3. For any $\chi\bmod M$ and any zero $\rho$ of $L(s,\chi)$ with $\Re\rho<1$, either $\rho$ is real and $(\chi,\Re\rho)$ satisfies (1), or
   $\Re\rho\le1-c/\log(M(|\Im\rho|+2))$.

## Euler factors preserve orders of vanishing

For every $M\ge1$ and $\Re\rho>0$, excluding $\rho=1$ for the principal character, $L(s,\chi)$ and $L(s,\chi^*)$ have the same order of vanishing at $\rho$, where order zero means a nonzero value. This follows by comparing Euler factors in $\Re s>1$ and continuing:
$$
L(s,\chi)=L(s,\chi^*)\prod_{p\mid M}(1-\chi^*(p)p^{-s}).
\tag{2}
$$
For $p\nmid M$ the character values coincide, while for $p\mid M$ the lifted Euler factor is $1$. Near $\rho$ both $L$-functions are holomorphic under the stated exclusion. Each extra factor is nonzero at $\rho$ because $|\chi^*(p)p^{-\rho}|\le p^{-\Re\rho}<1$. Taking out the vanishing power of $s-\rho$ on the right proves the claim, including the equivalence of the two zero conditions.

## Uniform constants

Let $c_{\rm R}>0$ be the constant in the [real-zero uniqueness theorem](unique-simple-exceptional-zero.md). Let $c_{\rm P},c_{\rm N}>0$ be the principal and nonprincipal [region constants](three-four-one-zero-free-region.md), the latter covering $\chi^2\ne\chi_0$ or nonreal zeros. Finally let $c_{\rm S}>0$ be the [low-height gap constant](effective-low-height-zero-gap.md). Set
$$
h_0=\min(1/8,c_{\rm R}/2,c_{\rm P}/2),\qquad
c=\min(h,c_{\rm P},c_{\rm N},c_{\rm S}/2).
$$
For $M\ge3$ we have $\log M\ge1$ and $\log(2M),\log(3M)\le2\log M$.

For a pair in (1) we get $\beta\ge7/8$ and use (2) to move its zero to $L(s,\chi)$. Since $h/\log M\le c_{\rm P}/\log(2M)$, $\chi$ cannot be principal. Also $\beta\ge1-c_{\rm R}/\log(2M)$, so uniqueness and simplicity follow. The low-height gap gives $1-\beta\ge c_{\rm S}/(M^2\log(3M))\ge c/(M^2\log M)$.

For the third assertion the principal and ordinary nonprincipal cases have the required region bounds. In the remaining case $\chi^2=\chi_0$ and $\rho=\beta$ is real. If $\beta>1-h/\log M$, it is positive and (2) gives the primitive zero required in (1). Otherwise $1-\beta\ge h/\log M\ge c/\log(2M)$.

For a reduced residue class $b$, the project predicate `ExcData h M b θ β` gives $\theta=0$ when there is no exceptional pair, or supplies a pair in (1) with $\theta=\chi(b)\in\{-1,1\}$. Orthogonality over characters then places the one term $-\theta u^\beta/\beta$ in the progression formula. Simplicity gives its coefficient and the gap bounds the main term $u-\theta u^\beta/\beta$ away from zero at the required scales.

## Lean correspondence

- `GlobalTheory.Lin.zeros_eq_zeros_primitiveCharacter` uses Mathlib's `DirichletCharacter.LFunction_changeLevel` in (2). [Proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/DirichletLZerosEqPrimitiveCharacterZeros.lean#L11) · [Forwarding statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/DirichletLZerosEqPrimitiveCharacterZerosStatement.lean#L8)
- `GlobalTheory.ExceptionalPair.main` combines the region, uniqueness, gap and change-of-level inputs. [Definitions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/ZerosDisc.lean#L26) · [Proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExceptionalDirichletZeroUniqueZeroFreeRegion.lean#L47) · [Forwarding statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExceptionalDirichletZeroUniqueZeroFreeRegionStatement.lean#L8)
- `GlobalTheory.Lin.PsiRel.psiAP_relative` uses this proposition to set up the relative progression error. [Application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ChebyshevPsiProgressionRelativeError.lean#L294)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
