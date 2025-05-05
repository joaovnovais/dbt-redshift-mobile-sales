# Projeto dbt_mobile_sales

Este projeto utiliza o **dbt (data build tool)** para transformar e testar dados de vendas de dispositivos móveis armazenados no **Amazon Redshift**. O foco está em preparar os dados para análises de receita e volume de vendas por marca e produto.

---

## Estrutura do Projeto

```bash
dbt_mobile_sales/
├── dbt_project/
│   ├── models/
│   │   ├── raw_mobile_sales/
│   │   │   └── raw_mobile_sales.sql        # Modelo raw (dados brutos)
│   │   ├── clean_mobile_sales/
│   │   │   └── clean_mobile_sales.sql      # Modelo clean (transformado)
│   │   └── schema.yml                      # Metadados e testes
│   ├── dbt_project.yml                     # Configurações do dbt
│   ├── packages.yml                        # Dependências dbt
│   └── profiles.yml                        # Conexão com Redshift

---

Modelos
raw_mobile_sales
Tipo: View

Tabela: mobile_sales.raw_data

Descrição: Representa os dados brutos carregados no Redshift, sem transformação.

clean_mobile_sales
Tipo: View

Descrição: Modelo transformado com:

Agrupamento por marca e produto

Cálculo de receita total (receita_total)

Cálculo de unidades vendidas (total_vendido)

Remoção de nulos e duplicatas

---

# Fonte de Dados

sources:
  - name: mobile_sales
    schema: public
    tables:
      - name: raw_data

---

# Testes Implementados
Coluna	Testes Aplicados
marca	not_null, unique
produto	not_null
receita_total	not_null
total_vendido	not_null

---

# Como Executar
Requisitos
Python com Poetry

Amazon Redshift configurado (via profiles.yml)

Passos
# Limpar diretórios temporários
poetry run dbt clean

# Executar os modelos
poetry run dbt run

# Rodar os testes
poetry run dbt test
