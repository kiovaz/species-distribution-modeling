# Análise Comparativa de Modelos de Distribuição de Espécies

Este projeto implementa um pipeline computacional para análise de distribuição e abundância de espécies arbóreas na Amazônia, replicando a metodologia descrita no artigo *"Species Distribution Modelling: Contrasting presence-only models with plot abundance data"* (Gomes et al., Scientific Reports, 2018).

> **Nota:** Este projeto utiliza **dados simulados** para demonstração da metodologia. Os dados de coletas (NHCs) e parcelas de abundância são gerados artificialmente para fins educacionais e de validação do pipeline.

## Objetivo

Validar a correlação entre modelos de adequabilidade ambiental (MaxEnt) e abundância real observada em campo (IDW), contrastando o **Nicho Fundamental** (onde a espécie *pode* viver) com o **Nicho Realizado** (onde ela *realmente* é abundante).

## 🛠️ Funcionalidades

### 1. Pipeline de Limpeza de Dados
Implementação de regras para mitigar o viés de coleta comum em dados de herbários (NHCs):
- **Sanitização:** Remoção de coordenadas nulas ou inconsistentes (latitude = 0.0 ou lat == lon)
- **Filtro Espacial:** Eliminação de duplicatas usando grid de resolução **0.5°** para reduzir *collectors' bias*

### 2. Algoritmo IDW (Inverse Distance Weighting)
Implementação manual de interpolação espacial com restrições biológicas:
- **Raio de dispersão:** Limite de **3.0°** (~300 km)
- **Vizinhos:** Máximo de **150 plots** mais próximos
- **Função de peso:** $w = 1/\sqrt{d}$ (otimização baseada no artigo)

### 3. Análise Estatística
- Simulação de dados MaxEnt (adequabilidade 0-1) com ruído controlado
- Cálculo da **Correlação de Spearman (ρ)** para avaliar relação não-linear
- Visualização com scatter plot e linha de tendência

## Estrutura dos Dados Simulados

### Coletas Naturais (NHCs)
- **20 registros** de ocorrência da espécie "Tree_X"
- Coordenadas na região amazônica (-4° a -2° lat, -62° a -58° lon)
- Inclui registros com **erros intencionais** para testar o pipeline de limpeza

### Parcelas de Abundância
- **10 plots** com contagens de árvores (0 a 22 indivíduos)
- Distribuição espacial heterogênea simulando gradientes ecológicos
- Base para cálculo do IDW

## 🚀 Como Executar

### Pré-requisitos
```bash
pip install pandas numpy matplotlib scipy
```
