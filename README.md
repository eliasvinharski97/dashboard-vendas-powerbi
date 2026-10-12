# Dashboard de Vendas | Power BI

Análise de faturamento, lucro e descontos por país, produto e segmento, com três páginas interativas. Projeto de portfólio com a base demonstrativa **Financial Sample**, da Microsoft.

![Dashboard — Visão Executiva](Vis%C3%A3o%20Executiva.png)

## Três resultados da análise

- **Países:** os Estados Unidos lideram o faturamento, enquanto a Alemanha apresenta a maior margem de lucro, de **15,66%**.
- **Produtos:** Paseo lidera em faturamento e lucro absoluto; Amarilla tem a maior margem, de **15,86%**.
- **Segmentos:** Enterprise registra margem de **-3,13%**, sem apresentar o maior percentual de desconto. O resultado orienta uma investigação de custos, preços e composição das vendas.

**[Acessar o dashboard (.pbix)](Dashboard_Analise_Vendas.pbix)** · [Consultar a base Excel](Financial%20Sample.xlsx)

**Ferramentas:** Power BI Desktop · Power Query · DAX · Excel

## Indicadores gerais

| Indicador | Resultado |
| --- | ---: |
| Faturamento | US$ 118,73 milhões |
| Lucro | US$ 16,89 milhões |
| Margem de lucro | 14,23% |
| Unidades vendidas | 1,13 milhão |

Valores arredondados, considerando a base completa sem filtros.

## Páginas do relatório

A **Visão Executiva**, apresentada acima, reúne indicadores, evolução mensal e comparação entre países, com filtro por país.

### Análise de Produtos

![Dashboard — Análise de Produtos](An%C3%A1lise%20de%20Produtos.png)

Compara faturamento, lucro absoluto e margem por produto. O filtro por segmento permite investigar diferenças entre os tipos de cliente.

### Análise de Descontos

![Dashboard — Análise de Descontos](An%C3%A1lise%20de%20Descontos.png)

Compara descontos e margens por segmento:

| Segmento | Margem de lucro | Percentual de desconto |
| --- | ---: | ---: |
| Channel Partners | 73,13% | 6,95% |
| Midmarket | 27,71% | 7,77% |
| Government | 21,69% | 6,91% |
| Small Business | 9,77% | 7,65% |
| Enterprise | -3,13% | 6,92% |

Os seis produtos apresentam margens negativas no segmento Enterprise.

## Preparação e decisões técnicas

Os dados foram importados do Excel e examinados no Power Query: tipos de dados, valores nulos, erros, consistência das colunas e organização dos campos.

- **Margem:** lucro total dividido pelo faturamento total, evitando uma média simples das margens das linhas.
- **Desconto:** descontos divididos pela venda bruta (`Gross Sales`). A margem utiliza `Sales`, portanto os indicadores têm denominadores diferentes.
- **Evolução mensal:** a coluna `AnoMes` distingue os meses de cada ano. As medidas são recalculadas conforme os filtros do relatório.

### Medidas DAX e coluna auxiliar

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

**Total de Descontos**

```dax
Total de Descontos =
SUM('F_Vendas'[Discounts])
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

## Fonte e limites da análise

| Característica | Descrição |
| --- | --- |
| Fonte | Microsoft — Financial Sample |
| Registros e colunas originais | 700 registros e 16 colunas |
| Período | 2013 e 2014 |
| Países | Canadá, França, Alemanha, México e Estados Unidos |
| Produtos | Paseo, VTT, Velo, Amarilla, Montana e Carretera |

[Fonte oficial da Microsoft](https://learn.microsoft.com/pt-br/power-bi/create-reports/sample-financial-download).

- A base é fictícia e demonstrativa; os resultados não representam operações ou melhorias obtidas em uma empresa real.
- Os valores são apresentados em dólares (USD), sem conversão cambial.
- Comparações temporais precisam considerar a cobertura de meses de cada ano.
- As associações observadas não comprovam causalidade. Não é possível atribuir o prejuízo de Enterprise exclusivamente aos descontos.

## Como abrir e conferir

1. Baixe este repositório e abra `Dashboard_Analise_Vendas.pbix` no [Power BI Desktop](https://www.microsoft.com/pt-br/download/details.aspx?id=58494).
2. Explore as três páginas e os filtros de país e segmento.
3. Para atualizar os dados, ajuste o caminho da fonte no Power Query para o arquivo `Financial Sample.xlsx` baixado.
4. Para conferir os indicadores, remova os filtros e compare os totais com a planilha. Depois filtre Enterprise e compare a razão entre a soma de `Profit` e a soma de `Sales` com a margem exibida.

O último passo é um roteiro de conferência para quem abrir o projeto.

## Próximas melhorias

- Criar uma tabela calendário e comparar períodos equivalentes.
- Acrescentar indicadores de crescimento percentual.
- Ampliar as verificações entre vendas, custos, descontos e lucros.
- Aprofundar a análise dos segmentos com rentabilidade negativa.

[GitHub — Elias Santos Vinharski](https://github.com/eliasvinharski97)
