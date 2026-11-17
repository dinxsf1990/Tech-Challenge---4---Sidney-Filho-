# Amazon Product Performance & Customer Insights

Projeto de Data Analytics desenvolvido como parte do **Tech Challenge – Fase 04**, com foco na análise de desempenho de produtos, estratégias comerciais e percepção dos consumidores em um marketplace.

A solução utiliza Python para preparação e análise exploratória dos dados e Power BI para construção de um dashboard interativo, transformando informações de produtos e avaliações em insights para apoiar decisões de negócio.

---

## Objetivo do projeto

Investigar o desempenho do portfólio de produtos de um marketplace, buscando responder a questões como:

- Quais categorias e produtos apresentam maior relevância?
- Quais produtos possuem maior engajamento dos consumidores?
- Existe relação entre descontos e avaliações?
- Quais categorias apresentam maior ou menor satisfação?
- Existem produtos com alto engajamento, mas baixa avaliação?
- Quais problemas aparecem com maior frequência nos comentários?
- Quais oportunidades podem ser identificadas para o negócio?

O projeto busca conectar quatro dimensões principais:

**Preço → Desconto → Engajamento → Satisfação do Cliente**

## Tecnologias utilizadas

| Tecnologia | Aplicação |
|---|---|
| Python | Preparação, limpeza e análise exploratória dos dados |
| Pandas | Manipulação e transformação de dados |
| Google Colab | Ambiente de desenvolvimento e análise |
| Power BI | Modelagem, indicadores e dashboard interativo |
| DAX | Criação de medidas e indicadores |
| Power Query | Transformação e preparação dos dados |

## Fonte dos dados

A base utilizada foi disponibilizada no Kaggle:

