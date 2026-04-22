# Data Warehouse no PostgreSQL

## Visão geral da aula
A aula mostra como implementar um **Data Warehouse (DW)** no **PostgreSQL**, unindo:

- modelagem dimensional;
- PostgreSQL aplicado;
- integração com Power BI.



## Revisão conceitual
Antes da prática, a aula relembra alguns pontos importantes de BI:

- conceito de **Business Intelligence**;
- diferenças entre **BI, Data Science e Analytics**;
- **modelagem multidimensional**;
- uso de **Power Query** para transformação de dados.

A proposta da aula é sair da teoria e armazenar os dados em um **Data Warehouse real**.



## Por que usar um Data Warehouse?
O Data Warehouse é importante porque permite:

- **centralizar dados** vindos de vários sistemas;
- gerar **relatórios estratégicos**;
- manter o **histórico preservado**;
- apoiar decisões com base em dados consolidados.

Em vez de informações espalhadas, a empresa passa a ter uma fonte confiável para análise.



## Arquitetura simplificada de BI
O fluxo de uma solução de BI segue uma sequência de camadas:

1. **Núcleo OLTP**  
   Sistemas operacionais como ERP, CRM e vendas.

2. **Camada ETL**  
   Extração, transformação e carga dos dados.

3. **Armazenamento e BI**  
   Data Warehouse, ferramentas analíticas e dashboards.

Cada camada tem sua função:
- o sistema operacional gera os dados;
- o ETL prepara os dados;
- o DW armazena os dados de forma analítica;
- o BI apresenta as informações para decisão.



## OLTP x OLAP
### OLTP
É o ambiente operacional.

- muitas transações simultâneas;
- dados normalizados;
- foco em registro e atualização;
- exemplos: ERP, CRM, e-commerce.

### OLAP
É o ambiente analítico.

- leitura intensa;
- consultas complexas;
- dados agregados e desnormalizados;
- foco em análise e histórico;
- exemplos: Data Warehouse e Data Mart.

### Resumindo
- **OLTP** = operação do dia a dia  
- **OLAP** = análise para tomada de decisão



## O que é PostgreSQL?
PostgreSQL é um **SGBD relacional open source**, conhecido por:

- robustez;
- conformidade com SQL;
- bom desempenho;
- uso gratuito;
- grande adoção no mercado.



## Por que usar PostgreSQL em BI?
O PostgreSQL é uma boa escolha para BI porque oferece:

- **gratuidade e código aberto**;
- **alta performance e escalabilidade**;
- **SQL avançado**;
- **compatibilidade com Power BI**.

Ele é muito útil tanto em ambiente acadêmico quanto profissional.



## Ferramentas usadas na aula
A aula trabalha com este fluxo:

**CSV → PostgreSQL → Power BI**

Ferramentas:

- **PostgreSQL**: banco analítico onde o DW será criado  
- **PgAdmin**: interface gráfica para gerenciar o banco  
- **SQL**: linguagem usada para criar e manipular tabelas  
- **Power BI**: visualização e dashboards  



## Dataset usado
O projeto usa uma base fictícia chamada **Supermercado ABC 100k**, com:

- **100.000 registros**
- **5 dimensões**
- **1 tabela fato**

As dimensões citadas são:

- Produto
- Filial
- Cliente
- Pagamento
- Calendário

A tabela fato central é a **Fato_Vendas**.



## Problemas de qualidade na base bruta
A aula destaca que dados reais costumam vir com problemas, como:

- **datas inválidas**
- **espaços extras e problemas de encoding**
- **tipos incorretos**
- **duplicidades e campos vazios**

Exemplos:
- datas em formato errado;
- valores monetários armazenados como texto;
- campos obrigatórios em branco;
- linhas repetidas.

Isso mostra a importância do tratamento antes da análise.



## Objetivo do projeto
O objetivo é transformar a base bruta em um **Data Warehouse dimensional**, usando **Star Schema**.

Nesse modelo:

- as **dimensões** guardam o contexto;
- a **tabela fato** guarda as métricas.



## Star Schema do projeto
### Tabelas dimensão
As dimensões respondem perguntas como:

- quem?
- o quê?
- onde?
- quando?

Dimensões citadas:

- **Dim_Produto**: produto, marca, categoria, subcategoria  
- **Dim_Filial**: nome, cidade, estado  
- **Dim_Cliente**: código e segmento do cliente  
- **Dim_Pagamento**: forma de pagamento  
- **Dim_Calendario**: data, mês, trimestre, ano  

### Tabela fato
A **Fato_Vendas** armazena:

- chaves estrangeiras das dimensões;
- medidas numéricas do negócio.

Métricas citadas:

- quantidade vendida;
- valor líquido;
- custo total;
- imposto aplicado.


## Implementação no PostgreSQL
### 1. Criar o banco de dados
Primeiro, cria-se um banco específico para o DW.

Exemplo:
```sql
CREATE DATABASE dw_supermercado;
