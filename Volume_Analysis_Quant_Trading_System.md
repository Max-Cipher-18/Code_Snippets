# Volume Analysis: Quant Trading System Design Guide
### Derived from *Investing with Volume Analysis* by Buff Pelz Dormeier (Charles Dow Award, 2006)
*Curated for Positional & Swing Traders*

---

## Executive Summary

This guide extracts every mechanically applicable insight from Dormeier's book into a full, layered trading system. The core thesis is simple but powerful: **volume is the cause; price is the effect.** A price move without volume support is a mirage. Price confirmed by volume is a high-conviction signal. The system built here integrates five proprietary indicators, a five-step market positioning framework, dynamic trailing stops, and position-sizing rules — all grounded in documented backtested results.

**Expected improvement in returns:** The book's own studies show that volume-enhanced systems produced **+10.41% outperformance vs. benchmark** in the top-VPCI bucket, a **34.6% → 47.5% win-rate improvement** when switching from MACD to TTI, and **$261,403 additional profit** over the MACD across 60 securities tested over 2,000–3,000 days. These are not cherry-picked anecdotes — they are systematic backtests across 12 subgroups.

---

## Part 1: Foundational Concepts You Must Internalize

Before building the system, you must understand the physics underlying it.

### 1.1 The B = S = T Identity

Every trade requires a buyer and a seller. Volume is not "more buyers than sellers" — it is the number of shares exchanged when buyers and sellers **agree on a price despite disagreeing on direction**. What volume actually tells you is the **conviction intensity** on both sides, not who outnumbers whom. High volume means both sides had strong conviction; low volume means apathy.

**Actionable implication:** High-volume price moves carry information. Low-volume moves can be reversed easily.

### 1.2 Volume Leads Price

Volume changes precede price changes. This is the foundational law of technical volume analysis (Granville, Wyckoff, Dow). Institutions must accumulate or distribute large positions before a price trend is fully established. The footprints of this activity show up in volume before the price move matures.

**Actionable implication:** A shift in volume pattern is your leading indicator. Use it to enter before the crowd and exit before the trend reverses.

### 1.3 Force = Mass × Acceleration (Newton Applied to Markets)

Dormeier maps Newton's three laws of motion onto price-volume dynamics:
- **Law 1 (Inertia):** A trend in motion stays in motion. Only a force (volume) can change it.
- **Law 2 (Force = Mass × Acceleration):** Price acceleration requires volume (mass). A fast price move on thin volume will stall or reverse — the force is insufficient.
- **Law 3 (Equal & Opposite Reaction):** Every climactic volume event is followed by a reaction in the opposite direction.

**Actionable implication:** Never trust a breakout that lacks proportional volume. Always qualify acceleration with volume.

---

## Part 2: The Four Phases of Volume Analysis (Your Market Map)

This is the core interpretive framework for reading any chart. Every stock and market index cycles through four phases. Your edge comes from identifying which phase a security is in and trading accordingly.

| Phase | Price | Volume | Character | Signal |
|---|---|---|---|---|
| **1 – Strong Demand** | Rising | Rising | Greed with Energy | **BUY / Hold Long** |
| **2 – Weak Demand** | Rising | Falling | Greed without Energy (Complacency) | **Prepare to Exit Long** |
| **3 – Strong Supply** | Falling | Rising | Fear with Energy | **Short / Avoid** |
| **4 – Weak Supply** | Falling | Falling | Fear without Energy (Apathy) | **Prepare to Buy** |

### Phase Details

**Phase 1 (Strong Demand):** The best time to be long. Institutions are accumulating on weakness; uninformed public is selling rallies. Volume expanding with each up move confirms institutional conviction. Higher lows + rising volume = textbook accumulation.

**Phase 2 (Weak Demand):** Price keeps rising but volume shrinks. The pyramid is topping out. Late retail buyers are the marginal buyer. Institutions are quietly selling into strength. This is a distribution phase disguised as an uptrend. **This is your exit zone.**

**Phase 3 (Strong Supply):** Price breaks below support with expanding volume. Fear is in control. Wide, erratic price swings to the downside on high volume. Do NOT buy the dip here — supply is dominant.

