# Second obstructions bound the number of deformation relations

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E5%8F%98%E5%BD%A2%E7%9A%84%E5%85%B3%E7%B3%BB%E6%95%B0%E7%94%B1%E4%BA%8C%E9%98%B6%E9%9A%9C%E7%A2%8D%E6%8E%A7%E5%88%B6.md)

## Statement

Let $O$ be a complete Noetherian local ring with finite residue field $k$ of odd characteristic $\ell$. Let $\Gamma$ be a profinite group satisfying `PhiCond`, meaning that every open subgroup has finitely many continuous homomorphisms to the additive group of $\mathbb F_\ell$. Choose coordinate weights $w_a$ in a finite-rank free abelian group $X$, a block decomposition, and a nondegenerate symmetric or alternating form $J$. The nonzero entries of $J$ pair blocks under an involution, and $w_a+w_b$ is constant on paired positions. The reference lift $r_0$ and its reduction $\bar r$ preserve weights, permute the blocks, and act by similitudes of $J$. Let $H$ be the subgroup of block-diagonal isometries congruent to the identity. For each weight $j$ let $\mathfrak g_j$ be the block-diagonal Lie algebra piece over $k$, given by $Y^{\mathsf T}J+JY=0$ and support in $w_a-w_b=j$, with $\Gamma$ acting by conjugation by $\bar r$.

The frame has finitely many framed places $v$, with one distinguished $v_0$, and finitely many places $q$ with local conditions. There are continuous maps $\phi_v:G_v\to\Gamma$ and $\psi_q:G_q\to\Gamma$, and $N_q\le G_q$ with $\bar r\psi_q|_{N_q}=1$. The condition $L_q$ contains the reference lift and is given by an ideal compatible with change of coefficients among the allowed lifts. It is invariant under $H$-conjugation and diagonal torus parameters congruent to one. It lifts across surjections $A\to A'$ whose kernel is killed by $\mathfrak m_A$. If two lifts across one such surjection agree over $A'$ and one satisfies $L_q$, the other satisfies $L_q$ exactly when they agree on $N_q$.

Let $B$ be a complete local algebra with residue field $k$ and a weighted formal presentation with coordinates in its maximal ideal. For each $v$ take a $B$-valued reference lift $\rho_v$ differing from $r_0\phi_v$ by $H$, with weighted entries. Over $B\to R$ we seek a lift $r$ differing from $r_0$ by $H$, satisfying $L_q$ at $q$, and matrices $\alpha_v\in H(R)$ with
$$
r(\phi_v(s))\alpha_v=\alpha_v\rho_v(s),\qquad \alpha_{v_0}=1.
$$
Suppose each obstruction space $\mathrm{Ob}_j$ defined below is finite dimensional. The problem has a universal ring with a weighted presentation over $B$. There are exactly $\dim_k H^1_{\mathrm{fr},j}$ new weight-$j$ variables, chosen from matrix entries of $r-r_0$ and $\alpha_v-1$. The number of weight-$j$ relations can be taken to be $\dim_k\mathrm{Ob}_j$ by padding with zero relations. Both universal matrices and frame matrices have entries of weight $w_a-w_b$. This is `LemmaP`.

## First-order variables

Write $M=\mathfrak g_j$. Define $H^1_{\mathrm{fr},j}$ to consist of a locally constant cocycle $x:\Gamma\to M$ vanishing on $\psi_q(N_q)$, together with $Y_v\in M$ such that
$$
x(\phi_v(s))=\phi_v(s)\cdot Y_v-Y_v,\qquad Y_{v_0}=0.
$$
In $k[\epsilon]/(\epsilon^2)$ over the constant map from $B$, put $r(g)=(1+\epsilon x(g))\bar r(g)$ and $\alpha_v=1-\epsilon Y_v$. The linearized group law, form, frame, and local conditions give exactly these equations. Conversely these data give a first-order lift. Thus this is the weight-$j$ tangent space.

Use the [universal ring and its homogeneous coordinates](the-universal-framed-ring-has-homogeneous-coordinates.md). Its relative cotangent space is $\mathfrak m_R/(\mathfrak m_B R+\mathfrak m_R^2)$. The indicated matrix entries distinguish first-order points, so in each weight they span the cotangent space and a basis can be chosen from them. Denote these variables by $Y$. Completeness gives $P=B[[Y]]\twoheadrightarrow R$ by successive approximation in the maximal ideal.

## The obstruction class

