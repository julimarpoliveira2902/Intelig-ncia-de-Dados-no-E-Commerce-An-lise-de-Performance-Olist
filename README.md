# 📊 Inteligência de Dados no E-Commerce: Análise de Performance Olist

Este repositório contém o projeto final do meu curso de formação em **Análise de Dados**. O objetivo principal foi aplicar o ciclo completo de dados (Ingestão, Tratamento, Análise Exploratória e Visualização de Dados) utilizando dados reais do mercado de e-commerce brasileiro para gerar insights estratégicos de negócios.

---

## 🏗️ Arquitetura do Projeto

O fluxo de trabalho foi dividido de forma modular, garantindo eficiência de processamento e clareza analítica:

```mermaid
graph TD
    A[olist_orders_dataset.csv] --> D[Fato_Vendas]
    B[olist_order_items_dataset.csv] --> D
    C[olist_products_dataset.csv] --> E[Dim_Produtos]
    D --> F[Merge & Pipeline de Tratamento no Pandas]
    E --> F
    F --> G[Análise Exploratória - Python]
    F --> H[Exportação: olist_vendas_tratado.csv]
    H --> I[Dashboard Interativo - Looker Studio]

🛠️ Tecnologias e Ferramentas Utilizadas
Linguagem Principal: Python 3

Manipulação de Dados: Pandas & NumPy

Visualização Estatística: Matplotlib & Seaborn

Business Intelligence (BI): Looker Studio

IDE: Google Colab

📑 Etapas de Desenvolvimento
1. Seleção e Cruzamento de Dados (Merge)
Foram utilizadas 3 tabelas interligadas que atendem rigorosamente aos requisitos mínimos de volumetria da entrega:

olist_orders_dataset.csv (Tabela Fato - Pedidos): +99k linhas, contendo timestamps essenciais.

olist_order_items_dataset.csv (Tabela Fato - Itens): +112k linhas, com informações de preços e fretes.

olist_products_dataset.csv (Tabela Dimensão - Produtos): +32k linhas, contendo categorias e dimensões de produtos.

As tabelas foram unidas via chaves estrangeiras (order_id e product_id) em um dataframe consolidado utilizando a função pd.merge() do Pandas.

2. Tratamento de Dados (Data Cleaning)
Valores Ausentes: Identificação e preenchimento de dados nulos de categorias com a string "NÃO INFORMADO".

Padronização: Conversão de strings de data para o tipo nativo datetime e padronização dos textos de categoria para letras maiúsculas.

Colunas Derivadas (Regras de Negócio):

valor_total_item: Soma do preço do produto com o custo do frete (price + freight_value).

ano_mes_pedido: Extração do ano/mês (YYYY-MM) do carimbo de data para criação de eixos cronológicos eficientes.

3. Análise Exploratória de Dados (EDA)
As principais descobertas estatísticas do projeto foram:

Ticket Médio: O valor médio gasto por item foi de R$ 137,75, enquanto a mediana foi de R$ 84,90. Essa discrepância aponta para uma cauda longa à direita provocada por produtos premium (outliers).

Dinâmica do Frete: A correlação linear entre o preço do produto e o frete cobrado é nula (0.01). Isso indica que o preço final não dita o frete, o qual depende exclusivamente de fatores geográficos (distância) e peso/cubagem.

Otimização de SEO: A maior parte dos produtos cadastrados apresenta nomes entre 40 e 60 caracteres, um padrão de indexação otimizado para buscadores.

## 📊 Dashboard Interativo (Looker Studio)

O dashboard de BI foi projetado em **duas páginas estratégicas** utilizando técnicas de *Data Storytelling* para facilitar a tomada de decisão:

### 📱 Página 1 - Overview Comercial & Receita
Focada em acompanhar a saúde financeira do negócio, permitindo analisar picos de venda históricos e as categorias de maior faturamento. Contém controles interativos de período temporal e categorias de produtos.

![Overview Comercial & Receita](./imagens/Pagina_1.jpeg)

---

### ⚙️ Página 2 - Eficiência Operacional & Dinâmica de Preços
Focada no monitoramento logístico e análise de dispersão de fretes para identificação de distorções geográficas e anomalias de cobrança de envio.

![Eficiência Operacional & Dinâmica de Preços](./imagens/Pagina_2.jpeg)

🔗 Links do Projeto

📓 Notebook do Google Colab [https://colab.research.google.com/drive/1XLXy5BPYXZyYSW1SoY8Le2PdgFURogcx?usp=sharing]

👤 Autor

Julimar Pedro de Oliveira

Meu LinkedIn [https://www.linkedin.com/in/julimar-oliveira-59984a1a4/]