**Phase 4 (Weak Supply):** Price falls but volume contracts to near nothing. Sellers are exhausted; no one willing to sell at these depressed prices. This is the setup for Phase 1. Watch for a volume pickup at the bottom — that signals accumulation beginning. **This is your bottom-fishing zone.**

### Step-by-Step Phase Identification

1. Plot a 20-period moving average of volume on your chart.
2. Compare each price bar's volume to the moving average.
3. Identify whether price is in an uptrend or downtrend (use 50-day and 200-day SMAs).
4. Cross-reference: Is volume expanding or contracting relative to its MA?
5. Map the quadrant: Rising price + rising volume = Phase 1. Rising price + falling volume = Phase 2. Falling price + rising volume = Phase 3. Falling price + falling volume = Phase 4.
6. Act accordingly per the table above.

---

## Part 3: Bar-by-Bar Volume Price Spread Analysis (Entry Precision)

At the individual price bar level, the combination of close position within the bar and volume gives fine-grained entry and exit signals.

### The Four Critical Bar Types

**Most Bullish (Reversal Signal):**
- Price opens low, closes near the HIGH of the bar
- Volume: HIGH
- Interpretation: Aggressive buyers overwhelmed sellers; demand is robust
- Action: Strong long entry signal, especially near support

**Moderately Bullish:**
- Price closes above midpoint of bar
- Volume: Moderate to high
- Interpretation: Buyers in control, conviction moderate
- Action: Long entry, secondary confirmation needed

**Most Bearish (Reversal Signal):**
- Price opens high, closes near the LOW of the bar
- Volume: HIGH
- Interpretation: Sellers overwhelmed buyers; supply is robust
- Action: Exit long or enter short, especially near resistance

**High-Volume Depreciation (Exhaustion Signal):**
- Price moves strongly in one direction on very high volume but closes weakly (near the open or prior close)
- Interpretation: Climactic exhaustion — the dominant side ran out of new participants
- Action: Counter-trend positioning alert; prepare for reversal

### Volume Price Spread Decision Tree

```
Step 1: Where did price close relative to the bar's range?
         ├── Upper third → Bullish bar
         ├── Middle → Neutral bar
         └── Lower third → Bearish bar

Step 2: What was the volume?
         ├── Above 1.5× 20-period average → HIGH volume
         ├── 0.7×–1.5× average → NORMAL volume
         └── Below 0.7× average → LOW volume

Step 3: Cross-reference:
         ├── Bullish bar + HIGH volume → Strong demand; buy signal
         ├── Bullish bar + LOW volume → Weak demand; caution, may not sustain
         ├── Bearish bar + HIGH volume → Strong supply; sell/short signal
         ├── Bearish bar + LOW volume → Weak supply; may be near bottom
         ├── Neutral bar + HIGH volume → Climactic struggle; watch for resolution
         └── Neutral bar + LOW volume → Disinterest; avoid trading

Step 4: Consider prior trend context (Phase 1–4) for confirmation.
```

### Gap Analysis with Volume

- **Upside gap + HIGH volume:** Legitimate breakout; momentum is real. Trade in gap direction.
- **Upside gap + LOW volume:** False move; likely to fill. Fade with caution.
- **Downside gap + HIGH volume:** Legitimate breakdown; continue short or exit long.
- **Downside gap + LOW volume:** Exhaustion gap; may be near bottom.

---

## Part 4: The Core Indicators — Formulas & Implementation

### 4.1 Volume-Weighted Moving Average (VWMA)

The foundation of everything that follows. VWMA weights each closing price by that day's volume, giving higher-volume days more influence.

**Formula:**
```
VWMA(n) = Σ(Close_i × Volume_i) / Σ(Volume_i)   for i = 1 to n
```

**Properties vs. SMA:**
- VWMA > SMA → Recent high-volume days are at higher prices → Bullish (accumulation)
- VWMA < SMA → Recent high-volume days are at lower prices → Bearish (distribution)
- VWMA ≈ SMA → Volume is distributed evenly → Neutral

**Implementation Steps:**
1. Choose your lookback period (e.g., 10-day short, 50-day long).
2. For each day: multiply Close × Volume.
3. Sum the products over n days.
4. Divide by the sum of Volume over n days.
5. Plot alongside the corresponding SMA for divergence.

**Backtested Edge (from book):** Using VWMA signals instead of SMA crossover signals produced earlier entries, smaller losses when wrong, and larger profits when right — across all 12 capitalization/volatility subgroups tested.

