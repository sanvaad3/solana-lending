# Solana Lending Protocol

A decentralized lending protocol built on Solana that enables users to deposit collateral, borrow assets, and participate in liquidations with real-time price feeds via Pyth Network.

## Features

- **Multi-Asset Support**: Deposit and borrow SOL and USDC tokens
- **Collateralized Lending**: Secure borrowing backed by deposited collateral
- **Real-Time Price Feeds**: Integration with Pyth Network for accurate asset pricing
- **Liquidation System**: Automated liquidation of undercollateralized positions
- **Health Factor Monitoring**: Track account health and borrowing capacity
- **Interest Rate Management**: Dynamic interest rate calculations

## Core Functionality

### User Operations
- **Deposit**: Add SOL or USDC as collateral to earn interest
- **Withdraw**: Remove deposited assets (subject to collateralization requirements)
- **Borrow**: Take loans against deposited collateral
- **Repay**: Pay back borrowed amounts plus accrued interest
- **Liquidate**: Liquidate undercollateralized positions for profit

### Admin Operations
- **Initialize Banks**: Create lending pools for different assets
- **Configure Parameters**: Set liquidation thresholds, LTV ratios, and interest rates

## Architecture

### Programs
- **Lending Protocol** (`CdZeD33fXsAHfZYS8jdxg4qHgXYJwBQ1Bv6GJyETtLST`): Core lending logic

### Key Components
- **Bank Account**: Manages liquidity pools for each asset type
- **User Account**: Tracks individual user positions and health metrics
- **Price Feeds**: Pyth Network integration for real-time asset valuations

### State Management
- **Bank State**: Total deposits, borrows, shares, and risk parameters
- **User State**: Individual deposit/borrow positions and health factor

## Prerequisites

- [Rust](https://rustup.rs/) 1.70+
- [Solana CLI](https://docs.solana.com/cli/install-solana-cli-tools) 1.16+
- [Anchor Framework](https://www.anchor-lang.com/docs/installation) 0.30.1
- [Node.js](https://nodejs.org/) 18+
- [Yarn](https://yarnpkg.com/)

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd solana-lending-main
```

2. Install dependencies:
```bash
yarn install
```

3. Build the program:
```bash
anchor build
```

## Testing

Run the comprehensive test suite:

```bash
anchor test
```

The tests include:
- Bank initialization and funding
- User account creation
- Deposit and withdrawal operations
- Borrowing and repayment flows
- Liquidation scenarios

## Development

### Code Formatting
```bash
# Check formatting
yarn lint

# Fix formatting
yarn lint:fix
```

### Project Structure
```
├── programs/lending/          # Core Rust program
│   ├── src/
│   │   ├── instructions/      # Program instructions
│   │   ├── state.rs          # Account structures
│   │   ├── error.rs          # Custom errors
│   │   └── lib.rs            # Program entry point
├── tests/                     # TypeScript tests
├── migrations/               # Deployment scripts
└── bankrun-utils/           # Testing utilities
```

## Configuration

### Anchor.toml
- Configured for localnet development
- Program ID: `CdZeD33fXsAHfZYS8jdxg4qHgXYJwBQ1Bv6GJyETtLST`
- Test timeout: 1,000,000ms for complex operations

### Risk Parameters
- **Liquidation Threshold**: Maximum borrowing ratio before liquidation
- **Max LTV**: Maximum loan-to-value ratio for new borrows
- **Health Factor**: Calculated based on collateral value vs borrowed amount

## Integration

### Price Feeds
The protocol integrates with Pyth Network for real-time price data:
- SOL/USD price feed for SOL asset valuations
- Configurable price feed addresses for different networks

### Token Support
- **SOL**: Native Solana token
- **USDC**: USD Coin stablecoin
- Extensible architecture for additional SPL tokens

## Security Considerations

- All operations validate user permissions and account ownership
- Liquidation thresholds prevent excessive risk exposure
- Interest calculations use precise mathematical operations
- Price feed validation ensures accurate asset valuations

## License

ISC

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Run tests and linting
5. Submit a pull request

For issues and feature requests, please create an issue in the repository.
