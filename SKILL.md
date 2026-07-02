---
name: eth-btc-ratio-rotation
description: >
  example Skill for the CWC AI Trading Skill Challenge.
  This Skill demonstrates a transparent ETH/BTC ratio rotation strategy that can be used as a reference
  structure for user submissions. It monitors the ETH/BTC ratio trend to identify whether market risk
  preference is favoring ETH or BTC, and provides a rules-based rotation framework.
---

# ETH/BTC Ratio Rotation Strategy

> example template for the CWC AI Trading Skill Challenge.
> This example is designed to show how a trading Skill can be structured, reviewed, and executed by an AI Agent.

## 1. Skill Name

**ETH/BTC Ratio Rotation Strategy**

## 2. Strategy Type

**Trend Rotation**

This strategy sits between trend following and relative-strength rotation. It does not attempt to predict the absolute price direction of BTC or ETH. Instead, it uses the ETH/BTC ratio to judge which asset is currently showing stronger relative momentum.

## 3. Applicable Market

- **Markets:** Crypto spot or perpetual futures
- **Trading pairs:** `BTC/USDT`, `ETH/USDT`
- **Signal pair:** `ETH/BTC`
- **Primary timeframe:** 1D
- **Secondary confirmation timeframe:** 4H
- **Best suited for:** Trending markets
- **Less suited for:** Sideways markets with frequent false breakouts

## 4. Core Logic

The strategy answers one core question:

**Should the portfolio currently overweight ETH, overweight BTC, or remain neutral?**

The decision is based on the position and slope of the ETH/BTC ratio relative to its moving averages.

```text
Signal source:
R = ETH/BTC ratio
MA_fast = 21-day moving average of R
MA_slow = 55-day moving average of R

Rule 1: ETH-Led Market
If R crosses above MA_fast, MA_fast is above MA_slow, and MA_fast is sloping upward:
→ Market risk preference is improving.
→ ETH is showing relative strength.
→ Suggested action: overweight ETH and underweight BTC.

Rule 2: BTC-Led Market
If R crosses below MA_fast, MA_fast is below MA_slow, and MA_fast is sloping downward:
→ Market risk preference is weakening.
→ BTC is showing relative strength.
→ Suggested action: overweight BTC and underweight ETH.

Rule 3: Neutral Market
If MA_fast and MA_slow are intertwined, or R repeatedly moves between the two averages:
→ No clear rotation signal.
→ Suggested action: keep a balanced BTC / ETH allocation or reduce total exposure.

Risk Overlay:
If BTC closes below its 200-day moving average:
→ Maximum total position is reduced to 30%.

If the Fear & Greed Index is below 15:
→ Stop opening new positions until the risk signal improves.
```

## 5. Why Use ETH/BTC?

The ETH/BTC ratio can be treated as a risk preference indicator for the crypto market.

When ETH/BTC rises, capital is often rotating from BTC into ETH and higher-beta assets. When ETH/BTC falls, capital is often rotating back into BTC or reducing risk exposure.

This makes the ETH/BTC ratio useful for identifying relative leadership between BTC and ETH.

## 6. Agent Execution Flow

```text
Step 1: Fetch market data
- BTC price history
- ETH price history
- ETH/BTC ratio history
- Fear & Greed Index

Step 2: Calculate indicators
- ETH/BTC ratio
- MA21 of ETH/BTC
- MA55 of ETH/BTC
- Slope of MA21 and MA55
- BTC price versus BTC 200-day moving average

Step 3: Apply signal rules
- ETH-led market
- BTC-led market
- Neutral market
- Risk-reduction mode

Step 4: Produce output
- Current state
- Suggested allocation
- Executable action
- Invalidation condition
- Confidence level
```

## 7. Core Parameters

| Parameter | Default Value | Meaning | Adjustment Notes |
|---|---:|---|---|
| `MA_fast` | 21 | Fast moving average for ETH/BTC | Lower value is more sensitive |
| `MA_slow` | 55 | Slow moving average for ETH/BTC | Higher value is more stable |
| `confirm_tf` | 4H | Secondary confirmation timeframe | Can be changed to 1H for shorter-term use |
| `btc_trend_ma` | 200 | BTC long-term trend filter | Used as a risk overlay |
| `fng_pause` | 15 | Fear & Greed pause threshold | Higher value is more conservative |
| `max_position` | 80% | Maximum single-sided allocation | Should be lowered for conservative users |
| `rebalance` | 1D close | Rebalancing frequency | Avoids excessive intraday switching |

## 8. Standard Output Format

```text
ETH/BTC Rotation Signal | [Date] (UTC+8)

ETH/BTC ratio: 0.0XXX
MA21: 0.0XXX
MA55: 0.0XXX
MA slope: Up / Down / Flat
BTC vs MA200: Above / Below
Fear & Greed Index: NN

Current State:
ETH-Led / BTC-Led / Neutral / Risk-Reduction

Suggested Allocation:
BTC __% | ETH __% | Cash __%

Executable Action:
[Example: Rotate 30% of BTC allocation into ETH.]

Invalidation Condition:
[Example: If ETH/BTC falls back below MA21, the signal is invalidated.]

Confidence:
__%

Risk Notice:
This output is for strategy demonstration only and does not constitute investment advice.
```

## 9. Risk Notice

- Moving average signals are lagging indicators and may generate false signals in sideways markets.
- A correct ETH/BTC rotation signal does not guarantee profit if the broader crypto market declines.
- This strategy does not replace independent research, risk management, or portfolio planning.
- If used with perpetual futures or leverage, funding fees, liquidation risk, and slippage may significantly increase losses.
- If market data is delayed, missing, or unreliable, the Agent should stop generating trading actions until data quality is restored.
- This Skill is provided for educational and activity demonstration purposes only. It does not constitute investment advice, financial advice, or trading advice.

## 10. Submission Checklist

Participants using this template should replace the example content with their own strategy and confirm that the final submission includes:

- Skill name
- Strategy type
- Applicable market
- Core logic
- Core parameters
- Risk notice
- Public GitHub link
- Agent execution flow
- Standard output format
- Invalidation conditions

## 11. Public GitHub Link

Replace this section with the public GitHub repository link for your own submitted Skill.

```text
https://github.com/<your-account>/<your-skill-repository>
```

## 12. Disclaimer

This Skill is an example template for the CWC AI Trading Skill Challenge and is provided for educational and demonstration purposes only.

It does not represent a commitment that the strategy will be listed, supported, executed, or productized by CoinW. It does not constitute investment advice or a guarantee of returns.

Users are responsible for their own research, risk assessment, and trading decisions.
