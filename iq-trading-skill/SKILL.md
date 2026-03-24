---
name: iq-option-trading
description: "IQ Option Binary Options TF 5-minute candle-close trading mastery skill. Use this skill EVERY TIME the user asks about trading analysis, chart reading, signal generation, OHLC analysis, candlestick patterns, support/resistance, or anything related to IQ Option / binary options / forex price action on 5-minute timeframe. This skill contains the complete 0.01% mastery framework built around S/R as the core, with Regime Detection, Candle Sequence Narrative, Liquidity Hunt, SMC Concepts, and Probability Calibration. Claude must read this skill before any trading-related response."
---

# IQ Option Binary Options — TF 5 Minute Candle-Close Trading Skill
## Target: Top 0.01% Mastery
## Core: Support & Resistance

---

## CRITICAL RULES (Read First)

1. **S/R is the foundation of EVERYTHING** — no trade without a valid S/R zone
2. **Never use lagging indicators (RSI/MACD/Bollinger) as primary decision makers** — they show the past, not the future
3. **Never memorize patterns in isolation** — always read context (regime + sequence + zone)
4. **Binary Options payout ~80-90% win / 100% loss** — need >55.6% win rate minimum for positive EV
5. **Growth Hacker mindset always applies** — data-driven decisions, Build-Measure-Learn loop, kill what doesn't work immediately
6. **When in doubt, DON'T TRADE** — the best trade is often no trade

---

## MODULE 1: S/R MASTERY FRAMEWORK (5 Levels)

### Level 1: Basic S/R (What 90% Do — Skip This)
- Drawing horizontal lines at obvious highs/lows
- Waiting for price to reach the line
- Entering immediately
- **WHY THIS FAILS:** Everyone sees the same lines → smart money exploits this

### Level 2: Zone Grading System

Not all S/R zones are equal. Score every zone before considering a trade.

**Zone Scoring Criteria (0-10 scale):**

| Criteria | High Score (8-10) | Medium Score (5-7) | Low Score (1-4) |
|----------|-------------------|--------------------|-----------------| 
| Test Count | 1-2 tests (fresh) | 3 tests | 4+ tests (weakened) |
| TF Origin | From H1/H4/D1 | From M15/M30 | From M5 only |
| Confluence | OB + FVG + round number | OB or FVG present | Price level only |
| Reaction History | Sharp V-reversals | Moderate reactions | Weak/slow reactions |
| Distance | Price far from zone (>2 ATR) | Medium distance | Very close/already touched |
| Liquidity | Equal highs/lows behind zone | Some stops likely there | No visible liquidity |

**Grading:**
- Score 7-10: HIGH quality zone → trade with confidence
- Score 4-6: MEDIUM quality → trade only with 3+ confluence
- Score 0-3: LOW quality → DO NOT TRADE

**Zone Width Rules:**
- S/R is a ZONE (5-15 pips wide for EURUSD), not a single line
- Zone = area between the closest wick tips at the level
- Price doesn't have to touch exact level — entering the zone counts

### Level 3A: Approach Reading

**How price arrives at the S/R zone determines the probability of bounce vs break.**

**Exhausted Approach (HIGH probability of bounce):**
- Candle bodies getting SMALLER as price nears zone
- Shadows getting LONGER (buyers/sellers fighting back)
- 3+ candles to travel distance that took 1 candle earlier
- Quantitative: body_avg_last3 < 0.5 × body_avg_prev3

**Strong Approach (HIGH probability of break):**
- Candle bodies getting LARGER
- Shadows SHORT or non-existent
- 1-2 large candles covering distance quickly
- Quantitative: body_avg_last3 > 1.5 × body_avg_prev3

**Choppy Approach (NO TRADE):**
- Bodies alternating direction
- No clear momentum either way
- Quantitative: directional_consistency < 3/5 candles same direction

### Level 3B: Reaction Confirmation

**NEVER enter just because price reached a zone. Wait for rejection.**

