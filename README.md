# Dashboard de Vendas | Power BI

**Análise de desempenho comercial, faturamento, lucratividade e descontos com Power BI, Power Query e DAX.**

Projeto de portfólio em Análise de Dados e Business Intelligence desenvolvido a partir da base pública **Financial Sample**, disponibilizada pela Microsoft.

O objetivo foi transformar dados de vendas em indicadores e visualizações interativas para analisar o desempenho comercial, identificar diferenças de rentabilidade e explorar oportunidades de melhoria por país, produto e segmento de clientes.

**Tecnologias utilizadas:** Power BI Desktop | Power Query | DAX | Excel | Business Intelligence

## Leitura rápida

- **Pergunta:** quais países, produtos e segmentos combinam faturamento e rentabilidade?
- **Entrega:** três páginas interativas, [arquivo PBIX](Dashboard_Analise_Vendas.pbix) e [base demonstrativa](Financial%20Sample.xlsx).
- **Achado:** o segmento Enterprise apresenta margem de -3,13%. Isso orienta uma investigação de custos, preços e composição das vendas; não comprova que os descontos causaram o prejuízo.
- **Escopo:** projeto de portfólio com dados fictícios da Microsoft, sem resultado operacional atribuído a uma empresa real.

## Decisões técnicas e como conferir

1. **Margem como razão entre totais:** a medida divide o lucro total pelo faturamento total, evitando uma média simples das margens das linhas. As fórmulas DAX estão na seção de desenvolvimento técnico.
2. **Desconto sobre venda bruta:** o percentual divide os descontos pela venda bruta, enquanto a margem usa `Sales`. Os indicadores têm denominadores diferentes e respondem a perguntas diferentes.
3. **Cuidado de interpretação:** Enterprise tem margem negativa sem ter o maior percentual de desconto. Por isso, a análise trata descontos como um fator a investigar, sem atribuir causalidade.
4. **Roteiro de conferência:** abra o PBIX sem filtros e compare os totais com a planilha. Depois, filtre Enterprise e compare `SUM(Profit) / SUM(Sales)` com a margem exibida. Esse roteiro permite verificar o cálculo; não representa uma nova auditoria do arquivo PBIX.

## Visualização do Dashboard

O dashboard foi desenvolvido em três páginas, organizadas para facilitar a navegação e a interpretação dos resultados.

### 1. Visão Executiva

![Dashboard - Visão Executiva](Vis%C3%A3o%20Executiva.png)

Apresenta uma visão consolidada dos principais indicadores financeiros e comerciais:

- Faturamento total.
- Lucro total.
- Margem de lucro.
- Total de unidades vendidas.
- Evolução mensal do faturamento.
- Comparação de faturamento e rentabilidade entre países.

A página conta com filtros interativos para explorar os resultados por país.

### 2. Análise de Produtos

![Dashboard - Análise de Produtos](An%C3%A1lise%20de%20Produtos.png)

Permite comparar o desempenho dos produtos a partir de três indicadores:

- Faturamento por produto.
- Lucro absoluto por produto.
- Margem de lucro por produto.

A segmentação por tipo de cliente permite identificar como a rentabilidade dos produtos varia entre diferentes mercados.

### 3. Análise de Descontos

![Dashboard - Análise de Descontos](An%C3%A1lise%20de%20Descontos.png)

Apresenta uma análise comparativa entre:

- Percentual de desconto por segmento.
- Margem de lucro por segmento.

O objetivo é investigar possíveis associações entre as condições comerciais praticadas e os resultados de rentabilidade.

## Objetivos da Análise

O dashboard foi desenvolvido para responder às seguintes perguntas de negócio:

1. Como o faturamento evoluiu ao longo dos meses?
2. Quais países apresentam os maiores faturamentos?
3. Os países que mais faturam também possuem as maiores margens de lucro?
4. Quais produtos geram mais faturamento e lucro?
5. Quais produtos apresentam maior rentabilidade proporcional?
6. Como o desempenho dos produtos varia entre os segmentos de clientes?
7. Quais segmentos apresentam os maiores percentuais de desconto?
8. Existe associação entre descontos e margens de lucro?
9. Quais segmentos apresentam resultados negativos e exigem investigação?

## Indicadores de Desempenho (KPIs)

Os indicadores foram desenvolvidos com medidas DAX e respondem dinamicamente aos filtros aplicados no relatório.

### Resultados gerais

| Indicador | Resultado |
|---|---:|
| Faturamento Total | US$ 118,73 milhões |
| Lucro Total | US$ 16,89 milhões |
| Margem de Lucro | 14,23% |
| Total de Unidades Vendidas | 1,13 milhão |

*Valores arredondados conforme apresentados no Power BI, considerando a visão geral da base sem filtros aplicados.*

## Principais Resultados Identificados

### 1. Maior faturamento não significa maior rentabilidade

A análise por país demonstrou que os **Estados Unidos lideram o faturamento**, enquanto a **Alemanha apresenta a maior margem de lucro, com 15,66%**.

Esse resultado evidencia a importância de avaliar faturamento e rentabilidade como indicadores complementares.

Um mercado com maior volume de vendas não necessariamente apresenta o melhor desempenho proporcional em lucro.

### 2. Produtos com maior receita nem sempre possuem maior margem

Na análise geral, o produto **Paseo** apresentou o maior faturamento e lucro absoluto.

Entretanto, o produto **Amarilla** apresentou a maior margem de lucro, de **15,86%**.

Essa diferença demonstra que a avaliação do portfólio de produtos deve considerar tanto os valores absolutos quanto a rentabilidade proporcional.

### 3. Segmento Enterprise apresenta resultado negativo

