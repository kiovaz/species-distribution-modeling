# Descrição

Este projeto implementa um pipeline completo para análise de distribuição e abundância de espécies arbóreas, comparando duas abordagens complementares:

- **MaxEnt**: Modelo de adequabilidade ambiental baseado em entropia máxima (valores 0-1)
- **IDW (Inverse Distance Weighting)**: Interpolação espacial para estimar abundância real em parcelas

## Funcionalidades

- Limpeza e validação de dados de coletas naturais (NHCs)
- Remoção de duplicatas espaciais usando grid de 0.5°
- Implementação manual do IDW com raio de busca de 3.0° e até 150 vizinhos
- Análise estatística usando correlação de Spearman (ρ)
- Visualização comparativa com scatter plot e linha de tendência

## Metodologia

Baseado em **Gomes et al. (2018)**, este projeto replica a metodologia de validação de modelos de distribuição de espécies usando dados de abundância observada em campo.