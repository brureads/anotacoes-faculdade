# Modelagem Multidimensional

## Visão geral da aula
A aula apresenta os conceitos fundamentais da **modelagem multidimensional**, que é uma forma de organizar dados para facilitar análises em Business Intelligence.

Os principais temas estudados são:

- Data Warehouse
- Star Schema
- Tabelas Fato
- Tabelas Dimensão
- Granularidade

## Objetivo da aula
Ao final da aula, o objetivo é entender e aplicar os conceitos centrais da modelagem multidimensional, especialmente para uso em BI.

A aula busca desenvolver a compreensão sobre:

- o que é um **Data Warehouse**
- como funciona a **modelagem multidimensional**
- a diferença entre **fato** e **dimensão**
- o que significa **granularidade**

## Do operacional ao analítico
A aula começa mostrando um problema importante: o modelo relacional tradicional funciona muito bem para sistemas operacionais do dia a dia, como registrar pedidos, atualizar cadastros e processar pagamentos.

Mas quando a empresa precisa:

- cruzar dados
- identificar tendências
- gerar relatórios
- apoiar decisões estratégicas

esse modelo se torna mais difícil para análise, porque costuma envolver:

- muitas tabelas
- muitos JOINs
- consultas mais complexas e lentas

Por isso surge a necessidade de uma estrutura voltada para análise.

## O que é Data Warehouse
O **Data Warehouse (DW)** é um ambiente preparado especificamente para análise de dados.

Ele funciona como um **repositório centralizado de dados históricos**, reunindo informações de várias fontes da empresa em um único lugar otimizado para consultas analíticas.

### O DW não é feito para:
- inserções rápidas e frequentes
- operações transacionais do dia a dia
- processamento em tempo real

### O DW é feito para:
- consultas analíticas complexas
- relatórios gerenciais
- dashboards estratégicos

## Exemplo prático: supermercado
A aula usa o exemplo de uma rede de supermercados para mostrar a diferença entre ambiente operacional e analítico.

### Sistema Operacional (OLTP)
- registra vendas no caixa
- atualiza estoque em tempo real
- processa pagamentos e devoluções

### Data Warehouse (OLAP)
- mostra faturamento por mês e região
- compara desempenho entre lojas
- identifica produtos mais vendidos

## Características fundamentais do Data Warehouse
Segundo Bill Inmon, um Data Warehouse deve ter quatro características principais:

### 1. Orientado por assunto
Os dados são organizados por temas do negócio, como vendas, clientes e produtos.

### 2. Integrado
O DW reúne dados de várias fontes e os padroniza em um formato consistente.

### 3. Histórico
Armazena dados ao longo do tempo, permitindo comparações e análises de evolução.

### 4. Não volátil
Depois de carregados, os dados não sofrem alterações constantes. Eles ficam estáveis para consulta.

## OLTP x OLAP
A aula reforça a diferença entre os dois modelos.

### OLTP
É voltado para o ambiente operacional.

- foco em operações do dia a dia
- muitas escritas
- dados atuais
- consultas rápidas e simples
- usado por operadores e sistemas

### OLAP
É voltado para análise.

- foco em leitura
- consultas complexas e agregadas
- dados históricos e consolidados
- usado por analistas e gestores

## Modelagem multidimensional
A modelagem multidimensional é usada dentro do Data Warehouse para facilitar a análise dos dados.

Diferente da modelagem relacional, ela organiza os dados de maneira mais intuitiva, pensando nas perguntas que o negócio quer responder.

Ela se baseia em dois elementos principais:

### Fatos
São os números e métricas que queremos analisar.

### Dimensões
São os contextos usados para analisar os fatos.

## Ralph Kimball e o Star Schema
A aula cita Ralph Kimball como um dos nomes mais importantes da modelagem para Data Warehouse.

Ele propôs a **modelagem dimensional bottom-up**, com foco nas necessidades analíticas dos usuários de negócio.

Sua principal contribuição foi o:

### Star Schema (Modelo Estrela)
É um modelo simples, intuitivo e eficiente para consultas analíticas.

## O que é Star Schema
O **Star Schema** é um modelo em que existe:

- uma **tabela fato** no centro
- várias **tabelas dimensão** ao redor

A tabela fato guarda as métricas.
As dimensões guardam o contexto.

Essa estrutura parece uma estrela, por isso recebe esse nome.

## Exemplo de Star Schema de vendas
No exemplo apresentado na aula, a **Fato_Vendas** fica no centro com métricas como:

- valor
- quantidade
- comissão

Ao redor ficam dimensões como:

- **Dim_Cliente**
- **Dim_Produto**
- **Dim_Tempo**
- **Dim_Vendedor**
- **Dim_Cidade**

Cada dimensão se conecta diretamente à tabela fato.

## O que é uma tabela fato
A **tabela fato** é o coração do modelo estrela.

Ela guarda os **eventos mensuráveis do negócio**, ou seja, os números que serão analisados.

### Características da tabela fato
- contém métricas
- armazena valores numéricos
- permite cálculos e agregações
- apoia indicadores e KPIs

