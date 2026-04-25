## 10. Example User Reconciliation Table

| Symbol | Broker Pos | Local Pos | Discovered Manual | Status                          |
|--------|------------|-----------|-------------------|----------------------------------|
| AAPL   | 3          | 2         | 1                 | Imbalance                        |
| MSFT   | 0          | 0         | 0                 | Reconciled                       |
| TSLA   | 4          | 1         | 3                 | Broker Extra Positions           |
| AMZN   | 2          | 2         | 0                 | Fully Matched                    |
| GOOGL  | 0          | 2         | 0                 | Local Book Overstated            |
| NFLX   | 5          | 4         | 1                 | Partial Match/Unaligned          |
| NIO    | 1          | 0         | 1                 | Discovered at Broker             |
| BABA   | 3          | 3         | 0                 | Reconciled                       |
| META   | 0          | 1         | 0                 | Local Position Missing at Broker  |
| NVDA   | 6          | 5         | 1                 | One Trade Not Synced             |
| XOM    | 0          | 5         | 0                 | All Local Only, Missing @ Broker |
| ZM     | 8          | 7         | 1                 | Broker Shows More Than Local     |
| SONY   | 2          | 0         | 2                 | Manual Trades at Broker Only     |

**Status Column Explanations**
- Imbalance: Broker has more than local, source must be found or adopted.
- Reconciled: Both positions agree.
- Broker Extra Positions: Broker shows more positions than local trade book.
- Fully Matched: Perfect agreement.
- Local Book Overstated: Local thinks there are positions, but broker shows none for that symbol; requires investigation/removal from local.
- Partial Match/Unaligned: Most positions matched, but one or more positions only at broker or local.
- Discovered at Broker: Position found at broker, not locally; may require manual adoption.
- Local Position Missing at Broker: Local trade book shows a position, broker does not; system must reconcile local to broker.
- One Trade Not Synced: Likely a trade confirmation missed; needs resolution.
- All Local Only, Missing @ Broker: All positions exist only locally; likely all were not confirmed at broker and need removal or archival.
- Broker Shows More Than Local: Possible missed logging of a trade locally; needs reconciliation and investigation.
- Manual Trades at Broker Only: All positions present at broker, likely due to manual trades outside the system.
