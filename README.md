# A modified MKS for health time series data

## Data
The file *data.csv* includes varaibles derived by the MKS. The variables are the outputs generated at each step of the analysis (i.e., Case, Mi, Sk, E(Sk), VAR(Sk), R_case, R_Mi, R_Sk, R_Uf, and U_b). The file also includes the final plots with the forward sequence U_f and the backward sequence U_b for each of the 50 US states.

### Data columns
Week: week ID, where Week 1 starts on March 23, 2020 and Week 45 ends on January 31, 2021.
Case: new weekly cases in the time series X.
Mi: cumulative times that the case value of the current week is larger than that of each preceding week.
Sk: test statistics of X.
E(Sk): mean of Sk.
VAR(Sk): variance of Sk.
U_f: forward sequence of X.
R_case: X_r, the reversed time series X.
R_Mi: Mi of R_case.
R_Sk: Sk of the reversed time series X (X_r).
R_Uf: Intermediate sequence (U_fr) derived by applying the same equation generating U_f to the reversed time series data X
U_b: backward sequence of time series data X

### Excel function used for each step
1. D2, E2, F2, G2, H2, J2, K2, L2 = 0.
2. P1 = A46.
3. I2 = INDIRECT(“C”&P$1-A2+2).
4. Apply the INDIRECT function to all rows from I2 to I46.
5. D3 = COUNTIF (C$2:C2,”<”&C3), then apply the same function to the rest of the column.
6. E3 = E2+D3, then apply the same function to the rest of the column.
7. F3 = A3*(A3-1)*(2*A3+5)/72, then apply the same function to the rest of the column.
8. H3=(E3-F3)/SQRT(G3), then apply the same function to the rest of the column.
9. J3 = COUNTIF (I$2:I2,”<”&I3), then apply the same function to the rest of the column.
10. K3 = K2+J3, then apply the same function to the rest of the column.
11. L3 = (K3-F3)/SQRT(G3), then apply the same function to the rest of the column.
12. M2 = -INDIRECT(“L”&P$1-A2+2), then apply the same function to the rest of the column.
13. Q2 = 1.96 (positive z-score for the upper 95% CI), then apply the same function to the rest of the column.
14. R2 = -1.96 (negative z-score for the lower 95% CI, then apply the same function to the rest of the column.
15. Plot U_f, U_b, and y = ±1.96 in a figure for each state.
