# IDX Aggregator

## What it is, and how to run it
IDX Aggregator is a personal dashboard designed to consolidate Indonesian stock market portfolios across multiple brokerages (sekuritas) into a single, unified view. 

**To run it locally:**
1. Clone the repository and run `npm install`.
2. Set up your environment variables (`NEXT_PUBLIC_SUPABASE_URL` and `NEXT_PUBLIC_SUPABASE_ANON_KEY`).
3. Run `npm run dev`.

## Who it's for, and the one job it has to do well
It is built primarily for myself (and retail investors like me) who actively trade or invest using multiple brokers. Its one job that it must do well is calculating and visualizing the **aggregated daily Unrealized & Realized PnL** across all accounts accurately, using live market data.

## Why this problem, and how you know it's worth solving
As an active investor, tracking overall exposure and risk is difficult when assets are scattered. Managing risk properly requires a holistic view of the portfolio. I knew this was worth solving because I personally experienced the pain of manually compiling spreadsheets every day just to know my exact net worth and daily performance.

## What's already out there for it, and why you built this anyway
Most brokerages (sekuritas) provide their own internal reporting, but they operate in silos. You cannot connect Ajaib, Stockbit, and Ciptadana into one native broker app. Furthermore, the internal reporting in some brokers I use lacks granular details (like historical daily PnL charts). I built this to bridge that gap and own my data.

## What you put in scope, what you left out, and why
**In Scope:** 
- A ledger-based transaction system (BUY/SELL).
- Live stock price fetching using Yahoo Finance API (`yahoo-finance2`).
- Daily automated snapshots using Vercel Cron jobs.
- Visual charts for daily performance.

**Left Out:** 
- Corporate actions (Dividends, Stock Splits, Rights Issues).
- Multi-user authentication.
*Why?* Given the 48-hour timeframe, I focused strictly on the core loop of tracking asset value. Corporate actions introduce massive ledger complexity that isn't necessary for a rough MVP.

## Where you didn't have answers, what you assumed
I didn't have a direct API to pull transaction data seamlessly from Indonesian brokers (as they don't provide public OpenAPI access). 
*Assumption:* I assumed the user (myself) is willing to manually log transactions or upload periodic CSVs/summaries to keep the ledger updated.

## Three questions you'd ask a real user before building more
1. *Data Entry:* Would you prefer manually logging every trade as they happen, or uploading your monthly trade confirmation PDFs for automated parsing?
2. *Metrics:* Besides Unrealized/Realized PnL, what is the #1 metric you look at to evaluate your portfolio's health (e.g., dividend yield, alpha against IHSG)?
3. *Brokers:* Which brokers do you use the most, and how often do you check your portfolio per day?

## How you'd know it's working, and what you'd do next
I'll know it's working when I completely stop opening my Excel spreadsheets and rely 100% on this dashboard for my daily end-of-day portfolio review. 

**What's next:** 
1. Build a parser to automatically extract transactions from Broker Trade Confirmation PDFs.
2. Add Dividend tracking.
3. Introduce benchmark comparisons (e.g., comparing portfolio growth vs. IHSG).
