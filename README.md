# Hawkeye: AI-Powered Fraud Detection System

**Fraud has a pattern. Hawkeye sees it first.**

- Name: B Dhanesh guptha
- College / USN: NXT - S003 / 2102508542
- Live demo: https://github.com/dhaneshguptha15253-tech/HAWKEYE.git
- Colab notebook: https://colab.research.google.com/drive/1YIEfw7dBlmfe4YwVMtNnON8a0Ab5Sp8X?usp=sharing

---

## 1. Problem Statement
Digital payments (UPI, cards, net banking) are growing fast, and so is financial fraud. Banks cannot check millions of transactions by hand, so they need an automatic system that flags suspicious transactions and decides what to do about them.

## 2. Solution
Hawkeye is a fraud detection system that:
1. Learns what a normal transaction looks like from past data.
2. Gives every transaction a risk score.
3. Flags unusual transactions and explains why.
4. Decides an action: approve, verify with OTP, or block.

It is built in two forms: a Python version (Google Colab, text menu) and a website (HTML, CSS and JavaScript). Both use the same logic and no external libraries.

## 3. How AI Is Used
- **AI tools for development:** AI tools (Claude) were used to design the logic, write and debug the code, and design the interface.
- **Learning from data:** the program calculates the average and the standard deviation (spread) of past transaction amounts. This is how it learns what "normal" looks like (statistical anomaly detection).
- **Risk scoring:** each transaction is compared with normal behaviour using a z-score (how many standard deviations the amount is above average), plus four other warning signs.
- **Explainability:** every flagged transaction shows the reasons behind the decision.

## 4. Features Used to Detect Fraud

| Feature | Rule | Points | Why it matters |
|---|---|---|---|
| Amount | z-score above 3 (or above 2) | 40 (or 20) | Fraudsters cash out big |
| Hour of day | Before 5 AM | 20 | Owners are usually asleep |
| Distance from home | Over 200 km | 20 | Card used far from the owner |
| Transactions in last hour | 4 or more | 20 | Rapid repeated spending |
| Overseas transaction | Yes | 20 | Higher risk for stolen cards |

**Action tiers (website):**

| Score | Action |
|---|---|
| Below 30 | Approved instantly |
| 30 to 49 | Verify first (OTP required) |
| 50 and above | Blocked and held for review |

On the dashboard, a transaction scoring 50 or more is counted as flagged.

## 5. Functionality
- Generates sample data: 200 normal and 6 fraud transactions.
- Learns normal spending behaviour automatically.
- Dashboard with summary: transactions scanned, flagged, frauds caught, false alarms, amount at risk.
- Table of suspicious transactions with reasons.
- "Analyze my transaction" panel: enter any transaction and get a verdict and an action.
- Simulated OTP verification for medium-risk transactions.

## 6. How to Run
**Website:** open the live demo link above, or download `index.html` and open it in any browser.

**Python version:** open the notebook in Google Colab, run all cells in order, then use the menu (1: summary, 2: flagged list, 3: check a new transaction, 4: exit).

## 7. Testing and Results
- Sample data: 200 normal transactions (small amounts, daytime, close to home) and 6 fraud transactions (huge amounts, night time, far away, many swipes).
- Each transaction carries a hidden label, used only to check the answers.
- Result: all 6 fraud transactions were caught with 0 false alarms.
- Example tests: 45000 rupees at 3 AM, 1200 km away, 5 swipes in an hour, overseas gives SUSPICIOUS. 800 rupees at 2 PM, 5 km away, 0 swipes, domestic gives normal.

## 8. Benefits and Practical Applications
- Faster fraud detection and lower financial loss.
- Less manual review, so analysts focus on the highest-risk cases.
- Useful for banks, UPI and payment apps, e-commerce, and insurance claims.

## 9. Limitations
- The data is synthetic. The fraud was designed to look clearly different, so 100 percent accuracy here does not mean the same result on real data.
- Only the average and spread of amounts are learned. The other rules and all point values are set by hand.
- There is no separate test set.
- The OTP is simulated (the code is shown on screen). A real system would send it by SMS through a provider.

## 10. Future Work
- Test on real datasets (for example the public credit-card fraud dataset).
- Use a machine-learning model such as Isolation Forest.
- Learn per-customer behaviour instead of one global average.
- Send real OTPs and real-time alerts.

## 11. Technology
Python 3 (built-in `random` module only), HTML, CSS, JavaScript, Google Colab, GitHub Pages.

## 12. Files in This Repository
- `index.html`: the Hawkeye website
- `README.md`: this file
- Colab notebook and `.py` file: the Python version
- Screenshots of the output
