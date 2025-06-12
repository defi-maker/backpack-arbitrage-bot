# Backpack Liquidation Arbitrage Bot

This Python bot is designed for automated liquidation arbitrage on the Backpack exchange's perpetual markets (e.g., SOL_USDC_PERP). It implements a delta-neutral strategy by simultaneously opening a short position on one sub-account and a long position on another sub-account. The core innovation lies in setting take-profit orders for each position based on the *estimated liquidation price of the opposing position*, aiming to capture profits efficiently during market volatility and liquidation cascades. The bot also automates initial fund deposits and post-trade fund sweeping to optimize capital management and minimize transaction costs.

## Features

*   **Delta-Neutral Strategy**: Opens simultaneous long and short positions to hedge market exposure.
*   **Strategic Order Placement**: Utilizes maker limit orders for the short position (to potentially earn maker rebates) and market orders for the long position (for immediate execution).
*   **Dynamic Take-Profit**: Sets take-profit limit orders for each position based on the *estimated liquidation price of the counterparty position*, with configurable offsets.
*   **Automated Fund Management**: Handles initial USDC deposits from a main account to sub-accounts and sweeps all remaining funds back to the main account after positions are closed.
*   **Robustness**: Includes retry mechanisms for order placement, position verification, and API calls, along with comprehensive logging for monitoring.
*   **Configurable**: Parameters like leverage, maker/take-profit offsets, order timeouts, and operational delays are fully customizable via `config.yaml`.

## Installation

1.  Clone the repository:
    ```bash
    git clone https://github.com/defi-maker/backpack-arbitrage-bot
    cd backpack-arbitrage-bot
    ```
2.  Install dependencies using uv:
    ```bash
    uv sync
    ```

## Configuration

Copy `config.yaml.example` to `config.yaml` and fill in your API keys, secrets, and desired parameters.

## Usage

Run the bot:
    ```bash
    uv run main.py
    ```
