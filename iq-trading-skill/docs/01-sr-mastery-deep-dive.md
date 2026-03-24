# S/R Mastery — Deep Dive

## Zone Grading Detailed Examples

### Example 1: HIGH Quality Zone (Score 8/10)
```
Zone: EURUSD 1.0850 area
- Test count: 2 (fresh) → +2
- TF origin: H4 swing low → +2  
- Confluence: Bullish OB + FVG overlap → +2
- Reaction history: Sharp V-reversal last time → +1
- Liquidity: Equal lows at 1.0848 (stops below) → +1
Total: 8/10 → HIGH quality, trade with confidence
```

### Example 2: LOW Quality Zone (Score 3/10)
```
Zone: EURUSD 1.0900 area
- Test count: 5 (heavily tested) → +0
- TF origin: M5 only → +0
- Confluence: Just a price level → +1
- Reaction history: Weak, slow bounces → +1
- Liquidity: No visible equal highs/lows → +1
Total: 3/10 → LOW quality, DO NOT TRADE
```

## Approach Reading Quantitative Guide

### Measuring Approach Strength via OHLC

Given last 8 candles approaching a Support zone:

```
Candle 8 (oldest): body=12 pips, shadow=3 pips → strong seller
Candle 7: body=10 pips, shadow=4 pips → still strong
Candle 6: body=8 pips, shadow=5 pips → weakening
Candle 5: body=5 pips, shadow=6 pips → exhaustion starting
Candle 4: body=3 pips, shadow=7 pips → clear exhaustion
Candle 3: body=2 pips, shadow=8 pips → almost no momentum
→ EXHAUSTED APPROACH → HIGH probability of bounce at Support
```

### Body Trend Calculation
```python
bodies = [12, 10, 8, 5, 3, 2]  # absolute body sizes
# Linear regression slope = negative → exhaustion
# slope < -1.0 = strong exhaustion
# slope > 1.0 = momentum building
```

## Session-Specific S/R Behavior

### Asian Session Range Strategy (Detailed)

1. Wait until 14:00 Thailand time
2. Mark the HIGH and LOW of price from 06:00-14:00
3. These levels become your S/R zones for London session
4. London open (14:00-16:00) often:
   - Sweeps Asian High → then reverses DOWN
   - Sweeps Asian Low → then reverses UP
5. The sweep creates a liquidity grab → enter reversal after rejection
6. Target: midpoint of Asian range or opposite edge

### Why Each Session Matters

**Asian (06:00-14:00):** Low volatility, price builds a range. DON'T trade breakouts — they're usually fake. USE this session to identify S/R zones and liquidity pools.

**London Open (14:00-16:00):** The "manipulation" phase. Smart money sweeps overnight liquidity. WAIT for the sweep to complete, then trade the reversal.

**London Body (16:00-20:00):** Real trends develop. Trade S/R bounces WITH the trend. This is where most genuine moves happen.

**New York Open (20:00-22:00):** Second wave of volatility. Can create a second sweep or continuation. Be cautious — sometimes NY reverses London's move.

**NY-London Overlap (21:00-24:00):** Maximum liquidity and momentum. Best time for trend-following trades at S/R zones.
