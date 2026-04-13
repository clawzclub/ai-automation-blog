---
title: "AI Trading Bots with Alpaca and Finnhub: A Hands-Off Investment Approach"
date: 2026-04-13
slug: ai-trading-bots-with-alpaca-and-finnhub-a-hands-off-investme
keywords: [Alpaca trading bot, Finnhub data, AI stock trading]
description: "AI Trading Bots with Alpaca and Finnhub: A Hands-Off Investment Approach"
---

## A Hands-Off Investment Approach Using AI Trading Bots with Alpaca and Finnhub

If you’re anything like me, you know that manual trading can be exhausting and emotionally draining. Endless screen time, market fluctuations, and second-guessing your decisions take a toll. That’s why I turned to AI trading bots powered by reliable APIs like [Alpaca (free stock + crypto trading API)](https://alpaca.markets) and [Finnhub (free real-time stock API)](https://finnhub.io). Together, they enable a seamless, hands-off stock trading experience with accurate data and automated executions.

In this deep dive, I’ll share how I built an AI stock trading bot that harnesses these APIs, combined with intelligent automation via [OpenClaw (open-source AI agent)](https://openclaw.ai). I’ll guide you step-by-step through the process, with code examples and practical tips to help you build your own automated investing system that trades efficiently while you enjoy life.

## Why Use AI Trading Bots?

Markets move fast, and emotions often cloud judgment. AI bots bring consistent execution based on quantitative data, eliminate reactionary decisions, and can monitor the market 24/7 without fatigue.

I’ve found that pairing real-time market data with an execution platform creates a closed-loop “smart trading system”. This setup enables the bot to analyze when to enter or exit positions and execute trades swiftly.

Using [Alpaca](https://alpaca.markets) for trade execution and [Finnhub](https://finnhub.io) for market insights lets me operate within a free-tier cost structure, making it accessible without sacrificing reliability.

## Step 1: Setting Up Your Alpaca and Finnhub APIs

Before coding, register for API keys:

- **Alpaca:** Get your API key and secret from [Alpaca’s dashboard](https://alpaca.markets).
- **Finnhub:** Sign up for a free API key at [Finnhub’s website](https://finnhub.io).

Install Python SDKs for easy integration:

```bash
pip install alpaca-trade-api finnhub-python
```

## Step 2: Accessing Real-Time Market Data from Finnhub

I use Finnhub’s WebSocket streams and REST API to get live quotes, candlestick data, and news sentiment that influence trading decisions.

Example: Fetch current price for Apple (AAPL):

```python
import finnhub

finnhub_client = finnhub.Client(api_key="YOUR_FINNHUB_API_KEY")

quote = finnhub_client.quote('AAPL')
print(f"Current price: {quote['c']}")
```

I incorporate such data in algorithmic triggers. For example, using technical indicators like RSI or MACD computed over Finnhub’s historical data feeds.

## Step 3: Building a Simple Trading Strategy

My go-to has been the Moving Average Crossover (MAC) strategy. When the short-term moving average crosses above the long-term average, it signals a buy, and vice versa for a sell.

Here’s a minimal Python snippet processing historical data:

```python
import pandas as pd

def moving_average_crossover(data, short_window=40, long_window=100):
    data['short_ma'] = data['close'].rolling(window=short_window).mean()
    data['long_ma'] = data['close'].rolling(window=long_window).mean()
    data['signal'] = 0
    data.loc[data['short_ma'] > data['long_ma'], 'signal'] = 1
    data.loc[data['short_ma'] <= data['long_ma'], 'signal'] = -1
    return data
```

You can fetch the historical candlestick data via Finnhub or [Polygon.io (stock market data API)](https://polygon.io) for more extensive datasets.

## Step 4: Executing Trades via Alpaca API

Alpaca makes automated trading straightforward with RESTful endpoints.

Example: Place a market buy order for 5 shares of Tesla (TSLA):

```python
import alpaca_trade_api as tradeapi

api = tradeapi.REST('YOUR_ALPACA_KEY', 'YOUR_ALPACA_SECRET', base_url='https://paper-api.alpaca.markets')

api.submit_order(
    symbol='TSLA',
    qty=5,
    side='buy',
    type='market',
    time_in_force='gtc'
)
```

I recommend running your bot in Alpaca’s “paper trading” environment first to reduce risk while you refine your strategy.

## Step 5: Orchestrating with OpenClaw for AI Automation

[OpenClaw](https://openclaw.ai) provides an extensible, autonomous AI agent environment ideal for managing these workflows—fetching data, analyzing signals, and executing trades automatically.

You can integrate your Alpaca/Finnhub scripts as OpenClaw skills. OpenClaw monitors asset behavior, reacts to alerts, and handles exceptions dynamically, adding AI reasoning to your bot’s toolkit.

## Step 6: Adding Risk Management and Alerts

Automated trading means you’ve got to safeguard your capital. Implement stop-loss thresholds and position sizing. I use alerts via:

- Email notifications
- Telegram bots
- Dashboards deployed on [Vercel (deploy web apps)](https://vercel.com)

Also consider integrating market sentiment and event data from prediction platforms like [Kalshi (regulated prediction markets)](https://kalshi.com) for major economic events.

## Step 7: Deploying Your Bot on Reliable Infrastructure

To maintain uptime and smooth operations, I deploy my bot on affordable VPS hosting such as [Hetzner Cloud (affordable VPS hosting)](https://hetzner.cloud). This ensures 24/7 execution with minimal latency.

Pair it with logging and monitoring tools for full operational insights.

## Wrapping Up: Embrace Hands-Off Intelligent Investing

When I combine Alpaca’s free trading API, Finnhub’s real-time market data, and OpenClaw’s AI automation, I get a powerful, hands-off investing system that trades rationally and consistently.

You don’t need to be at your screen all day. The bot scans, decides, and executes while I focus on other priorities. If you’re a developer looking to automate your trading workflow or an AI enthusiast wanting hands-free portfolio management, this approach is ideal.

Get started today by signing up for:

- [Alpaca](https://alpaca.markets)
- [Finnhub](https://finnhub.io)
- Exploring AI automation with [OpenClaw](https://openclaw.ai)

Build smart; trade smarter.

---

If you’re ready to develop your personalized AI trading bot or want to leverage market signals with automation, dive into these tools now. And don’t forget to check out the [Market Oracle skill on ClawHub](https://clawhub.com/skills/market-oracle) for enhanced market intelligence.

Happy automated trading!
