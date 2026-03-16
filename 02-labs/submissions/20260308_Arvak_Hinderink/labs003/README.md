# Submission for labs003

This directory contains the submission for the problem **labs003**.

## Conversion: 6 QUBO variables -> 3 qubits -> 3 original variables

The QUBO formulation of labs003 has **6 binary variables**: 3 original sequence variables `x[1], x[2], x[3]` and 3 auxiliary linearisation variables `z[i,k] = x[i] * x[i+k]`.

**Parity Correlation Encoding (PCE)** maps all 6 QUBO variables onto **3 qubits** using a dense parity scheme:

| QUBO var | Parity mask | Decoded as |
|----------|-------------|------------|
| x₀ (= x[1]) | `001` | qubit 2 |
| x₁ (= x[2]) | `010` | qubit 1 |
| x₂ (= x[3]) | `011` | parity of qubits 1, 2 |
| x₃ (= z[1,1]) | `100` | qubit 0 |
| x₄ (= z[2,1]) | `101` | parity of qubits 0, 2 |
| x₅ (= z[1,2]) | `110` | parity of qubits 0, 1 |

Each variable `i` (0-indexed) gets mask `i+1`. Decoding a 3-qubit measurement bitstring `b`:

```
x_i = popcount(b AND mask_i) mod 2
```

The QUBO objective is reformulated as a sum of Pauli Z-correlation operators (each mask corresponds to a product of Z operators on the masked qubits). A variational circuit is optimised with COBYLA to minimise the expectation value.

**Solution conversion**: The optimiser returns all 6 QUBO variable values. The solution file contains only the first 3 (the original LABS sequence variables `x[1], x[2], x[3]`), since the auxiliary `z` variables are fully determined by these.

**Energy**: QUBO objective = -4, plus ObjectiveOffset = 5, gives LABS energy = **1** (optimal).

## CSV Summary

| Field | Value |
|-------|-------|
| Problem | labs003 |
| Submitter | Daniel Hinderink (hiq-lab) |
| Date | 8. Mar. 2026 |
|======||
| Reference | https://arvak.io |
|======||
| Best Objective Value | 1 |
| Optimality Bound | N/A |
|======||
| Modeling Approach | QUBO |
| # Decision Variables | 6 |
| # Binary Variables | 6 |
| # Integer Variables | 0 |
| # Continuous Variables | 0 |
| # Non-Zero Coefficients | 21 |
| Coefficients Type | Integer |
| Coefficients Range | {-8, 12} |
|======||
| Workflow | PCE dense: 6 QUBO vars -> 3 qubits via parity masks. COBYLA + statevector sim (2048 shots/eval). Solution converted back to 3 original LABS variables. |
| Algorithm Type | Stochastic |
| # Runs | 1 |
| # Feasible Runs | 1 |
| # Successful Runs | 1 |
| Success Threshold | 0 |
|======||
| Hardware Specifications | Apple M3 Pro (statevector simulation) |
|======||
| Total Runtime | 0.11 |
| CPU Runtime | 0.11 |
| GPU Runtime | N/A |
| QPU Runtime | N/A |
| Other HW Runtime | N/A |
|======||
| Remarks | QUBO objective: -4 + offset 5 = LABS energy 1. 2.0x qubit compression via PCE. Arvak v1.9.3. |
