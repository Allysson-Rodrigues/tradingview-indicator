# Plano de Melhorias Futuras - ICT + FVG + RSI V1.2.10

Data: 2026-03-10
Escopo: registrar uma avaliacao tecnica objetiva do projeto e um plano de implementacao para execucao futura.
Status: documento de planejamento, sem alteracao funcional no indicador.

## Resumo Executivo

- Nota geral atual: `8/10`
- Maturidade: boa para um projeto Pine Script standalone, com historico de releases consistente e preocupacao real com anti-repaint, MTF e UX.
- Principal limitacao atual: concentracao excessiva de responsabilidade em um unico arquivo Pine, elevando custo de manutencao e risco de regressao.

## Base da Avaliacao

Pontos fortes observados:

- Politica HTF explicitamente separada entre `Confirmado` e `Tempo Real`.
- Uso consistente de helpers para partes sensiveis de sincronizacao visual.
- Historico de release disciplinado no `CHANGELOG.md`.
- README alinhado ao modelo operacional real do projeto: evolucao local e validacao manual no TradingView.
- Correcao recente de pontos importantes, como timer via `time_close()` e alertas de FVG baseados em evento real.

Pontos que reduzem a nota:

- Arquivo principal monolitico e grande, reunindo configuracao, estado, calculo, renderizacao e alertas.
- Duplicacao estrutural ainda presente no pipeline de HTFs e nas leituras RSI MTF.
- Projecao temporal dos FVGs ainda depende de aproximacao por tempo-relogio.
- Validacao ainda e exclusivamente manual e visual.
- Documento de analise tecnica existente esta defasado em relacao a versao atual.

## Criterios da Nota

### Correcao funcional: 8/10

- A base esta estavel e houve correcoes recentes relevantes.
- Ainda existem zonas com maior risco de regressao por acoplamento estrutural.

### Anti-repaint e MTF: 8.5/10

- O contrato `Confirmado` vs `Tempo Real` esta tecnicamente bem direcionado.
- O uso de `request.security()` foi encapsulado de forma mais madura do que o normal em scripts Pine.

### Performance: 7.5/10

- Ha esforco visivel para limitar recalculo e controlar custo de historico.
- Ainda existe espaco para simplificar fluxos e reduzir caminhos redundantes.

### Manutenibilidade: 6.5/10

- O codigo tem boas extracoes locais, mas o arquivo unico continua caro para evoluir.
- O custo cognitivo ainda e alto para qualquer mudanca transversal.

### UX e configurabilidade: 8.5/10

- O indicador oferece boa flexibilidade e controle visual.
- A experiencia do usuario final esta acima da media para Pine Script.

## Objetivo do Plano

Melhorar a capacidade de evolucao do indicador sem alterar indevidamente a logica de sinais, o comportamento MTF ou a experiencia visual que ja foi estabilizada nas versoes recentes.

## Estrategia de Implementacao

Ordem de prioridade:

1. Proteger comportamento atual com uma baseline de validacao.
2. Reduzir duplicacao estrutural.
3. Desacoplar contratos de dados HTF/RSI/FVG.
4. Refatorar a camada visual sem alterar semantica funcional.
5. Atualizar documentacao tecnica para evitar drift futuro.

## Plano Priorizado

### P0 - Baseline de Validacao Antes de Refatorar

Objetivo:

- Definir como provar que o indicador continua correto antes de iniciar refactors maiores.

Entregas:

- Checklist manual fixo para validacao em TradingView.
- Matriz de cenarios cobrindo:
  - HTF em modo `Confirmado`
  - HTF em modo `Tempo Real`
  - FVG no timeframe atual
  - FVG em timeframe custom superior
  - Trace lines com `First Timeframe`
  - Trace lines com `Last Timeframe`
  - tabela RSI com mudanca de posicao e colunas
  - ligamento e desligamento de grupos HTF em runtime

Criterio de pronto:

- Cada mudanca futura deve ser comparada contra a mesma bateria manual de validacao.

Risco mitigado:

- Refatorar estrutura e quebrar comportamento visual ou alertas sem perceber.

### P1 - Refactor Estrutural do Nucleo HTF

Objetivo:

- Reduzir o custo de manutencao da parte mais central do indicador.

Implementacoes sugeridas:

- Consolidar a definicao dos 6 HTFs em uma estrutura mais orientada a dados.
- Reduzir repeticao entre `SettingsHTF1..6`, `candles_1..6`, `imbalances_1..6`, `htf1..6`.
- Isolar melhor os contratos de:
  - habilitacao do HTF
  - renderizacao permitida
  - calculo de offset
  - limpeza de estado visual

Resultado esperado:

- Menor risco de corrigir um HTF e esquecer os demais.

### P1 - Consolidacao do Pipeline RSI MTF

Objetivo:

- Tornar o fluxo RSI MTF mais barato de manter e menos sujeito a divergencia.

Implementacoes sugeridas:

- Centralizar configuracao de slots RSI em estrutura unica.
- Encapsular nome exibido, timeframe, valor RSI, close, AUC e ADC por slot.
- Avaliar migracao do trecho de atribuicoes explicitas para pipeline orientado a arrays, desde que o compilador Pine mantenha consistencia.

