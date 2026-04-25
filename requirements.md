## 10. Example User Reconciliation Table

| Symbol | Broker Pos | Local Pos | Discovered Manual | Status                          | System Solution / Behavior                                                                                                              |
|--------|------------|-----------|-------------------|----------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| AAPL   | 3          | 2         | 1                 | Imbalance                        | Suggest adoption of discovered trade; system updates local book to match broker upon user approval.                                     |
| MSFT   | 0          | 0         | 0                 | Reconciled                       | No action needed.                                                                                                                      |
| TSLA   | 4          | 1         | 3                 | Broker Extra Positions           | System auto-adopts extra broker trades or alerts user to annotate/adopt as manual, updates local book to reconcile.                    |
| AMZN   | 2          | 2         | 0                 | Fully Matched                    | No action needed.                                                                                                                      |
| GOOGL  | 0          | 2         | 0                 | Local Book Overstated            | System auto-identifies 2 unmatched local trades, removes/archives them, syncs Local Pos to 0, logs action for audit; broker is truth.  |
| NFLX   | 5          | 4         | 1                 | Partial Match/Unaligned          | System prompts review of unmatched broker trades or fills, auto-adopts or archives per policy.                                          |
| NIO    | 1          | 0         | 1                 | Discovered at Broker             | System auto-adopts broker trade to local book or flags for review.                                                                     |
| BABA   | 3          | 3         | 0                 | Reconciled                       | No action needed.                                                                                                                      |
| META   | 0          | 1         | 0                 | Local Position Missing at Broker  | System detects 1 unmatched local trade, removes/archives it, syncs Local Pos to 0, all changes logged.                                 |
| NVDA   | 6          | 5         | 1                 | One Trade Not Synced             | System attempts auto-adopt and logs/alerts if unresolved; user review may be required.                                                 |
| XOM    | 0          | 5         | 0                 | All Local Only, Missing @ Broker | System auto-removes/archives all 5 unmatched local trades, sets Local Pos=0, logs all changes.                                         |
| ZM     | 8          | 7         | 1                 | Broker Shows More Than Local     | System attempts to auto-adopt broker extra or prompts user for manual adoption; local updated to 8.                                    |
| SONY   | 2          | 0         | 2                 | Manual Trades at Broker Only     | System detects 2 broker-only trades, auto-adopts or alerts user for annotation; local is updated.                                      |
| XYZ    | 5          | 7         | 0                 | Local Greater Than Broker        | System auto-removes/archives 2 unmatched local trades, reduces Local Pos to 5, logs for audit; broker is always the source of truth.   |

**Status Column Explanations**
- Imbalance: Broker has more than local, source must be found or adopted.
- Reconciled: Both positions agree.
- Broker Extra Positions: Broker shows more positions than local trade book.
- Fully Matched: Perfect agreement.
- Local Book Overstated: Local thinks there are positions, but broker shows none for that symbol; system automatically removes/archives extra from local.
- Partial Match/Unaligned: Most positions matched, but one or more positions only at broker or local. System auto-adopts or archives accordingly.
- Discovered at Broker: Position found at broker, not locally; system adopts to local book or flags for manual review.
- Local Position Missing at Broker: System finds position only in local, removes/archives as needed to match broker.
- One Trade Not Synced: System tries auto-adopt; alerts if unresolved.
- All Local Only, Missing @ Broker: System removes/archives all unmatched local positions to match broker.
- Broker Shows More Than Local: System adopts or prompts user to sync local with broker.
- Manual Trades at Broker Only: System adopts broker-only trades to local book.
- Local Greater Than Broker: System removes/archives unmatched local trades until positions match broker; all actions are audited.
