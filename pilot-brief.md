# Austin Peak Pilot

**Decision.** Keep the utility’s current recruitment rule in place. Test appliance-level targeting in shadow mode before changing who receives invitations.

## Buyer and product hypothesis

Start with a demand-side management lead who already runs a residential smart-thermostat program and has a limited outreach budget for a summer recruitment wave. The product hypothesis is that a dated, explainable comparison of invitation lists could help that lead and the utility’s measurement team decide where appliance signals justify changing the list. Bidgely already markets HVAC and thermostat targeting in Analytics Workbench. This work sample tests a way to validate the targeting decision with the buyer’s data and existing process. [Bidgely Analytics Workbench](https://www.bidgely.com/pdf/pge-utility-moonshot-case-study) · [Bidgely load shaping](https://www.bidgely.com/load-shaping)

## Evidence from the replay

At three invitations, the recent-HVAC list captured **8.845 kW** of observed HVAC draw in the ERCOT peak interval on August 23. That’s **1.712 kW** more than the longer-history panel list and **0.777 kW** more than the same-hour panel list. Home 07 ranked first under every rule and fell from **4.732 kW** in the input hour to **0.004 kW** in the scored quarter-hour.

Applying the same protocol at the same time on August 24 and 25 reversed the result. The HVAC list trailed the same-hour panel list by **0.716 kW** and **2.365 kW**. Both are follow-up intervals in the same homes. Only August 23 is the ERCOT coincident peak. No dispatch or outreach took place. [Pecan Street data](https://www.pecanstreet.org/2025/07/public-data/) · [ERCOT peak workbook archive](https://www.ercot.com/mktinfo/data_agg/4cp)

## How I’d test the opportunity

1. **Customer discovery.** Ask the program lead to walk through the last list they approved. Ask the measurement lead what would count as credible evidence for changing the list. Ask the utility’s data owner whether interval data and appliance estimates arrive in time for the proposed cutoff. Test whether the strongest buying reason is higher verified kW per invite or a more defensible list approval process. Bring the actual list format to the next meeting.
2. **Shadow evaluation.** Compare the utility’s actual list logic, a time-matched panel baseline, and appliance estimates at equal fixed budgets. Use independently measured HVAC for a validation subset and freeze rules before evaluating multiple new peak dates. Report wins, losses, and exclusions by date. Check latency, thermostat eligibility, solar and non-solar coverage, and whether exclusions concentrate in particular customer groups. Agree on the minimum improvement and quality floor before seeing outcomes.
3. **Go/no-go for a field pilot.** If the shadow result clears the agreed bar, randomize eligible customers between outreach policies and preserve a dispatch holdout among eligible enrollees. Measure incremental coincident kW per invite, enrollment, opt-outs, comfort, and rebound. Keep outreach and incentive rules comparable across arms. Finance supplies the value per verified kW and full incremental cost. The break-even value per kW is incremental program cost divided by incremental verified kW, when the measured increment is positive. The Austin replay provides neither input.

## Build record

Daniel directed the use of real Austin data, deterministic outcomes, and review against Bidgely’s hiring brief. Codex implemented the analysis and interface. The review added two same-clock follow-ups after the first version led with a favorable peak. Integer readings, explicit UTC windows, tests for cutoff and missing data, and an independent cohort calculation check the generated work. The browser displays the resulting evidence without a live model call. [Reproduction protocol](README.md)
