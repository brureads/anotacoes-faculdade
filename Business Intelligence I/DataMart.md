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