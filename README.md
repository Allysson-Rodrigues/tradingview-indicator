# TradingView Analytical Tools

This repository contains algorithmic trading tools and custom Pine Script scripts designed for structured technical analysis. The primary focus is code efficiency and logical rigor in market data interpretation.

---

### Featured Script: ICT FVG + RSI (v1.2.2)

A comprehensive implementation of Inner Circle Trader (ICT) concepts, specifically targeting Fair Value Gaps (FVG) and Relative Strength Index (RSI) divergences.

#### Technical Specifications
- **Core Logic**: Detects Fair Value Gaps (FVG) across multiple timeframes to identify institutional liquidity voids.
- **RSI Integration**: Filters signals using momentum divergences to increase probability.
- **Risk Management**: Integrated calculation of displacement and breakout levels.

#### Key Parameters
- `FVG Transparency`: Adjusts the visibility of historical gaps.
- `RSI Length`: Standard 14-period momentum calculation.
- `Show Broken Gaps`: Toggles display of filled liquidity voids.

---

### Development Principles
1. **Performance**: Optimized for minimal repainting and low computational overhead.
2. **Clarity**: Modular Pine Script structure for easy parameter tuning.
3. **Accuracy**: Precise detection of Price Action patterns (ICT Methodology).

---

**Allysson Rodrigues**
Backend Developer | Algorithmic Trader
