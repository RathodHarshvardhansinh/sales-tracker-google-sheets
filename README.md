# Sales Tracker in Google Sheets

**Veda Technology Data Analytics Internship, Task 8**
**Author:** Rathod Harshvardhansinh J

A lightweight sales tracker that automatically calculates **daily, weekly and monthly totals** from raw sales entries. Enter data on one tab and the summary updates by itself.

## Live Google Sheet
🔗 **[Open the tracker](PASTE_YOUR_GOOGLE_SHEET_LINK_HERE)** (set sharing to "Anyone with the link: Viewer")

## Objective
Practice structuring a spreadsheet for ongoing data entry and automatic aggregation, keeping raw data and calculations on separate tabs.

## Tool
Google Sheets

## Dataset
Retail sales data. `sample_data.csv` holds 64 sample orders from 14 Sep to 16 Oct 2026 across 4 categories and 4 regions. The data is synthetic and created for practice.

## Sheet structure
| Tab | Purpose |
|---|---|
| `Instructions` | How to use the tracker |
| `Raw_Data` | The only place for data entry (Date, Order ID, Product, Category, Region, Qty, Unit Price, Sales) |
| `Summary` | Daily, weekly (Mon-Sun) and monthly totals using `SUMIFS` |
| `Verification` | Formula totals compared with manually calculated totals |

## Key formulas
```
Sales (Raw_Data!H2):   =IF(OR(F2="",G2=""),"",F2*G2)
Daily (Summary!B3):    =SUMIFS(Raw_Data!$H$2:$H$1000, Raw_Data!$A$2:$A$1000, A3)
Weekly (Summary!G3):   =SUMIFS(Raw_Data!$H$2:$H$1000, Raw_Data!$A$2:$A$1000, ">="&E3, Raw_Data!$A$2:$A$1000, "<="&F3)
Monthly (Summary!J3):  =SUMIFS(Raw_Data!$H$2:$H$1000, Raw_Data!$A$2:$A$1000, ">="&I3, Raw_Data!$A$2:$A$1000, "<"&EDATE(I3,1))
```

## Data validation (prevents bad entries)
- **Date:** must be a valid date
- **Qty:** whole number greater than 0
- **Unit Price:** number greater than 0
- **Category / Region:** dropdown lists only

## Verification (formula vs manual check)
Totals were calculated independently and compared with the sheet formulas. All checks match with a difference of 0.

| Period | Formula | Manual | Status |
|---|---|---|---|
| Week 1 (14-20 Sep) | 46,544 | 46,544 | ✅ |
| Week 2 (21-27 Sep) | 39,253 | 39,253 | ✅ |
| Week 3 (28 Sep-4 Oct) | 35,006 | 35,006 | ✅ |
| Week 4 (5-11 Oct) | 56,239 | 56,239 | ✅ |
| Week 5 (12-16 Oct) | 8,479 | 8,479 | ✅ |
| Sep 2026 | 99,481 | 99,481 | ✅ |
| Oct 2026 | 86,040 | 86,040 | ✅ |
| **Grand total** | **185,521** | **185,521** | ✅ |

## How to use
1. Open the sheet and go to `Raw_Data`.
2. Add a new row in columns A-G (blue text). Column H calculates itself.
3. Open `Summary` to see updated totals. Formulas cover rows 2-1000.

## Interview answers
**How would you design a spreadsheet so non-technical staff can enter data safely?**
Give them one clean input tab, use data validation (dropdowns, number and date rules), keep formulas out of the entry columns, and add an instructions tab with a clear example row.

**What's the risk of mixing raw data and formulas on the same tab?**
Formulas can be overwritten or deleted by accident. Sorting, filtering or inserting rows can break references. Mixed tabs are also harder to audit and extend, which is why raw entry and summaries are kept separate.

## Files in this repo
```
sales-tracker-google-sheets/
├── README.md
├── Sales_Tracker.xlsx      (import into Google Sheets)
├── sample_data.csv
├── formulas.md
```
