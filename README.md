# Dashboard de Vendas | Power BI

**Análise de desempenho comercial, faturamento, lucratividade e descontos utilizando Power BI, Power Query e DAX.**

Projeto de análise de dados desenvolvido com a base pública *Financial Sample*, disponibilizada pela Microsoft.

O objetivo foi transformar dados de vendas em informações para apoiar decisões de negócio, permitindo identificar diferenças de rentabilidade entre países, produtos e segmentos de clientes.

**Tecnologias:** Power BI Desktop | Power Query | DAX | Excel | Business Intelligence

## Visualização do Dashboard

### Visão Executiva

![Dashboard - Visão Executiva](Vis%C3%A3o%20Executiva.png)

Visão consolidada dos principais indicadores de desempenho comercial, incluindo faturamento, lucro, margem, unidades vendidas, evolução mensal e resultados por país.

### Análise de Produtos

![Dashboard - Análise de Produtos](An%C3%A1lise%20de%20Produtos.png)

Análise comparativa de faturamento, lucro absoluto e margem de lucro por produto, com segmentação interativa para investigar o desempenho em diferentes grupos de clientes.

### Análise de Descontos

![Dashboard - Análise de Descontos](An%C3%A1lise%20de%20Descontos.png)

Comparação dos percentuais de desconto e margens de lucro entre segmentos, identificando diferenças de rentabilidade e possíveis pontos de atenção.

## Objetivos da análise

O projeto foi desenvolvido para responder às seguintes perguntas de negócio:

1. Como o faturamento evoluiu ao longo dos meses?
2. Quais países apresentam os melhores resultados de faturamento e rentabilidade?
3. Quais produtos geram maior faturamento e lucro?
4. Os produtos mais vendidos são necessariamente os mais rentáveis?
5. Quais segmentos apresentam os maiores percentuais de desconto?
6. Existe associação entre descontos e margens de lucro?
7. Quais segmentos apresentam resultados negativos e exigem investigação?

## Indicadores de desempenho (KPIs)

Resultados gerais da base, sem filtros aplicados:

| Indicador | Resultado |
|---|---:|
| Faturamento Total | US$ 118,73 milhões |
| Lucro Total | US$ 16,89 milhões |
| Margem de Lucro | 14,23% |
| Unidades Vendidas | 1,13 milhão |

Os indicadores são dinâmicos e respondem aos filtros disponíveis no relatório.

## Principais resultados identificados

### 1. Faturamento não significa maior rentabilidade

Os Estados Unidos apresentam o maior faturamento, enquanto a Alemanha possui a maior margem de lucro, de 15,66%.

Esse resultado demonstra a importância de avaliar faturamento e rentabilidade separadamente.

### 2. Produtos com maior receita nem sempre possuem maior margem

O produto **Paseo** lidera o faturamento e o lucro absoluto na visão geral.

Entretanto, **Amarilla** apresenta a maior margem percentual, de 15,86%.

Isso mostra que diferentes indicadores podem produzir rankings distintos de desempenho.

### 3. Segmento Enterprise apresenta prejuízo

A análise por segmento identificou:

- Channel Partners: margem de lucro de 73,13%.
- Midmarket: margem de lucro de 27,71%.
- Enterprise: margem de lucro de -3,13%.

O resultado negativo do segmento Enterprise aponta para a necessidade de investigar os custos, preços praticados e composição das vendas.

### 4. Maiores descontos não representam necessariamente menores margens

Os segmentos Midmarket (7,77%) e Small Business (7,65%) apresentam os maiores percentuais de desconto.

Entretanto, as diferenças de rentabilidade entre os segmentos não acompanham necessariamente a mesma ordem dos descontos.

Portanto, os dados não permitem concluir que os descontos, isoladamente, sejam responsáveis pelas menores margens.

### 5. A análise mensal revela oscilações no faturamento

A visualização mensal permite identificar períodos de crescimento e queda que poderiam passar despercebidos em comparações agregadas por ano ou trimestre.

Essa análise reforça a importância da granularidade temporal na interpretação dos indicadores.

## Desenvolvimento técnico

### Preparação dos dados — Power Query

A base foi importada de um arquivo Excel e examinada no Power Query, incluindo:

- Conferência dos tipos de dados.
- Verificação de valores nulos e erros.
- Análise da distribuição e qualidade das colunas.
- Organização dos campos utilizados nas análises.

### Modelagem e cálculos — DAX

Foram utilizadas medidas para calcular indicadores financeiros e comerciais.

**Faturamento Total**

```dax
Faturamento Total =
SUM('F_Vendas'[Sales])
```

**Lucro Total**

```dax
Lucro Total =
SUM('F_Vendas'[Profit])
```

**Margem de Lucro**

```dax
Margem de Lucro =
DIVIDE(
    [Lucro Total],
    [Faturamento Total],
    0
)
```

**Total de Unidades Vendidas**

```dax
Total de Unidades Vendidas =
SUM('F_Vendas'[Units Sold])
```

**Percentual de Desconto**

```dax
Percentual de Desconto =
DIVIDE(
    SUM('F_Vendas'[Discounts]),
    SUM('F_Vendas'[Gross Sales]),
    0
)
```

**Coluna auxiliar para análise mensal**

```dax
AnoMes =
FORMAT(
    DATE(
        'F_Vendas'[Year],
        'F_Vendas'[Month Number],
        1
    ),
    "yyyy-MM"
)
```

### Visualização e interação

O relatório contém três páginas com indicadores, gráficos de linhas, gráficos de barras e filtros interativos.

As segmentações permitem explorar os resultados em diferentes contextos e comparar o comportamento dos indicadores.

## Como executar o projeto

1. Instale o [Power BI Desktop](https://www.microsoft.com/pt-br/download/details.aspx?id=58494).
2. Baixe este repositório.
3. Abra o arquivo `Dashboard_Analise_Vendas.pbix`.
4. Explore as páginas e utilize os filtros disponíveis.

Caso seja necessário atualizar os dados, a base original está disponível na [documentação da Microsoft](https://learn.microsoft.com/pt-br/power-bi/create-reports/sample-financial-download).

## Fonte e considerações

O projeto utiliza o conjunto de dados demonstrativo **Financial Sample**, disponibilizado pela Microsoft.

Os registros são fictícios e servem para demonstrar a aplicação de técnicas de análise de dados e Business Intelligence.

A base contém registros de 2013 e 2014. Comparações entre períodos devem considerar a cobertura dos meses disponíveis.

Os resultados representam os cálculos e relacionamentos observados na base e não devem ser interpretados como comprovação de causalidade.

## Evolução do projeto

Possibilidades de aprimoramento incluem a implementação de uma tabela calendário dedicada, análises de variação entre períodos equivalentes e verificações adicionais de consistência dos indicadores financeiros.

---

**Projeto de portfólio | Análise de Dados e Business Intelligence**

[GitHub — Elias Santos Vinharski](https://github.com/eliasvinharski97)