---

### 4.2 VW-MACD (Volume-Weighted MACD)

A direct enhancement of Appel's MACD: replace the two exponential moving averages with VWMAs.

**Standard MACD:**
```
MACD Line = EMA(12) − EMA(26)
Signal Line = EMA(9) of MACD Line
```

**VW-MACD:**
```
VW-MACD Line = VWMA(12) − VWMA(26)
Signal Line = EMA(9) of VW-MACD Line   [signal line stays as EMA]
```

**Trading Rules:**
- **Buy:** VW-MACD crosses above its Signal Line
- **Sell/Short:** VW-MACD crosses below its Signal Line
- **Bull confirmation:** VW-MACD above zero and rising
- **Bear confirmation:** VW-MACD below zero and falling
- **Divergence alert:** Price makes new high but VW-MACD does not → sell warning

**Why it's better:** Volume-weighting makes the fast average more responsive during high-volume periods (when information content is highest) and less jumpy during low-volume noise.

---

### 4.3 Trend Thrust Indicator (TTI) — The Flagship Momentum Signal

The TTI is Dormeier's most refined indicator, winning the Charles Dow Award. It takes VW-MACD and adds a **volume multiplier** that exponentially amplifies the signal when volume confirms price and dampens it when volume contradicts price.

**TTI Construction:**

**Step 1:** Calculate short-term and long-term VWMAs (e.g., 12 and 26 periods).

**Step 2:** Calculate the Volume Multiplier (VM):
```
VM = VWMA_short_volume / VWMA_long_volume
   = SMA(Volume, short_period) / SMA(Volume, long_period)
```

**Step 3:** Create Volume-Enhanced Averages:
```
Enhanced_Fast_MA  = VWMA(12) × VM²
Enhanced_Slow_MA  = VWMA(26) × (1/VM)²
```
*(When volume rises, fast MA gets bigger and slow MA gets smaller — spreading them apart for a stronger signal. When volume falls, the opposite occurs — compressing them and reducing signal strength.)*

**Step 4:** Calculate the Buff Spread:
```
Buff Spread = Enhanced_Fast_MA − Enhanced_Slow_MA
```

**Step 5:** Calculate the Adaptive Signal Line:
```
Signal Period = Base_Period × (1/VM)   [adaptive: shortens when volume falls, lengthens when volume rises]
TTI Signal Line = EMA(Buff Spread, adaptive_period)
```

**Trading Rules:**
- **Buy:** Buff Spread crosses ABOVE TTI Signal Line (accumulation)
- **Sell/Short:** Buff Spread crosses BELOW TTI Signal Line (distribution)
- **Strong Buy:** Buff Spread crosses above zero AND above Signal Line simultaneously
- **Strong Sell:** Buff Spread crosses below zero AND below Signal Line simultaneously

**Backtested Performance vs. MACD (60 securities, 2,000–3,000 days each):**

| Metric | MACD | TTI | TTI Edge |
|---|---|---|---|
| Average Win Rate | 34.67% | 47.5% | **+12.8 percentage points** |
| Total Profit (all groups) | Baseline | +$261,403 more | **Consistent across all 12 subgroups** |
| Best category (large cap, high vol) | Lower | Higher | TTI dominated |
| Worst group (TTI vs MACD) | — | TTI still won | **No group where MACD beat TTI** |

---

### 4.4 Volume Price Confirmation Indicator (VPCI) — The Trend Validator

VPCI is the indicator for which Dormeier won the Charles Dow Award. It measures the divergence between what price says and what volume-weighted price says — quantifying whether volume is confirming or contradicting the trend.

**Formula — Three Components:**

**Step 1: Volume-Price Confirmation (VPC)**
```
VPC = VWMA(long) − SMA(long)

Example: 50-day VWMA = 50, 50-day SMA = 48.5 → VPC = +1.5 (bullish confirmation)
```
Positive VPC = high-volume days at higher prices = accumulation
Negative VPC = high-volume days at lower prices = distribution

**Step 2: Volume-Price Ratio (VPR)**
```
VPR = VWMA(short) / SMA(short)

Example: 10-day VWMA = 25, 10-day SMA = 20 → VPR = 1.25
```
VPR > 1 amplifies VPC (short-term volume confirming)
VPR < 1 diminishes VPC (short-term volume contradicting)

