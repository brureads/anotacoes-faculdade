# Revisão - Prova

Last Updated: 14 de abril de 2026 14:48

- criar um data base

- ir em schema e criar um repositorio

```sql
CREATE TABLE repositorio.hospital (
id_atendimento TEXT,
data_atendimento TEXT,
id_paciente TEXT,
nome_paciente TEXT,
cidade_paciente TEXT,
estado_paciente TEXT,
faixa_etaria TEXT,
sexo TEXT,
convenio TEXT,
forma_pagamento TEXT,
origem_paciente TEXT,
unidade_id TEXT,
unidade TEXT,
cidade_unidade TEXT,
estado_unidade TEXT,
especialidade TEXT,
medico TEXT,
procedimento TEXT,
categoria_procedimento TEXT,
status_atendimento TEXT,
tempo_internacao_horas TEXT,
valor_procedimento TEXT,
custo_hospital TEXT,
valor_repassado_convenio TEXT,
lucro_estimado TEXT
)
```

- depois pegar o arquivo csv e passar pro postgreSQL

```sql
COPY repositorio.hospital
FROM 'C:\Users\Public\Hospital_50k_Revisao_Prova_v2 (1).csv'
DELIMITER ';'
CSV HEADER
ENCODING 'UTF8';
```

- agora é hora de criar as dimensões, vá em schema e crie um schema chamado dw

- dentro do dw iremos criar as  3 dimensões que o professor pediu
1. Primeira dimensão: dim_paciente

- criar a tabela

```sql
CREATE TABLE dw.dim_paciente (
id_paciente SERIAL PRIMARY KEY,
nome_paciente VARCHAR(150),
cidade_paciente VARCHAR(100),
estado_paciente VARCHAR(100),
faixa_etaria VARCHAR(100),
sexo VARCHAR(100)
);
```

- inserir os dados na tabela

```sql
INSERT INTO dw.dim_paciente(nome_paciente, cidade_paciente, estado_paciente, faixa_etaria, sexo)
SELECT DISTINCT
nome_paciente,
cidade_paciente,
estado_paciente,
faixa_etaria,
sexo
FROM repositorio.hospital
WHERE nome_paciente IS NOT NULL;
```

- conferir a tabela e ver se deu certo

```sql
SELECT * FROM dw.dim_paciente
```

1. Segunda dimensão: dim_unidade

- criar tabela

```sql
CREATE TABLE dw.dim_unidade (
unidade_id SERIAL PRIMARY KEY,
unidade VARCHAR(150),
cidade_unidade VARCHAR(100),
estado_unidade VARCHAR(100)
);
```

- inserir os dados na tabela

```sql
INSERT INTO dw.dim_unidade(unidade, cidade_unidade, estado_unidade)
SELECT DISTINCT
unidade,
cidade_unidade,
estado_unidade
FROM repositorio.hospital
WHERE unidade IS NOT NULL;
```

- conferir a tabela e ver se deu certo

```sql
SELECT * FROM dw.dim_unidade
```

1. Terceira dimensão: dim_identificacao_de_atendimento

- criar tabela

```sql
CREATE TABLE dw.dim_identificacao_de_atendimento (
id_atendimento SERIAL PRIMARY KEY,
data_atendimento VARCHAR(150),
status_atendimento VARCHAR(100)
);

```

- inserir os dados na tabela

```sql
INSERT INTO dw.dim_identificacao_de_atendimento(data_atendimento, status_atendimento)
SELECT DISTINCT
data_atendimento,
status_atendimento
FROM repositorio.hospital
WHERE unidade IS NOT NULL;
```

- conferir a tabela e ver se deu certo

```sql
SELECT * FROM dw.dim_identificacao_de_atendimento
```

- tabela fato

```sql
CREATE TABLE dw.fato_atendimentos (
    id_atendimento INT PRIMARY KEY,
    data_atendimento TIMESTAMP,
    id_paciente_dw INT,
    id_unidade INT,
    id_identificacao_atendimento INT,
    convenio TEXT,
    forma_pagamento TEXT,
    status_atendimento TEXT,
    tempo_internacao_horas INT,
    valor_procedimento NUMERIC(12,2),
    custo_hospitalar NUMERIC(12,2),
    valor_repassado_convenio NUMERIC(12,2),
    lucro_estimado NUMERIC(12,2),

    FOREIGN KEY (id_paciente_dw) REFERENCES dw.dim_paciente(id_paciente),
    FOREIGN KEY (id_unidade) REFERENCES dw.dim_unidade(unidade_id),
    FOREIGN KEY (id_identificacao_atendimento) REFERENCES dw.dim_identificacao_de_atendimento(id_atendimento)
);
```

- insert da tabela fato

```sql
INSERT INTO dw.fato_atendimentos (
    id_atendimento,
    data_atendimento,
    id_paciente_dw,
    id_unidade,
    id_identificacao_atendimento,
    convenio,
    forma_pagamento,
    status_atendimento,
    tempo_internacao_horas,
    valor_procedimento,
    custo_hospitalar,
    valor_repassado_convenio,
    lucro_estimado
)
SELECT
    b.id_atendimento::INT,
    b.data_atendimento::TIMESTAMP,
    p.id_paciente,
    u.unidade_id,
    i.id_atendimento,
    b.convenio,
    b.forma_pagamento,
    b.status_atendimento,
    REPLACE(b.tempo_internacao_horas, ',', '.')::NUMERIC(12,2),
    REPLACE(b.valor_procedimento, ',', '.')::NUMERIC(12,2),
    REPLACE(b.custo_hospital, ',', '.')::NUMERIC(12,2),
    REPLACE(b.valor_repassado_convenio, ',', '.')::NUMERIC(12,2),
    REPLACE(b.lucro_estimado, ',', '.')::NUMERIC(12,2)
FROM repositorio.hospital b
JOIN dw.dim_paciente p
    ON b.id_paciente::INT = p.id_paciente
JOIN dw.dim_unidade u
    ON b.unidade = u.unidade
JOIN dw.dim_identificacao_de_atendimento i
    ON b.id_atendimento::INT = i.id_atendimento;
```

- agora ir pro POWER BI
