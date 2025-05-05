# Modelagem de Dados com dbt e Amazon Redshift

Este projeto tem como objetivo demonstrar a modelagem e transformação de dados utilizando **dbt (Data Build Tool)**, com destino final em um **data warehouse na AWS Redshift Serverless**. A modelagem segue boas práticas de engenharia de dados, incluindo versionamento, modularização, testes de qualidade e documentação.

## Contexto

Utilizamos dados simulados de vendas de celulares para construir um modelo dimensional limpo e confiável. O objetivo é mostrar como transformar dados brutos em dados prontos para análise, utilizando dbt em conjunto com serviços da AWS.

## Tecnologias Utilizadas

- **Amazon Redshift Serverless** – Armazena os dados modelados para consultas analíticas.
- **dbt (Data Build Tool)** – Realiza transformações SQL, testes e documentação de forma modular.
- **Python 3.12** – Ambiente de execução para o dbt via Poetry.
- **Poetry** – Gerenciador de dependências para manter o ambiente isolado.
- **WSL2 (Ubuntu 24.04)** – Ambiente de desenvolvimento Linux dentro do Windows.
- **Git & GitHub** – Controle de versão e compartilhamento do projeto.
- **Terminal CLI** – Para execução de comandos do dbt (`dbt run`, `dbt test`, etc).

## Estrutura dos Dados

- `raw_mobile_sales`: Tabela bruta com os dados originais.
- `clean_mobile_sales`: Modelo dbt que limpa e agrega os dados por marca e produto.

## Testes Implementados com dbt

- `not_null`: Garante que colunas essenciais não contenham valores nulos.
- `unique`: Valida unicidade para colunas como `marca`.
- `accepted_values`: (removido após falha proposital para garantir integridade dos dados).

## Estrutura do Projeto

dbt_mobile_sales/
├── dbt_project/
│ ├── models/
│ │ ├── raw_mobile_sales.sql
│ │ └── clean_mobile_sales.sql
│ ├── models/raw_mobile_sales/schema.yml
│ ├── dbt_project.yml
│ └── profiles.yml
├── README.md
└── pyproject.toml


## Como Executar

1. **Instale as dependências** com Poetry:
   ```bash
   poetry install
   
Configure o perfil dbt (profiles.yml) com as credenciais do Redshift Serverless.

Execute a limpeza do projeto dbt:
poetry run dbt clean

Compile e execute os modelos:
poetry run dbt run

Rode os testes de qualidade dos dados:
poetry run dbt test

---

Exemplos de Execução
Você pode incluir capturas de tela dos seguintes comandos executados via WSL:

poetry run dbt run

poetry run dbt test

Visualização das tabelas no Redshift (ex: SELECT * FROM clean_mobile_sales)
