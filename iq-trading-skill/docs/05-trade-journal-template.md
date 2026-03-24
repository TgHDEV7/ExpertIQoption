# Trade Journal Template

## Purpose
Track every trade to build statistical data for probability calibration.
Growth Hacker rule: What gets measured gets improved.

## Trade Record Format (JSON)

```json
{
  "id": "TRADE_001",
  "timestamp": "2026-03-24T14:35:00+07:00",
  "pair": "EURUSD",
  "timeframe": "M5",
  "direction": "CALL",
  
  "analysis": {
    "regime": "EXPANSION",
    "session": "London",
    "sr_zone": {
      "level": 1.0850,
      "type": "support",
      "score": 8,
      "test_count": 2,
      "tf_origin": "H4"
    },
    "approach_type": "exhausted",
    "rejection_type": "pin_bar",
    "wick_ratio": 2.8,
    "liquidity_grab": true,
    "ob_present": true,
    "fvg_present": false,
    "htf_trend_aligned": true,
    "bos_choch": "BOS_continuation"
  },
  
  "confluence": {
    "count": 5,
    "factors": [
      "high_quality_sr_zone",
      "exhausted_approach",
      "pin_bar_rejection",
      "liquidity_grab_completed",
      "htf_trend_aligned"
    ]
  },
  
  "ohlc_context": {
    "entry_candle": {"o": 1.08520, "h": 1.08545, "l": 1.08490, "c": 1.08535},
    "atr_5": 0.00082,
    "atr_20": 0.00095,
    "atr_ratio": 0.86,
    "body_trend_slope": -1.8,
    "shadow_trend_slope": 1.2
  },
  
  "result": "WIN",
  "payout_percent": 85,
  "notes": "Clean setup. Exhausted approach + liquidity sweep below equal lows + pin bar rejection. High confidence."
}
```

## Weekly Analysis Template

```
Week: [date range]
Total trades: [N]
Win/Loss: [W] / [L]
Win rate: [W/N × 100]%

By Regime:
  COMPRESSION: [trades] | [win rate]%
  EXPANSION:   [trades] | [win rate]%
  EXHAUSTION:  [trades] | [win rate]%
  CHOPPY:      [trades] | [win rate]% (should be 0 trades)

By Session:
  Asian:      [trades] | [win rate]%
  London:     [trades] | [win rate]%
  NY:         [trades] | [win rate]%
  Overlap:    [trades] | [win rate]%

By Pattern:
  Liq Sweep Rejection: [trades] | [win rate]%
  Engulfing at S/R:    [trades] | [win rate]%
  Pin Bar at S/R:      [trades] | [win rate]%
  Other:               [trades] | [win rate]%

By Confluence Count:
  2 factors: [trades] | [win rate]%
  3 factors: [trades] | [win rate]%
  4 factors: [trades] | [win rate]%
  5+ factors: [trades] | [win rate]%

ACTIONS:
  Scale: [setups with win rate > 60%]
  Kill:  [setups with win rate < 55% after 20+ trades]
  Adjust: [probability estimates to update]
```
