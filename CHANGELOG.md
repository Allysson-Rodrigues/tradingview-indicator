// ═══════════════════════════════════════════════════════════════════════════
// 📜 CHANGELOG
// ═══════════════════════════════════════════════════════════════════════════
// V1.2.2 (2026-02-19)
//    - Bug Fix: FVG expiração migrada de tempo-relógio para bar_index
//      (corrige inflação de idade em mercados com gap noturno, ex: ações)
//    - Bug Fix: Garbage collection de candles HTF ao desativar o grupo
//    - Performance: Reorder/Update restritos a barstate.isnew/islast
//    - Performance: FindImbalance com dirty flag — evita recriação total
//    - Hotfix: Monitor refatorado para evitar warnings de consistência do Pine v6
//    - Refactor: Variáveis globais de dirty flag removidas (rastreamento via objeto)

// V1.2.1 (2026-02-14)
//    - Anti-Repaint: Monitor usa barstate.ishistory em vez de barstate.islast
//    - Bug Fix: RSI fallback nz() removido — evita mistura de dados entre TFs
//    - Limpeza: helper.name (código morto) removido de todos os métodos
//    - Manutenção: Constantes SEC_1H, SEC_4H, SEC_1D extraídas
//
// V1.2.0 (2026-02-12)
//    - Bug Fix: request.security desenrolado do loop (5 chamadas explícitas)
//    - Bug Fix: DayofWeek corrigido (usa constantes dayofweek.monday etc.)
//    - Bug Fix: str.tonumber substituído por timeframe.in_seconds no Monitor
//    - Anti-Repaint: Monitor agora exige barstate.isconfirmed para criar candle
//    - Anti-Repaint: Mitigação/expiração FVG apenas em barstate.isconfirmed
//    - Performance: var adicionado a Settings, Helper e color_transparent
//    - Robustez: ValidTimeframe usa modulo (n2 % n1 == 0)
//    - Robustez: Debug table protegido contra NaN (nz/na checks)
//
// V1.1.8 (2025-12-20)
//    - Robustness: Zero-division protection in isExpired method.
//    - Robustness: Bounds checking and fallback for invalid RSI data.
//    - Robustness: RSI table automatically recreates when changing columns.
//    - Extensibility: ATR Period is now configurable via user input.
//    - Extensibility: Configurable Timezone (5 options).
//    - Extensibility: RSI table timeframes are now dynamic.
//
// V1.1.6 (2025-12-19)
//    - Optimization: Simplified conditional calculation of RSI levels.
//    - Refactoring: RSI Cache only calculates levels when visual lines are active.
//    - UX: Updated Debug table version to reflect current release.
//
// V1.1.5 (2025-12-18)
//    - New: Checkboxes to toggle RSI columns in the table.
//    - Improved UX: Independent control for RSI display and levels.
//
// V1.1.4 (2025-12-18)
//    - Optimization: RSI_ALPHA pre-calculated as a 'var' constant.
//    - Fix: f_fvg_detect() now normalizes gap size by ATR when ATR Auto is active.
//    - Prevents false positives on volatile or low-priced assets.
//    - Logical Consistency: Threshold and gap size now use the same unit of measure.
//
// V1.1.3 (2025-12-17)
//    - Tooltips added to all 60+ indicator inputs.
//    - Improved inline documentation for better TradingView UX.
//    - Clear descriptions for every parameter.
//
// V1.1.2 (2025-12-16)
//    - Critical Fix: box.set_top/bottom now uses math.max/min.
//    - Bugfix: Corrected rendering for bullish HTF candles.
//    - Improvement: Candle body now always uses correct coordinates.
//
// V1.1.1 (2025-12-16)
//    - Historical timer changed from '---' to '--:--' (time format).
//    - Optimized FindImbalance: Now processes only on new HTF candles.
//    - Performance: Removed unnecessary box.copy() + box.delete() calls.
//    - Tracking: Implemented idx-based tracking to prevent imbalance duplication.
//    - Visual Sync: FVG boxes now follow HTF candle movement.
//    - Fix: Condition FVG >= 3 (detects with exactly 3 candles).
//
// V1.1 (2025-12-15)
//    - Removed scale=scale.none for better candle visualization.
//    - Timer changed from 'n/a' to '---' on historical data.
//    - Added comprehensive documentation.
//
// V1.0 (2025-12-14)
//    - Initial Release: ICT HTF Candles + FVG + RSI + MTF merge.
//    - RSI Cache system implemented.
//    - Added Debug mode for FVG.
//    - Configured alerts.