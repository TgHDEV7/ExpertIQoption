# Regime Detection + Quantitative OHLC — Reference Guide

## Regime Detection Algorithm

### Input Requirements
- Minimum 20 candles of OHLC data (TF 5 minutes)
- Each candle: open, high, low, close, timestamp

### Step-by-Step Classification

```
STEP 1: Calculate Base Metrics
─────────────────────────────
ATR_5  = mean of TrueRange for last 5 candles
ATR_20 = mean of TrueRange for last 20 candles
  where TrueRange = max(high-low, |high-prev_close|, |low-prev_close|)

range_5  = max(high of last 5) - min(low of last 5)
range_20 = max(high of last 20) - min(low of last 20)

avg_body_5  = mean of |close-open| for last 5 candles
avg_body_20 = mean of |close-open| for last 20 candles

avg_range_5 = mean of (high-low) for last 5 candles

body_range_ratio = avg_body_5 / avg_range_5

bullish_count = count of (close > open) in last 5
bearish_count = count of (close < open) in last 5
dir_count = max(bullish_count, bearish_count)

STEP 2: Classify Regime
───────────────────────
ATR_ratio = ATR_5 / ATR_20
range_ratio = range_5 / range_20

IF ATR_ratio < 0.6 AND range_ratio < 0.4:
  regime = COMPRESSION
  confidence = "HIGH" if ATR_ratio < 0.4 else "MEDIUM"
  action = "Wait for breakout. Do NOT trade reversal."
  sr_behavior = "S/R zones being respected tightly. Breakout will be explosive."

ELIF ATR_ratio > 1.3 AND dir_count >= 4:
  regime = EXPANSION
  confidence = "HIGH" if ATR_ratio > 1.5 AND dir_count == 5 else "MEDIUM"
  action = "Trade WITH trend only. S/R against trend will break."
  sr_behavior = "Only HTF S/R zones in trend direction will hold."

ELIF body_range_ratio < 0.3 AND dir_count <= 2:
  regime = CHOPPY
  confidence = "HIGH" if body_range_ratio < 0.2 else "MEDIUM"
  action = "DO NOT TRADE. No edge. Wait for regime change."
  sr_behavior = "S/R unreliable. Random bounces and breaks."

ELIF avg_body_5 > avg_body_20 * 1.8:
  regime = EXHAUSTION
  confidence = "needs_context"  # must verify prior trend exists
  action = "Watch for reversal at major S/R zone."
  sr_behavior = "S/R may finally hold after extended trend."

ELSE:
  regime = TRANSITIONAL
  action = "Reduce position size. Be extra selective."
  sr_behavior = "Uncertain. Need more candles to classify."
```

## Quantitative OHLC Analysis

### Per-Candle Metrics
```
For each candle i:
  body[i]          = |close[i] - open[i]|
  upper_shadow[i]  = high[i] - max(open[i], close[i])
  lower_shadow[i]  = min(open[i], close[i]) - low[i]
  total_range[i]   = high[i] - low[i]
  
  body_ratio[i]    = body[i] / total_range[i]
    → 0.0 = perfect doji
    → 0.3 = small body, long shadows
    → 0.7 = dominant body
    → 1.0 = no shadows (marubozu)
  
  wick_ratio[i]    = max(upper_shadow[i], lower_shadow[i]) / body[i]
    → < 0.5 = conviction (body dominates)
    → 1.0-2.0 = moderate rejection
    → > 2.0 = strong rejection (pin bar territory)
  
  relative_size[i] = total_range[i] / ATR_20
    → < 0.5 = small candle (low energy)
    → 0.8-1.2 = normal candle
    → > 1.5 = large candle (high energy)
    → > 2.0 = very large (potential exhaustion or breakout)
  
  is_bullish[i]    = close[i] > open[i]
```

### Sequence Metrics (5-8 candle window)
```
body_trend:
  Calculate linear regression of body[i] values over window
  slope > 0 → bodies growing → momentum building
  slope < 0 → bodies shrinking → exhaustion
  |slope| > 2.0 → strong trend in body sizes

shadow_trend:
  Calculate linear regression of max(upper_shadow, lower_shadow) values
  slope > 0 → shadows growing → increasing rejection/fighting
  slope < 0 → shadows shrinking → increasing conviction

color_consistency:
  = max(bullish_count, bearish_count) / window_size
  > 0.8 → strong directional trend
  0.6-0.8 → moderate trend
  0.4-0.6 → no direction (choppy)

range_contraction:
  = range of last 3 candles / range of first 3 candles in window
  < 0.5 → contracting (compression forming)
  0.8-1.2 → stable
  > 1.5 → expanding (breakout or trend acceleration)
```

### Exhaustion Detection Formula
```
exhaustion_score = 0

IF body_trend < -1.5:        exhaustion_score += 2  # bodies shrinking fast
IF shadow_trend > 1.0:       exhaustion_score += 2  # shadows growing
IF color_consistency < 0.6:  exhaustion_score += 1  # colors starting to alternate
IF relative_size[-1] > 2.0:  exhaustion_score += 2  # last candle abnormally large
IF at_sr_zone:               exhaustion_score += 2  # at key level

Interpretation:
  0-3: Not exhausted, trend may continue
  4-6: Early exhaustion signs, monitor closely
  7-9: Strong exhaustion, prepare for reversal
```

### Compression Detection Formula
```
compression_score = 0

IF ATR_ratio < 0.6:          compression_score += 2
IF range_ratio < 0.4:        compression_score += 2
IF range_contraction < 0.5:  compression_score += 2
IF body_ratio avg < 0.3:     compression_score += 1
IF volume declining:         compression_score += 1  # if volume data available

Interpretation:
  0-3: Normal market
  4-6: Moderate compression, breakout possible
  7-8: Strong compression, breakout imminent
```