[Amazon Sales Dataset – Kaggle](https://www.kaggle.com/datasets/karkavelrajaj/amazon-sales-dataset)

O conjunto contém informações relacionadas a produtos, categorias, preços, descontos, avaliações e comentários de consumidores.

Principais variáveis utilizadas:

- `product_id`
- `product_name`
- `category`
- `discounted_price`
- `actual_price`
- `discount_percentage`
- `rating`
- `rating_count`
- `about_product`
- `review_title`
- `review_content`

## Preparação e tratamento dos dados

A preparação foi realizada em Python, com o objetivo de estruturar uma base consistente para as análises e para a utilização no Power BI.

Principais procedimentos:

- Inspeção inicial da estrutura e qualidade dos dados.
- Identificação de registros duplicados por `product_id`.
- Remoção de duplicidades, mantendo o primeiro registro de cada produto.
- Conversão de variáveis monetárias e numéricas.
- Tratamento de valores ausentes e inconsistências.
- Extração da categoria principal a partir da hierarquia original.
- Consolidação das categorias em grupos estratégicos.
- Criação de faixas de desconto e avaliação.
- Classificação de engajamento por grupo de categoria.
- Conversão dos preços de INR para BRL utilizando uma taxa histórica de referência.
- Identificação exploratória de temas positivos e negativos nos comentários.

A base final utilizada no Power BI contém **1.351 produtos distintos**.

### Conversão monetária

Os preços originais estavam expressos em rúpias indianas (INR). Para facilitar a interpretação dos indicadores, foi realizada uma conversão para reais (BRL), utilizando a taxa de referência adotada no projeto:

- Taxa utilizada: 1 INR = R$ 0,05731.
- Data de referência: 01/11/2026.

Os valores originais em INR foram preservados na base, juntamente com os valores convertidos.

A conversão é uma referência histórica utilizada para padronização analítica, não uma cotação em tempo real.

## Estrutura do dashboard

O dashboard foi desenvolvido no Power BI e organizado em cinco páginas:

### 01 — Visão Executiva

Apresentação dos principais indicadores do portfólio:

- Total de produtos.
- Quantidade de categorias.
- Preço médio original.
- Preço médio promocional.
- Desconto médio.
- Avaliação média.
- Distribuição de produtos por categoria e faixa de avaliação.

### 02 — Produtos e Categorias

Exploração da composição do portfólio:

- Distribuição de produtos por categoria.
- Análise de subcategorias.
- Produtos com maior engajamento por categoria.
- Comparação de avaliações, preços e quantidade de avaliações.

### 03 — Preços e Estratégia Comercial

Investigação das estratégias comerciais:

- Distribuição dos produtos por faixa de desconto.
- Comparação de descontos entre grupos de categorias.
- Relação entre preço promocional e avaliação.
- Investigação de possíveis associações entre descontos e engajamento.

### 04 — Customer Insights

Exploração da percepção dos consumidores:

- Distribuição dos produtos por faixa de avaliação.
- Identificação de temas negativos nos comentários.
- Comparação de sinais negativos por categoria.
- Relação entre avaliação e quantidade de sinais identificados.

### 05 — Recomendações

Consolidação dos principais achados em quatro frentes de atuação:

1. **Qualidade dos produtos:** investigar produtos com alto engajamento e avaliações abaixo de 4,0.
2. **Oportunidades de visibilidade:** identificar produtos bem avaliados, mas com baixo engajamento.
3. **Estratégia de preços:** avaliar descontos de maneira direcionada por categoria e produto.
4. **Experiência do consumidor:** investigar os principais sinais negativos identificados nos comentários.

## Principais resultados

A análise identificou alguns padrões relevantes:

### Composição do portfólio

- 1.351 produtos distintos.
- 9 categorias principais.
- Aproximadamente 97,19% dos produtos concentrados em três categorias: Electronics, Home&Kitchen e Computers&Accessories.

### Engajamento e satisfação

- Mediana de 4.740 avaliações por produto.
- 118 produtos classificados com alto engajamento e avaliação inferior a 4,0.
- 46 produtos com avaliação igual ou superior a 4,5 e engajamento abaixo da mediana.

### Estratégia de preços

A correlação de Spearman entre percentual de desconto e avaliação foi de **-0,150**, indicando uma associação negativa fraca.

Esse resultado não demonstra causalidade e sugere que descontos maiores, isoladamente, não explicam avaliações melhores.

### Customer Insights

No subconjunto de 118 produtos prioritários analisados para identificação de sinais negativos:

- 53 produtos apresentaram pelo menos um sinal identificado.
- Foram identificadas 69 ocorrências de sinais negativos.
- Os temas mais frequentes foram:
  - Durabilidade: 22 ocorrências.
  - Bateria: 17 ocorrências.
  - Desempenho: 13 ocorrências.
  - Preço: 9 ocorrências.

Os indicadores representam a presença de temas nos textos analisados em nível de produto, não a contagem individual de reclamações ou avaliações negativas.

## Recomendações para o negócio

A partir dos resultados, foram estruturadas quatro linhas de ação:

- Investigar a qualidade dos produtos com alto engajamento e avaliações inferiores a 4,0.
- Avaliar oportunidades de exposição para produtos bem avaliados e com menor visibilidade.
- Evitar estratégias generalizadas de desconto, considerando as particularidades de cada categoria.
- Monitorar os principais problemas identificados nos comentários para orientar melhorias no portfólio.

## Estrutura sugerida do repositório

```text
amazon-product-performance-customer-insights/
│
├── README.md
│
├── data/
│   └── amazon_powerbi_br.csv
│
├── notebook/
│   └── amazon_analysis.ipynb
│
├── powerbi/
│   └── amazon_product_performance.pbix
│
└── images/
    ├── 01-TechChallenge4.pdf
    ├── 02-Minimal E-Commerce Dashboard Background.png


## Considerações e limitações

A interpretação dos resultados deve considerar algumas limitações da base:

- A quantidade de avaliações (`rating_count`) é utilizada como indicador de engajamento, não como quantidade de vendas.
- Não há dados transacionais que permitam medir vendas, faturamento ou conversão.
- Os comentários estão agregados por produto, não sendo possível estabelecer correspondência individual entre cada comentário e sua respectiva avaliação.
- A identificação de temas nos comentários utiliza critérios textuais exploratórios e pode não capturar todas as manifestações dos consumidores.
- As correlações identificadas não demonstram relações causais.
- A análise de sinais negativos está restrita ao subconjunto de produtos prioritários selecionados.

## Entregáveis

- Notebook Python com preparação e análise exploratória dos dados.
- Base tratada e estruturada para utilização no Power BI.
- Dashboard interativo em Power BI (`.pbix`).
- Apresentação executiva em vídeo.

---

## Autor

Projeto desenvolvido como parte do **Tech Challenge – Fase 04**.

**Área:** Data Analytics  
**Tema:** Amazon Product Performance & Customer Insights

