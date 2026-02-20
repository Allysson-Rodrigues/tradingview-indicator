# ICT + FVG + RSI for TradingView

An advanced multi-timeframe analytical engine developed in Pine Script v6. This tool integrates institutional order flow concepts with momentum analysis and fair value gap detection into a high-performance execution dashboard.

## Overview

The indicator is engineered to provide high-fidelity market context for active traders, minimizing visual noise while maintaining computational efficiency on high-frequency charts.

### Technical Methodology
- **Inner Circle Trader (ICT) Framework:** Focus on institutional liquidity and order flow.
- **Fair Value Gaps (FVG):** Systematic identification and tracking of price imbalances.
- **Multi-Timeframe (MTF) Analysis:** Real-time correlation across distinct time horizons.
- **RSI Momentum:** Relative strength index cache system for multi-period momentum tracking.

## Technical Specifications

- **HTF Candle Projection:** Visualizes up to 6 higher timeframes concurrently.
- **Automated FVG Management:** Dynamic detection with proprietary mitigation and expiration logic.
- **MTF RSI Matrix:** Real-time dashboard with inverse RSI target price calculations.
- **Adaptive Thresholds:** Parameters derived from volatility (ATR) or timeframe-specific scaling.
- **Trend Filtering:** Integrated Exponential Moving Averages (EMA) with configurable sources.
- **Zero-Latency Execution:** Optimized for minimal impact on browser and chart performance.
- **Audit & Alert System:** Granular notifications for gap formation, mitigation, and momentum extremes.

## Technical Infrastructure

For comprehensive details on logic implementation, custom types (UDTs), and anti-repaint protocols, refer to the [Technical Architecture Documentation](.agent/ARCHITECTURE.md).

## Deployment

1. Initialize the **Pine Editor** within your TradingView terminal.
2. Copy the source code from [src/ict_fvg_rsi_v1.2.2.pine](src/ict_fvg_rsi_v1.2.2.pine).
3. Append the script to your chart and initialize via the **Add to Chart** command.
4. Calibrate parameters via the **Inputs** interface based on specific asset volatility.

### Recommended Configurations
- **Scalping:** 1m/3m/5m horizons.
- **Intraday:** 5m/15m execution with 1H/4H context.
- **Swing:** 1H/4H execution with Daily/Weekly context.

## Best Practices

- **Execution Confluence:** Prioritize entries where FVG formation aligns with RSI momentum and HTF trend.
- **Dynamic Calibration:** Adjust gap thresholds based on the specific asset's Average True Range.
- **Analytical Bias:** This tool is designed to support discretionary decision-making, not for autonomous execution without human verification.

## Versioning & Support

- **Current Release:** v1.2.2
- **Compiler:** Pine Script v6
- **Lead Developer:** Allysson Rodrigues ([GitHub](https://github.com/Allysson-Rodrigues))

---

### Legal Disclaimer
This software is provided for research and educational purposes. Trading financial instruments carries high risk. The author holds no liability for financial outcomes resulting from the use of this technical tool.

### License
© Allysson Rodrigues. Proprietary software for personal and educational use.
