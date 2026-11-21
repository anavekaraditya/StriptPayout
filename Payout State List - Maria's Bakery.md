# Payout State List: Maria's Bakery

Account: `acct_test_maria_bakery` (Stripe test mode). Source: *Current Dashboard Home - the 11 Panels Owners See Today.md*. The "Home text" for each state is the author's own wording. Bracketed values are not supplied yet and are left as brackets.

There are **4 payout states**. Each owner moment maps to exactly one.

## Summary

| # | State id | Moment | Balance panel (9) today | Payouts page today |
|---|---|---|---|---|
| 1 | `payout_scheduled` | Payout on its way | "$312.40 available" | "$4,200.00 · In transit" (arrival date only inside the row) |
| 2 | `pending_only` | Money only pending | "$0.00 available" | "No upcoming payouts" |
| 3 | `no_payout` | Nothing scheduled | Current available figure only | "No upcoming payouts" |
| 4 | `negative_after_refund` | Morning after the catering refund | "-$1,874.55" in grey, no label | Payout row reads "Canceled" |

## 1. `payout_scheduled` — Payout on its way
- **Condition:** A payout exists and is in transit to the bank.
- **Home shows today:** "$312.40 available". Nothing about the $4,200.00 payout.
- **What's missing:** The $4,200.00 payout and its arrival date. They appear only after 4 clicks, and the date only inside the row.
- **Home text:** "$4,200.00 is on its way to your bank. It should arrive on [date]. You also have $312.40 available now."

## 2. `pending_only` — Money only pending
- **Condition:** Money is pending, none is available, and no payout is scheduled.
- **Home shows today:** "$0.00 available". The pending balance is never shown.
- **What's missing:** The pending amount and the date it becomes available. The money looks gone.
- **Home text:** "Your money isn't gone, it's on hold. [$ amount] from recent sales becomes available on [date]. Nothing is scheduled to pay out until then."

## 3. `no_payout` — Nothing scheduled
- **Condition:** No payout is scheduled and none is in transit.
- **Home shows today:** The current available figure only.
- **What's missing:** Any reason why no payout is scheduled.
- **Home text:** "No payout is scheduled right now. You have $[available] available. A payout will be scheduled once [reason]."

## 4. `negative_after_refund` — Morning after the catering refund
- **Condition:** The catering refund took the balance below zero and the payout was canceled.
- **Home shows today:** "-$1,874.55" in grey, with no label or explanation.
- **What's missing:** Why the balance is negative, why the payout was canceled, and when payouts start again.
- **Home text:** "Your balance is -$1,874.55 because of the catering refund. Your payout was canceled. New sales will cover this first, and payouts restart once your balance is back above $0."

## Open brackets
`payout_scheduled`: [date]. `pending_only`: [$ amount], [date]. `no_payout`: $[available], [reason].

## Notes
- Across all four states, Home never shows the next payout amount, its arrival date, or the pending balance. Finding it takes 4 clicks: Balance "View" → Payouts tab → "Upcoming" filter → open the row.
- The Home capture lists no failed-payout state, and the CSV has no payout failure reasons, so none is included.
- The CSV does not contain the figures in these states. See *Test-Mode Cases - Maria's Bakery.md*.
