# The norm congruence makes the one-row Cayley Gauss sum real

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $V,H,\Lambda,\alpha$ be a finite-dimensional positive definite Hermitian space, a full lattice self-dual for $E=\operatorname{Im}H$, and its semicharacter. Let $\delta$ be unitary with no nonzero fixed vector, with $\delta\Lambda$ commensurable with $\Lambda$ and carrying the same semicharacter, and with $\alpha(\delta x)=\alpha(x)$ for $x\in\Lambda$. Set
$$
A=1-\delta^{-1},\qquad C=A^{-1}-\tfrac12,\qquad L_A=A(\Lambda\cap\delta\Lambda)\subseteq\Lambda.
$$
The inclusion holds because $Ax=x-\delta^{-1}x$ lies in $\Lambda$ for $x\in\Lambda\cap\delta\Lambda$. The quotient $Q=\Lambda/L_A$ is finite since $A$ is invertible and the two lattices are commensurable. The phase and normalized Gauss sum in [the Cayley comparison](the-unitary-theta-scalar-from-a-cayley-gaussian.md#unfold-the-same-integral) are
$$
\phi(x)=\alpha(x)e^{-\pi H(Cx,x)},\qquad
G=|Q|^{-1/2}\sum_{x\in Q}\phi(x).
$$
The phase descends and has nondegenerate quadratic polarization there. This gives $G^8=1$ by [the finite Gauss sum law](the-eighth-power-of-a-finite-quadratic-gauss-sum.md), which does not require a one-dimensional theta space.

For the standard one-row period lattice of the host, and a source unitary in even rank acting on this row without fixed vectors, the stronger equality is
$$
G^2=1.
\tag{1}
$$
We prove it under the following data satisfied by that lattice. The Hermitian norm $q(x)=c\operatorname{Re}H(x,x)$, for fixed $c=\sqrt d/2$, is integer on $\Lambda$, and $\alpha(x)=(-1)^{q(x)}$ there. The complex space is a product indexed by embeddings of the host CM field, so an integral host scalar acts in each block by that embedding and preserves $\Lambda$. This action commutes with $\delta$. The field has the two imaginary quadratic generators of [the norm congruence](two-quadratic-norms-represent-minus-one-modulo-every-integer.md).

### Reverse the phase on the finite quotient

Put $e=|Q|>0$, so $e\Lambda\subset L_A$. Choose the host multipliers $\ell,s$, with $\bar s=s$ and
$$
\bar\ell\ell=-1+4es ,
$$
by the norm congruence. Multiplications by them and by $\bar\ell$ act as linear maps on $V$, and commute with $A,C,\delta$. The adjoint of multiplication by $\ell$ is multiplication by $\bar\ell$, since the Hermitian form is a sum over complex blocks. The multiplier by $s$ is self-adjoint. Every one of these maps preserves $L_A$, since it preserves $\Lambda$ and $\delta\Lambda$ and commutes with $A$. Modulo $L_A$, multiplication by $-\bar\ell$ inverts multiplication by $\ell$, as their composition is $1-4es$ and $e\Lambda\subseteq L_A$. Thus multiplication by $\ell$ permutes $Q$.

For $x\in\Lambda$ the polarization of $q$ gives
$$
2c\,\operatorname{Re}H(x,sx)=q(x+sx)-q(x)-q(sx)\in\mathbb Z.
$$
As $q(\ell x)=-q(x)+4ec\operatorname{Re}H(x,sx)$, the two diagonal phases have equal parity. Hence $\alpha(\ell x)=\alpha(x)$. For the other factor of $\phi$, the adjoint identity and commutation yield
$$
H(C\ell x,\ell x)=-H(Cx,x)+4eH(Cx,sx).
$$
The last inner product is purely imaginary because $C^*=-C$ and $s$ is self-adjoint and commutes with $C$. Also $H(x,sx)$ is real. Since $ex\in L_A$, $A^{-1}(ex)\in\Lambda$, so
$$
e\,\operatorname{Im}H(Cx,sx)
 =\operatorname{Im}H(A^{-1}(ex),sx)\in\mathbb Z
$$
by self-duality of $\Lambda$. The correction $4eH(Cx,sx)$ therefore contributes $1$ to the exponential. As $H(Cx,x)$ is purely imaginary, we obtain $\phi(\ell x)=\overline{\phi(x)}$. Summing over the permuted quotient shows $G=\bar G$. Its eighth power is $1$, so it is real of absolute value one, and (1) holds.

### The one-row host input

For standard source and target lattices, each matrix slot ranges independently in the same complex period module. Taking two target rows gives the product of two identical one-row lattices. The Hermitian form, phase, and action of a source unitary are products across the rows. The usual self-duality, commensurability and semicharacter hypotheses are available for two rows with an even source rank, and hence also for one row. For example a vector self-dual against the single row can be put in one coordinate and zero in the other, so self-duality of the two-row lattice puts the first vector in the one-row lattice. Likewise the indices and law of the sign on one row are obtained by restriction. Integer scalar multiplication on each slot comes from multiplication of the period module by $\mathcal O_{E_0}$. Thus all the data in the proof apply to the one-row normalized Gauss sum, even though an admitted host pair uses even ranks. Its sign disappears when the one-row phase is taken to an even power in the standard unitary constant.

### Lean correspondence

- [`cayC`, `phiC`, `latA` and `gaussC`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/UnitaryConstant.lean#L12) give the group, phase and normalization. The normalized eighth power is [`unitaryGauss`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/SelfDualCovolume.lean#L25).
- [`Multipliers`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/IntegralSquareRoots/CardSmulMem.lean#L49) gives the preservation, adjoint and norm relations. [`alpha_mult`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/IntegralSquareRoots/CharSingle.lean#L164) proves preservation of the sign and [`phi_conj`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/IntegralSquareRoots/CardSmulMem.lean#L80) reverses the complex phase. [`gauss_sq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/IntegralSquareRoots/CardSmulMem.lean#L138) concludes (1).
- [`Copies.unitaryData₁`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/IntegralSquareRoots/CharSingle.lean#L89) extracts the one-row hypotheses. [`mul_integer_mem_base_lattice`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/IntegralSquareRoots/MulIntegerMemBaseLattice.lean#L50) proves the integral scalar action; [`gaussRow_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/IntegralSquareRoots/MulIntegerMemBaseLattice.lean#L78) combines it with the host norm congruence and `qInt0` for the standard pair.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
