# A common window avoiding finitely many exceptional twists

[Chinese proof](../zh/%E6%9C%89%E9%99%90%E4%B8%AA%E4%BE%8B%E5%A4%96%E6%80%8E%E6%A0%B7%E8%AE%A9%E5%87%BA%E4%B8%80%E6%95%B4%E4%B8%AA%E5%85%B1%E5%90%8C%E7%AA%97%E5%8F%A3.md) · [Reading and review status](../../STATUS.md)

## The window lemma

Let $R\ge0$ be an integer, let $0<\eta\le C_t$, and let $X>1$. Let $\mathcal E$ be a set of at most $R$ nonnegative integers. Put $J=2^{R+2}(C_t/\eta)^R$. Then some $Y$ satisfies $X^{1/J}\le Y$ and $Y^2\le X$, and for every $x\in[Y,Y^2]$ and every $a\in\mathcal E$,

$$
a\le x^{C_t}\quad\Longrightarrow\quad a\le x^\eta. \tag{1}
$$

The integers in $\mathcal E$ are exceptional twist indices. The exponent $C_t$ describes the full range under consideration, whereas the available treatment of an exception needs the smaller range given by $\eta$.

## Proof on the logarithmic scale

Set $U=\log X>0$ and $B=C_t/\eta\ge1$. For a finite set $T\subseteq\mathbb R$ with $|T|\le R$, we first find $[y,2y]\subseteq(0,U]$ with $y\ge U/(2^{R+2}B^R)$, on which $a\le u$ implies $Ba\le u$ for every $a\in T$. Equivalently the interval avoids every $[a,Ba)$.

Induct on $R$. For $R=0$ take $y=U/2$. For $R>0$, if there exists $a_0\in T$ with $U/(2B)<a_0\le U$, set $U'=U/(2B)$ and remove $a_0$. The inductively chosen window in $(0,U']$ automatically avoids $[a_0,Ba_0)$. Its start satisfies

$$
y\ge\frac{U'}{2^{R+1}B^{R-1}}=\frac{U}{2^{R+2}B^R}.
$$

If there is no such $a_0$, every $a\in T$ with $a\le U$ satisfies $Ba\le U/2$. Thus $[U/2,U]$ works directly. This proves the induction.

Apply it to $T=\{(\log a)/C_t:a\in\mathcal E,\ a\ge1\}$ and set $Y=e^y$. For $x\in[Y,Y^2]$, the premise in (1) gives $(\log a)/C_t\le\log x$, and the new implication gives $B(\log a)/C_t\le\log x$. This is $a\le x^\eta$. The conclusion is automatic for $a=0$. Exponentiating the endpoint conditions gives the required bounds on $Y$.

## How a finite set of centres supplies the exceptions

Fix a prime $\ell$, an integer $Z\ge1$, and a centre $s$ in a nonarchimedean extension of $\mathbb Q_\ell$. Set $k=\lfloor\log_\ell Z\rfloor$. If two integers $1\le a,b\le Z$ both satisfy $|s-a|_\ell,|s-b|_\ell<\ell^{-k}$, ultrametricity gives $|a-b|_\ell<\ell^{-k}$. Thus $\ell^{k+1}\mid a-b$. But $|a-b|<\ell^{k+1}$ in the ordinary absolute value, so $a=b$.

The tower input `ABound` gives a base-field parameter $c$ with a primitive $\ell^c$th root of unity, and $R'\le R$ centres $s_i$. For each positive twist index $a$, each cyclotomic tower layer $L_1/L_0$ of degree $\ell^m$, and each integer $b\ge0$, if $|s_i-a|_\ell\ge\ell^{-b}$ for every $i$, then

$$
\operatorname{shaInv}(L_1,\ell,a)\le R'\big(\max(m,j_0)+c+b\big),
\qquad j_0=\lfloor\log_\ell R\rfloor+3.
$$

At $R=0$, use $j_0=3$, the value given by Lean's convention that the integer logarithm at zero is zero. The length `shaInv` is expressed using Selmer conditions on the absolute Galois group. The project identifies it with the localization-kernel length defined using ramification allowed above $\ell$. Take $b=k$ and set aside the possible single near integer for each centre. The exceptional set in $[1,Z]$ has size at most $R$. Every integer outside it meets all the distance hypotheses, so the bound applies and we may use $R$ in place of $R'$. This gives `FirstBound`. For $Z=0$, the index range is empty.

## Using the same window for all the towers

Fix $\varepsilon>0$ and uniform constants $C_K,C_t\ge1$. In the application $\varepsilon<1/52$, so $\eta=\varepsilon/(2C_K)$ satisfies $0<\eta\le C_t$. The dyadic tower contributes an exceptional set of size at most $R_0$. Each odd prime $\ell$ in a fixed finite set $B'$ contributes one of size at most $R_\ell$. It suffices to form these sets up to $Z=\lfloor X^{C_t}\rfloor$, since all points of the chosen window are at most $X$. Their union has size at most $R=R_0+\sum_{\ell\in B'}R_\ell$. The lemma gives a single window for the union, with

$$
J=2^{R+2}(2C_K C_t/\varepsilon)^R.
$$

Take $x_1\ge1$ above all the finitely many thresholds of the pointwise estimates and then take $X\ge\max(2,x_1^J)$. Every point of the chosen window is at least $Y\ge X^{1/J}\ge x_1$. Thus `ThmBab` fixes $J$ from the tower and field constants before choosing the outer scale and its exceptional sets. The start $Y$ is chosen after those sets are known.

## Lean references and review

- The real induction is [`window1`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LayeredIsomorphisms/Window1.lean), and the exponential version is [`window`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LayeredIsomorphisms/Window.lean).
- The uniqueness argument is [`near1`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LayeredIsomorphisms/Near1.lean), and [`exc`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LayeredIsomorphisms/Exc.lean#L7) gives `FirstBound` from the input in [`SecondBound.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LayeredIsomorphisms/SecondBound.lean).
- The combined application uses [`thmBab_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LayeredIsomorphisms/ThmBabOf.lean#L11), [`PartA.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LayeredIsomorphisms/PartA.lean), and [`PartB.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LayeredIsomorphisms/PartB.lean).

English translation draft. The proof uses `ABound` for the centres. The Chinese notes explain [the tower input](../zh/%E5%88%86%E5%9C%86%E5%A1%94%E7%9A%84%E9%95%BF%E5%BA%A6%E7%95%8C%E4%B8%BA%E4%BB%80%E4%B9%88%E5%8F%AA%E9%9C%80%E8%A6%81%E6%9C%89%E9%99%90%E4%B8%AA%E8%BF%9B%E8%B5%8B%E5%80%BC%E4%B8%AD%E5%BF%83.md) and [the cohomological length bound obtained on the common window](cohomological-window.md).
