# A uniform integral correction for a rational Herr lift

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E6%8A%8A%E6%9C%89%E7%90%86%E7%9A%84Herr%E6%8F%90%E5%8D%87%E6%94%B9%E6%88%90%E6%9C%89%E7%BB%9F%E4%B8%80%E4%BB%A3%E4%BB%B7%E7%9A%84%E6%95%B4%E6%8F%90%E5%8D%87.md)

Let $\mathcal O$ be commutative, $A$ a commutative $\mathcal O$-algebra, $p$ prime, $X,Q\in A$, and $M\ge0$. For $i=0,1,2$ let $N_i\subseteq D_i$ be $A$-modules with commuting semilinear $\varphi_i,\gamma_i$ over endomorphisms fixing $\mathcal O$. Assume $X$ acts injectively and $Q$ bijectively on each $D_i$, and $\varphi_A(X)=Xv$ with $v\in A$. Write $U_i=\{y:Q^My\in N_i\}$. Assume $Q^M\varphi_i(N_i)\subseteq N_i$, $(\gamma_i-1)N_i\subseteq XN_i$, and $(\gamma_i-1)U_i\subseteq XU_i$. The allowed terms in degrees zero through two are $N_i$, $U_i\times XN_i$, and $XU_i$, with differentials $d_0(x)=((\varphi_i-1)x,(\gamma_i-1)x)$ and $d_1(y,z)=(\gamma_i-1)y-(\varphi_i-1)z$.

Let $\iota:D_0\to D_1$, $F:D_1\to D_2$ be $A$-linear maps preserving the lattices and commuting with the operators, with $\iota$ injective, $\ker F=\iota(D_0)$ and $\iota^{-1}(N_1)=N_0$. Let $e\ge0$ and $c\in\mathcal O$ satisfy:

1. $p^eN_2\subseteq F(N_1)$.
2. For each allowed cocycle $h$ of $D_2$, there are $k\ge0$, an allowed cocycle $h_1$ of $D_1$, and $x\in N_2$ with $Fh_1=p^k h+d_0(x)$. This is `RatSurj`.
3. For $\omega\in XU_0$, if $p^k\omega$ is a differential of an allowed pair for some $k\ge0$, then $c\omega$ is such a differential.

**Proposition.** Every allowed target cocycle $h$ has a closed allowed source pair $h^*$ with $Fh^*=cp^e h$ coordinatewise.

First, $\iota(w)\in U_1$ implies $w\in U_0$ by multiplying by $Q^M$ and using $\iota^{-1}(N_1)=N_0$. If $\iota(w)=Xt$, then $XF(t)=0$, hence $t=\iota(t_0)$ and $w=Xt_0$. For $t$ in $N_1$ or $U_1$, the corresponding $t_0$ is in $N_0$ or $U_0$. Thus the allowed terms in the kernel of $F$ descend to allowed terms in the kernel complex.

Given $h=(y,Xn)$, lift $p^e Q^M y$ and $p^e n$ to $a,b\in N_1$ using 1. Set $\tilde h=(Q^{-M}a,Xb)$, an allowed pair with $F\tilde h=p^e h$. Because $h$ is closed, $d_1\tilde h=\iota(\omega)$. It lies in $XU_1$, since it equals $X(u-v\varphi_1(b)+b)$ for $Xu=(\gamma_1-1)Q^{-M}a$ and $u\in U_1$. Thus $\omega\in XU_0$ by descent.

Use 2 to choose $k,h_1,x$, and by 1 choose $m\in N_1$ with $F(m)=p^e x$. Put $h_{\rm cl}=p^e h_1-d_0(m)$, closed since $d_1d_0=0$ by commutation. It maps to $p^{e+k}h$. Therefore $p^k\tilde h-h_{\rm cl}=\iota(\alpha)$ with $\alpha$ an allowed pair of $D_0$. Apply the differential and use injectivity to get $d_1\alpha=p^k\omega$. By 3 obtain $\beta$ with $d_1\beta=c\omega$. Then $h^*=c\tilde h-\iota(\beta)$ is closed and maps to $cp^e h$. The final multiplier is uniform in the target class.

## Lean correspondence

- `CokerKilled`, `RatSurj` and `Lifts` specify the coordinate costs. `cocycleLiftOfExact_holds` corrects the kernel differential. [Conditions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CoboundaryTransfers/Statement.lean#L158) · [Correction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CoboundaryTransfers/GammaStableTransfers/DiffOneSmulOfTower.lean#L83)
- `lift_wach` uses $c=R(0)C_\gamma$ from the [second-obstruction lemma](killing-the-second-herr-obstruction.md). [Wach application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CoboundaryTransfers/WachBridges.lean#L23)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
