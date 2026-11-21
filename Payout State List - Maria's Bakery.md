# Payout State List: Maria's Bakery

Account: `acct_test_maria_bakery` (Stripe test mode). Source: *Current Dashboard Home - the 11 Panels Owners See Today.md*, checked against the Sep-Nov 2026 balance transactions CSV.

There are **4 payout states**. Each owner moment maps to exactly one.

## Summary

| # | State id | Moment | Balance panel (9) today | Payouts page today | Owner question Home can't answer |
|---|---|---|---|---|---|
| 1 | `payout_scheduled` | Payout on its way | "$312.40 available" | "$4,200.00 · In transit" (arrival date only inside the row) | How much is coming and when? |
| 2 | `pending_only` | Money only pending | "$0.00 available" | "No upcoming payouts" | Where is my money, and when can I use it? |
| 3 | `no_payout` | Nothing scheduled | Current available figure only | "No upcoming payouts" | Why is nothing scheduled? |
| 4 | `negative_after_refund` | Morning after the catering refund | "-$1,874.55" in grey, no label | Payout row reads "Canceled" | Why is it negative, why was my payout canceled, when do payouts resume? |

## State details

### 1. `payout_scheduled` — Payout on its way
- **Condition:** A payout exists and is in transit to the bank.
- **Home shows:** "$312.40 available" (panel 9). Nothing about the $4,200.00 payout.
- **After 4 clicks:** Row "$4,200.00 · In transit". The arrival date appears only after opening the row.
- **Missing on Home:** The payout amount and its arrival date.

### 2. `pending_only` — Money only pending
- **Condition:** Funds from recent charges are pending and none is available yet, so no payout is scheduled.
- **Home shows:** "$0.00 available". Pending balance is never shown.
- **After 4 clicks:** "No upcoming payouts".
- **Missing on Home:** The pending amount and the date it becomes available. The money looks gone.

### 3. `no_payout` — Nothing scheduled
- **Condition:** No payout is scheduled and none is in transit.
- **Home shows:** The current available figure only.
- **After 4 clicks:** "No upcoming payouts".
- **Missing on Home:** Any reason why no payout is scheduled.

### 4. `negative_after_refund` — Morning after the catering refund
- **Condition:** A large refund (the catering refund) pushed the balance below zero and the scheduled payout was canceled.
- **Home shows:** "-$1,874.55" in grey, with no label or explanation.
- **After 4 clicks:** Payout row reads "Canceled".
- **Missing on Home:** Why the balance is negative, why the payout was canceled, and when payouts start again.

## Notes
- Across all four states, Home never shows the next payout amount, its arrival date, or the pending balance. Finding it takes 4 clicks: Balance "View" → Payouts tab → "Upcoming" filter → open the row.
- The CSV only contains `paid` and `canceled` payout statuses (68 payouts, 4 `payout_cancel` rows) and no failure reasons. A failed-payout state (bank rejection, etc.) is not in the capture, so it is not listed. Add it if you want it covered.
- The CSV is test-mode data and its running balances don't line up with the $312.40 / -$1,874.55 figures in the capture, so the four states above come from the Home capture, not the CSV.
