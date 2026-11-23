# Austin Peak Pilot

An offline work sample for Bidgely’s New Products Market Introduction track.

Open `index.html` in a browser. It includes all three observed scores, invitation-budget sensitivity, household evidence, and the pilot decision. `pilot-brief.md` is the companion briefing. The browser uses frozen analysis output and performs no network requests.

## Evaluation protocol

- Event: August 23, 2018, 16:30 inclusive to 16:45 exclusive CDT (21:30–21:45 UTC). See cell F3 of ERCOT’s `ERCOTFourCoincidentPeakLoadCalculation2018.xlsx` in the [historical 4CP workbook archive](https://www.ercot.com/mktinfo/data_agg/4cp). F3 is the quarter-hour ending time.
- Main baseline: descending mean signed main-panel real power across the 1,230 labeled minutes through the ranking cutoff (August 23, 00:00–20:30 UTC, end exclusive). Negative main-panel readings remain signed. The baseline represents net grid demand as measured at the panel, so behind-the-meter generation may affect it.
- HVAC rule: descending mean of condenser plus indoor fan real power in the fixed hour from 14:30 to 15:30 CDT on August 23. The ranking cutoff is one hour before the event. The preceding day’s matching interval falls outside the publisher archive. The input is directly measured HVAC power. A production version that uses disaggregation would require separate validation.
- Time-matched baseline: descending mean signed main-panel power during that same 14:30–15:30 CDT window. This comparison isolates the effect of including an HVAC signal from the change in the hours used to rank households.
- Break ties by ascending dataset household ID. Compare the top three households as the primary illustration and expose every equal invitation budget. The three slots are illustrative.
- Use the same pre-event-eligible households for all rules. Incomplete pre-event windows exclude a household from every rule. An incomplete event channel for an eligible household stops scoring. No missing readings are filled. Tiny negative meter readings remain signed.
- Score mean event HVAC kW for each home and sum it across the selected cohort. All accumulation and rank comparisons use exact integer watt readings or rational arithmetic. Rounding is for presentation. Treat timestamps as minute labels and use half-open windows.
- Robustness check: run those identical clock windows, durations, cutoffs, ranking rules, and invitation budgets on August 24 and 25. Both are same-clock follow-ups. Only August 23 is the ERCOT August coincident peak. The August 23 result drove the original demo. The follow-ups were added in review, with no parameter tuning between dates.
- Outcome scope: three quarter-hours in the same ten homes. No intervention took place. The replay cannot establish curtailment, enrollment, generalization, or business economics.

## Reproduce

Download Pecan Street’s [source ZIP](https://www.kaggle.com/api/v1/datasets/download/pecanstreetinc/ps-data-10-homes-1min-frequency-aug-2018) from its [published dataset](https://www.kaggle.com/datasets/pecanstreetinc/ps-data-10-homes-1min-frequency-aug-2018). The expected member is `PecanStreet_10_Homes_1Min_Data.csv`. Only the derived summaries are included here.

With Python 3.10 or newer, run `python3 replay.py /path/to/source.zip`. The verifier pins the CSV member by SHA-256, checks the schema and canonical minute keys, and writes `results.json` and `index.html`. Run `python3 replay.py /path/to/source.zip --verify` to regenerate both in memory and compare every byte with the deliverables. Run `python3 -m unittest -v` for the behavioral checks.
