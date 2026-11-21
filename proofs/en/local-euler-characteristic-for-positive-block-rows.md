# The local Euler characteristic bounds the positive-block row cost

[Chinese proof](../zh/%E5%B1%80%E9%83%A8Euler%E7%89%B9%E5%BE%81%E6%80%8E%E6%A0%B7%E6%8A%8A%E6%AD%A3%E5%8F%B7%E5%9D%97%E8%A1%8C%E4%BB%A3%E4%BB%B7%E5%8E%8B%E5%88%B0%E5%B1%80%E9%83%A8%E6%AC%A1%E6%95%B0%E5%8A%A0%E4%B8%80.md)

Let $L/\mathbb Q_\ell$ be a finite extension of degree $d$ with $D=G_L$. Let $K/\mathbb Q_\ell$ be a finite coefficient extension with integers $\mathcal O$, uniformizer $\varpi$, residue size $q$, and $e=\operatorname{ord}_{\mathcal O}(\ell)$. Let $\epsilon$ be the cyclotomic character of $D$. For integer $a\ge0$ put $M_a=(K/\mathcal O)(\epsilon^{-a})$, with action by $\epsilon(g)^{-a}$. Let $H_a=H^1_{\rm cont}(D,M_a)$. Set $F_a=0$ for $a>0$, and let $F_0\subseteq H_0$ be the classes vanishing on inertia.

**Proposition.** The $\mathcal O$-module $H_a/F_a$ is isomorphic to $(K/\mathcal O)^d\oplus C$ for a finite cyclic $\mathcal O$-module $C$, possibly zero. In particular for every integer $c\ge0$,
$$
\operatorname{length}_{\mathcal O}((H_a/F_a)[\ell^c])\le ec(d+1).
\tag{1}
$$

## The finite layers

For finite $\ell$-primary $D$-module $U$, local Tate duality gives $|H^2(D,U)|=|H^0(D,U^\vee(1))|$, with $U^\vee=\operatorname{Hom}(U,\mathbb Q/\mathbb Z)$. The local Euler characteristic gives $|H^1(D,U)|=|H^0(D,U)||H^2(D,U)||U|^d$. [Milne, Arithmetic Duality Theorems, I.2, Corollary 2.3](https://www.jmilne.org/math/Books/ADTnot.pdf#page=36) · [Theorem 2.8](https://www.jmilne.org/math/Books/ADTnot.pdf#page=39)

Set $U_n=M_a[\varpi^n]\simeq\mathcal O/(\varpi^n)$ as an $\mathcal O$-module. Since the cyclotomic image of $G_L$ is open in $\mathbb Z_\ell^\times$, for each positive $b$ there is $g$ with $\epsilon(g)^b\ne1$. For $a>0$, $M_a^D$ is finite, being killed by a nonzero scalar of this form, so its $\varpi^n$ cokernel and kernel have the same order $|U_n^D|$. For $a=0$, $M_0^D$ is divisible and the cokernel is zero, while $|U_n^D|=q^n$. The long exact sequence of $0\to U_n\to M_a\xrightarrow{\varpi^n}M_a\to0$ gives $H_a[\varpi^n]$ as the quotient of $H^1(D,U_n)$ by $M_a^D/\varpi^n M_a^D$. Consequently its order is $q^{nd}|H^2(D,U_n)|$ for $a>0$ and $q^{n(d+1)}|H^2(D,U_n)|$ for $a=0$.

The finite dual $U_n^\vee(1)$ is cyclic of underlying module $\mathcal O/(\varpi^n)$, with action by $\epsilon^{a+1}$. One sees cyclicity by taking an additive character nontrivial on the smallest nonzero ideal and multiplying its argument by ring elements. The resulting map to the dual is injective because every nonzero ideal contains that ideal, and the two groups have the same size. Its invariants are killed by a fixed nonzero scalar $\epsilon(g)^{a+1}-1$. Thus $1\le|H^2(D,U_n)|\le C_0$ independent of $n$, with $|H^2(D,U_1)|\le q$.

For $a=0$, the unramified submodule $\operatorname{Hom}_{\rm cont}(\widehat{\mathbb Z},K/\mathcal O)$ is isomorphic to $K/\mathcal O$ by evaluation at Frobenius. It is divisible, so $H_0[\varpi^n]\to(H_0/F_0)[\varpi^n]$ is onto: an element killed in the quotient has a lift whose $\varpi^n$ multiple can be removed by subtracting an element of $F_0$. The kernel has order $q^n$. Hence for $B=H_a/F_a$ in both cases,
$$
q^{nd}\le |B[\varpi^n]|\le C_0 q^{nd},\qquad |B[\varpi]|\le q^{d+1}.
\tag{2}
$$

## Recovering the module

Continuous cocycles have finite image in the discrete torsion module, so $B$ is $\varpi$-primary torsion. Put $s=\dim_{k_\mathcal O}B[\varpi]<\infty$. Embed $B[\varpi]$ in $(K/\mathcal O)^s$ and extend to a map from $B$ by injectivity of divisible modules over a PID. It is still injective since every nonzero $\varpi$-primary torsion submodule has nonzero $\varpi$-torsion. Dualizing into $K/\mathcal O$ shows $B^\vee_{\mathcal O}$ is a quotient of $\mathcal O^s$, as $\operatorname{End}_{\mathcal O}(K/\mathcal O)=\varprojlim_n\mathcal O/\varpi^n=\mathcal O$. Double dualization identifies $B$ with the elements of $(K/\mathcal O)^s$ annihilated by functionals vanishing on $B$. Indeed any element outside $B$ has a nonzero cyclic image in the quotient, which admits a functional nonzero on that element, extended to the quotient by injectivity. Apply the DVR module structure theorem to the finitely generated dual and dualize back to obtain $B\simeq(K/\mathcal O)^m\oplus U$ with $U$ finite.

For large $n$, the order of $B[\varpi^n]$ is $q^{nm}|U|$. The two bounds in (2) force $m=d$. The bound at $n=1$ gives $\dim_k U[\varpi]\le1$, so $U$ is cyclic. Finally $\ell^c$ is a unit times $\varpi^{ec}$, giving length $dec$ from the divisible part and at most $ec$ from the cyclic part. This proves (1).

If the produced row classes are sent into $F_a$ after multiplication by $\ell^{c_B}$, the relaxed condition is its inverse image under that multiplication. The quotient of the relaxation by the strict condition is $(H_a/F_a)[\ell^{c_B}]$. The project uses the resulting bound at each row, relaxing $d_w+1$ to $d_w+2$ in the final lattice index. The local annihilation hypothesis comes from a Wach-lattice comparison.

## Lean correspondence

- `shapeG_of_localDuality` and `shapeUnr_of_localDuality` give the two cohomological structures. [Twist](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CohomologyShapeOfTateDualityEuler.lean#L34) · [Unramified quotient](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/GaloisHomModuloUnramifiedShapeOfLocalDuality.lean#L142)
- `rowChiReal` chooses the conditions and `rowTB` bounds the relaxation quotient. [Row conditions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/RealClassMaps/RealClassMapProofs/RowChiReal.lean) · [Bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/CoprimeLiftBounds/CoprimeLiftProofs/LengthMapQuotLe.lean#L47)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