Resultado esperado:

- Menos repeticao manual.
- Mais facilidade para adicionar ou remover slots no futuro.

Observacao:

- Mesmo que a leitura continue explicitada por compatibilidade do Pine, o contrato logico pode ser centralizado.

### P1 - Contrato Unificado para Leitura HTF

Objetivo:

- Padronizar a politica de leitura HTF entre RSI, FVG e futuros recursos.

Implementacoes sugeridas:

- Criar helpers conceituais claros para:
  - leitura confirmada
  - leitura realtime
  - leitura local no mesmo timeframe do grafico
- Padronizar o criterio de quando `lookahead_on` e `lookahead_off` devem ser usados.

Resultado esperado:

- Menor chance de repaint acidental.
- Contrato tecnico mais claro para futuras manutencoes.

### P2 - Refino da Camada FVG

Objetivo:

- Tornar a logica FVG mais coesa e mais previsivel entre ativos e contextos diferentes.

Implementacoes sugeridas:

- Separar mais claramente:
  - deteccao
  - projecao visual
  - mitigacao
  - expiracao
- Revisar a projecao temporal baseada em tempo-relogio e documentar claramente sua limitacao.
- Avaliar uma estrategia visual alternativa para ativos com sessao, se a experiencia atual se mostrar inconsistente.

Resultado esperado:

- Menor ambiguidade entre comportamento funcional e comportamento visual.

### P2 - Ciclo de Vida Visual e Limpeza de Estado

Objetivo:

- Garantir que qualquer mudanca de input em runtime tenha sincronizacao visual previsivel.

Implementacoes sugeridas:

- Consolidar ainda mais helpers de `box`, `line`, `label` e `table`.
- Padronizar pontos de criacao, update e remocao.
- Tratar limpeza de estado como fluxo de primeira classe, nao apenas como remendo por feature.

Resultado esperado:

- Menos residuos visuais.
- Menos hotfixes de UX em releases futuras.

### P2 - Variante de Validacao Tecnica

Objetivo:

- Diminuir dependencia exclusiva de inspeção visual manual.

Implementacoes sugeridas:

- Criar uma variante de apoio para validacao futura, como:
  - modo debug mais deterministico
  - versao auxiliar com foco em observabilidade
  - ou uma estrategia de apoio apenas para comparacao de eventos

Resultado esperado:

- Mais confianca em alteracoes estruturais futuras.

### P3 - Higiene Documental

Objetivo:

- Evitar drift entre codigo, changelog e documentos auxiliares.

Implementacoes sugeridas:

- Atualizar a analise tecnica para a versao atual.
- Manter README, changelog e analise tecnica coerentes a cada marco relevante.
- Registrar explicitamente limitacoes conhecidas da versao.

Resultado esperado:

- Onboarding tecnico mais rapido.
- Menor risco de decisoes baseadas em documentacao antiga.

## Backlog Sugerido por Sprint

### Sprint 1

- Criar baseline manual de validacao.
- Atualizar documento de analise tecnica para a versao atual.
- Mapear pontos de duplicacao estrutural que precisam ser atacados primeiro.

### Sprint 2

- Refatorar o nucleo HTF.
- Consolidar contratos de leitura HTF.

### Sprint 3

- Refatorar pipeline RSI MTF.
- Revisar ciclo de vida da tabela RSI e sincronizacao visual.

### Sprint 4

- Refinar a camada FVG.
- Melhorar observabilidade e variante de validacao tecnica.

## Matriz Minima de Validacao Futura

Cada mudanca relevante deve ser validada, no minimo, nestes cenarios:

1. Grafico em timeframe baixo com HTFs 1 a 4 ativos.
2. Grafico em `1H` com `Daily Auto` ativo.
3. Grafico em `4H` com `Weekly Auto` ativo.
4. Modo HTF `Confirmado`.
5. Modo HTF `Tempo Real`.
6. FVG no timeframe do grafico.
7. FVG em timeframe custom superior.
8. Liga/desliga de trace lines e price labels em runtime.
9. Mudanca de posicao da tabela RSI.
10. Mudanca de cores, tamanhos e estilos sem reload do script.

## Escopo Deliberadamente Fora Deste Plano

- Medicao de edge operacional da estrategia.
- Backtests de performance financeira.
- Automacao externa fora do TradingView.
- Conversao do projeto para uma arquitetura multi-arquivo fora das limitacoes praticas do Pine.

## Definicao de Sucesso

Este plano tera sido bem executado quando:

- o custo de manutencao do arquivo principal cair perceptivelmente;
- o comportamento MTF permanecer estavel;
- o indicador continuar sem regressao visual relevante;
- a documentacao refletir com precisao a versao publicada;
- e qualquer evolucao futura puder ser validada com um checklist previsivel.

## Referencias de Contexto

- `README.md`
- `CHANGELOG.md`
- `src/ict_fvg_rsi_v1.2.10.pine`
- `ANALISE_TECNICA_INDICADOR_V1.2.4.md`
