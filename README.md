# Análise RFM para E-commerce

![GitHub](https://img.shields.io/badge/-GitHub-181717?style=flat-square&logo=github)
![Python](https://img.shields.io/badge/-Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/-Pandas-150458?style=flat-square&logo=pandas)
![Scikit-learn](https://img.shields.io/badge/-Scikit--learn-F7931E?style=flat-square&logo=scikit-learn)

Projeto completo de análise e tratamento de dados para cálculo de indicadores RFM (Recência, Frequência, Ticket Médio) em um dataset de e-commerce internacional.

## 📊 Resultados e Aplicações

**Principais outputs gerados:**
- 🧹 Dataset tratado e pronto para análise
- 📈 Indicadores RFM calculados para cada cliente
- 📊 Visualizações estratégicas de vendas
- 🔍 Insights sobre comportamento do consumidor

**Aplicações práticas:**
- 🎯 Segmentação de clientes para campanhas de marketing
- 📉 Identificação de tendências de compra
- 💰 Otimização de investimento em publicidade
- 🏆 Priorização de clientes VIP
- 🔄 Detecção de clientes em risco de churn

## 🛒 Contexto do Projeto

Análise de dados transacionais de um e-commerce internacional com operação em 37 países, com os seguintes objetivos:
1. Calcular indicadores RFM para segmentação de clientes
2. Identificar padrões de compra
3. Desenvolver modelo preditivo para estimativa de ROI em publicidade

## 📁 Sobre os Dados

Dataset contendo registros de compras com as seguintes características:

| Coluna | Descrição | Tipo Original | Problemas Identificados |
|--------|-----------|---------------|-------------------------|
| InvoiceNo | Número da fatura | object | - |
| StockCode | Código do produto | object | - |
| Description | Descrição do produto | object | Valores nulos |
| Quantity | Quantidade comprada | int64 | Valores negativos e outliers |
| InvoiceDate | Data da compra | object | - |
| UnitPrice | Preço unitário | float64 | Valores negativos e outliers |
| CustomerID | ID do cliente | float64 | Valores nulos |
| Country | País da compra | object | - |

## 🔧 Processo de Data Wrangling

### 1️⃣ Pré-processamento Inicial
- Carregamento do dataset e análise exploratória
- Identificação de valores nulos, outliers e dados inconsistentes
- Utilização de bibliotecas como `missingno` e `ydata-profiling` para análise

### 2️⃣ Tratamento de Dados
- **Valores nulos**: Remoção de registros sem CustomerID
- **Dados inconsistentes**:
  - Filtragem de valores negativos em Quantity e UnitPrice
  - Tratamento de outliers nas colunas numéricas
- **Tipagem correta**:
  - Conversão de CustomerID para int64
  - Conversão de InvoiceDate para datetime

### 3️⃣ Engenharia de Features
- Criação da coluna `Total_Compra` (Quantity × UnitPrice)
- Cálculo dos indicadores RFM:
  - **Recência**: Dias desde última compra
  - **Frequência**: Número de compras realizadas
  - **Ticket Médio**: Valor médio gasto por compra

### 4️⃣ Visualização de Dados
Principais visualizações geradas:
1. Top 10 países por volume de vendas
2. Produtos mais vendidos
3. Sazonalidade de vendas (mensal)
4. Distribuição de valores RFM
5. Comparativo de vendas por país/mês

## 🛠️ Tecnologias Utilizadas

```python
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
from ydata_profiling import ProfileReport
from sklearn.preprocessing import StandardScaler
```
## 📌 Conclusões e Próximos Passos

### 🔍 Insights Obtidos
- 🌎 **Países com maior potencial**: Identificação clara dos mercados com melhor performance de vendas e maior ticket médio
- 📅 **Sazonalidade**: Reconhecimento de padrões cíclicos e períodos de alta/média/baixa temporada
- 🎯 **Segmentação de clientes**: Classificação eficiente dos consumidores por:
  - Valor gasto (Ticket Médio)
  - Frequência de compras
  - Tempo desde última compra (Recência)
