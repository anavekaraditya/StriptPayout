# Test-Mode Cases: Maria's Bakery

Account `acct_test_maria_bakery`, Stripe **test mode** only. Sources: *Current Dashboard Home - the 11 Panels Owners See Today.md* and *Maria's Bakery Balance Transactions, Sep-Nov 2026 (Stripe test mode).csv* (420 rows, 2026-09-01 to 2026-11-16: 246 charges, 78 fees, 68 payouts, 24 refunds, 4 payout cancels).

**Headline finding:** the CSV does not contain either case. None of $4,200.00, $312.40 or -$1,874.55 appears in any amount, net or running-balance column, there is no catering refund, and the running available balance never goes below $152.46. The cases below are defined from the Home capture. The CSV rows are the closest supporting data, not a match. No data was invented to close the gap.

## Case A: the $4,200.00 payout (`payout_scheduled`, variant `pending_only`)

**From the Home capture**
- Balance panel: "$312.40 available". Payouts page: "$4,200.00 · In transit", with the arrival date only inside the row.
- Variant `pending_only`: "$0.00 available" and "No upcoming payouts" while money is pending.

**Closest CSV rows (all `paid`, none in transit)**

| txn | created | type | amount | payout_id | payout_status | arrival | running available | running pending |
|---|---|---|---|---|---|---|---|---|
| txn_85 | 2026-09-16 | payout | -4,194.01 | po_00txn_85 | paid | 2026-10-02 | 5,736.91 | 4,438.73 |
| txn_47 | 2026-09-10 | payout | -4,193.77 | po_00txn_47 | paid | 2026-09-05 | 6,353.04 | 1,288.15 |
| txn_229 | 2026-11-06 | payout | -4,174.59 | po_00txn_229 | paid | 2026-09-21 | 5,790.74 | 4,385.10 |

**Mismatches**
- No payout of exactly $4,200.00, and no payout with an in-transit status.
- No row where running available is $312.40.
- Several payouts have an arrival date before their created date (txn_47, txn_229).

## Case B: the catering refund below zero (`negative_after_refund`)

**From the Home capture**
- Balance panel: "-$1,874.55" in grey with no label. Payouts page: payout row "Canceled".

**Closest CSV rows**

| txn | created | type | amount | note |
|---|---|---|---|---|
| txn_191 | 2026-10-06 | refund | -179.32 | Largest refund: "item sold out" |
| txn_253 | 2026-09-05 | refund | -179.17 | "item sold out" |
| txn_402 | 2026-09-26 | refund | -175.34 | "duplicate charge" |
| txn_365 | 2026-11-16 | payout | -4,080.64 | Last payout (paid) |

| txn | created | type | amount | payout_status | arrival |
|---|---|---|---|---|---|
| (payout_cancel) | 2026-10-16 | payout_cancel | 868.41 | canceled | 2026-11-06 |
| (payout_cancel) | 2026-10-14 | payout_cancel | 566.96 | canceled | 2026-09-06 |
| (payout_cancel) | 2026-09-22 | payout_cancel | 422.88 | canceled | 2026-11-13 |
| (payout_cancel) | 2026-10-17 | payout_cancel | 802.65 | canceled | 2026-09-14 |

**Mismatches**
- No catering refund. "Catering order - office breakfast" appears only on charges.
- The largest refund is $179.32, nowhere near $1,874.55.
- The balance never goes negative in the CSV. Minimum running available is $152.46.
- The 4 canceled payouts are $422.88 to $868.41 and are not tied to a refund.
- The cancel rows' payout_failure_reason is empty, so the CSV gives no reason.

## Data quality notes
- `net` does not equal `amount` minus `fee` on many rows (for example txn_1: amount 102.18, fee 9.90, net 128.91).
- Running balances move inconsistently between rows, so they can't be treated as a true ledger.
- Treat the CSV as seed-style test data. To reproduce the two cases exactly, the missing rows would have to be added to the test data, which needs the author's go-ahead.
