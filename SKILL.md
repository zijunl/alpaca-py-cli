---
name: alpaca-py-cli
description: Trade stocks and crypto via Alpaca API using Python CLI. Use for market data (quotes, bars, news), placing orders (market, limit, stop), checking positions, portfolio management, and account info. Supports both paper and live trading. Use when user asks about stock prices, wants to buy/sell securities, check portfolio, or manage trades.
metadata: {"clawdbot":{"emoji":"📈","requires":{"bins":["python3"],"packages":["alpaca-py","pytz"]},"install":[{"id":"pip-alpaca","kind":"pip","package":"alpaca-py","label":"Install alpaca-py (pip3 install alpaca-py)"},{"id":"pip-pytz","kind":"pip","package":"pytz","label":"Install pytz (pip3 install pytz)"}],"setup":{"instructions":["Get API keys from https://alpaca.markets","Run: alpaca auth (interactive setup)","Test: alpaca clock"]}}}
homepage: https://github.com/zijunl/alpaca-py-cli
---

# Alpaca Trading (Python CLI)

[![ClawHub](https://img.shields.io/badge/ClawHub-alpaca--py--cli-blue)](https://clawhub.ai/skills/alpaca-py-cli)
[![GitHub](https://img.shields.io/badge/GitHub-zijunl%2Falpaca--py--cli-green)](https://github.com/zijunl/alpaca-py-cli)

Trade stocks and crypto programmatically via Alpaca's API using a Python-based CLI tool.

**Links:**
- ClawHub: https://clawhub.ai/skills/alpaca-py-cli
- GitHub: https://github.com/zijunl/alpaca-py-cli
- Alpaca Markets: https://alpaca.markets

## Overview

Manage your Alpaca Markets trading account using the `alpaca` CLI tool and Python SDK. Supports both paper trading (simulated) and live trading.

## Installation

### Recommended: Homebrew Python (avoids urllib3/LibreSSL warnings)

```bash
# Install Homebrew Python 3.11+
brew install python@3.11

# Install alpaca-py
/opt/homebrew/bin/pip3.11 install alpaca-py pytz
```

### Alternative: System Python

```bash
pip3 install alpaca-py pytz
```

**Note:** System Python may show urllib3 warnings on macOS due to LibreSSL compatibility. Use Homebrew Python for a cleaner experience.

## Configuration

### Quick Setup with CLI

```bash
alpaca auth
```

This will interactively prompt you for:
- API Key
- Secret Key (hidden input)
- Trading mode (Paper or Live)

The command automatically saves your credentials to your shell config file (`~/.zshrc`, `~/.bashrc`, or `~/.profile`).

### Manual Setup

Alternatively, set these in your shell profile manually:

```bash
export ALPACA_API_KEY="your_api_key"
export ALPACA_SECRET_KEY="your_secret_key"
export ALPACA_PAPER="true"  # Use "false" for live trading
```

Get your API keys from https://alpaca.markets (Dashboard → API Keys)

**Paper Trading** (recommended for testing):
- Use paper trading API keys
- Virtual $100,000 starting balance
- No real money at risk

**Live Trading** (real money):
- Use live trading API keys
- Real money, real risk
- Test thoroughly with paper trading first

## CLI Commands

### Setup & Configuration

#### Configure Credentials

```bash
alpaca auth
```

Interactive setup wizard that guides you through:
1. Enter API Key
2. Enter Secret Key (hidden)
3. Choose trading mode (Paper/Live)
4. Automatically saves to shell config

### Account & Market Info

#### Check Account

```bash
alpaca account
```

Shows:
- Account number and status
- Portfolio value, cash, buying power
- P&L (equity, last equity)
- Trading restrictions (pattern day trader, blocks)

#### Check Market Status

```bash
alpaca clock
```

Shows:
- Market status (🟢 OPEN or 🔴 CLOSED)
- Current time
- Next open/close times

#### View Market Calendar

```bash
# Show next 30 trading days (default)
alpaca calendar

# Show next 7 trading days
alpaca calendar --days 7
```

Shows trading days with open/close times (Eastern Time).

#### View Portfolio History

```bash
# Default: 1 month, daily bars
alpaca history

# Last week
alpaca history --period 1W

# Last 3 months with hourly bars
alpaca history --period 3M --timeframe 1H
```

**Periods:** 1D, 1W, 1M, 3M, 1Y, all  
**Timeframes:** 1Min, 5Min, 15Min, 1H, 1D

Shows:
- Start and end equity
- Total change ($ and %)
- Recent history (last 10 data points)

### Portfolio Management

#### View Positions

```bash
alpaca positions
```

Shows all current holdings with:
- Symbol, quantity, current price
- Entry price and market value
- Unrealized P&L ($ and %)
- Total portfolio value and P&L

#### Get Stock Quotes

```bash
# Single symbol
alpaca quote AAPL

# Multiple symbols
alpaca quote AAPL,TSLA,MSFT
```

Shows:
- Bid and ask prices
- Mid price and spread
- Quote timestamp

**Note:** Quotes may show incomplete data when market is closed. Best used during market hours (9:30 AM - 4:00 PM ET).

### Order Management

#### View Orders

```bash
# Show open orders (default)
alpaca orders

# Show all recent orders
alpaca orders --status all

# Show last 20 closed orders
alpaca orders --status closed --limit 20
```

Shows:
- Order status with emoji indicators (⏳ pending, ✓ filled, ✗ canceled)
- Symbol, side (BUY/SELL), quantity
- Order ID and creation time
- Fill price (if filled)

#### Place Orders

```bash
# Buy shares
alpaca buy AAPL 10

# Sell shares
alpaca sell AAPL 5
```

Places a market order that executes at market price when market is open.

#### Cancel Orders

```bash
# Cancel specific order
alpaca cancel <order_id>

# Cancel all open orders
alpaca cancel-all
```

### Position Management

#### Close Positions

```bash
# Close specific position
alpaca close AAPL

# Close all positions (requires confirmation)
alpaca close-all
```

**Note:** `close-all` will prompt for confirmation before closing all positions.

## Example Workflows

### First Time Setup

```bash
# Configure credentials
alpaca auth

# Check account
alpaca account

# Check if market is open
alpaca clock
```

### Trading Workflow

```bash
# Check current price
alpaca quote TSLA

# Check account balance
alpaca account

# Buy some shares
alpaca buy TSLA 5

# Check pending orders
alpaca orders

# View positions (after order fills)
alpaca positions

# Get updated quote
alpaca quote TSLA

# Sell some shares
alpaca sell TSLA 2

# Check order history
alpaca orders --status all
```

### Portfolio Analysis

```bash
# View current positions
alpaca positions

# View portfolio history
alpaca history --period 1M

# Check market calendar
alpaca calendar --days 7
```

### Risk Management

```bash
# Check all open orders
alpaca orders

# Cancel specific order
alpaca cancel <order_id>

# Cancel all orders
alpaca cancel-all

# Close specific position
alpaca close AAPL

# Close all positions
alpaca close-all
```

## Agent Usage

When the user asks about their portfolio or wants to trade:

1. **Configure credentials**: Run `alpaca auth` for first-time setup
2. **Check market status**: Run `alpaca clock` to see if market is open
3. **Check account**: Run `alpaca account` to see current balance and buying power
4. **Get positions**: Run `alpaca positions` to list current holdings
5. **View orders**: Run `alpaca orders` to see pending/recent orders
6. **Get quotes**: Run `alpaca quote <symbols>` to check current prices
7. **Place orders**: Run `alpaca buy/sell` to execute trades
8. **Manage risk**: Run `alpaca cancel/close` commands as needed

## Safety Tips

- **Always test with paper trading first** (`ALPACA_PAPER=true`)
- Use `alpaca auth` to safely configure credentials (secret key is hidden)
- Check `alpaca clock` before trading to see if market is open
- Check quotes before placing orders to understand current prices
- Check `account.buying_power` before placing orders
- Use `TimeInForce.DAY` to auto-cancel unfilled orders at market close
- Monitor positions regularly with `alpaca positions`
- Check order status with `alpaca orders`
- Review portfolio performance with `alpaca history`
- Use `alpaca cancel-all` to quickly cancel all pending orders
- Use `alpaca close-all` with caution (requires confirmation)
- Set stop-loss orders for risk management
- Never share your API keys publicly

## Market Hours

US stock market hours (Eastern Time):
- **Regular hours**: 9:30 AM - 4:00 PM ET
- **Pre-market**: 4:00 AM - 9:30 AM ET
- **After-hours**: 4:00 PM - 8:00 PM ET

Orders placed outside market hours will be queued and executed when market opens.

Quotes may show incomplete or stale data when market is closed.

Use `alpaca clock` to check current market status.

## Troubleshooting

### urllib3 Warning (LibreSSL)

If you see:
```
NotOpenSSLWarning: urllib3 v2 only supports OpenSSL 1.1.1+, currently using LibreSSL
```

**Solution:** Install and use Homebrew Python 3.11+ which uses OpenSSL:
```bash
brew install python@3.11
/opt/homebrew/bin/pip3.11 install alpaca-py pytz
```

Then update the script shebang to use Homebrew Python:
```bash
sed -i '' '1s|#!/usr/bin/env python3|#!/opt/homebrew/bin/python3.11|' ~/.openclaw/workspace/skills/alpaca-py-cli/scripts/alpaca
```

### Missing pytz

If you see:
```
ModuleNotFoundError: No module named 'pytz'
```

**Solution:**
```bash
pip3 install pytz
# or
/opt/homebrew/bin/pip3.11 install pytz
```

### Command Not Found

If `alpaca` command is not found, use the full path:
```bash
~/.openclaw/workspace/skills/alpaca-py-cli/scripts/alpaca
```

Or add to PATH in your shell config:
```bash
export PATH="$HOME/.openclaw/workspace/skills/alpaca-py-cli/scripts:$PATH"
```

## Files

- **CLI Tool**: `~/.openclaw/workspace/skills/alpaca-py-cli/scripts/alpaca`
- **Config**: Environment variables in `~/.zshrc` (or `~/.bashrc`, `~/.profile`)

## Official Documentation

- Python SDK: https://alpaca.markets/docs/python-sdk/
- API Reference: https://docs.alpaca.markets/reference/
- Trading API: https://docs.alpaca.markets/docs/trading-api
- Market Data API: https://docs.alpaca.markets/docs/market-data

## Initialization (For Agents)

### Intelligent Setup with `alpaca init`

The `init` command provides an intelligent setup wizard that adapts based on the agent's capabilities.

#### Command

```bash
alpaca init
```

#### How It Works

**Step 1: Detection**
The wizard first checks if Alpaca is already configured by looking for environment variables:
- `ALPACA_API_KEY`
- `ALPACA_SECRET_KEY`
- `ALPACA_PAPER`

If already configured, it offers to reconfigure.

**Step 2: Mode Selection**
The wizard presents two setup modes:

1. **Automatic Mode** (for agents with email access)
2. **Manual Mode** (fallback for all agents)

#### Automatic Mode (Recommended for Capable Agents)

**Requirements:**
- Browser skill (for web automation)
- Email skill (for verification) - e.g., `gog` skill for Gmail access
- User information (name, address, date of birth)

**Agent Workflow:**

1. **Check Capabilities**
   ```bash
   # Agent checks if it has email access
   # Example: Check if gog skill is available
   which gog || check for email tools
   ```

2. **Gather User Information**
   ```
   Agent: "I'll help you set up Alpaca paper trading. I need some information:"
   Agent: "What's your full name?"
   User: "John Doe"
   Agent: "What's your email address?"
   User: "john@example.com"
   Agent: "What's your date of birth? (YYYY-MM-DD)"
   User: "1990-01-15"
   Agent: "What's your address?"
   User: "123 Main St, San Francisco, CA 94102"
   ```

3. **Run Init with Automatic Mode**
   ```bash
   alpaca init
   # Choose option 1 (Automatic)
   ```

4. **Browser Automation** (Future Implementation)
   ```
   Agent uses browser skill to:
   - Navigate to https://alpaca.markets
   - Click "Sign Up"
   - Fill registration form with user info
   - Submit form
   ```

5. **Email Verification**
   ```
   Agent uses email skill to:
   - Check inbox for verification email from Alpaca
   - Extract verification link
   - Click verification link in browser
   ```

6. **API Key Retrieval**
   ```
   Agent uses browser skill to:
   - Log in to Alpaca dashboard
   - Navigate to API Keys section
   - Generate Paper Trading API keys
   - Copy API Key and Secret Key
   ```

7. **Configuration**
   ```
   Agent automatically runs:
   - Saves keys to environment variables
   - Sets ALPACA_PAPER=true
   - Writes to shell config (~/.zshrc)
   ```

8. **Verification**
   ```bash
   alpaca clock
   # Agent confirms setup is working
   ```

**Note:** Automatic mode is currently a placeholder. Full implementation requires browser and email skill integration.

#### Manual Mode (Current Implementation)

**For agents without email access or as fallback:**

**Agent Workflow:**

1. **Run Init**
   ```bash
   alpaca init
   # Choose option 2 (Manual)
   ```

2. **Open Browser**
   ```
   Agent: "I'll open the Alpaca registration page for you."
   # Wizard opens: https://alpaca.markets/docs/trading/paper-trading/
   ```

3. **Guide User Through Registration**
   ```
   Agent: "Please follow these steps:
   1. Click 'Sign Up' on the Alpaca website
   2. Fill in your information and create an account
   3. Check your email and verify your account
   4. Log in to your Alpaca dashboard
   5. Go to 'API Keys' section
   6. Click 'Generate New Key' for Paper Trading
   7. Copy both the API Key and Secret Key
   8. Come back here when you're ready"
   ```

4. **Wait for User Input**
   ```
   Agent: "Do you have your API keys now?"
   User: "Yes"
   Agent: "Great! The wizard will prompt you to enter them."
   ```

5. **Collect Keys**
   ```
   # Wizard prompts:
   API Key: [user pastes key]
   Secret Key: [user pastes secret]
   ```

6. **Save Configuration**
   ```
   # Wizard automatically:
   - Saves to ~/.zshrc (or ~/.bashrc, ~/.profile)
   - Sets ALPACA_PAPER=true
   - Displays confirmation
   ```

7. **Verify Setup**
   ```bash
   # Agent runs:
   source ~/.zshrc
   alpaca clock
   
   Agent: "✓ Setup complete! Your Alpaca paper trading account is ready.
   You have $100,000 in virtual money to practice with."
   ```

#### Agent Best Practices

**When to Use Init:**
- User asks to "set up Alpaca" or "start trading"
- User mentions they don't have an Alpaca account
- Commands fail with "API keys not configured" error

**Communication Tips:**
```
Good: "I'll help you set up Alpaca paper trading. This is a safe 
      practice account with virtual money. Let me guide you through it."

Bad:  "Run alpaca init and follow the prompts."
```

**Error Handling:**
```bash
# If init fails, agent should:
1. Check if browser opened successfully
2. Ask user if they completed registration
3. Verify keys were entered correctly
4. Test with: alpaca clock
5. If still failing, suggest manual auth:
   alpaca auth
```

**Security Reminders:**
```
Agent should remind user:
- "These are Paper Trading keys (virtual money only)"
- "Never share your Secret Key with anyone"
- "I won't store your keys - they're saved in your shell config"
```

#### Example Agent Conversation

```
User: "I want to start trading stocks"

Agent: "Great! I can help you set up Alpaca paper trading. This gives 
       you $100,000 in virtual money to practice with - no real money 
       at risk. Let me check if you're already set up..."
       
       *runs: alpaca clock*
       
Agent: "You're not set up yet. I'll guide you through registration. 
       Do you have an Alpaca account already?"

User: "No"

Agent: "No problem! I'll help you create one. 
       *runs: alpaca init*
       
       I'm opening the Alpaca registration page. Please:
       1. Sign up with your email
       2. Verify your email
       3. Generate Paper Trading API keys
       4. Come back here with your keys
       
       Let me know when you're ready!"

User: "I have the keys"

Agent: "Perfect! Please enter them when prompted..."
       
       *wizard collects keys*
       
Agent: "✓ All set! Let me verify...
       *runs: alpaca clock*
       
       Your account is active! Market is currently CLOSED.
       You have $100,000 in paper money to trade with.
       
       What would you like to do? Check a stock price? View your account?"
```

#### Future Enhancements

**Planned for Automatic Mode:**
- Browser skill integration for form filling
- Email skill integration for verification
- Automatic key extraction from dashboard
- Support for multiple email providers (Gmail, Outlook, etc.)
- CAPTCHA handling (if needed)
- Error recovery and retry logic

**To Enable Full Automation:**
Agent needs to check for these skills:
```bash
# Check for browser skill
which browser || check browser skill availability

# Check for email skill  
which gog || check email skill availability

# If both available: use automatic mode
# If not: fallback to manual mode
```