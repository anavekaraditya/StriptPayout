# Current Dashboard Home: the 11 Panels Owners See Today

This is a capture of the live Stripe Dashboard Home screen in November 2026. It lists each panel and the exact text Home shows on Maria's bakery account (acct_test_maria_bakery) in four balance situations.

## The 11 panels, top to bottom

| # | Panel title | What it shows | Example text on screen |
|---|---|---|---|
| 1 | Setup guide banner | Setup tips for the account | "Add your business logo to receipts" |
| 2 | Today | Gross volume chart for today against yesterday | "Gross volume $1,284.60 · Yesterday $1,102.15" |
| 3 | Recommendations | Stripe feature suggestions for the account | "New: send invoices by text message" |
| 4 | Gross volume | Total charged this month before refunds and fees | "Gross volume this month" |
| 5 | Net volume | Volume this month after refunds and fees | "Net volume this month" |
| 6 | Successful payments | Last 5 successful charges with amount and status | "$18.50 · Succeeded · Croissant box" |
| 7 | New customers | Count of new customers this week | "12 new customers this week" |
| 8 | Failed payments | Charges that failed in the last 7 days | "2 failed payments · Card declined" |
| 9 | Balance | Available balance only, as a small figure with a "View" link | "$312.40 available · View" |
| 10 | Disputes | Open disputes with a response deadline | "No disputes need a response" |
| 11 | Recent activity | Latest events on the account | "Harbor Café · $2,310.00" |

No panel on Home shows the next payout amount or its arrival date. The Balance panel (9) never shows the pending balance.

## Path to the next payout today (4 clicks)

1. Click the "View" link on the Balance panel (panel 9).
2. Click the "Payouts" tab.
3. Click the "Upcoming" filter.
4. Open the payout row. The arrival date appears only inside the row.

## What Home shows today on Maria's account

The text in quotes below is the literal text on screen.

| Moment | Matching state id | Balance panel (9) on Home | Payouts page (after 4 clicks) | What is missing |
|---|---|---|---|---|
| Payout on its way | payout_scheduled | "$312.40 available" | Row "$4,200.00 · In transit". The arrival date shows only after opening the row | The $4,200.00 payout and its arrival date are not on Home |
| Money only pending | pending_only | "$0.00 available" | "No upcoming payouts" | The pending amount and the date it becomes available. The money looks gone |
| Nothing scheduled | no_payout | "$ available", showing the current available figure only | "No upcoming payouts" | Any reason why no payout is scheduled |
| Morning after the catering refund | negative_after_refund | "-$1,874.55" in grey, with no label or explanation | Payout row reads "Canceled" | Why the balance is negative, why the payout was canceled, and when payouts start again |