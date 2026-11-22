# Reducing lattice moves to finite residue data

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix a class representative of a split decorated point model at one layer and a selected place $P$ above the word prime $T$. Write $q=T$, $\mathcal O=\mathcal O_{E,P}$ and $k_P=\mathcal O_E/P$. Let $N$ be its global lattice, $L=N_P$ its localization, and $f:L\to k_P$ its nonzero residue functional. Set $L_0=\ker f$ and let $N_0$ be the global lower lattice with $(N_0)_P=L_0$. The following residue data determine the moves on this layer.

- For an upper move, the class of $e\in L$ in $L/qL$ with $f(e)=1$ determines the enlarged lattice and the new functional.
- The distinguished class of $qe$ in $L_0/qL_0$ is independent of the choice of such an $e$.
- For a lower point with lattice $L_0$, its residue functional is specified by a linear form on $L_0/qL_0$. When that form takes value one on the distinguished class, the lower point moves back up to the original one.
- For a diamond move, a residue unit multiplies the current functional and leaves the lattice fixed.

These descriptions give the maps to the finite coefficient quotients used by the actual point model.

### Reduction of localized vectors

For a full global lattice $A$ with localization $A_P$, define a reduction of $x\in A_P$ with values in $A/PA$ as follows. Choose $s\in\mathcal O_E\setminus P$ with $sx\in A$ and put
$$
\operatorname{red}_A(x)=\bar s^{-1}[sx].
$$
If another denominator $s'$ is chosen, cross multiplication represents the same class because $s'(sx)=s(s'x)$ and both residues are nonzero. Using a common denominator for two vectors proves additivity. With a local scalar written as a fraction whose denominator is prime to $P$, the same formula gives semilinearity through reduction to $k_P$. Each global residue class has a representative in $A$, so the reduction is surjective. Its kernel is $P A_P=q A_P$, since reduction is zero exactly when $sx\in PA$ for a permitted denominator.

In particular $L/qL\simeq N/PN$ and $L_0/qL_0\simeq N_0/PN_0$. The functional on $L$ factors through $\operatorname{red}_N$, since it kills $qL$. This is the abstract class functional on the first finite quotient. The reduction $\operatorname{red}_{N_0}$ is the map on the kernel lattice.

### Reading the three moves

For the upper move choose a global representative $e'\in N$ of $\operatorname{red}_N(e)$. Then $f(e')=1$ and $e'-e\in qL$. The local formula $L^+=L+\mathcal O q^{-1}e$ is unchanged by this difference, as is $f^+(v)=f(qv)$. The global upper move therefore has exactly the prescribed local pair, keeps the other local pairs and retains the off-prime component, by [the split construction](splitting-a-point-into-its-word-prime-data-and-off-prime-data.md).

To compute the distinguished class, note that $qe\in L_0$. If $f(e)=f(e')=1$ then $e-e'\in L_0$, so $qe$ and $qe'$ have the same reduction in $L_0/qL_0$. This class is nonzero, because $qe\in qL_0$ would imply $e\in L_0$. For a lower move from the original point, an arbitrary prescribed nonzero functional on $L_0/qL_0$ gives the new functional on $L_0$ by composition with its reduction. The function is extended by zero outside $L_0$. If the form sends the distinguished class to one, then for every $v\in L$ its value on $qv$ is $f(v)$ by decomposing $v$ as an element of $L_0$ plus a multiple of $e$. This verifies the inverse condition in [the elementary move proof](matching-one-prime-lattice-neighbours-by-a-residue-map.md). The last move multiplies $f$ by a residue unit, which directly agrees with the local diamond relation.

The moved arithmetic point belongs to a class $c_{\rm new}$. Choose its arithmetic frame-group transporter from that class's representative. The equality of the point actions from [the quotient realization](constructing-the-point-model-by-a-torsion-quotient.md) sends the complex point representative of $c_{\rm new}$ to the point with exactly the changed local pair. The action on its values is the action of the **same** transporter. This proves the point-model readout of the upper, lower and diamond transports.

### Lean correspondence

- [`redL` and `redL_spec`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/InvSmulMemOfRedL.lean#L180) give the reduction by a permitted denominator. [`redL_add`, `redL_smul`, `redL_surj` and `inv_smul_mem_of_redL`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/InvSmulMemOfRedL.lean#L211) verify the quotient laws.
- [`fv_redL` and `redL_te`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsLevelPrimePointModelRealisation.lean#L316) identify the residue functional and the distinguished vector. [`up_spec`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsLevelPrimePointModelRealisation.lean#L353), [`dn_spec`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsLevelPrimePointModelRealisation.lean#L375) and [`dil_spec`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsLevelPrimePointModelRealisation.lean#L399) match the three moves.
- [`PtModel`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/FormsStable.lean#L76) states the required interfaces. [`model`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsLevelPrimePointModelRealisation.lean#L421) uses these reductions for the two finite spaces and the class transporters.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
