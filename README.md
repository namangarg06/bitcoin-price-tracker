# Bitcoin Price Hourly Logger

Har ghante Bitcoin ka price (USD + INR) automatically fetch karke
`bitcoin_price_log.xlsx` me store karta hai — GitHub Actions ke through,
bilkul free, aur aapka PC on hone ki zaroorat nahi.

## Setup (5 minute, one-time)

1. **GitHub pe naya repository banao**
   - github.com/namangarg06 pe jao → New Repository → naam do (e.g. `bitcoin-price-tracker`)
   - Public rakho (free GitHub Actions minutes ke liye)

2. **Ye teeno files upload karo** (same folder structure rakhna zaroori hai):
   ```
   fetch_btc_price.py
   .github/workflows/btc_price.yml
   ```
   Upload karte time "Add file" → "Upload files" use karo, ya git se push karo.

3. **Bas ho gaya!**
   - Workflow automatically har ghante (UTC time pe) chalega
   - Pehli baar turant test karne ke liye: GitHub repo → "Actions" tab → "Hourly Bitcoin Price Logger" → "Run workflow" button dabao
   - Kuch minute baad repo me `bitcoin_price_log.xlsx` file aa jayegi, aur har ghante update hoti rahegi

4. **Excel file download karna ho to:**
   - Repo me `bitcoin_price_log.xlsx` pe click karo → "Download raw file"
   - Ya repo ko apne PC pe clone/pull kar lo

## Notes

- Cron schedule UTC time follow karta hai. `0 * * * *` matlab har ghante ke start me (e.g., 12:00, 1:00, 2:00 UTC = 5:30 PM, 6:30 PM, 7:30 PM IST).
- Agar IST me exact hour chahiye (e.g. sharp 9 AM IST), to `.github/workflows/btc_price.yml` me cron time ko IST - 5:30 karke adjust kar sakte ho.
- Free GitHub account me public repo ke liye Actions minutes practically unlimited hain is tarah ke chhote task ke liye.
- Price data CoinGecko ke free public API se aata hai — koi API key ya cost nahi lagti.
