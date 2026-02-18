# Alpaca Trading (Python CLI)

A Python-based command-line interface for trading stocks and crypto via Alpaca Markets API.

## Features

- 📈 Real-time stock quotes
- 💼 Portfolio management
- 📊 Account information
- 🔄 Order execution (market orders)
- ⏰ Market status checking
- 🔐 Secure credential management
- 📝 Paper trading support

## Quick Start

1. Install dependencies:
   ```bash
   brew install python@3.11
   /opt/homebrew/bin/pip3.11 install alpaca-py pytz
   ```

2. Configure API keys:
   ```bash
   alpaca auth
   ```

3. Test it out:
   ```bash
   alpaca clock
   alpaca account
   alpaca quote AAPL
   ```

## Why This Skill?

This is a lightweight Python implementation of the Alpaca Trading CLI, designed to be:

- **Easy to install**: Just Python + pip packages
- **Cross-platform**: Works on macOS, Linux, Windows
- **Well-documented**: Clear examples and troubleshooting
- **Safe**: Emphasizes paper trading and credential security
- **Agent-friendly**: Designed for OpenClaw agent automation

## Differences from Other Alpaca Skills

- **alpaca-trading** (ClawHub): Uses `apcacli` (Rust CLI, third-party tool)
- **alpaca** (ClawHub): Uses Python scripts but different implementation
- **alpaca-py-cli** (this skill): Custom Python CLI with Homebrew Python support

## Safety & Security

- Always test with paper trading first
- API keys stored in shell config (not in code)
- Interactive `alpaca auth` hides secret key input
- Market orders only (no complex order types to reduce risk)
- Confirmation required for `close-all` command

## License

MIT License - Free to use, modify, and distribute

## Support

- Alpaca Markets: https://alpaca.markets
- Python SDK Docs: https://alpaca.markets/docs/python-sdk/
- Issues: Report via OpenClaw Discord or ClawHub

## Author

Created for the OpenClaw community by @zijunl
