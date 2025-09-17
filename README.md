# Trading Bot Framework

A Python framework for building automated trading bots for cryptocurrency exchanges. This library provides the foundational components to create your own trading strategies without dealing with low-level API complexities.

## Features

- **Exchange API Abstraction** - Unified interface for multiple cryptocurrency exchanges
- **Strategy Framework** - Easy-to-implement pattern for trading strategies
- **Risk Management** - Built-in tools for position sizing and risk control
- **Backtesting Support** - Historical data testing capabilities
- **Event-Driven Architecture** - Responsive to market data updates

## Supported Exchanges

- Binance
- Kraken
- Coinbase Pro
- (Additional exchanges can be easily added)

## Quick Start

### Installation

```bash
pip install crypto-trading-framework
```

### Basic Usage

```python
from trading_framework import BotBase, ExchangeAPI
from trading_framework.strategies import MovingAverageCrossover

# Initialize exchange connection
exchange = ExchangeAPI('binance', api_key='your_key', secret='your_secret')

# Create trading bot with strategy
bot = BotBase(
    exchange=exchange,
    strategy=MovingAverageCrossover(fast_period=10, slow_period=20),
    symbols=['BTC/USDT', 'ETH/USDT'],
    initial_balance=1000
)

# Start trading
bot.run()
```

### Creating Custom Strategies

```python
from trading_framework.strategies import BaseStrategy

class MyCustomStrategy(BaseStrategy):
    def __init__(self, rsi_period=14, oversold=30, overbought=70):
        self.rsi_period = rsi_period
        self.oversold = oversold
        self.overbought = overbought
        
    def calculate_signals(self, data):
        # Your trading logic here
        rsi = self.calculate_rsi(data, self.rsi_period)
        
        if rsi < self.oversold:
            return 'BUY'
        elif rsi > self.overbought:
            return 'SELL'
        
        return 'HOLD'
```

## Documentation

- [Getting Started Guide](docs/getting-started.md)
- [API Reference](docs/api-reference.md)
- [Strategy Development](docs/strategy-development.md)
- [Risk Management](docs/risk-management.md)

## Contributing

We welcome contributions! Please see our [Contributing Guidelines](CONTRIBUTING.md) for details.

## Disclaimer

Cryptocurrency trading involves significant risk and may not be suitable for all investors. This software is provided for educational purposes only. Past performance is not indicative of future results.

## License

MIT License - see [LICENSE](LICENSE) file for details.

## Support

If you find this framework useful, consider supporting its development:

- BTC: `1A2b3C4d5E6f7G8h9I0jK1L2mN3oP4qR5sT6u`
- ETH: `0x1234567890abcdef1234567890abcdef12345678`
- LTC: `Labcdef1234567890abcdef1234567890abcdef12`
