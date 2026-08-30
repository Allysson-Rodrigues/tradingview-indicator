# TradingView Analytical Tools

TradingView-focused repository for Pine Script indicators built around structured technical analysis, price imbalance mapping, and multi-timeframe context.

## Featured indicator

### ICT FVG + RSI (v1.2.12)

Main capabilities:

- Fair Value Gap detection across multiple timeframes
- Higher-timeframe candle projection on the active chart
- Dynamic-request MTF pipeline for RSI and FVG context reads
- Shared HTF orchestration helpers to reduce maintenance risk
- HTF labels and timers synchronized safely when runtime options change
- Trace lines, trace labels e DOW labels reagem corretamente a mudanças visuais em runtime
- Sync de trace lines e price labels concentrado em helpers para reduzir manutenção
- RSI target level projections for configurable thresholds
- Optional MTF RSI table for faster discretionary review
- RSI table recreation when the chart corner changes
- Explicit `Confirmado` or `Tempo Real` handling for HTF `request.security()` data

Key controls exposed to the user:

- `Threshold ATR Auto`
- `Mitigação`
- `Extensão Temporal`
- `Modo Dados HTF`
- `RSI Length`
- `Tabela RSI MTF`

## Repository layout

```text
.
├── src/ict_fvg_rsi_v1.2.12.pine  Main Pine Script source
├── CHANGELOG.md                 Versioned release history
├── LICENSE
└── README.md
```

## Validation and release model

This repository does not depend on a backend, package manager, or environment variables. The current operational workflow is:

1. Evolve the Pine Script source in `src/`
2. Validate behavior manually on TradingView charts
3. Record every shipped change in [CHANGELOG.md](./CHANGELOG.md)
4. Publish the updated script version on TradingView

That keeps the repository honest about its maturity model: versioned source control and release history are in place, while runtime validation remains chart-driven and manual.

## Design principles

1. Performance: low-overhead execution and reduced unnecessary recalculation
2. Clarity: modular structure and explicit configuration points
3. Accuracy: careful handling of multi-timeframe state and imbalance logic

## Notes on deployment

For Pine Script projects, delivery happens inside TradingView itself. There is no separate infrastructure deploy step; the source code here is the versioned canonical reference, and publication occurs by copying the script into the TradingView editor/publishing flow.

## License

See [LICENSE](./LICENSE).
