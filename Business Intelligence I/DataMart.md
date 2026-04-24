# Data Mart e Camada Semântica

## Onde estamos na arquitetura de dados

A arquitetura analítica segue uma sequência de camadas:

`OLTP → Staging/Repositório → Data Warehouse → Data Mart → Camada Semântica → Dashboard`

Cada camada deixa os dados mais organizados e mais próximos da tomada de decisão.

- OLTP: sistemas operacionais, onde os dados nascem.
- Staging/Repositório: área onde os dados brutos são carregados e tratados inicialmente.
- Data Warehouse: repositório central integrado, usado para análise histórica.
- Data Mart: subconjunto do DW focado em uma área de negócio.
- Camada Semântica: traduz os dados técnicos para linguagem de negócio.
- Dashboard: visualização final para análise.
  
 ## Data Warehouse

O Data Warehouse é o repositório central de dados analíticos da empresa.

Ele reúne dados de várias áreas, como:

- Vendas
- Clientes
- Logística
- Financeiro
- Operações

O DW é importante porque garante uma visão integrada e histórica da organização.

Mas atenção: o Data Warehouse não é feito diretamente para o usuário final. Ele pode ter muitas tabelas, várias dimensões, tabelas fato e relacionamentos complexos.

Por isso, para um analista ou gerente, navegar direto no DW pode ser difícil.

## Problema do Data Warehouse para usuários

Um usuário de negócio geralmente não quer mexer no DW inteiro.

Por exemplo, um gerente de vendas quer apenas saber:

1. Receita por produto
2. Desempenho por filial
3. Evolução das vendas
3. Ranking de clientes

Ele não precisa ver dados de RH, logística ou financeiro.

**É aí que entra o Data Mart.**

# O que é Data Mart

Um Data Mart é um subconjunto especializado do Data Warehouse.

Ele é organizado por área de negócio, como:

- Data Mart de Vendas
- Data Mart de Marketing
- Data Mart Financeiro
- Data Mart Hospitalar
- Data Mart de Logística

A ideia é entregar apenas os dados necessários para uma equipe específica.

Exemplo:
```
DW completo → contém tudo da empresa
Data Mart de Vendas → contém só dados úteis para análise comercial 
```

## Objetivos do Data Mart

O Data Mart serve para:

1. Simplificar o acesso aos dados
2. Focar em um domínio específico
3. Melhorar a performance das consultas
4. Facilitar a análise para usuários de negócio
5. Evitar que o usuário precise conhecer SQL ou modelagem dimensional

Ele deixa os dados mais fáceis de consumir no Power BI, Tableau ou outra ferramenta de BI.

## Data Mart vs Data Warehouse

| Data Warehouse                   | Data Mart                     |
| -------------------------------- | ----------------------------- |
| Visão completa da empresa        | Visão de um setor ou domínio  |
| Muitas tabelas e relacionamentos | Estrutura simplificada        |
| Centralizado e integrado         | Especializado por área        |
| Mais complexo de navegar         | Mais fácil de usar            |
| Base para toda a organização     | Usado por equipes específicas |
| Consultas mais pesadas           | Consultas mais rápidas        |

O Data Mart não substitui o Data Warehouse. Ele é criado a partir dele.

## Tipos de Data Mart

Existem três tipos principais:

- Data Mart Dependente

É criado diretamente a partir do Data Warehouse.

É o modelo mais recomendado, porque aproveita dados já tratados, integrados e consistentes.

- Data Mart Independente

É criado diretamente a partir dos sistemas operacionais, sem passar pelo DW.

Pode ser útil em alguns casos, mas tem risco de inconsistência e duplicação de regras.

- Data Mart Híbrido

Combina dados do Data Warehouse com fontes externas ou dados operacionais específicos.

É usado quando o DW não possui todos os dados necessários.

## Camada Semântica

A Camada Semântica é uma ponte entre o modelo técnico dos dados e a linguagem do negócio.