**Step 3: Volume Multiplier (VM)**
```
VM = SMA(Volume, short) / SMA(Volume, long)

Example: 10-day avg volume = 1.5M, 50-day avg volume = 750K → VM = 2.0
```
VM > 1 = volume is accelerating (overweights VPCI signal)
VM < 1 = volume is decelerating (underweights VPCI signal)

**Final VPCI Calculation:**
```
VPCI = VPC × VPR × VM

Continuing example: VPCI = 1.5 × 1.25 × 2.0 = 3.75 (strongly bullish)
```

**Standard parameters:** Long = 5× short (e.g., short=10, long=50)

**Smoothed VPCI:**
```
VPCI_Smoothed = VWMA(VPCI, short_period)
```

**VPCI Interpretation Table:**

| Price Trend | VPCI Direction | Relationship | Signal |
|---|---|---|---|
| Rising | Rising | Confirmation | **Strongly Bullish** |
| Rising | Falling | Contradiction | **Bearish Warning — Exit** |
| Falling | Rising | Contradiction | **Bullish — Buy Opportunity** |
| Falling | Falling | Confirmation | **Strongly Bearish** |

**The VPCI V-Bottom Signal (High-Conviction Major Bottom)**

Since 2002, every major intermediate-term S&P 500 bottom was marked by a VPCI V-bottom:
- VPCI drops below the lower Bollinger Band (2 standard deviations) of VPCI
- Then rapidly rebounds above the lower band, forming a V shape
- This signals panic selling exhaustion followed by sudden resumption of buying conviction
- Documented at: March 2003 bottom, June 2006 correction low, March 9, 2009 bear market low

**Rules:**
1. Apply Bollinger Bands to VPCI (period = short_period, width = 2 std deviations)
2. Alert when VPCI pierces below the lower band
3. BUY signal confirmed when VPCI crosses back above the lower band (the V formation)
4. This is a rare but extremely high-conviction signal

---

### 4.5 Anti-Volume Stop Loss (AVSL) — The Intelligent Trailing Stop

AVSL replaces a fixed percentage stop with a dynamic stop that accounts for volatility AND the price-volume relationship. Tight stops on weak-volume trends; loose stops on strong-volume trends.

**Formula:**
```
AVSL = Lower_Bollinger_Band(Price_series, Length, StdDev_Factor)

Where:
  Length    = Round(3 + VPCI)           [VPCI > 0 → longer period → looser stop]
  Price     = Average(Daily_Lows × (1/VPC) × (1/VPR), Length)  [volume-adjusted low]
  StdDev    = 2 × (VPCI × VM)           [VPCI high → wider bands → looser stop]
```

**What AVSL does dynamically:**
- **High VPCI (strong volume confirmation):** Length increases, StdDev widens → stop moves further away → avoids being shaken out of strong trends
- **Low or negative VPCI (volume diverging):** Length shortens, StdDev narrows → stop tightens → exits quicker before full reversal

**Implementation Steps:**
1. Calculate VPCI for the security.
2. Plug VPCI into the Length formula: e.g., VPCI = 2.0 → Length = Round(3 + 2) = 5.
3. Calculate volume-adjusted lows: multiply each bar's low by (1/VPC) × (1/VPR).
4. Take SMA of these adjusted lows over Length periods.
5. Compute lower Bollinger Band: subtract (StdDev_Factor × StdDev) from the SMA.
6. This is your stop price for the day. Update daily (or weekly for swing trades).

**Time-frame Applications:**
- **Short-term/swing (3–10 day holds):** Use daily data, recalculate daily
- **Intermediate swing (weeks to months):** Use weekly data, recalculate weekly
- **Position/long-term:** Use monthly data, recalculate monthly

**Exit Rule:** Close position when the security closes BELOW the AVSL on that time frame.

---

## Part 5: The Five-Step Market Positioning System (MPS)

This is the top-down hierarchical framework for building a full trading system. Work through each step in order before committing capital.

### Step 1: Identify the Primary Trend Direction

Determine the direction of the broad market's primary trend. Use the S&P 500 or appropriate index.

**Tools:**
- 200-day SMA: Price above = bull market bias; below = bear market bias
- TTI on the index: Above zero and rising = confirm bull; below zero and falling = confirm bear
- Higher highs + higher lows = uptrend. Lower highs + lower lows = downtrend.