Put $J_{\mathrm{rel}}=\ker(P\to R)$ and $V=J_{\mathrm{rel}}/\mathfrak m_PJ_{\mathrm{rel}}$. This is finite dimensional by Noetherianity, and homogeneous representatives of a weight basis generate $J_{\mathrm{rel}}$ by Nakayama. Consider $P/\mathfrak m_PJ_{\mathrm{rel}}\to R$, whose kernel $V$ is killed by the maximal ideal. Use [square-zero lifting](lifting-form-preserving-matrices-across-square-zero-extensions.md) to choose homogeneous pointwise lifts $\widetilde r,\widetilde\alpha$ respecting the form and blocks. For each $q$ choose a lifted homomorphism $r_q$ satisfying $L_q$.

The errors are
$$
\begin{aligned}
d(s,t)&:\ \widetilde r(s)\widetilde r(t)-\widetilde r(st),\\
b_v(s)&:\ \widetilde r(\phi_v(s))\widetilde\alpha_v-\widetilde\alpha_v\rho_v(s),\\
c_q(s)&:\ \widetilde r(\psi_q(s))-r_q(s).
\end{aligned}
$$
Normalize on the right by $\bar r(st)^{-1}$, $\bar r(\phi_v(s))^{-1}$ and $\bar r(\psi_q(s))^{-1}$, respectively. Because the compared matrices agree modulo $V$ and $V^2=0$, the errors are Lie algebra valued with coefficients in $V$. A weight-$j$ coefficient in $V$ takes values in $\mathfrak g_j$. Associativity of triple multiplication gives $\delta d=0$ for the usual group differential. Substituting the frame comparison successively at $s,t$ gives $d|_{G_v}=\delta b_v$. The homomorphism identity for $r_q$ gives $d|_{G_q}=\delta c_q$. In each calculation a factor multiplying an error need only be taken residually, producing the $\bar r$ conjugation action.

Define $\mathrm{Ob}_j$ as the space of locally constant triples satisfying these identities modulo triples
$$
\left(\delta h,\quad h|_{G_v}-(s\mapsto\phi_v(s)\cdot U_v-U_v),\quad h|_{G_q}-e_q\right),
$$
where $h$ is a locally constant one-cochain, $U_v\in\mathfrak g_j$, and $e_q$ is a cocycle zero on $N_q$. On a one-dimensional kernel direction $\eta$, a triple of this form can be removed by multiplying $\widetilde r(g)$ on the left by $1-\eta h(g)$ and adding $\eta U_v$ to the frame. The remaining local difference is $-e_q$, which vanishes on $N_q$ and therefore preserves $L_q$. If necessary the $v_0$ frame is restored by conjugating the new representation by $1-\eta U_{v_0}$ and multiplying all frames on the left by it. The local conditions are invariant under this conjugation.

## Independence of the relations

Let $\lambda:V_j\to k$ be a functional, extended by zero on the other weights. If its contraction of the triple gives zero in $\mathrm{Ob}_j$, the correction gives a framed lift to $A_\lambda=(P/\mathfrak m_PJ_{\mathrm{rel}})/\ker\lambda$ over $B$, reducing to the universal object. Universality produces a section $R\to A_\lambda$ over $B$.

For $\lambda\ne0$ this is impossible. The section changes each variable's canonical lift by a multiple of the one-dimensional kernel generator $\eta$. For $F\in J_{\mathrm{rel}}$, this replacement cannot change the value of $F$ because $F\in\mathfrak m_B P+\mathfrak m_P^2$ by relative cotangent independence. Each variable's first-order derivative in $k$ is zero. The section makes all relations vanish, but the canonical substitution of a relation with nonzero $\lambda(F)$ gives $\lambda(F)\eta\ne0$. Hence $V_j^\vee$ injects into $\mathrm{Ob}_j$. Choose the minimal weight relations and pad with zeros to reach its dimension. Only finitely many differences of coordinate weights can contribute. In rank three the [relative Euler characteristic](the-real-place-contribution-to-global-deformation-equations.md) then gives $a_j+\mathbf1_{\{|j|\le1\}}$ equations of weight $j$.

## Lean correspondence

- [`lemmaP` and `lp_detect`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CommutativeAlgebra/LemmaP.lean#L256) give the presentation and the section contradiction. [`FormData`, `IsLocCond`, `Frame`, `H1c`, `Ob` and `LemmaP`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CommutativeAlgebra/FramedTwoCoboundaries.lean) give the hypotheses and spaces. [`PhiCond`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CommutativeAlgebra/ResMapBijective.lean#L336) is the finiteness condition.
- [`framed_tangent`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CommutativeAlgebra/FramedTangent.lean#L522) and [`rel_pres`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CommutativeAlgebra/RelPres.lean#L87) give variables and minimal relations.
- [`obs_class`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CommutativeAlgebra/ObsClass.lean#L94), [`obs_cocycle`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CommutativeAlgebra/ObsCocycle.lean#L141) and [`obs_correct`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CommutativeAlgebra/ObsCorrect.lean#L35) construct, test, and correct the obstruction.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
