# Realizando data Cleaning/Wrangling para tratamento dos dados.

## Contexto

Uma empresa do ramo de e-commerce contratou você para levantar os indicadores de recência, frequência e ticket médio (RFM) dos seus clientes. O objetivo é entender melhor a relação entre as variáveis presentes nos registros e identificar os fatores que mais impactam na geração de leads. Além disso, a empresa busca criar um modelo de predição de valores para estimar o retorno de vendas que pode ser gerado a partir de um determinado investimento em publicidade.

## Sobre os Dados

O dataset contém informações de compras de um e-commerce em 37 países. As colunas incluem:

- **InvoiceNo**: Número da fatura.
- **StockCode**: Código do produto.
- **Description**: Descrição do produto.
- **Quantity**: Quantidade de produtos comprados.
- **InvoiceDate**: Data da compra.
- **UnitPrice**: Preço unitário do produto.
- **CustomerID**: Identificação do cliente.
- **Country**: País onde a compra foi realizada.

## Etapas de Desenvolvimento

### 1. Carregando o Arquivo e Realizando Primeiras Análises

- **Bibliotecas Utilizadas**: `numpy`, `pandas`, `seaborn`, `matplotlib`, `sidetable`, `ydata-profiling`, `missingno`, `ipywidgets`, `sklearn`.
- **Carregamento do Dataset**: O dataset foi carregado e analisado para verificar a distribuição dos dados e os tipos de colunas.
- **Análise Inicial**: Verificou-se que as colunas `Quantity` e `UnitPrice` apresentam valores negativos, desvio padrão superior à média e possivelmente outliers. Além disso, as colunas `Description`, `CustomerID` e `Country` possuem valores nulos.

### 2. Tratamento de Valores Faltantes em `CustomerID`

- **Identificação de Valores Nulos**: Utilizou-se a biblioteca `sidetable` para identificar a quantidade de valores nulos em cada coluna.
- **Remoção de Valores Nulos**: Os valores nulos na coluna `CustomerID` foram removidos, pois são essenciais para a análise.

### 3. Tratamento de Preços Unitários e Quantidades Inválidas

- **Filtragem de Valores Negativos**: Foram removidas as linhas com valores negativos ou nulos nas colunas `UnitPrice` e `Quantity`.
- **Resultado**: O dataset foi limpo de valores inválidos, garantindo a consistência dos dados.

### 4. Verificação de Duplicatas

- **Identificação de Duplicatas**: Foram identificadas e removidas as linhas duplicadas no dataset.
- **Resultado**: O dataset foi limpo de duplicatas, garantindo a unicidade dos registros.

### 5. Alteração de Tipos de Dados

- **Conversão de Tipos**: A coluna `CustomerID` foi convertida para o tipo `int64`, e a coluna `InvoiceDate` foi convertida para o tipo `datetime`.
- **Resultado**: Os tipos de dados foram ajustados para facilitar análises posteriores.

### 6. Tratamento de Outliers

- **Identificação de Outliers**: Foram identificados outliers nas colunas `Quantity` e `UnitPrice`.
- **Limitação de Valores**: Valores superiores a 10 para `Quantity` e superiores a 5 para `UnitPrice` foram limitados para evitar distorções nas análises.
- **Resultado**: Os outliers foram tratados, garantindo uma distribuição mais equilibrada dos dados.

### 7. Adição de Coluna de Total de Compra

- **Cálculo do Total de Compra**: Foi adicionada uma nova coluna `Total_Compra`, que representa o valor total de cada compra (`Quantity * UnitPrice`).
- **Resultado**: A nova coluna facilita a análise do valor total das vendas.

### 8. Cálculo da Última Data

- **Identificação da Última Data**: A última data de compra no dataset foi identificada para ser usada no cálculo da recência.
- **Resultado**: A última data foi armazenada para uso posterior.

### 9. Plotagem de Gráficos

- **Top 10 Países com Maior Valor em Vendas**: Gráfico de barras mostrando os países com maior valor total de vendas.
- **Top 10 Produtos Mais Vendidos**: Gráfico de barras mostrando os produtos mais vendidos.
- **Valor Total de Vendas por Mês**: Gráfico de barras mostrando o valor total de vendas por mês.
- **Valor de Venda Total por Mês e por País**: Gráfico de barras mostrando o valor total de vendas por mês, considerando apenas os top 10 países.

### 10. Cálculo de RFM (Recência, Frequência, Ticket Médio)

- **Cálculo de RFM**: Foram calculados os indicadores RFM para cada cliente:
  - **Recência**: Número de dias desde a última compra.
  - **Frequência**: Número de compras realizadas.
  - **Ticket Médio**: Valor médio gasto por compra.
- **Resultado**: O dataset foi enriquecido com os indicadores RFM, que serão usados para análises e modelagem futuras.

## Conclusão

O dataset foi limpo, tratado e enriquecido com novas colunas e indicadores. Os gráficos gerados fornecem insights valiosos sobre o comportamento dos clientes e as tendências de vendas. Os indicadores RFM serão úteis para a criação de modelos de predição e estratégias de marketing mais eficazes.

---
