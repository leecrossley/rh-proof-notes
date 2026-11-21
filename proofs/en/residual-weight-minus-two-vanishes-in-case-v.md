# Residual weight minus two vanishes in case V

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88V%E7%B1%BB%E7%9A%84%E5%89%A9%E4%BD%99%E8%B4%9F%E4%BA%8C%E6%9D%83%E6%B2%A1%E6%9C%89%E4%B8%80%E9%98%B6%E7%B1%BB.md)

## Statement

Use the [Gaussian frame for the large-conductor branch](the-large-conductor-v-case-over-the-gaussian-field.md) at general weight $e\ge1$. Put $k=O/\mathfrak m$, let $\eta$ be the character modulo $4$, and let $\bar\Psi$ be the reduction of $\Psi=\varepsilon_\ell^e\psi_G$. For $\gamma=\eta\bar\Psi^{-2}$, suppose the continuous cocycle $z:\Gamma\to k$ satisfies $z(gh)=z(g)+\gamma(g)z(h)$, is a coboundary on $D_\ell$, and vanishes on $N_v=I_v\cap\ker\eta\cap\ker\bar\Psi$ for $v\in S\setminus\{\ell\}$. Then $z(g)=\gamma(g)b-b$ for all $g$ for some $b\in k$. This is the local condition and conclusion of `Frame.Xpp`.

## Conductors for the vanishing theorem

For a primitive characteristic-zero character $\theta_2$ of conductor $2^c$ with $c\ge4$, its square kills $1+2^{c-1}$. But $(1+2^{c-2})^2\equiv1+2^{c-1}\pmod{2^c}$, on which $\theta_2$ has value $-1$ by primitivity. Since $\eta(1+2^{c-2})=1$, the conductor of $\theta_2^2\eta$ is exactly $2^{c-1}$.

Take $c=c_2(\psi)$ and $n=c-1$. Thus $\psi_2^2\eta$ induces a primitive odd character $\xi$ of conductor $2^n$. Let $\theta$ be $\psi$ with its $\ell$-power-order and mod-$2$-power parts removed, and $\omega$ the Teichmüller lift of the residual cyclotomic character. The odd-modulus character $\omega^{2e}\theta^2$ induces a primitive even character $\phi$ of conductor $f\mid \ell\operatorname{cond}(\theta^2)\mid\ell Q$. Hence $\phi\xi$ is odd. Set $d=f_0$, the order of $\ell$ modulo $\operatorname{lcm}(4,\operatorname{ord}\theta)$. The integers $4,\ell-1,\operatorname{ord}\theta$ divide $\ell^d-1$, so $\operatorname{ord}\phi\mid\ell^d-1$. The large-conductor hypothesis gives
$$
f4^{v_2(\ell^d-1)}\le \ell Q4^{n_0}\le2^{c-1}=2^n.
$$
These are the numeric hypotheses of [`CorX`](large-two-power-conductors-force-residual-cocycles-to-be-coboundaries.md).

## Identifying the residual cocycle

The $\ell$-power-order part reduces to one, and $\bar\omega=\bar\varepsilon_\ell$, so the pullback of $\phi\xi$ reduces to $\bar\Psi^2\eta$ with inverse $\gamma$. Pull $z$ back to $G_{\mathbb Q}$. Outside $S$ it vanishes on inertia since it descends to $\Gamma$. At $v\in S\setminus\{\ell\}$, the index of $N_v$ in $I_v\cap\ker\gamma$ is prime to $\ell$ by the map to $\{1,-1\}\times k^\times$, and $z$ vanishes on $N_v$. The analogous facts hold for conjugate places. At $\ell$, the coboundary restricts to zero on inertia intersected with $\ker\gamma$. Apply `CorX` to get a coboundary on the absolute group. Surjectivity gives the same formula on $\Gamma$.

For the connection to deformation theory, the unique matrix unit of weight $-2$ is $E_{20}$ when coordinate weights are $1,0,-1$. Diagonal conjugation multiplies it by $\bar\Psi^{-2}$. The outer coset acts on the Lie algebra by $X\mapsto-JX^{\mathsf T}J$ with reversing matrix $J$, giving a minus sign on $E_{20}$. Thus the weight line is exactly $\gamma$, and its first local-condition quotient vanishes as required for `HostXpp`.

## Lean correspondence

- [`xiSq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/HcXiSq.lean) proves the conductor calculation.
- [`dirData`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/HcDirData.lean#L28) and [`dir`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/DirGPowOne.lean#L23) give the primitive factors and reduction.
- [`adRep_baseLift_apply`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeGroups/AdRepBaseLiftApply.lean#L16), [`xppOf`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/HcXppOf.lean#L60) and [`xpp`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/Xpp.lean#L11) identify the weight and local conditions.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
