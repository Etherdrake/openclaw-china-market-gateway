# China Market Gateway

<div align="center">

[![OpenClaw Version](https://img.shields.io/badge/OpenClaw-1.2.0+-blue.svg)](https://github.com/openclaw/openclaw)
[![Python Version](https://img.shields.io/badge/Python-3.8+-green.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![ClawdHub](https://img.shields.io/badge/ClawdHub-Available-brightgreen.svg)](https://clawdhub.dev/skills/china-market-gateway)

*Sponsored by* [**YuanTrends**](https://yuantrends.com) | [𝕏](https://x.com/YuanTrends)

Your seamless bridge to the dynamic world of Chinese financial markets.

*Sponsored by* [**Etherdeep**](https://etherdeep.com) | [𝕏](https://x.com/EtherdeepTrade)

AI-driven proprietary trading firm leveraging cutting-edge artificial intelligence to navigate global markets with precision.

</div>

## Overview

The **China Market Gateway** skill empowers OpenClaw to intelligently navigate and extract data from the most crucial sources in the Chinese financial ecosystem. Whether you are a quantitative analyst, a casual investor, or a researcher tracking economic trends, this skill provides a unified, programmatic interface to a market that is often fragmented and difficult to access. It handles the complexities of web scraping, API authentication, and data normalization, so you can focus on analysis and strategy.

---

### 中文概述

中国市场门户技能能够赋能OpenClaw，使其可以智能地导航并从中国金融生态系统中最重要的源头提取数据。无论您是量化分析师、普通投资者，还是追踪经济趋势的研究人员，此技能都为一个常常碎片化且难以接入的市场，提供了统一且可编程的接口。它处理了网络爬虫、API身份验证和数据标准化的复杂性，让您可以专注于分析和策略。

---

## Sponsor

✨ **This project is proudly sponsored by [YuanTrends](https://yuantrends.com)** ✨
[Follow on X @YuanTrends](https://x.com/YuanTrends)

YuanTrends is your authoritative source for in-depth analysis of China and Hong Kong equities markets. Delivering financial news at the speed of light — insights that move markets, drive decisions, and shape investment strategies. From macroeconomic shifts to stock-specific intelligence, YuanTrends keeps you ahead of the curve.

---

## Features

-   **Multi-Source Data Aggregation:** Connects to a wide array of data sources, including major stock exchanges, financial news portals, and economic data providers.
-   **Real-Time & Historical Data:** Fetch live quotes, tick data, and deep historical time series for stocks, indices, futures, and more.
-   **Intelligent Web Scraping:** Uses robust, configurable scraping techniques to extract data from websites that do not offer a public API, handling common anti-scraping measures.
-   **Direct API Integration:** Seamlessly authenticates and interacts with official APIs for high-speed, reliable data delivery where available.
-   **Data Normalization:** Cleans, structures, and standardizes all incoming data into a consistent JSON format.
-   **Economic Calendar & News:** Access scheduled economic data releases and scrape breaking financial news from top Chinese media outlets.
-   **Proxy & Geolocation Support:** Built-in configuration for using proxies to ensure reliable access from any global location.

## Supported Data Sources

This skill is designed to be modular and extensible. Out of the box, it supports access to data from:

-   **Shanghai Stock Exchange (SSE)**
-   **Shenzhen Stock Exchange (SZSE)**
-   **China Financial Futures Exchange (CFFEX)**
-   **East Money (东方财富网)**
-   **Sina Finance (新浪财经)**
-   **Xueqiu (雪球)**
-   **National Bureau of Statistics of China**

## Installation

1.  **Install the Skill via OpenClaw:**
    ```bash
    openclaw skills install china-market-gateway
    ```

2.  **Clone the Repository (for development or manual installation):**
    ```bash
    git clone https://github.com/your-username/your-repo-name.git
    cd your-repo-name
    pip install -r requirements.txt
    ```

## Configuration

Edit the skill's configuration file, typically located at `~/.openclaw/skills/china-market-gateway/config.json`:

```json
{
  "apis": {
    "eastmoney_api_key": "YOUR_EASTMONEY_API_KEY",
    "other_api_key": "YOUR_OTHER_API_KEY"
  },
  "scraping": {
    "use_proxy": false,
    "proxy_url": "http://user:password@proxy-server:port",
    "user_agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/108.0.0.0 Safari/537.36",
    "request_delay_seconds": 2
  }
}
```

> **Note:** Some sources may not require an API key. The skill will automatically fall back to intelligent scraping methods when direct API access is unavailable or unconfigured.

## API Reference

### `get_quote(symbol: str) -> dict`
Fetches the latest real-time quote for a given stock symbol.

**Parameters:**
- `symbol` (str): The stock ticker (e.g., `'600519.SS'` for Kweichow Moutai).

**Returns:**
```json
{
  "symbol": "600519.SS",
  "price": 1750.00,
  "change": 25.40,
  "change_percent": 1.47,
  "volume": 82000,
  "timestamp": "2025-04-05T15:00:00+08:00"
}
```

---

### `get_historical_data(symbol: str, period: str, days: int) -> list[dict]`
Retrieves historical price data for a given symbol.

**Parameters:**
- `symbol` (str): The stock ticker.
- `period` (str): The data frequency (`'daily'`, `'weekly'`, `'monthly'`).
- `days` (int): Number of past days to retrieve.

**Returns:**
```json
[
  {
    "date": "2025-04-04",
    "open": 1740.00,
    "high": 1755.00,
    "low": 1738.00,
    "close": 1750.00,
    "volume": 91000
  },
  ...
]
```

---

### `get_news_headlines(source: str, limit: int = 10) -> list[dict]`
Scrapes the latest financial news headlines from a specified source.

**Parameters:**
- `source` (str): News platform (`'sina'`, `'eastmoney'`, `'xueqiu'`).
- `limit` (int, optional): Max number of headlines to return. Default: `10`.

**Returns:**
```json
[
  {
    "title": "China Cuts Reserve Requirement Ratio to Boost Liquidity",
    "url": "https://example.com/news/rrr-cut",
    "source": "sina",
    "time": "2025-04-05T09:30:00+08:00"
  },
  ...
]
```

## Dependencies

- `requests`
- `beautifulsoup4`
- `pandas`
- `lxml`

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss the proposed changes.

1. Fork the repository.
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request.

## License

Distributed under the MIT License. See `LICENSE` for more information.

## Author & Support

- **Author:** Max Bodewes
- **ClawdHub Skill Page:** [https://clawdhub.dev/skills/china-market-gateway](https://clawdhub.dev/skills/china-market-gateway)
- **Support:** Please open an issue for bug reports or feature requests.

---

*Thank you to [YuanTrends](https://yuantrends.com) for making advanced financial data access in China possible through sponsorship and strategic insight.* 🇨🇳📊