**Decision:** Are you operating in a bull or bear market environment? This governs whether you favor long or short positions.

### Step 2: Confirm Trend Sustainability with Volume (VPCI Index)

After establishing trend direction, verify that volume supports it. Use either index-level VPCI or — better — a VPCI Index constructed from the VPCI of each individual S&P 500 constituent.

**Rules:**
- Broad market rising + VPCI Index rising → trend confirmed → full long exposure
- Broad market rising + VPCI Index falling → trend weakening → reduce exposure, tighten stops
- Broad market falling + VPCI Index falling → downtrend confirmed → avoid longs, consider shorts
- Broad market falling + VPCI Index rising → downtrend contradicted → watch for bottom, begin accumulating

**Key Warning Signal:** VPCI Index turning down while the market continues to rise = major top in formation (the book shows this warned of the 2007 market top).

### Step 3: Assess Market Breadth (Market Positioning System Map)

Build a 2D map with two axes:
- **X-axis (horizontal):** Advance-Decline Line of the index (left = more advancers, right = more decliners)
- **Y-axis (vertical):** Cap-Weighted Up Volume minus Cap-Weighted Down Volume (up = more up volume, down = more down volume)

**Four Quadrants and Their Meaning:**
- **Upper-Left (Best):** Strong price breadth + strong volume breadth → Full bull, maximum long exposure
- **Upper-Right:** Weak price breadth + strong volume breadth → Mixed; rotation happening, selective longs
- **Lower-Left:** Strong price breadth + weak volume breadth → Caution; breadth advance lacks conviction
- **Lower-Right (Worst):** Weak price breadth + weak volume breadth → Bear market conditions, minimize longs

**Track the direction of movement:** Coordinates moving toward upper-left = increasingly bullish. Coordinates moving toward lower-right = increasingly bearish.

### Step 4: Sector Selection via VW-MACD Relative Strength

Once the market environment is confirmed, identify the sectors most likely to outperform.

**Two-Part Sector Ranking Process:**

**Part A — Momentum Score:** For each sector ETF (XLE, XLK, XLF, etc.), calculate the VW-MACD and compare its reading relative to the S&P 500's VW-MACD. Rank sectors by relative VW-MACD strength (momentum differential).

**Part B — Persistence Score:** Among the top-performing sectors, rank by how long each has been in the top quartile of VW-MACD relative strength. Sectors with sustained high rankings score higher than sectors that just broke into the top quartile.

**Final Rank:** Combine both scores (weight equally or 60/40 in favor of persistence). The top two to three sectors are your investment universe for Step 5.

**Key principle:** You want sectors where money is flowing in AND has been flowing in — not just a momentary spike.

### Step 5: Individual Stock Selection via MPS (TTI + VPCI)

Within your top sectors, plot every constituent on the individual stock MPS:
- **X-axis:** Trend Thrust Indicator (TTI) percentile rank within the index (left = strongest uptrend, right = strongest downtrend)
- **Y-axis:** VPCI percentile rank within the index (top = highest VPCI, bottom = lowest VPCI)

**The Four Stock Quadrants with Backtested Returns (S&P 500, Jan–Apr 2010, benchmark = −2.04%):**

| Quadrant | Trend | VPCI | Backtested Return | Action |
|---|---|---|---|---|
| **Upper-Left** | Strong uptrend | High (bullish vol) | **9.4%** (held to overbought) | Primary buy zone |
| **Upper-Right** | Downtrend | High (bullish vol) | **5.11%** (held until trend reverses) | Contrarian buy |
| **Lower-Right** | Downtrend | Low (bearish vol) | **4.54%** (held until both reverse) | V-bottom candidates |
| **Lower-Left** | Strong uptrend | Low (bearish vol) | **1.57%** | Caution; trend may be fading |
| **Center (equilibrium)** | Mixed | Mixed | **1.01%** | Slight outperformance; not worth the risk |

**Direction within the map matters as much as location:**

| Starting Position | Movement | Return |
|---|---|---|
| Upper-Left | Moving further up and left (acceleration) | 9.4% |
| Upper-Left | Moving down (losing volume) | 7.48% |
| Upper-Left | Moving right (losing momentum) | 1.06% |
| Upper-Left held to opposite corner | Held until lower-right | **11.43%** |
| Upper-Right held to lower-left | Held until trend reverses | **8.91%** |