### Exemplos de métricas
- receita
- custo
- quantidade
- comissão

## Exemplo de Fato_Vendas
No exemplo da aula, a tabela fato possui:

### Chaves
- data
- id_cliente
- id_produto
- id_vendedor

Essas chaves ligam a tabela fato às dimensões.

### Métricas
- valor
- quantidade
- comissão

Ou seja, a tabela fato mistura:

- **chaves estrangeiras**, que conectam aos contextos
- **métricas**, que são os números analisados

## O que é uma dimensão
As **tabelas dimensão** fornecem o contexto descritivo para os fatos.

Elas permitem:

- filtrar
- agrupar
- segmentar
- analisar os números por diferentes perspectivas

As dimensões ajudam a responder perguntas como:

- **Quem?**
- **O quê?**
- **Onde?**
- **Quando?**

## Exemplos de dimensões
### Dim_Cliente
- nome do cliente
- cidade e estado
- segmento

### Dim_Produto
- nome do produto
- categoria
- marca
- fabricante

### Dim_Tempo
- dia
- mês
- ano
- trimestre
- semestre
- dia da semana
- feriados

## Exemplo prático de análise
A aula traz a pergunta:

**“Qual categoria de produto vende mais no mês de dezembro em Brasília?”**

Para responder isso, seria necessário combinar:

- **Dim_Produto** → categoria
- **Dim_Tempo** → dezembro
- **Dim_Cidade** → Brasília
- **Fato_Vendas** → valor total

Esse é o poder da análise multidimensional: cruzar contextos diferentes com uma métrica.

## Por que o Star Schema é ideal para BI
O modelo estrela é muito usado em BI porque traz várias vantagens:

### Menos JOINs
Reduz a quantidade de junções nas consultas.

### Leitura facilitada
Fica mais fácil de entender, até para quem não é muito técnico.

### Alta performance
Consultas analíticas tendem a ser mais rápidas.

### Relatórios simples
Ferramentas como Power BI e Tableau se conectam muito bem a esse modelo.

## Modelo relacional x modelo estrela
A aula compara os dois modelos:

### Modelo relacional
- muitas tabelas
- muitas dependências
- muitas chaves estrangeiras
- altamente normalizado
- melhor para operações

### Modelo estrela
- menos tabelas
- estrutura mais simples
- dimensões desnormalizadas
- menos JOINs
- melhor para leitura e análise

Na prática, os dados costumam nascer no modelo relacional e depois são transformados para o modelo estrela no processo de ETL.

## O que é granularidade
A **granularidade** define o nível de detalhe que cada linha da tabela fato representa.

A pergunta principal é:

**O que exatamente cada linha da tabela fato representa?**

Essa é uma das decisões mais importantes da modelagem dimensional.

## Exemplos de granularidade
### Granularidade mensal
Cada linha representa o total de vendas por mês.

- menos dados
- menos detalhe
- análises mais limitadas

### Granularidade diária
Cada linha representa o total de vendas por dia.

- equilíbrio entre detalhe e performance

### Granularidade por venda individual
Cada linha representa uma venda específica.

- máximo detalhe
- maior volume de dados

## Granularidade no app de transporte
A aula usa o exemplo de um app como Uber ou 99.

### Granularidade por corrida
Cada linha representa uma corrida individual.

Permite:
- analisar trajetos
- identificar motoristas
- avaliar tempo e distância

Mas gera muito mais dados.

### Granularidade diária
Cada linha representa os totais do dia por cidade.

Permite:
- ver tendências diárias
- comparar cidades

Mas perde o detalhe individual.

## Impacto da granularidade
A escolha da granularidade afeta diretamente o projeto.

### Volume de dados
Quanto mais detalhe, mais registros serão armazenados.

### Performance
Mais dados podem deixar consultas mais lentas.

### Tipo de análise possível
Se os dados forem agregados demais, perde-se a capacidade de fazer análises detalhadas.

A aula destaca uma regra importante:

**se você perder o detalhe na granularidade, não consegue recuperar depois**

Por isso, muitas vezes é melhor armazenar dados mais detalhados e agregar depois quando necessário.

## Resumo final da aula
Os principais pontos da aula foram:

### Data Warehouse
É um repositório centralizado de dados históricos voltado para análise.

### OLTP x OLAP
OLTP serve para operação; OLAP serve para análise.

### Star Schema
É o modelo estrela com uma tabela fato central e dimensões ao redor.

### Fatos e dimensões
- **Fatos** são métricas numéricas
- **Dimensões** são os contextos descritivos

### Granularidade
É o nível de detalhe de cada linha da tabela fato e influencia volume, desempenho e capacidade analítica.

## Conclusão
A modelagem multidimensional é essencial em BI porque organiza os dados de forma mais simples e eficiente para análise.

Com ela, é possível:

- entender melhor os dados
- montar modelos mais intuitivos
- criar relatórios e dashboards com mais facilidade
- apoiar decisões estratégicas com mais clareza
