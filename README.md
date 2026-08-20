# SignalDesk — weekly health check

**Track A.** One file, `index.html` — open in a browser, nothing to install. Data is embedded; a file picker takes next week's export.

**For:** the teammate deciding whether to roll these workflows out more broadly.

**Data:** `sample-data/product_usage_events.csv` as provided, 41 rows, Aug 1–7 2026. Not an event log despite the filename — pre-aggregated to date × team × workflow × source.

**What it does:** decides which numbers are trustworthy this week, then reports them. Every row it strikes, repairs, or caveats stays on the page with its reason, so you can disagree with a call and see which rows to put back.

## Assumptions

- Acceptance is a share of `completed`, not `sessions`: an unfinished run was never offered to anyone.
- Aug 4–6 counts as post-change. The note says the version *started*; nothing says it stopped. Unverified.
- Both Aug 5 email rows are struck — deduplicating alone leaves one copy of demo traffic, which is still not usage.
- Aug 7 arrived with 4 of 6 rows and is held out of every comparison.
- Minutes saved, rating and confidence are weighted by runs, not averaged flat.

## Issues found

Duplicated export row; demo traffic inflating the week; confidence written as text (`n/a`); a blank rating; `product` vs `Product` splitting a groupby; a partial final day; undefined denominators.

## What it says

The Aug 4 prompt change reads **+6.8pp** as exported, **−0.2pp** once the demo row is struck, and **+1.0pp** adjusted for the mix shift toward hand-started runs. Uncertainty, not a win. Separately, Reply draft acceptance halved on Aug 7 while model confidence hit its weekly high — which is why confidence is never treated as quality here.

## Next

Separate demo from internal traffic in the export; document the Aug 7 policy change; re-run the automated-versus-manual split next week to test whether the prompt only helps on messy input.
