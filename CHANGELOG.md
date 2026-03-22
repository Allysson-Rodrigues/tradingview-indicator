# Changelog

## V1.2.10 (2026-03-10)

- Refactor: sincronização de trace lines e price labels extraída para helpers dedicados.
- Limpeza: funções auxiliares mortas removidas do bloco RSI/HTF.
- Manutenção: redução de duplicação sem alterar lógica visual ou sinais.

## V1.2.9 (2026-03-10)

- UX: trace lines, trace labels e labels HTF agora reaplicam cor, tamanho e espessura em runtime.
- UX: DOW labels sincronizam texto e estilo ao alterar inputs visuais.
- Manutenção: update visual concentrado sem alterar lógica de sinais.

## V1.2.8 (2026-03-10)

- UX: labels e timers HTF agora sincronizam corretamente ao trocar posição, timer e visibilidade.
- UX: tabela RSI é recriada ao mudar a posição para evitar estado visual antigo.
- Refactor: ciclo de vida dos labels HTF extraído para helpers dedicados.
- Hotfix: fluxo HTF e leituras MTF ajustados para compatibilidade com o compilador do Pine v6.

## V1.2.7 (2026-03-10)

- Refactor: orquestração dos grupos HTF centralizada em helpers compartilhados.
- Refactor: critério de elegibilidade dos HTFs reutilizado entre cálculo agregado e renderização.
- Manutenção: avanço de offset HTF extraído para helper único.
- Estabilidade: refactor feito sem alterar a lógica de sinais, FVGs ou alertas.

## V1.2.6 (2026-03-10)

- Refactor: pipeline RSI MTF consolidado com dynamic requests e helper único.
- Performance: `request.security` é evitado quando o TF consultado é o do gráfico.
- Performance: tabela RSI passa a reutilizar células com `table.cell_set_*()`.
- Refactor: leitura FVG MTF centralizada em helper dedicado.
- Limpeza: `UpdateTime` deixa de carregar parâmetro não utilizado.

## V1.2.5 (2026-03-10)

- Bug Fix: timer HTF passa a usar `time_close()` com fallback visual seguro.
- Bug Fix: alertas de novo FVG agora dependem do evento real de inserção.
- Bug Fix: trace anchor `Last Timeframe` aponta para o último HTF efetivamente renderizado.
- UX: `Daily Auto` e `Weekly Auto` respeitam o toggle manual dos HTFs 5 e 6.
- UX: trace lines e labels agora são limpos ao desligar a feature ou zerar HTFs renderizados.

## V1.2.4 (2026-03-09)

- Anti-Repaint: `request.security` agora oferece modo HTF `Confirmado` ou `Tempo Real`.
- Robustez: FVG custom bloqueia timeframe inferior ao gráfico atual.
- Bug Fix: expiração do FVG passa a usar barras do gráfico atual, consistente com TF custom.
- Performance: `request.security` recebe `calc_bars_count` para reduzir custo de histórico.
- UX: inputs dependentes agora são ativados dinamicamente nos grupos EMA, RSI, Tabela e FVG.

## V1.2.3 (2026-03-09)

- Bug Fix: fluxo HTF reordenado para evitar contaminar o candle anterior na virada do período.
- Bug Fix: labels das trace lines agora atualizam texto junto com o preço em tempo real.
- Bug Fix: manutenção/remoção de FVGs percorre toda a lista ativa, respeitando o limite configurado.
- UX: extensão do FVG renomeada como projeção temporal para refletir o comportamento real no eixo X.
- Docs: README alinhado aos recursos realmente implementados no indicador.

## V1.2.2 (2026-02-19)

- Bug Fix: FVG expiração migrada de tempo-relógio para `bar_index` (corrige inflação de idade em mercados com gap noturno, ex: ações).
- Bug Fix: garbage collection de candles HTF ao desativar o grupo.
- Performance: `Reorder` e `Update` restritos a `barstate.isnew` e `barstate.islast`.
- Performance: `FindImbalance` com dirty flag evita recriação total.
- Hotfix: `Monitor` refatorado para evitar warnings de consistência do Pine v6.
- Refactor: variáveis globais de dirty flag removidas, com rastreamento via objeto.

## V1.2.1 (2026-02-14)

- Anti-Repaint: `Monitor` usa `barstate.ishistory` em vez de `barstate.islast`.
- Bug Fix: fallback `nz()` do RSI removido para evitar mistura de dados entre TFs.
- Limpeza: `helper.name` removido de todos os métodos.
- Manutenção: constantes `SEC_1H`, `SEC_4H` e `SEC_1D` extraídas.

## V1.2.0 (2026-02-12)

- Bug Fix: `request.security` desenrolado do loop com 5 chamadas explícitas.
- Bug Fix: `DayofWeek` corrigido com constantes `dayofweek.*`.
- Bug Fix: `str.tonumber` substituído por `timeframe.in_seconds` no `Monitor`.
- Anti-Repaint: `Monitor` agora exige `barstate.isconfirmed` para criar candle.
- Anti-Repaint: mitigação e expiração de FVG apenas em `barstate.isconfirmed`.
- Performance: `var` adicionado a `Settings`, `Helper` e `color_transparent`.
- Robustez: `ValidTimeframe` usa módulo (`n2 % n1 == 0`).
- Robustez: debug table protegida contra `NaN`.

## V1.1.8 (2025-12-20)

- Robustness: zero-division protection in `isExpired`.
- Robustness: bounds checking and fallback for invalid RSI data.
- Robustness: RSI table automatically recreates when changing columns.
- Extensibility: ATR period is now configurable via user input.
- Extensibility: configurable timezone (5 options).
- Extensibility: RSI table timeframes are now dynamic.

## V1.1.6 (2025-12-19)

- Optimization: simplified conditional calculation of RSI levels.
- Refactoring: RSI cache only calculates levels when visual lines are active.
- UX: debug table version updated to reflect current release.

## V1.1.5 (2025-12-18)

- New: checkboxes to toggle RSI columns in the table.
- Improved UX: independent control for RSI display and levels.

## V1.1.4 (2025-12-18)

- Optimization: `RSI_ALPHA` pre-calculated as a `var` constant.
- Fix: `f_fvg_detect()` now normalizes gap size by ATR when ATR Auto is active.
- Prevents false positives on volatile or low-priced assets.
- Logical Consistency: threshold and gap size now use the same unit of measure.

## V1.1.3 (2025-12-17)

- Tooltips added to all 60+ indicator inputs.
- Improved inline documentation for better TradingView UX.
- Clear descriptions for every parameter.

## V1.1.2 (2025-12-16)

- Critical Fix: `box.set_top` e `box.set_bottom` agora usam `math.max` e `math.min`.
- Bug Fix: rendering corrigido para candles HTF bullish.
- Improvement: candle body sempre usa coordenadas corretas.

## V1.1.1 (2025-12-16)

- Historical timer changed from `---` to `--:--`.
- Optimized `FindImbalance`: now processes only on new HTF candles.
- Performance: removed unnecessary `box.copy()` e `box.delete()`.
- Tracking: idx-based tracking added to prevent imbalance duplication.
- Visual Sync: FVG boxes now follow HTF candle movement.
- Fix: condition `FVG >= 3` now detects cases with exactly 3 candles.

## V1.1 (2025-12-15)

- Removed `scale=scale.none` for better candle visualization.
- Timer changed from `n/a` to `---` on historical data.
- Added comprehensive documentation.

## V1.0 (2025-12-14)

- Initial release: ICT HTF Candles + FVG + RSI + MTF merge.
- RSI cache system implemented.
- Added debug mode for FVG.
- Configured alerts.