Ela transforma elementos técnicos como:

`IDs, chaves, joins, tabelas fato e dimensões`

em conceitos mais simples, como:

`Receita Total, Ticket Médio, Clientes Ativos, Margem de Lucro`

Ela funciona como um “tradutor” entre o banco de dados e o usuário final.

## Exemplos de métricas da Camada Semântica

Algumas métricas comuns são:

- Receita Total: soma dos valores de venda.
- Ticket Médio: receita total dividida pelo número de vendas.
- Margem de Lucro: diferença entre receita e custo.
- Número de Clientes: contagem de clientes únicos.
- Taxa de Cancelamento: percentual de clientes que cancelaram.

Essas métricas são criadas uma vez e reutilizadas em vários dashboards.

## Camada Semântica no Power BI

No Power BI, a camada semântica aparece no modelo de dados.

Ela pode ser construída com:

- Medidas DAX
- Colunas calculadas
- Hierarquias
- Relacionamentos entre tabelas
- KPIs

Exemplos de medidas DAX:
```DAX
Receita Total =
SUM(vendas_analitico[valor_total])
```
```DAX
Qtd Vendida =
SUM(vendas_analitico[quantidade])
```
```DAX
Ticket Médio =
DIVIDE([Receita Total], COUNT(vendas_analitico[id_venda]))
```
```DAX
Clientes =
DISTINCTCOUNT(vendas_analitico[id_cliente])
```
```DAX
Lucro Estimado =
SUM(vendas_analitico[valor_total])
- SUM(vendas_analitico[custo_total])
```

## Benefícios da Camada Semântica

A camada semântica ajuda em quatro pontos principais:

1. Padronização de métricas

Todo mundo usa a mesma definição de “Receita”, “Lucro”, “Ticket Médio” etc.

2. Consistência nas análises

Os relatórios usam as mesmas regras de negócio.

3. Facilidade para usuários

O usuário consegue criar análises sem escrever SQL.

4. Redução de erros

Evita cálculos diferentes para o mesmo indicador.

## Exemplo prático: Data Mart de Vendas

No exemplo da aula, o Data Mart de Vendas é criado com um schema separado no PostgreSQL.

Exemplo:

```SQl
CREATE SCHEMA datamart_vendas;
```

Depois, cria-se uma view analítica:
```SQL
CREATE OR REPLACE VIEW datamart_vendas.vendas_analitico AS
SELECT
    f.data,
    f.id_venda,
    f.id_item,
    p.produto,
    p.categoria,
    p.subcategoria,
    c.id_cliente,
    c.cidade_cliente,
    c.estado_cliente,
    fi.filial,
    fi.cidade,
    fi.estado,
    f.quantidade,
    f.valor_total,
    f.custo_total
FROM dw.fato_vendas f
JOIN dw.dim_produto p
    ON f.id_produto = p.id_produto
JOIN dw.dim_cliente c
    ON f.id_cliente_dw = c.id_cliente_dw
JOIN dw.dim_filial fi
    ON f.id_filial = fi.id_filial;
```

Essa view junta a tabela fato com as dimensões e entrega uma tabela mais simples para o Power BI.

## Por que criar uma view no Data Mart?

A view vendas_analitico facilita muito a análise porque:

- Esconde a complexidade dos joins
- Entrega os dados prontos
- Facilita a conexão com o Power BI
- Centraliza a lógica
- Evita que o usuário precise mexer diretamente nas tabelas do DW

Ou seja, para o Power BI, essa view aparece como uma tabela plana e fácil de usar.

## Dashboard de Vendas

Com o Data Mart conectado ao Power BI, o dashboard pode ter:

1. KPIs no topo
- Receita Total
- Quantidade Vendida
- Ticket Médio
- Número de Clientes Únicos
2. Gráficos recomendados
- Receita por mês
- Receita por produto
- Receita por filial
- Receita por categoria
- Top 10 produtos
- Vendas ao longo do tempo