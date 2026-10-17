# Formulas used (Google Sheets)

| Where | Formula |
|---|---|
| Raw_Data!H2 (Sales) | `=IF(OR(F2="",G2=""),"",F2*G2)` |
| Summary!B3 (Daily) | `=SUMIFS(Raw_Data!$H$2:$H$1000,Raw_Data!$A$2:$A$1000,A3)` |
| Summary!F3 (Week end) | `=E3+6` |
| Summary!G3 (Weekly) | `=SUMIFS(Raw_Data!$H$2:$H$1000,Raw_Data!$A$2:$A$1000,">="&E3,Raw_Data!$A$2:$A$1000,"<="&F3)` |
| Summary!J3 (Monthly) | `=SUMIFS(Raw_Data!$H$2:$H$1000,Raw_Data!$A$2:$A$1000,">="&I3,Raw_Data!$A$2:$A$1000,"<"&EDATE(I3,1))` |
| Verification!E2 | `=C2-D2` |
| Verification!F2 | `=IF(ABS(E2)<0.005,"MATCH","CHECK")` |
