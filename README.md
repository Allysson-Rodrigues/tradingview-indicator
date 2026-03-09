# TradingView Analytical Tools

This repository contains algorithmic trading tools and custom Pine Script scripts designed for structured technical analysis. The primary focus is code efficiency and logical rigor in market data interpretation.

---

### Featured Script: ICT FVG + RSI (v1.2.3)

A comprehensive implementation of Inner Circle Trader (ICT) concepts, specifically targeting Fair Value Gaps (FVG), multi-timeframe candle mapping and Relative Strength Index (RSI) target levels.

#### Technical Specifications
- **Core Logic**: Detects Fair Value Gaps (FVG) across multiple timeframes to identify institutional liquidity voids.
- **RSI Integration**: Calculates projected price levels for configurable RSI thresholds and renders an MTF RSI table.
- **Visual Structure**: Projects HTF candles, labels, timers and imbalance zones directly over the chart.

#### Key Parameters
- `Threshold ATR Auto`: Normalizes FVG detection with ATR for better cross-asset behavior.
- `Mitigação`: Defines when a FVG is considered filled (25%, 50% or 100%).
- `Extensão Temporal`: Controls how far FVG boxes are projected on the time axis.
- `RSI Length`: Standard 14-period momentum calculation.
- `Tabela RSI MTF`: Displays RSI values and projected target prices for selected timeframes.

---

### Development Principles
1. **Performance**: Optimized for minimal repainting and low computational overhead.
2. **Clarity**: Modular Pine Script structure for easy parameter tuning.
3. **Accuracy**: Precise detection of Price Action patterns (ICT Methodology).

---

**Allysson Rodrigues**
Algorithmic Trader