A comparação de margens entre segmentos identificou diferenças relevantes de desempenho.

| Segmento | Margem de Lucro |
|---|---:|
| Channel Partners | 73,13% |
| Midmarket | 27,71% |
| Government | 21,69% |
| Small Business | 9,77% |
| Enterprise | -3,13% |

O segmento **Enterprise apresentou margem negativa de -3,13%**, indicando prejuízo na base analisada.

A análise por produto mostrou que todos os seis produtos apresentam margens negativas nesse segmento.

Esse resultado indica a necessidade de aprofundar a investigação sobre custos, preços e composição das vendas.

### 4. Os descontos não explicam isoladamente a rentabilidade

A comparação dos percentuais de desconto entre os segmentos apresentou:

| Segmento | Percentual de Desconto |
|---|---:|
| Midmarket | 7,77% |
| Small Business | 7,65% |
| Channel Partners | 6,95% |
| Enterprise | 6,92% |
| Government | 6,91% |

Os segmentos que apresentam maiores descontos não são necessariamente aqueles com menores margens.

Por exemplo, o segmento Enterprise possui a menor margem de lucro, mas não apresenta o maior percentual de desconto.

Assim, não é possível atribuir o prejuízo exclusivamente aos descontos. Outros fatores financeiros e comerciais devem ser considerados.

### 5. A análise mensal revela oscilações no faturamento

A evolução mensal permitiu identificar períodos de crescimento e redução do faturamento ao longo da série histórica.

As variações mostram que o aumento do faturamento entre períodos mais amplos não representa necessariamente crescimento contínuo mês a mês.

Essa análise demonstra a importância de utilizar a granularidade temporal adequada para compreender o comportamento dos indicadores.

## Desenvolvimento Técnico

### Preparação e tratamento dos dados — Power Query

Os dados foram importados de um arquivo Excel e examinados no Power Query.

As principais atividades incluíram:

- Verificação dos tipos de dados.
- Análise de valores nulos e erros.
- Conferência da consistência das colunas.
- Inspeção da distribuição dos registros.
- Organização dos campos utilizados nas análises.

### Modelagem e cálculos — DAX

Foram desenvolvidas medidas para calcular os principais indicadores financeiros e comerciais.

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

A utilização de medidas DAX permite recalcular os indicadores conforme o contexto dos filtros aplicados, mantendo a interatividade das análises.

### Visualização e interatividade

Foram utilizados:

- Cartões de indicadores.
- Gráficos de linhas.
- Gráficos de barras horizontais.
- Segmentações interativas.
- Ordenação por desempenho.
- Rótulos de dados.
- Formatação de indicadores financeiros e percentuais.

O relatório foi organizado para permitir uma navegação entre a visão consolidada e análises mais específicas.

## Base de Dados e Fonte

O projeto utiliza a base pública **Financial Sample**, disponibilizada pela Microsoft para demonstração de análises financeiras e comerciais.

O arquivo original está incluído neste repositório e pode ser acessado pelo link:

**[Acessar Financial Sample.xlsx](Financial%20Sample.xlsx)**

### Características da base

| Característica | Descrição |
|---|---|
| Fonte | Microsoft — Financial Sample |
| Formato | Excel (.xlsx) |
| Quantidade de registros | 700 |
| Quantidade de colunas originais | 16 |
| Período | 2013 e 2014 |
| Países | Canadá, França, Alemanha, México e Estados Unidos |
| Produtos | Paseo, VTT, Velo, Amarilla, Montana e Carretera |
| Informações | Vendas, custos, descontos, lucros, produtos, países e segmentos |

**Fonte oficial:** [Microsoft — Financial Sample](https://learn.microsoft.com/pt-br/power-bi/create-reports/sample-financial-download).

### Reprodutibilidade da análise

A disponibilização da planilha permite consultar os registros utilizados no projeto e reproduzir as análises desenvolvidas no Power BI.

O arquivo `.pbix` contém as páginas, os visuais, as medidas DAX e as configurações do relatório.

### Considerações e limitações

- Os dados são fictícios e utilizados para fins educacionais e de portfólio.
- As comparações temporais devem considerar a cobertura de meses disponível em cada ano.
- As associações observadas entre descontos, custos e margens não comprovam relações de causa e efeito.
- Os valores financeiros são apresentados em dólares (USD), sem conversão cambial.
- Os resultados correspondem à base demonstrativa utilizada e não representam operações de uma empresa real.

## Como Executar o Projeto

1. Instale o [Power BI Desktop](https://www.microsoft.com/pt-br/download/details.aspx?id=58494).
2. Baixe ou clone este repositório.
3. Abra o arquivo `Dashboard_Analise_Vendas.pbix`.
4. Navegue pelas três páginas do relatório.
5. Utilize os filtros de países e segmentos para explorar os resultados.

Caso seja necessário atualizar os dados, verifique o caminho da fonte no Power Query e aponte para o arquivo `Financial Sample.xlsx` disponibilizado neste repositório.

## Evolução do Projeto

Como possibilidades de aprofundamento técnico, o projeto poderá incorporar:

- Tabela calendário dedicada para análises temporais.
- Comparações de faturamento e lucro entre períodos equivalentes.
- Indicadores de crescimento percentual.
- Verificações adicionais de consistência entre vendas, custos, descontos e lucros.
- Análises mais detalhadas dos segmentos com rentabilidade negativa.

Essas melhorias permitirão explorar técnicas adicionais de modelagem, DAX e análise financeira.

---

**Projeto de Portfólio | Análise de Dados e Business Intelligence**

[GitHub — Elias Santos Vinharski](https://github.com/eliasvinharski97)