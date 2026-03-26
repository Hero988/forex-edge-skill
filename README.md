# Forex Edge Skill

AI agent skill for automated forex strategy discovery and MQL5 Expert Advisor generation. Backtests thousands of strategy combinations across forex pairs via MetaTrader 5, ranks by equity curve smoothness (R², profit factor, Sharpe ratio), and generates complete compilable MQL5 Expert Advisors with prop firm compliance baked in.

## Installation

### Claude Code

**Git Bash / macOS / Linux:**
```bash
mkdir -p ~/.claude/skills/forex-edge && curl -sL https://raw.githubusercontent.com/Hero988/forex-edge-skill/master/forex-edge/SKILL.md -o ~/.claude/skills/forex-edge/SKILL.md
```

**PowerShell (Windows):**
```powershell
New-Item -ItemType Directory -Force -Path "$HOME/.claude/skills/forex-edge" | Out-Null; Invoke-WebRequest -Uri "https://raw.githubusercontent.com/Hero988/forex-edge-skill/master/forex-edge/SKILL.md" -OutFile "$HOME/.claude/skills/forex-edge/SKILL.md"
```

The skill auto-loads in every Claude Code session. Verify with: "What skills are available?"

### Other Agents (Cursor, Codex, Gemini CLI, Copilot, etc.)

```bash
npx skills add Hero988/forex-edge-skill
```

Works with 40+ agents via [skills.sh](https://skills.sh).

## Usage

Invoke the skill by asking the agent:

> /forex-edge

On first run, the skill will:
1. Clone the [companion toolkit](https://github.com/Hero988/Forex-Trading-Skill) into your working directory
2. Walk you through interactive setup (MT5 credentials, prop firm rules, backtest preferences)
3. Install Python dependencies

## What It Does

1. **Backtests** thousands of strategy combinations (EMA cross, RSI reversal, MACD cross) across all available forex pairs on your MT5 account
2. **Ranks** results by equity curve smoothness using a composite score (R² × 50 + PF × 20 + WR × 0.5 + Sharpe × 5 + Monthly Consistency × 0.3 - Max DD × 10)
3. **Generates** complete, compilable MQL5 Expert Advisor `.mq5` files from winning strategies
4. **Bakes in** your prop firm rules (daily DD, trailing DD, float cap, news filter, weekend close, no hedging) as configurable EA input parameters

## Requirements

- MetaTrader 5 (with an active account — prop firm or personal)
- Python 3.10+
- Claude Code with this skill installed

## Supported Prop Firms

Ships with reference profiles for:
- **FundingPips Zero** — 3% daily DD, 5% trailing DD, 1% float cap
- **FTMO** — 5% daily DD, 10% max DD
- **MyFundedFX** — 5% daily DD, 8% trailing DD
- **Personal account** — no restrictions

Select a profile during setup or enter custom rules.

## Companion Toolkit

The skill uses a companion repo for scripts, templates, and prop firm profiles:

- **Repo:** [Hero988/Forex-Trading-Skill](https://github.com/Hero988/Forex-Trading-Skill)
- Auto-cloned on first invocation

## License

MIT