**Selection Rule:** Buy stocks in the upper-left quadrant that are continuing to move in the northwesterly direction (gaining both TTI rank and VPCI rank). The longer they sustain this trajectory, the more profitable the hold. Exit when movement turns southeasterly (losing both TTI and VPCI rank).

---

## Part 6: Complete Signal Generation Logic

### Entry Rules (Long)

All six conditions should be checked, with at least four required for a trade:

1. ☐ **Market Environment** (Step 1): Index above 200-day SMA, TTI above zero
2. ☐ **Volume Confirmation** (Step 2): VPCI Index rising or positive
3. ☐ **Breadth** (Step 3): Market breadth coordinates in upper-left or moving toward it
4. ☐ **Sector Strength** (Step 4): Stock is in one of the top two ranked sectors
5. ☐ **Stock VPCI** (Step 5): Stock in top 30% of VPCI index; VPCI positive and rising
6. ☐ **Stock TTI** (Step 5): TTI Buff Spread has crossed above its Signal Line; TTI above zero preferred

**Additional Entry Triggers (High-Conviction):**
- VPCI V-bottom formation detected → major buy signal regardless of other conditions
- Phase 4 transitioning to Phase 1 (falling price + falling volume reverting to rising volume at base)
- High-volume bullish reversal bar (closes in upper third of range on 1.5×+ average volume) at prior support

### Entry Rules (Short)

1. ☐ Index below 200-day SMA, TTI below zero
2. ☐ VPCI Index falling or negative
3. ☐ Market breadth in lower-right quadrant or moving toward it
4. ☐ Stock in bottom two ranked sectors
5. ☐ Stock VPCI in bottom 30%, negative and falling
6. ☐ TTI Buff Spread crossed below Signal Line

### Exit Rules

**Primary Exit — AVSL Trailing Stop:**
- Exit (close position) when price closes below the AVSL on your designated time frame.
- Recalculate AVSL at the start of each day (daily), week (swing), or month (position).
- Never manually override this stop downward.

**Secondary Exit — Volume Phase Shift:**
- If stock transitions from Phase 1 → Phase 2 (price rising but volume contracting sharply), reduce position by 50%.
- Full exit on Phase 1 → Phase 3 transition (price breaks support on rising volume).

**Tertiary Exit — VPCI Contradiction Signal:**
- If stock VPCI turns negative while price is still rising → exit on the next TTI sell signal.
- If stock falls from upper-left to lower-right quadrant rapidly → immediate exit.

**TTI Signal Exit:**
- Buff Spread crosses below the TTI Signal Line = distribution confirmed → exit signal.

---

## Part 7: Position Sizing and Money Management

### The Portfolio Tiering System

Allocate capital across four tiers (inspired by the "sports team salary cap" model in the book):

| Tier | Label | Description | Allocation | Position Size |
|---|---|---|---|---|
| Tier 1 | All-Stars | Top VPCI + strong TTI, Phase 1 confirmed | 40% | 4–5% each |
| Tier 2 | Starters | Solid but not top-tier signals | 30% | 2–3% each |
| Tier 3 | Rookies | Emerging signals, early Phase 1 or Phase 4 candidates | 15% | 1–1.5% each |
| Tier 4 | Watchlist/Speculative | High-risk contrarian plays (e.g., V-bottom candidates) | 15% | 0.5–1% each |

### Diversification Framework (Four Layers)

1. **Individual stock (vertical):** Max 5% in any single stock. Use AVSL; never bet the farm.
2. **Sector (horizontal):** Cap at 15–20% in any single sector. Overweight top VW-MACD sectors, underweight bottom.
3. **Market cap (vertical depth):** Spread across large, mid, small cap. TTI showed strongest relative improvement for mid and small cap (most alpha available).
4. **Factor (multiple performance drivers):** Combine VPCI-based momentum with TTI-based trend strength. Don't rely on a single catalyst — diversify the reason for owning a stock.

### Risk Compounding Table (From the Book)

**Why cutting losses aggressively matters:**

| Loss Taken | Recovery Needed to Break Even |
|---|---|
| 10% | 11% |
| 20% | 25% |
| 35% | 54% |
| 50% | **100%** |

