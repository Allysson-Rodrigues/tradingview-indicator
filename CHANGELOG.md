// ═══════════════════════════════════════════════════════════════════════════
// 📜 CHANGELOG
// ═══════════════════════════════════════════════════════════════════════════
// V1.1.8 (2025-12-20)
//    - Robustez: Proteção contra divisão por zero no método isExpired
//    - Robustez: Bounds checking e fallback para dados RSI inválidos
//    - Robustez: Tabela RSI recria automaticamente ao mudar colunas
//    - Extensibilidade: ATR Period agora é configurável via input
//    - Extensibilidade: Fuso horário configurável (5 opções)
//    - Extensibilidade: Timeframes da tabela RSI agora são dinâmicos
//
// V1.1.6 (2025-12-19)
//    - Otimização: Cálculo condicional simplificado de níveis RSI
//    - Refatoração: Cache RSI só calcula níveis com linhas visuais ativas
//    - UX: Versão do Debug table atualizada para refletir versão atual
//
// V1.1.5 (2025-12-18)
//    - Novo: Checkboxes para ativar/desativar colunas RSI na tabela
//    - UX melhorada: controle independente de exibição e nível RSI
//
// V1.1.4 (2025-12-18)
//    - Otimização: RSI_ALPHA pré-calculado como constante var
//    - Correção: f_fvg_detect() agora normaliza gap size pelo ATR quando ATR Auto está ativo
//    - Evita falsos positivos em ativos voláteis ou com preços baixos
//    - Consistência lógica: threshold e gap size usam mesma unidade de medida
//
// V1.1.3 (2025-12-17)
//    - Tooltips adicionados a todos os 60+ inputs do indicador
//    - Documentação inline melhorada para melhor UX no TradingView
//    - Descrições claras em português para cada parâmetro
//
// V1.1.2 (2025-12-16)
//    - Correção crítica: box.set_top/bottom agora usa math.max/min
//    - Bug corrigido: candles HTF de alta renderizam corretamente
//    - Melhoria: corpo do candle sempre com coordenadas corretas
//
// V1.1.1 (2025-12-16)
//    - Timer histórico alterado de '---' para '--:--' (formato tempo)
//    - FindImbalance otimizado: processa apenas em novo candle HTF
//    - Removido box.copy() + box.delete() desnecessário (performance)
//    - Tracking via idx para evitar duplicação de imbalances
//    - Sincronização visual: FVG boxes acompanham movimento dos candles HTF
//    - Correção: condição FVG >= 3 (detecta com exatamente 3 candles)
//
// V1.1 (2025-12-15)
//    - Removido scale=scale.none para melhor visualização dos candles
//    - Timer alterado de 'n/a' para '---' em dados históricos
//    - Documentação completa adicionada
//
// V1.0 (2025-12-14)
//    - Fusão inicial: ICT HTF Candles + FVG + RSI + MTF
//    - Sistema de cache RSI implementado
//    - Debug mode para FVG adicionado
//    - Alertas configurados