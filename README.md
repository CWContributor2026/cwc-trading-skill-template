# CWC Trading Skill Official Example Template

This repository provides an official example Skill template for the CWC AI Trading Skill Challenge.

Participants may use this repository as a reference when preparing and submitting their own trading strategy Skill. The example demonstrates how to describe a strategy in a clear, reproducible, and reviewable format.

## What This Template Includes

- Skill name and strategy type
- Applicable markets and timeframes
- Core strategy logic
- Key parameters and adjustment notes
- Risk notice and invalidation conditions
- Agent execution flow
- Standard output format
- Submission checklist

## Example Skill

The example Skill in this repository is:

**ETH/BTC Ratio Rotation Strategy**

It uses the ETH/BTC ratio as a market risk preference indicator and demonstrates how a trading Skill can define:

- when to overweight ETH;
- when to overweight BTC;
- when to stay neutral;
- when to reduce exposure due to risk controls.

## Repository Structure

```text
cwc-trading-skill-template/
├── README.md
├── SKILL.md
├── LICENSE
└── examples/
    └── eth-btc-ratio-rotation.md
```

## How To Use

1. Read `SKILL.md` as the official example template.
2. Copy the structure into your own public GitHub repository.
3. Replace the strategy logic, parameters, risks, and output format with your own trading Skill.
4. Make sure your GitHub repository is public and accessible.
5. Submit your public GitHub link through the official CWC activity form.

## Submission Checklist

Before submitting, please make sure your Skill includes:

- Skill name
- Strategy type
- Applicable market
- Core logic
- Core parameters
- Risk notice
- Public GitHub link
- Clear invalidation conditions
- Explanation of how the Skill could be used by an AI Agent

Bonus items:

- Backtest screenshot or simulation result
- Real trading review
- Parameter table
- Risk boundary explanation
- CWC / Agentic Trading scenario explanation

## Disclaimer

This repository is provided for educational and activity demonstration purposes only. It does not constitute investment advice, financial advice, trading advice, or a recommendation to buy or sell any crypto asset.

Crypto assets are highly volatile and may result in partial or total loss of funds. Users should conduct their own research and fully evaluate their risk tolerance before using any strategy.

CoinW reserves the right to interpret the final rules of the CWC AI Trading Skill Challenge.