**Strong Rejection Signals (enter after these):**
1. **Pin Bar at zone:** shadow ≥ 2× body, shadow touches zone, body closes AWAY from zone
2. **Engulfing at zone:** candle 2 body completely covers candle 1 body, direction reverses
3. **Rejection after liquidity sweep:** price pierces zone briefly (wick), then closes back inside range

**Weak/No Rejection (DO NOT enter):**
1. Small-body candle sitting ON the zone (indecision, not rejection)
2. Price reaches zone with large body candle and closes beyond it (breakout, not bounce)
3. Multiple candles sitting at zone without clear rejection direction

**Quantitative Rejection Score:**
- wick_ratio = rejection_shadow / body → needs ≥ 2.0
- close_distance = |close - zone_level| / ATR → needs ≥ 0.3 (closed away from zone)
- body_direction = must be AWAY from zone

### Level 4A: Liquidity Reading at S/R

**What separates good traders from 0.01% traders.**

**Key Concept:** Smart money needs liquidity to fill large orders. They push price INTO clusters of stop losses (at obvious S/R) to get filled, then reverse.

**Identifying Liquidity Pools:**
- Equal highs (2+ highs at same level) → buy stops stacked above
- Equal lows (2+ lows at same level) → sell stops stacked below
- Round numbers (1.0800, 1.0850) → both sides have orders
- Previous session high/low → heavy stop concentration

**The Liquidity Grab Sequence:**
1. Price approaches S/R zone with liquidity behind it
2. Price PIERCES the zone briefly (grabs liquidity / triggers stops)
3. Rejection candle forms (long wick through zone, body closes back)
4. **THIS is the entry** — after the grab, not before

**Fake Breakout vs Real Breakout Detection:**

