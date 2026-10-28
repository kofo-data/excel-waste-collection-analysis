# Waste Collection Performance Analysis (Excel)

An end-to-end Excel project: messy collection data cleaned with Power Query, analysed with lookups and pivot tables, and presented in an interactive summary with slicers.

> **Note:** the data is simulated for practice. It is not real LAWMA or any other organisation's data.

## Business problem
Which zones collect the least waste per truck trip, which months are busiest, and which zones miss the most pickups, so extra resources can go where they matter most?

## Questions answered
1. Which zones collect the most and the least tonnage per trip?
2. Which month peaks, and by how much?
3. Which zones have the highest missed pickup rate?

## Tools and skills
- **Power Query:** cleaning, type conversion, locale-aware dates, custom columns
- **Excel formulas:** XLOOKUP, SUM, AVERAGE, TEXT
- **Pivot tables, pivot charts and slicers:** interactive Zone and Month filters
- **Data documentation:** README, data dictionary and an issues log

## Data
1,030 rows of daily collection records for 8 Lagos zones (2025): date, zone, truck ID, trips, tonnage, fuel used and missed pickups. A second table holds each zone's supervisor and population.

## Data cleaning (Power Query)
| Issue found | How many | Fix |
| --- | --- | --- |
| Duplicate rows | 30 | Removed (1,030 rows became 1,000) |
| Zone spelled many ways (capitals, extra spaces) | 39 spellings for 8 zones | Trim, then Capitalize Each Word |
| Text in Tonnage (e.g. "17.8 tons") | 24 | Removed the text, converted to number |
| Impossible Tonnage value of 999 | 5 | Replaced with blank, treated as missing |
| Blank Tonnage | 15 | Kept the row, excluded from tonnage averages |
| Blank or "N/A" Fuel | 26 | Converted to blank |
| Blank Truck ID | 15 | Left blank (not needed for the three questions) |
| Blank Missed Pickups | 15 | Left blank, excluded from the missed pickup average |
| Dates in 3 formats | 990 / 15 / 25 | Converted to real dates using the UK locale, so 05/03 means 5 March |

Every problem, count and decision is recorded in the workbook's `Issue_logs` sheet.

## Key findings
- **Tonnage per trip:** Alimosho collects the most (about 7.2 tons per trip) and Epe the least (about 3.7), so a trip in Alimosho collects nearly twice as much. The all-zone average is 5.63.
- **Peak month:** December is the busiest month at about 2,347 tons, around 62% above August, the lowest month at about 1,444 tons.
- **Missed pickups:** Ikorodu (2.56), Badagry (2.51) and Epe (2.41) have the highest averages per record, against 1.10 in Surulere and 1.70 overall.
- **Combined picture:** Epe, Badagry and Ikorodu are the three weakest zones on both tonnage per trip and missed pickups.

## Recommendation
Prioritise Epe, Badagry and Ikorodu. Next steps would be to check route length, truck allocation and collection frequency in these zones, and to investigate why pickups are missed. Plan extra capacity ahead of December.

## Limitations
- Months with missing tonnage values are slightly understated.
- Monthly totals depend partly on how many records fall in each month.
- The data is simulated, so the findings illustrate the method rather than describe a real service.

## Files
- `waste_collection_tracker.xlsx`: the full workbook (raw data, cleaned data, pivot tables, summary, issues log)
- `summary.png`: screenshot of the Summary sheet
- `cleaning_steps.txt: the full Power Query cleaning script

