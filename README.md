# Alpaca Trading (Python CLI) - OpenClaw Agent Skill

> **🤖 AI Agent Skill for OpenClaw**  
> Enable your AI agent to trade stocks and crypto via Alpaca Markets API using natural language commands.

[![ClawHub](https://img.shields.io/badge/ClawHub-alpaca--py--cli-blue)](https://clawhub.ai/skills/alpaca-py-cli)
[![GitHub](https://img.shields.io/badge/GitHub-zijunl%2Falpaca--py--cli-green)](https://github.com/zijunl/alpaca-py-cli)
[![Version](https://img.shields.io/badge/version-1.6.0-orange)](https://clawhub.ai/skills/alpaca-py-cli)

## 🤖 What is this?

This is an **OpenClaw Agent Skill** that gives your AI assistant the ability to:
- Check stock prices and market status
- Manage your trading portfolio
- Execute buy/sell orders
- View trading history and performance
- **Set up Alpaca accounts automatically** with intelligent guided wizard
- All through natural language conversation!

**Example conversation:**
```
You: "I want to start trading stocks"
Agent: "I'll help you set up Alpaca paper trading."
       *runs: alpaca init*
       *guides you through registration*
Agent: "✓ Setup complete! You have $100,000 in virtual money."

You: "What's the current price of Apple stock?"
Agent: *runs alpaca quote AAPL* "AAPL is trading at $250.32"

You: "Buy 10 shares"
Agent: *runs alpaca buy AAPL 10* "✓ Order placed for 10 shares of AAPL"
```

## ✨ Key Features

- 📈 **Real-time stock quotes** - Get current prices instantly
- 💼 **Portfolio management** - Track your holdings and performance
- 📊 **Account information** - View balance, buying power, P&L
- 🔄 **Order execution** - Buy/sell with market orders
- 📅 **Market calendar** - See upcoming trading days
- 📉 **Portfolio history** - Analyze performance over time
- ⏰ **Market status** - Check if market is open/closed
- 🤖 **Intelligent setup wizard** - `alpaca init` guides users through registration
- 🔐 **Secure credentials** - Keys stored in shell config, not in code
- 📝 **Paper trading** - Practice with $100k virtual money (no risk!)
- 🎯 **Agent-optimized** - Minimal token usage, runtime guidance

## 🚀 Quick Install

### Via ClawHub (Recommended for OpenClaw users)

```bash
npm install -g clawhub
clawhub install alpaca-py-cli
```

### Manual Install

```bash
git clone https://github.com/zijunl/alpaca-py-cli.git
cd alpaca-py-cli
brew install python@3.11
/opt/homebrew/bin/pip3.11 install alpaca-py pytz
```

## 🎯 Quick Start

### For First-Time Users

```bash
alpaca init
```

The intelligent wizard will:
- Check if you're already set up
- Guide you through Alpaca registration
- Help you generate API keys
- Configure everything automatically
- Verify your setup

### For Existing Users

```bash
alpaca clock         # Check market status
alpaca account       # View your account
alpaca quote AAPL    # Get stock price
```

## 📚 Commands

```bash
alpaca init          # 🆕 Intelligent setup wizard (first-time users)
alpaca auth          # Quick API key configuration
alpaca clock         # Market status
alpaca calendar      # Trading calendar
alpaca history       # Portfolio history
alpaca account       # Account information
alpaca quote AAPL    # Stock quotes
alpaca positions     # Current holdings
alpaca orders        # Order management
alpaca buy/sell      # Execute trades
alpaca cancel/close  # Cancel/close positions
```

## 🤖 For AI Agents

This skill is designed specifically for AI agents like OpenClaw:

**Agent workflow:**
1. User asks to trade or check stocks
2. Agent runs appropriate `alpaca` command
3. Agent interprets output
4. Agent responds in natural language

**Setup workflow:**
1. User wants to start trading
2. Agent runs `alpaca init`
3. CLI guides user through registration
4. Agent confirms setup is complete

**Token-efficient design:**
- Minimal SKILL.md (low token usage when loaded)
- Detailed guidance shown at runtime (not in skill file)
- Clear, parseable CLI output
- Agent just needs to know which commands to run

## 🔗 Links

- **ClawHub**: https://clawhub.ai/skills/alpaca-py-cli
- **GitHub**: https://github.com/zijunl/alpaca-py-cli
- **OpenClaw**: https://openclaw.ai
- **Alpaca Markets**: https://alpaca.markets
- **Python SDK Docs**: https://alpaca.markets/docs/python-sdk/

## 🛡️ Why This Skill?

**Designed for AI Agents:**
- Token-efficient skill file
- Runtime guidance instead of documentation bloat
- Clear, parseable output
- Natural language ready

**Easy to Use:**
- One command setup: `alpaca init`
- Intelligent wizard handles complexity
- Works on macOS, Linux, Windows
- No manual configuration needed

**Safe & Secure:**
- Paper trading by default ($100k virtual money)
- API keys in shell config (not in code)
- Secret key input is hidden
- Confirmation required for risky operations

**Well-Maintained:**
- Active development
- Comprehensive documentation
- Example workflows
- Troubleshooting guide

## 🆚 Differences from Other Alpaca Skills

| Skill | Implementation | Setup | Agent-Optimized |
|-------|---------------|-------|-----------------|
| **alpaca-py-cli** (this) | Python CLI | `alpaca init` wizard | ✅ Yes |
| alpaca-trading | Rust CLI (apcacli) | Manual | ❌ No |
| alpaca | Python scripts | Manual | ❌ No |

## 🔒 Safety & Security

- ✅ Paper trading by default (virtual money)
- ✅ API keys stored securely in shell config
- ✅ Secret key input is hidden
- ✅ Market orders only (reduces complexity)
- ✅ Confirmation required for `close-all`
- ✅ Agent can't access keys directly
- ✅ Clear security reminders during setup

## 📖 Documentation

- **Quick Start**: See above
- **Full Documentation**: [SKILL.md](SKILL.md)
- **Setup Guide**: Run `alpaca init` for interactive guide
- **Troubleshooting**: See SKILL.md

## 🤝 Contributing

Contributions welcome! Please open an issue or PR on GitHub.

## 📄 License

MIT License - Free to use, modify, and distribute

## 👤 Author

Created for the OpenClaw community by [@zijunl](https://github.com/zijunl)

## 💬 Support

- GitHub Issues: https://github.com/zijunl/alpaca-py-cli/issues
- OpenClaw Discord: https://discord.com/invite/clawd
- ClawHub: https://clawhub.ai/skills/alpaca-py-cli

---

**Latest Updates (v1.6.0):**
- 🎯 Major refactor: Moved detailed guidance to CLI runtime
- 📉 Reduced token usage by ~250 lines
- ✨ Enhanced `alpaca init` with step-by-step instructions
- 🤖 Better agent experience with minimal skill file
- 📋 Clear progress indicators and formatted output
