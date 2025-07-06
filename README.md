# Sumário - Análise de Preços de Aluguel de Imóveis

## Execução

### Instalação das bibliotecas

- `pip install -r requiriments.txt`

### Execução

- Para execução, basta executar o arquivo `main.ipynb`

## Visão Geral

Este projeto apresenta uma análise completa de dados de aluguel de imóveis, utilizando técnicas de mineração de dados para predição de preços. O trabalho inclui análise exploratória, pré-processamento de dados e aplicação de modelos de machine learning.

## Dataset

- **Fonte**: `House_Rent_Dataset.csv`
- **Características**: Dataset contendo informações sobre imóveis para aluguel
- **Variáveis principais**:
  - `Rent`: Valor do aluguel (variável target)
  - `City`: Cidade onde está localizado o imóvel
  - `Size`: Tamanho do imóvel em pés quadrados
  - `BHK`: Número de quartos, sala e cozinha
  - `Bathroom`: Número de banheiros
  - `Furnishing Status`: Status de mobiliário (mobiliado, semi-mobiliado, não mobiliado)
  - `Tenant Preferred`: Tipo de inquilino preferido
  - `Area Type`: Tipo de área
  - `Point of Contact`: Ponto de contato

## Metodologia

### 1. Pré-processamento dos Dados

#### 1.1 Análise Exploratória

- **Estrutura dos dados**: Análise das dimensões, tipos de dados e informações gerais
- **Valores ausentes**: Verificação de dados faltantes
- **Duplicatas**: Identificação e tratamento de registros duplicados
- **Visualizações**:
  - Distribuição de imóveis por cidade
  - Status de mobiliário dos imóveis
  - Preferências de inquilinos
  - Relação entre tamanho e valor do aluguel
  - Distribuição de número de cômodos e banheiros
  - Mapas de calor para correlações

#### 1.2 Tratamento de Outliers

- **Método**: Remoção baseada no critério de 3 desvios padrão da média
- **Variáveis analisadas**: `Rent`, `Size`, `Bathroom`, `BHK`
- **Resultado**: Redução significativa no número de registros após remoção de outliers
- **Visualização**: Box plots antes e depois da remoção

#### 1.3 Transformação de Dados

- **Encoding de variáveis categóricas**: Aplicação de One-Hot Encoding
- **Variáveis transformadas**: `City`, `Furnishing Status`, `Tenant Preferred`, `Point of Contact`, `Area Type`
- **Estratégia**: Uso do parâmetro `drop='first'` para evitar multicolinearidade

#### 1.4 Análise de Correlação

- **Matriz de correlação**: Visualização das relações entre variáveis numéricas
- **Insights**: Identificação de variáveis mais correlacionadas com o preço do aluguel

### 2. Preparação dos Datasets

Foram criadas quatro versões do dataset para comparação:

1. **Dataset original**: Dados sem modificações
2. **Dataset original sem outliers**: Dados após remoção de outliers
3. **Dataset transformado**: Dados com encoding de variáveis categóricas
4. **Dataset transformado sem outliers**: Combinação de transformação e remoção de outliers

### 3. Divisão dos Dados

- **Proporção**: 90% treino / 10% teste
- **Método**: `train_test_split` do scikit-learn
- **Variáveis removidas**: `Posted On`, `Floor`, `Area Locality` (consideradas irrelevantes para predição)

## Modelos Aplicados

### 3.1 Regressão Linear

Modelo linear simples aplicado aos quatro datasets preparados.

### 3.2 Random Forest

Modelo ensemble com 1000 estimadores aplicado aos quatro datasets.

**Configuração:**

- `n_estimators=1000`
- `random_state=42`

## Métricas de Avaliação

Para cada modelo e dataset, foram calculadas as seguintes métricas:

### Conjunto de Teste

- **MSE**: Avaliação da capacidade de generalização
- **MAPE**: Interpretabilidade do erro em termos percentuais
- **R²**: Proporção da variância explicada
- **RMSE**: Erro em unidades originais (comparado com a média do aluguel)

## Principais Insights

### Análise Exploratória

1. **Distribuição geográfica**: Concentração de imóveis em determinadas cidades
2. **Padrões de mobiliário**: Maioria dos imóveis em determinado status de mobiliário
3. **Correlações**: Identificação de variáveis mais influentes no preço
4. **Outliers**: Presença significativa de valores extremos nos dados

### Performance dos Modelos

1. **Random Forest vs Regressão Linear**: Comparação de performance
2. **Impacto dos outliers**: Melhoria consistente após remoção
3. **Transformação de dados**: Benefícios do encoding de variáveis categóricas
4. **Overfitting**: Análise da diferença entre performance de treino e teste

## Arquivos do Projeto

- `main.ipynb`: Notebook principal com toda a análise
- `dataset/House_Rent_Dataset.csv`: Dataset original
- `dataset/Dataset Glossary.txt`: Dicionário dos dados
- `README.md`: Documentação do projeto
- `requirements.txt`: Dependências do projeto
