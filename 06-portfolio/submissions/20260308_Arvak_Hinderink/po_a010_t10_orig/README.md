# Submission for po_a010_t10_orig

This directory contains the submission for the problem **po_a010_t10_orig**.

## CSV Summary

| Field | Value |
|-------|-------|
| Problem | po_a010_t10_orig |
| Submitter | Daniel Hinderink (hiq-lab) |
| Date | 8. Mar. 2026 |
|======||
| Reference | https://arvak.io |
|======||
| Best Objective Value | -0.030604 |
| Optimality Bound | N/A |
|======||
| Modeling Approach | QUBO |
| # Decision Variables | 10 |
| # Binary Variables | 10 |
| # Integer Variables | 0 |
| # Continuous Variables | 0 |
| # Non-Zero Coefficients | 100 |
| Coefficients Type | Continuous |
| Coefficients Range | {-0.01, 0.001} |
|======||
| Workflow | 1) Portfolio QUBO built from stock prices and covariance data. 2) PCE dense encoding compresses 10 variables to 4 qubits. 3) COBYLA optimizer on statevector simulator (2048 shots/eval). |
| Algorithm Type | Stochastic |
| # Runs | 1 |
| # Feasible Runs | 1 |
| # Successful Runs | 1 |
| Success Threshold | 0 |
|======||
| Hardware Specifications | Apple M3 Pro (statevector simulation) |
|======||
| Total Runtime | 0.24 |
| CPU Runtime | 0.24 |
| GPU Runtime | N/A |
| QPU Runtime | N/A |
| Other HW Runtime | N/A |
|======||
| Remarks | Runtime in seconds. PCE dense: 10 vars -> 4 qubits (2.5x compression). Arvak v1.9.3. |
