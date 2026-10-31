# Shared date parser uses month-first order for day-first tenants

Covers **379 unique reports** merged into #4471 in the 2026-10-04 export, received 2026-04-01 through 2026-10-04. Deduplicated by report ID; classified by tenant locale, form version and channel using src/lib/kb/causes.ts, not intake tags or browser locale.

## Evidence
- R-41200, harbour.dental, app: Our 7 April reminder went out on 4 July. Is this a joke. It is not April Fools where we are.
- R-41201, harbour.dental, app: Sorry. 4 July went out on 7 April. I have been up since five.
- R-41202, kettle.books, email: Invite says Tuesday 12 May. Calendar says Monday 11 May. My client turned up on the Monday. We had coffee.

## Expected behavior and repair
Parse dates consistently with the tenant locale; 07/04/2026 means 7 April for en-GB. Exercise app, email and booking-v2 forms.

Keep this separate from the form hint repair. Counts and report IDs are in evidence/acceptance.json. Five footnoted reports have atypical timing or one-day symptoms: R-41202, R-41209, R-41236, R-41344, R-41620. They are classified here by the supplied rules; investigate source events and time zones before claiming a parser fix resolves them.

See src/routes/kb/decisions/0002-dedupe-by-cause/+page.svx and rendered/0002-dedupe-by-cause.html. Snapshot only; refresh with the desk before closing. No deployed fix is claimed.
