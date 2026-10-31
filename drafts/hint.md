# booking-v3 date hint disagrees with tenant date parsing

Covers **33 unique reports** merged into #4471 in the 2026-10-04 export, received 2026-04-17 through 2026-09-22. Deduplicated by report ID; classified by tenant locale, form version and channel using src/lib/kb/causes.ts, not intake tags or browser locale.

## Evidence
- R-41230, copper.studio, form: My client came on 1 June instead of 6 January. We sorted it out.
- R-41241, alder.physio, form: We had two people show up on 8 June. They were booked for 6 August.
- R-41251, pale.harbour, form: Wednesday 7 January showed as Wednesday 1 July. I moved it myself.

## Expected behavior and repair
Display a hint matching the tenant-aware form parser. Verify booking-v3 forms for alder.physio, copper.studio and pale.harbour; enter dates using the displayed hint and confirm the saved date.

Keep this separate from the shared parser repair. Counts and report IDs are in evidence/acceptance.json. 

See src/routes/kb/decisions/0002-dedupe-by-cause/+page.svx and rendered/0002-dedupe-by-cause.html. Snapshot only; refresh with the desk before closing. No deployed fix is claimed.
