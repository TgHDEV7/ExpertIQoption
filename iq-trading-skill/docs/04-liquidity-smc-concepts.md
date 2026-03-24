# Liquidity Hunt / SMC Concepts — Reference Guide

## Core Principle
Price moves toward liquidity. Smart money needs retail traders' stop losses to fill their large orders. Understanding WHERE liquidity sits and HOW it gets grabbed is the edge that separates 0.01% from the rest.

## Liquidity Pool Identification

### Where Stop Losses Cluster
```
1. Below equal lows (multiple lows at same price)
   → Sell stops accumulate here
   → Smart money drives price DOWN to grab them
   → Then price reverses UP

2. Above equal highs (multiple highs at same price)
   → Buy stops accumulate here
   → Smart money drives price UP to grab them
   → Then price reverses DOWN

3. Below obvious support lines
   → Retail traders place stops "just below support"
   → These are the easiest to hunt

4. Above obvious resistance lines
   → Same logic, retail puts stops "just above resistance"

5. At round numbers (1.0800, 1.0850, 1.0900)
   → Both buy and sell stops cluster at round numbers
   → Maximum liquidity available
```

### Liquidity Quality Assessment
```
HIGH liquidity (worth trading):
- 3+ equal highs/lows at same level
- Previous session high/low
- Round number + S/R confluence
- Level visible on H1/H4 (more traders see it = more stops)

LOW liquidity (skip):
- Single swing high/low
- M5-only level (few traders see it)
- Already swept recently (liquidity already grabbed)
```

## The Liquidity Grab — Complete Sequence

### Bullish Liquidity Grab (at Support)
```
Phase 1 — BUILD: Price creates equal lows or obvious support
  → Retail traders go long with stops below support
  → Stops accumulate = liquidity builds

Phase 2 — SWEEP: Price drops BELOW support
  → Stops get triggered → selling pressure spikes briefly
  → Smart money uses this selling to BUY at better prices
  → Candle shows long wick below support

Phase 3 — REJECTION: Price closes back ABOVE support
  → The candle that swept has small body, long lower wick
  → This IS the signal

Phase 4 — ENTRY: Next candle opens → enter CALL
  → Smart money is now positioned long
  → Price moves up with real buying pressure
```

### Bearish Liquidity Grab (at Resistance)
```
Same logic inverted:
Phase 1: Equal highs or obvious resistance builds
Phase 2: Price spikes ABOVE resistance (grabs buy stops)
Phase 3: Price closes back BELOW resistance (rejection)
Phase 4: Enter PUT on next candle
```

## Order Blocks — Detailed Guide

### Finding Valid Order Blocks
```
Bullish Order Block:
1. Identify a strong upward impulsive move (≥ 2× ATR)
2. Find the LAST bearish (red) candle before that move
3. That candle's range (open to close) = Bullish OB zone
4. When price returns to this zone later → expect bounce UP

Bearish Order Block:
1. Identify a strong downward impulsive move (≥ 2× ATR)
2. Find the LAST bullish (green) candle before that move
3. That candle's range (open to close) = Bearish OB zone
4. When price returns to this zone later → expect bounce DOWN

Validity rules:
- The impulsive move must create a Break of Structure (BOS)
- OB must be on FIRST retest (untested = strongest)
- OB zone should not have been "mitigated" (price traded through it)
```

### OB + S/R Confluence
```
When an Order Block aligns with an S/R zone:
- Zone score increases by +2
- Probability of bounce increases significantly
- This is one of the highest-confluence setups available
- Entry: Wait for rejection candle at the OB/S/R zone
```

## Fair Value Gaps (FVG) — Detection and Use

### Detection Algorithm
```
For each 3-candle window [c1, c2, c3]:

Bullish FVG:
  IF c1.high < c3.low:
    fvg_top = c3.low
    fvg_bottom = c1.high
    fvg_midpoint = (fvg_top + fvg_bottom) / 2
    → Price will likely return to this zone before continuing UP

Bearish FVG:
  IF c1.low > c3.high:
    fvg_top = c1.low
    fvg_bottom = c3.high
    fvg_midpoint = (fvg_top + fvg_bottom) / 2
    → Price will likely return to this zone before continuing DOWN
```

### FVG Trading Rules for Binary Options
```
1. FVG forms during impulsive move → mark the zone
2. Wait for price to RETURN to FVG zone (pullback)
3. At FVG zone, look for rejection candle
4. If rejection confirms → enter in original move direction
5. If price trades THROUGH FVG completely → FVG is "mitigated" → invalid

Best FVG setups:
- FVG at S/R zone (double confluence)
- FVG at Order Block (triple confluence if also at S/R)
- FVG during Expansion regime with trend
```

## Break of Structure (BOS) and Change of Character (CHoCH)

### Definitions
```
In an UPTREND (Higher Highs, Higher Lows):
  BOS = Price makes a new Higher High → trend continues
  CHoCH = Price makes the FIRST Lower Low → trend may be changing

In a DOWNTREND (Lower Highs, Lower Lows):
  BOS = Price makes a new Lower Low → trend continues
  CHoCH = Price makes the FIRST Higher High → trend may be changing
```

### Using BOS/CHoCH for Binary Options
```
Trend Continuation Trade:
1. Identify trend direction on M15/H1
2. Wait for BOS on M5 (confirming trend)
3. Wait for pullback to S/R zone / OB / FVG
4. Enter in trend direction after rejection at pullback zone

Trend Reversal Trade:
1. Identify CHoCH on M5 (first sign of change)
2. Confirm with M15 structure (is it also showing change?)
3. Wait for pullback to new S/R zone / OB
4. Enter in new direction after rejection

CHoCH + Liquidity Sweep = STRONGEST reversal signal
- Price sweeps a key high/low (grabs liquidity)
- Then creates CHoCH (structural break)
- Then pulls back to OB/FVG
- Enter reversal → highest probability setup
```

## Asian Range Sweep Strategy — Step by Step

```
Preparation (before 14:00 Thailand time):
1. Mark Asian session High (highest price 06:00-14:00)
2. Mark Asian session Low (lowest price 06:00-14:00)
3. Calculate Asian range = High - Low
4. These become your S/R zones for London session

During London Open (14:00-16:00):
5. Watch if price approaches Asian High or Low
6. WAIT — do not enter on first touch
7. Look for price to SWEEP (wick beyond) the level
8. After sweep, wait for rejection candle
9. Enter REVERSAL (if swept high → PUT, if swept low → CALL)
10. Target: midpoint of Asian range or opposite edge

Why this works:
- Asian session has low volume → creates clean H/L
- Millions of traders mark these levels → stops accumulate
- London smart money sweeps these stops for liquidity
- After sweep, real move begins in opposite direction

When to SKIP:
- Asian range is very small (< 15 pips for EURUSD) → not enough liquidity
- Major news during London open → unpredictable
- Asian session was already very volatile → levels less clean
```
