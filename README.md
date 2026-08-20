# SignalDesk: weekly health check

**Track A.** Everything is contained in `index.html`. Open it in a browser with nothing to install. The data is embedded, and a file picker accepts next week's export.

**For:** the teammate deciding whether to roll these workflows out more broadly.

**Data:** `sample-data/product_usage_events.csv` as provided, with 41 rows covering Aug 1–7, 2026. Despite the filename, this is not an event log. The data is already aggregated by date × team × workflow × source.

**What it does:** decides which numbers are trustworthy this week, then reports them. Every row it strikes, repairs, or caveats stays on the page with its reason, so you can disagree with a call and see which rows to put back.

## Assumptions

- Acceptance is a share of `completed`, not `sessions`: an unfinished run was never offered to anyone.
- Aug 4–6 counts as post-change. The note says the version *started*; nothing says it stopped. Unverified.
- Both Aug 5 email rows are struck. Deduplicating alone would leave one copy of demo traffic, which still does not represent real usage.
- Aug 7 arrived with 4 of 6 rows and is held out of every comparison.
- Minutes saved, rating and confidence are weighted by runs, not averaged flat.

## Issues found

Duplicated export row; demo traffic inflating the week; confidence written as text (`n/a`); a blank rating; `product` vs `Product` splitting a groupby; a partial final day; undefined denominators.

## What it says

The Aug 4 prompt change reads **+6.8pp** as exported, **−0.2pp** once the demo row is struck, and **+1.0pp** after adjusting for the shift toward hand-started runs. That is uncertainty, not a win. Separately, Reply draft acceptance halved on Aug 7 while model confidence hit its weekly high. That mismatch is why confidence is never treated as a measure of quality here.

## Next

Separate demo from internal traffic in the export; document the Aug 7 policy change; re-run the automated-versus-manual split next week to test whether the prompt only helps on messy input.