Never let a position reach the 25% loss threshold. The AVSL is designed to prevent this. Treat the AVSL as inviolable.

### Concentration vs. Conviction

Scale position size with conviction level:
```
Position Size = Base_Size × Conviction_Multiplier

Where Conviction_Multiplier is based on:
- VPCI > 2.0 AND TTI strongly positive AND Phase 1 confirmed → 1.5×
- VPCI > 0 AND TTI positive → 1.0× (standard)
- VPCI mixed or flat → 0.75×
- VPCI negative → 0.5× (if holding at all)
```

---

## Part 8: On-Balance Volume (OBV) and Supporting Indicators

### OBV as Trend Confirmation

OBV adds volume when price closes up and subtracts it when price closes down — creating a running cumulative volume line.

**Rules:**
- OBV making new highs while price makes new highs → strong trend
- OBV making new highs before price → early accumulation signal (buy setup)
- OBV diverging (falling) while price rising → bearish divergence (exit signal)
- OBV trending up during a sideways consolidation → breakout likely to be upward

**Implementation:** Use OBV as a confirmatory filter, not a standalone trigger. Require OBV to confirm before acting on a TTI or VPCI signal.

### Volume Price Trend (VPT) as OBV Enhancement

VPT weights the volume contribution by the percentage price change, making it more proportional.
```
VPT = VPT_previous + Volume × (Close − Close_previous) / Close_previous
```
Apply the same divergence rules as OBV. VPT is more sensitive to large percentage moves.

### Market Facilitation Index (MFI/Ease of Movement Proxy)

A quick filter for whether price is moving efficiently relative to volume:
```
MFI = (High − Low) / Volume
```
- High MFI = price is moving a lot per share traded = efficient, low-friction trend
- Low MFI = price is moving little per share traded = congestion, likely reversal zone
- High volume + low MFI → effort without results = top/bottom signal per Wyckoff

---

## Part 9: Seasonal and Structural Volume Adjustments

### Volume Seasonality (Calibrate Your Moving Averages)

Volume is not uniformly distributed across the year. Dormeier identifies predictable seasonal patterns:
- **January:** Higher volume (new year asset allocation)
- **Summer (July–August):** Lighter volume; signals less reliable
- **September–October:** Volume normalizes; historically volatile
- **December:** Light volume (holiday effect); low-volume moves are less informative

**Actionable Adjustment:**
- During low-volume seasons (summer, holidays), require stricter confirmation: both VPCI AND TTI must signal, not just one.
- During high-volume seasons, standard confirmation suffices.
- Avoid initiating new positions in the last two weeks of December.

### Modern Volume Issues to Account For

The book (Chapter 22) flags that raw volume data has been distorted by structural market changes:
- **HFT and algo trading** have inflated raw share volume without adding proportional information
- **ETF flows** can create artificial volume in constituent stocks
- **Stock splits** create volume jumps that are not informational

**Calibration advice:**
- Use **relative volume** (current volume / 20-day average) rather than absolute volume
- Apply **cap-weighted volume** for index-level analysis rather than simple share-count volume
- For breadth indicators, always use cap-weighted up/down volume, not raw share counts

---

## Part 10: Complete System Summary — Step-by-Step Checklist

### Pre-Trade Checklist (Run Weekly for Swing, Monthly for Position)

**Market Environment (Top-Down)**
- [ ] What phase is the broad market in (Phase 1–4)?
- [ ] Is the S&P 500 VPCI Index positive and rising?
- [ ] Is the advance-decline line trending upward?
- [ ] Is cap-weighted up volume exceeding cap-weighted down volume?
- [ ] Is the TTI on the S&P 500 above zero and above its signal line?

**Sector Analysis**
- [ ] Rank all 11 S&P sectors by VW-MACD relative to benchmark
- [ ] Filter to top 2–3 sectors by both momentum AND persistence
- [ ] Confirm these sectors are in Phase 1 on volume analysis

**Stock Selection**
- [ ] Screen for stocks in top sectors with VPCI > 0 and rising
- [ ] Screen for stocks with TTI Buff Spread crossing above Signal Line
- [ ] Verify stock is in Phase 1 or transitioning from Phase 4 to Phase 1
- [ ] Confirm OBV is trending up and confirming the price trend
- [ ] Check bar-by-bar: is recent volume expanding on up days, contracting on down days?