| Feature | Fake Breakout (Enter Reversal) | Real Breakout (Don't Fade) |
|---------|-------------------------------|---------------------------|
| Candle | Long wick, small body | Large body closing beyond zone |
| Penetration | < 0.3 ATR beyond zone | > 0.5 ATR beyond zone |
| Follow-through | Next candle reverses immediately | Next candle continues |
| Context | After exhausted approach | After compression breakout |
| Volume/momentum | Spike then fade | Sustained increase |

### Level 4B: Regime Detection

**The same S/R zone behaves differently depending on market regime.**

**4 Regimes (must identify before any trade):**

**COMPRESSION (prepare for breakout)**
- Range_Ratio = (High₅ - Low₅) / (High₂₀ - Low₂₀) < 0.4
- Bodies getting smaller, range narrowing
- ATR₅ / ATR₂₀ < 0.6
- Strategy: Wait for breakout. If breakout FROM S/R zone → trade continuation. Don't trade reversal in compression.

**EXPANSION (trade with trend)**
- Bodies getting larger
- ATR₅ / ATR₂₀ > 1.3
- Clear directional movement
- Strategy: Only trade S/R bounces that align with trend direction. S/R against trend will break.

**CHOPPY (NO TRADE)**
- Bodies alternating direction frequently
- Directional_consistency ≤ 2/5 candles
- Body/Range ratio < 0.3
- Strategy: **DO NOT TRADE.** No edge exists in choppy conditions. Wait.

**EXHAUSTION (prepare for reversal)**
- Largest body candle appears after extended trend
- Shadows start lengthening
- Price at major S/R zone
- Strategy: Watch for reversal at S/R. High probability setup when exhaustion meets strong S/R.

### Level 4C: Session Timing

**When you trade matters as much as what you trade.**

| Session | Time (Thailand) | S/R Behavior | Strategy |
|---------|----------------|--------------|----------|
| Asian | 06:00-14:00 | Creates range, builds liquidity at edges | Mark range H/L, DON'T trade breakouts |
| London Open | 14:00-16:00 | Often sweeps Asian range then reverses | Wait for sweep of Asian H/L → enter reversal |
| London | 16:00-20:00 | Trends develop, S/R from H1/H4 respected | Trade bounces from HTF S/R with trend |
| New York Open | 20:00-22:00 | High volatility, second sweep possible | Trade S/R with caution, wider zone consideration |
| Overlap | 21:00-24:00 | Maximum momentum | Best period for trend-following S/R bounces |
| Pre-News (30min) | Variable | Unpredictable | **DO NOT TRADE** |

### Level 5: Probability Calibration + Kill Switch (0.01% Mastery)

**Every setup gets a probability estimate. Only trade positive EV.**

**Expected Value Formula:**
```
EV = (Win_Probability × Payout_Amount) - (Loss_Probability × Stake)

If Payout = 80%:
EV = (Win% × 0.80) - ((1 - Win%) × 1.00)
Breakeven Win% = 1 / (1 + 0.80) = 55.6%
```

**Confluence-Based Probability Estimates:**

| Confluence Count | Estimated Win Rate | EV at 80% Payout | Decision |
|-----------------|-------------------|-------------------|----------|
| 1 factor | 48-52% | NEGATIVE | ❌ NO TRADE |
| 2 factors | 53-57% | MARGINAL | ⚠️ Only if very clean |
| 3 factors | 58-63% | POSITIVE | ✅ TRADE |
| 4+ factors | 63-70% | STRONG POSITIVE | ✅✅ HIGH CONFIDENCE |

**Confluence Factors (need ≥3 to trade):**
1. ✅ High-quality S/R zone (score ≥ 7)
2. ✅ Exhausted approach OR liquidity grab completed
3. ✅ Clear rejection candle (Pin Bar/Engulfing with wick_ratio ≥ 2)
4. ✅ Regime supports the trade (not Choppy)
5. ✅ Session timing is favorable (Kill Zone)
6. ✅ Higher TF trend alignment
7. ✅ FVG or Order Block confluence at zone

**KILL SWITCH — Immediately stop trading when:**
- Regime = Choppy → no edge
- 3 consecutive losses → probability miscalibration, review
- Within 30 min of red news event
- OTC pairs on weekends (different behavior)
- Confluence score < 3
- Emotional state compromised (revenge trading, FOMO)

---

## MODULE 2: CANDLE PATTERNS THAT WORK (Backtested)

### Patterns Ranked by Effectiveness for Binary Options TF 5

**IMPORTANT:** These patterns ONLY work when combined with S/R context. Standalone patterns have ~50% win rate = no edge.

### Tier 1: High-Probability Patterns (use these)

**1. Rejection Candle After Liquidity Sweep**
- Context: Price pierces S/R zone, wick extends through, body closes back inside range
- Quantitative: wick_penetration / ATR < 0.3, body closes on correct side of zone
- Win rate with S/R + regime context: ~62-68%
- Entry: Next candle open after rejection closes
- Direction: Opposite to the sweep direction

**2. Engulfing at S/R Zone**
- Context: At high-quality S/R zone (score ≥ 7)
- Quantitative: body₂ > body₁ × 1.5, opposite color, at zone
- Win rate with context: ~60-65%
- Enhancement: Volume confirmation (if available) pushes win rate higher
- Entry: Next candle after engulfing closes

**3. Pin Bar at S/R Zone**
- Context: Long shadow touches S/R zone, small body closes away from zone
- Quantitative: rejection_shadow ≥ 2× body, close away from zone
- Win rate with context: ~58-63%
- Entry: Next candle after pin bar closes
- Best when: Combined with exhausted approach

### Tier 2: Moderate Patterns (use with extra confluence)

**4. Inside Bar at S/R → Breakout**
- Context: After exhausted approach to S/R, price compresses
- Entry: When candle breaks inside bar in the bounce direction
- Needs: Regime = not choppy, zone score ≥ 6

**5. Three-Candle Exhaustion Sequence**
- Context: 3 candles with progressively smaller bodies approaching S/R
- Shows: Momentum dying before reaching zone
- Entry: After rejection candle at zone following the sequence
- Quantitative: body₃ < body₂ < body₁ AND shadow₃ > shadow₂

### Tier 3: Patterns to AVOID

**❌ Doji alone** — ~50% win rate, no edge
**❌ Hammer/Shooting Star without S/R context** — random
**❌ Any pattern during Choppy regime** — all patterns fail
**❌ Any pattern against Higher TF trend** — low win rate
**❌ Morning/Evening Star** — too rare on TF 5, insufficient data

---

## MODULE 3: REGIME DETECTION + QUANTITATIVE OHLC

### Regime Classification Algorithm

**Input:** Last 20 candles of OHLC data
**Output:** One of 4 regimes + confidence score

```
Step 1: Calculate metrics
  ATR_5  = Average True Range of last 5 candles
  ATR_20 = Average True Range of last 20 candles
  range_5  = Highest High(5) - Lowest Low(5)
  range_20 = Highest High(20) - Lowest Low(20)
  avg_body_5  = Average |Close - Open| of last 5 candles
  avg_body_20 = Average |Close - Open| of last 20 candles
  body_range_ratio = avg_body_5 / Average(High - Low) of last 5
  dir_count = count of candles in dominant direction out of last 5

Step 2: Classify
  IF ATR_5/ATR_20 < 0.6 AND range_5/range_20 < 0.4:
    → COMPRESSION (confidence: high if both < 0.4)
  
  ELIF ATR_5/ATR_20 > 1.3 AND dir_count >= 4:
    → EXPANSION (confidence: high if > 1.5 AND dir_count = 5)
  
  ELIF body_range_ratio < 0.3 AND dir_count <= 2:
    → CHOPPY (confidence: high if ratio < 0.2)
  
  ELIF avg_body_5 > avg_body_20 × 1.8 AND at major S/R:
    → EXHAUSTION (needs context of prior trend)
  
  ELSE:
    → TRANSITIONAL (treat as cautious, need more data)
```

### Quantitative OHLC Analysis Metrics

**For each candle, calculate:**
```
body = |close - open|
upper_shadow = high - max(open, close)
lower_shadow = min(open, close) - low
total_range = high - low
body_ratio = body / total_range  (0 = doji, 1 = no shadow)
upper_wick_ratio = upper_shadow / total_range
lower_wick_ratio = lower_shadow / total_range
is_bullish = close > open
relative_size = total_range / ATR_20  (>1.5 = large, <0.5 = small)
```

**For sequence analysis (last 5-8 candles):**
```
body_trend = linear regression slope of |body| values
  → positive = bodies growing (momentum building)
  → negative = bodies shrinking (exhaustion)
  
shadow_trend = linear regression slope of max(upper_shadow, lower_shadow)
  → positive = shadows growing (rejection increasing)
  → negative = shadows shrinking (conviction increasing)

color_consistency = max(bullish_count, bearish_count) / total_count
  → > 0.8 = strong trend
  → 0.4-0.6 = no direction (choppy)
```

---

## MODULE 4: LIQUIDITY HUNT / SMC CONCEPTS

### Order Blocks (OB)

**Definition:** The last opposite-color candle before a strong impulsive move.
- Bullish OB = last bearish (red) candle before a strong upward move
- Bearish OB = last bullish (green) candle before a strong downward move

**Valid OB Criteria:**
1. Impulsive move after OB must be ≥ 2× ATR
2. OB must not have been retested yet (first touch = strongest)
3. Must have created a Break of Structure (BOS)

**How to use with S/R:**
- When OB aligns with S/R zone → confluence increases significantly
- OB zone = open to close of the OB candle (use as entry zone)
- Stop hunt that grabs OB wick then reverses = highest probability setup

### Fair Value Gaps (FVG)

**Definition:** A 3-candle pattern where candle 1's high doesn't overlap with candle 3's low (bullish) or candle 1's low doesn't overlap with candle 3's high (bearish).

**Detection:**
```
Bullish FVG: candle_1_high < candle_3_low
  → gap zone = candle_1_high to candle_3_low
  
Bearish FVG: candle_1_low > candle_3_high
  → gap zone = candle_3_high to candle_1_low
```

**How to use:**
- Price often returns to fill FVG before continuing in original direction
- FVG at S/R zone = high confluence for entry
- Entry: When price returns to FVG zone AND shows rejection

### Break of Structure (BOS) / Change of Character (CHoCH)

**BOS:** Price makes a new Higher High (uptrend) or Lower Low (downtrend) → trend continues
**CHoCH:** Price makes the FIRST Lower Low in an uptrend (or first Higher High in downtrend) → potential trend change

**For Binary Options TF 5:**
- CHoCH at major S/R zone = strong reversal signal
- BOS confirming trend + S/R bounce = strong continuation signal
- Use M15 or H1 structure, enter on M5

### Kill Zones and Session-Based Liquidity

**Asian Range Setup (one of the most reliable):**
1. Mark Asian session High and Low (06:00-14:00 Thailand time)
2. During London open (14:00-16:00), wait for price to SWEEP Asian H or L
3. After sweep → look for rejection candle
4. Enter reversal back into the Asian range
5. Target: opposite side of Asian range

**Why this works:** Asian session builds liquidity at both edges. Smart money sweeps one side to get filled, then pushes price the other direction.

---

## MODULE 5: ENTRY DECISION FLOWCHART

```
START
│
├─ Step 1: What REGIME is the market in?
│   ├─ CHOPPY → DO NOT TRADE (stop here)
│   ├─ COMPRESSION → Wait for breakout, don't trade reversal
│   ├─ EXPANSION → Only trade WITH trend at S/R
│   └─ EXHAUSTION → Look for reversal at major S/R
│
├─ Step 2: Is there a HIGH-QUALITY S/R zone nearby?
│   ├─ Zone Score < 4 → DO NOT TRADE (stop here)
│   ├─ Zone Score 4-6 → Proceed but need 4+ confluence
│   └─ Zone Score 7-10 → Proceed with 3+ confluence
│
├─ Step 3: How is price APPROACHING the zone?
│   ├─ Exhausted approach → HIGH probability of bounce
│   ├─ Strong approach → Likely to break, DON'T fade
│   └─ Choppy approach → No clear read → skip
│
├─ Step 4: Is there a REJECTION signal at the zone?
│   ├─ Pin Bar (wick ≥ 2× body) → ✅ proceed
│   ├─ Engulfing → ✅ proceed
│   ├─ Liquidity grab + rejection → ✅✅ best setup
│   └─ No clear rejection → DO NOT TRADE (stop here)
│
├─ Step 5: Count CONFLUENCE factors
│   ├─ < 3 factors → DO NOT TRADE
│   ├─ 3 factors → TRADE (standard size)
│   └─ 4+ factors → TRADE (high confidence)
│
├─ Step 6: Check KILL SWITCH
│   ├─ Any kill switch active → DO NOT TRADE
│   └─ All clear → EXECUTE TRADE
│
└─ Step 7: DIRECTION
    ├─ At Support + rejection UP → CALL
    └─ At Resistance + rejection DOWN → PUT
```

---

## MODULE 6: POST-TRADE ANALYSIS (Build-Measure-Learn)

After every trade, record:
```
{
  "timestamp": "2026-03-24T14:35:00",
  "pair": "EURUSD",
  "direction": "CALL",
  "regime": "EXPANSION",
  "session": "London",
  "sr_zone_score": 8,
  "approach_type": "exhausted",
  "rejection_type": "pin_bar",
  "confluence_count": 4,
  "confluence_details": ["HTF_SR", "OB_at_zone", "pin_bar", "trend_aligned"],
  "result": "WIN",
  "notes": "Clean setup, rejection was very clear"
}
```

**Weekly Review Protocol:**
1. Calculate win rate by: regime, session, pattern type, confluence count
2. SCALE setups with win rate > 60%
3. KILL setups with win rate < 55% after 20+ trades
4. ADJUST probability estimates based on real data
5. Identify any new patterns emerging from the data

---

## QUICK REFERENCE CARD

**Before ANY trading analysis, Claude must verify:**
- [ ] What regime? (Compression/Expansion/Choppy/Exhaustion)
- [ ] Where is nearest high-quality S/R zone?
- [ ] How is price approaching? (Exhausted/Strong/Choppy)
- [ ] Is there rejection at zone? (Pin Bar/Engulfing/Grab)
- [ ] Confluence count ≥ 3?
- [ ] Any kill switch active?
- [ ] Session timing favorable?

**If ALL checks pass → provide signal with confidence level**
**If ANY check fails → recommend NO TRADE with explanation**
