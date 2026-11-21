# Prompt Note

Date: 2026-11-21

The prompt below was given to Claude Code to produce the payout state list, the test-mode cases, and this note. It is quoted verbatim.

---

I'm working in the stripe-home-payout repo (local folder: /Users/adityaanavekar/Projects/StriptPayout).

## 1. Source files and the two cases to recreate
Work from these two files:
- "Current Dashboard Home - the 11 Panels Owners See Today.md" (the current Home page)
- "Maria's Bakery Balance Transactions, Sep-Nov 2026 (Stripe test mode).csv" (balance transactions for acct_test_maria_bakery)

Recreate two Maria cases as test-mode cases:
- Case A: her $4,200.00 payout that is pending / on its way (state `payout_scheduled`, and the pending-money variant `pending_only`).
- Case B: the catering refund that takes her balance below zero, to -$1,874.55 (state `negative_after_refund`), with her payout canceled.
Use rows from the CSV where they support each case. Where the CSV figures don't match the Home capture, say so explicitly in the file and don't invent data to hide the gap. Test-mode only: never use live keys, and never read or print my .env.

## 2. Home text: use MY wording, not yours
Use the messages below exactly as written for the Home text of each state id. Do not rewrite, shorten, or "improve" them. If a bracketed value is missing, leave it as a bracket and tell me.

- `payout_scheduled`: "$4,200.00 is on its way to your bank. It should arrive on [date]. You also have $312.40 available now."
- `pending_only`: "Your money isn't gone, it's on hold. [$ amount] from recent sales becomes available on [date]. Nothing is scheduled to pay out until then."
- `no_payout`: "No payout is scheduled right now. You have $[available] available. A payout will be scheduled once [reason]."
- `negative_after_refund`: "Your balance is -$1,874.55 because of the catering refund. Your payout was canceled. New sales will cover this first, and payouts restart once your balance is back above $0."

## 3. What to create and push to stripe-home-payout
Create or update these files, then commit and push to `main` on stripe-home-payout:
1. `Payout State List - Maria's Bakery.md`: all four state ids, each with the condition, what Home shows today, what's missing, and my Home text from section 2.
2. `Test-Mode Cases - Maria's Bakery.md`: the two cases from section 1, with the supporting CSV rows and any mismatches.
3. `Prompt Note.md`: a short note that quotes this prompt (sections 1 to 3) verbatim, with the date.

Don't commit `.env` or anything with keys. Show me `git status` before committing, and tell me the commit and the repo URL when done.