**Trade Execution**
- [ ] Calculate AVSL before entry (this is your stop price)
- [ ] Assign tier based on conviction level → determine position size
- [ ] Verify risk (Entry − AVSL) × shares does not exceed 1% of portfolio per trade

### Daily Monitoring Checklist (During Trade)

- [ ] Has stock crossed below AVSL? → Exit immediately
- [ ] Has VPCI turned negative (crossed below zero)? → Reduce position 50%
- [ ] Has TTI Buff Spread crossed below Signal Line? → Prepare to exit
- [ ] Has stock's quadrant position on MPS shifted to lower-right? → Exit
- [ ] Is volume on down days exceeding volume on up days consistently? → Phase 2 → Phase 3 warning

---

## Part 11: Expected Return Improvements

### Conservative Estimates (Based on Book's Studies)

| Enhancement | Source | Estimated Improvement |
|---|---|---|
| VWMA over SMA signals | 60-security study | Earlier entries, smaller whipsaw losses |
| VW-MACD over MACD | Same study | Win rate +12.8 pts; avg $261K more per portfolio |
| TTI over MACD | Same study | **+47.5% win rate vs 34.67%** |
| VPCI top decile selection | MPS study, Jan–Apr 2010 | **+10.41% vs −2.04% benchmark** (+12.45% alpha) |
| AVSL over fixed-% stop | Qualitative; logic-based | Fewer premature exits; larger trend captures |
| Phase identification | Wyckoff/volume principles | Buy at Phase 4 bottom, exit at Phase 2 top |

### Realistic System-Level Expectations

For a positional/swing trader implementing the full five-step MPS with TTI entries and AVSL exits:

- **Win rate improvement over standard MACD-based system:** +10–15 percentage points
- **Average hold improvement:** Longer holds in Phase 1 (AVSL keeps you in); faster exits at Phase 2 (VPCI signals early)
- **Drawdown reduction:** AVSL tightens in weak-VPCI environments, reducing max drawdown on deteriorating positions
- **Annualized alpha vs. buy-and-hold (S&P 500):** The VPCI top-decile study showed 12.45% alpha in a 4-month period; this cannot be sustained year-round, but 3–6% annualized alpha over a full cycle is a reasonable, conservative expectation for disciplined application
- **Best environment for this system:** Trending bull markets with clear sector rotation. The system struggles in low-volume, choppy sideways markets (Step 4 of Phase table correctly flags these as low-confidence periods)

---

## Appendix: Quick-Reference Formulas

```
VWMA(n)       = Σ(Close_i × Vol_i) / Σ(Vol_i)            for i = 1 to n

VPC           = VWMA(long) − SMA(long)

VPR           = VWMA(short) / SMA(short)

VM            = SMA(Vol, short) / SMA(Vol, long)

VPCI          = VPC × VPR × VM

VPCI_Smooth   = VWMA(VPCI, short_period)

VW-MACD       = VWMA(12) − VWMA(26)

TTI_VM        = SMA(Vol, short) / SMA(Vol, long)
Enhanced_Fast = VWMA(short) × TTI_VM²
Enhanced_Slow = VWMA(long) × (1/TTI_VM)²
Buff_Spread   = Enhanced_Fast − Enhanced_Slow
TTI_Signal    = EMA(Buff_Spread, Round(9/TTI_VM))    [adaptive period]

AVSL_Length   = Round(3 + VPCI)
AVSL_Price    = Avg(Low × (1/VPC) × (1/VPR), AVSL_Length)
AVSL          = AVSL_Price − 2 × (VPCI × VM) × StdDev(AVSL_Price, AVSL_Length)

RelVol        = Volume_today / SMA(Volume, 20)
```

**Standard Default Periods:**
- Short period: 10 bars
- Long period: 50 bars (= 5 × short)
- TTI signal base: 9 bars (adaptive)
- AVSL base: 3 + VPCI (dynamic)

---

*All formulas, studies, and backtested results sourced from: "Investing with Volume Analysis" by Buff Pelz Dormeier, FT Press, 2011 (Charles Dow Award 2006). This guide is for educational purposes only and does not constitute financial advice. Past performance of indicators does not guarantee future results.*
