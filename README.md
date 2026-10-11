# Dashboard de Vendas | Power BI

**Análise de faturamento, lucratividade e descontos com Power BI, Power Query e DAX.**

Projeto de portfólio em análise de dados desenvolvido a partir da base demonstrativa **Financial Sample**, disponibilizada pela Microsoft. O objetivo é transformar registros de vendas em indicadores e visualizações interativas para explorar o desempenho comercial por período, país, produto e segmento de clientes.

> **Contexto:** projeto de estudo e portfólio com dados fictícios de demonstração. Os resultados não representam as operações de uma empresa real.

## Visão geral

O relatório foi estruturado em três páginas:

| Página | Análises disponíveis |
| --- | --- |
| **Visão Executiva** | Faturamento, lucro, margem, unidades vendidas, evolução mensal e comparação por país |
| **Análise de Produtos** | Rankings de faturamento, lucro e margem por produto, com filtro por segmento |
| **Análise de Descontos** | Comparação entre percentual de desconto e margem de lucro por segmento |

### Capturas do dashboard

As imagens serão adicionadas à pasta `imagens/` após a exportação das três páginas do Power BI.

<!-- Após incluir os arquivos, remover os comentários das linhas abaixo:
![Visão Executiva](imagens/visao-executiva.png)
![Análise de Produtos](imagens/analise-produtos.png)
![Análise de Descontos](imagens/analise-descontos.png)
-->

## Perguntas de negócio

O dashboard foi elaborado para explorar questões como:

1. Como o faturamento evolui mês a mês?
2. Quais países apresentam maior faturamento e maior margem de lucro?
3. Quais produtos geram mais receita e lucro absoluto?
4. A liderança de rentabilidade muda de acordo com o segmento de clientes?
5. Como os percentuais de desconto variam entre os segmentos?
6. Segmentos com maiores descontos necessariamente apresentam margens menores?
7. Quais segmentos e produtos requerem investigação por apresentarem margem negativa?

## Indicadores e resultados observados

**Visão geral da base, sem filtros aplicados** (valores arredondados conforme exibidos no relatório):

| KPI | Resultado |
| --- | ---: |
| Faturamento total | **US$ 118,73 milhões** |
| Lucro total | **US$ 16,89 milhões** |
| Margem de lucro | **14,23%** |
| Unidades vendidas | **1,13 milhão** |

**Exemplos de achados do dashboard:**

- **Países:** Estados Unidos lideram o faturamento, enquanto a Alemanha apresenta a maior margem de lucro (**15,66%**). Isso reforça a importância de avaliar volume de vendas e rentabilidade separadamente.
- **Produtos:** Paseo lidera em faturamento e lucro absoluto na visão geral; Amarilla apresenta a maior margem percentual (**15,86%**).
- **Segmentos:** Channel Partners apresenta a maior margem (**73,13%**), enquanto Enterprise apresenta margem negativa (**-3,13%**), indicando necessidade de investigar preços, custos e composição das vendas.
- **Descontos:** Midmarket (**7,77%**) e Small Business (**7,65%**) apresentam os maiores percentuais de desconto. Os dados não permitem atribuir diferenças de margem exclusivamente aos descontos.
- **Tempo:** o gráfico mensal revela oscilações que não ficam evidentes quando os valores são agregados apenas por ano ou trimestre.

Os indicadores são recalculados de acordo com os filtros aplicados. As observações acima dizem respeito à configuração geral do relatório e à amostra utilizada.

## Ferramentas e habilidades aplicadas

- **Power BI Desktop:** construção de relatórios, cartões, gráficos de linhas e barras, segmentações e interações.
- **Power Query:** importação do Excel, verificação de tipos de dados, valores vazios e erros.
- **DAX:** medidas para faturamento, lucro, margem, quantidade vendida e percentual de desconto.
- **Análise de dados:** comparação de indicadores, evolução temporal, identificação de contrastes entre segmentos e interpretação de resultados.

## Exemplos de cálculos DAX

```dax
Faturamento Total =
SUM('F_Vendas'[Sales])

Lucro Total =
SUM('F_Vendas'[Profit])

Margem de Lucro =
DIVIDE([Lucro Total], [Faturamento Total], 0)

Total de Unidades Vendidas =
SUM('F_Vendas'[Units Sold])

Total de Descontos =
SUM('F_Vendas'[Discounts])

Percentual de Desconto =
DIVIDE(
    SUM('F_Vendas'[Discounts]),
    SUM('F_Vendas'[Gross Sales]),
    0
)
```

Coluna de apoio para visualizar períodos mensais:

```dax
AnoMes =
FORMAT(
    DATE('F_Vendas'[Year], 'F_Vendas'[Month Number], 1),
    "yyyy-MM"
)
```

## Como abrir o projeto

1. Instale o [Power BI Desktop](https://www.microsoft.com/pt-br/download/details.aspx?id=58494).
2. Baixe ou clone este repositório.
3. Abra `Dashboard_Analise_Vendas.pbix` no Power BI Desktop.
4. Navegue pelas três páginas e experimente os filtros de país e segmento.

Se o Power BI solicitar a localização da planilha de origem ao atualizar os dados, ajuste o caminho da fonte no Power Query. A base demonstrativa pode ser obtida na [documentação da Microsoft — Financial Sample](https://learn.microsoft.com/pt-br/power-bi/create-reports/sample-financial-download).

## Fonte e limitações

- **Fonte:** *Financial Sample* da Microsoft, conjunto de dados demonstrativo.
- **Natureza:** registros fictícios, usados exclusivamente para aprendizado e demonstração de habilidades.
- **Período:** dados de 2013 e 2014, conforme disponíveis na fonte; não é adequado comparar anos sem verificar a cobertura de meses.
- **Interpretação:** diferenças entre descontos e margens são associações observadas; não comprovam causalidade.
- **Unidade monetária:** valores apresentados no relatório como dólares (USD), sem conversão cambial.

## Próximos aprimoramentos

- Estruturar uma tabela calendário dedicada e relacionamentos para análises temporais mais avançadas.
- Incluir comparações entre períodos equivalentes e métricas de variação percentual.
- Documentar verificações adicionais de reconciliação entre vendas, descontos, custos e lucro.

---

**Projeto de portfólio | Análise de Dados e Business Intelligence**

[Perfil no GitHub](https://github.com/eliasvinharski97)
