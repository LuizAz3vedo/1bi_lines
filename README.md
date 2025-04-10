# 🚀 Geração e Análise de Dados com 1 Bilhão de Registros usando DuckDB

Este projeto demonstra a geração de um arquivo de **1 bilhão de medições sintéticas** de temperatura por estação meteorológica, e a posterior análise estatística utilizando **DuckDB**.

## 📌 Objetivo

Simular um cenário de **Big Data** com dados meteorológicos sintéticos e realizar **consultas analíticas de forma eficiente** com DuckDB, operando diretamente sobre arquivos CSV, sem a necessidade de um banco de dados tradicional.

---

## 📂 Estrutura do Projeto

```
.
├── data/
│   ├── amostra_44k.csv         # Arquivo base com nomes de estações meteorológicas
│   ├── medicoes_1000000000.txt # Arquivo gerado com 1 bilhão de registros
├── criar_dataset_csv.py              # Script para geração dos dados sintéticos
├── usandoduckdb.py          # Script para análise estatística com DuckDB
└── README.md                   # Este arquivo
```

---

## ⚙️ Como Funciona

### 1. Geração dos Dados (`criar_dataset_csv.py`)

- **Entrada:** Um arquivo `amostra_44k.csv` com os nomes das estações meteorológicas.
- **Processamento:** 
  - Remove duplicatas dos nomes das estações.
  - Gera 1 bilhão de registros com valores de temperatura aleatórios entre -99.9 e 99.9.
  - Escrita no arquivo de saída em lotes de 10.000 linhas para otimização.
- **Saída:** Arquivo `medicoes_1000000000.txt` com registros no formato:
  
#### Execução

```bash
python criar_dataset_csv.py
```

### 2. Análise com DuckDB (`analisar_duckdb.py`)

- **Processamento:**
  - Lê o arquivo gerado diretamente utilizando o DuckDB.
  - Agrupa os dados por estação meteorológica.
  - Calcula estatísticas: **temperatura mínima**, **média** (arredondada) e **máxima** por estação.
  - Organiza a saída em ordem alfabética das estações.
- **Saída:** Exibição das estatísticas de temperatura por estação.

#### Execução

```bash
python usandoduckdb.py
```

---

## 📊 Exemplo de Saída

```plaintext
┌────────────────────────┬──────────────────┬──────────────────┬──────────────────┐
│ station                │ min_temperature  │ mean_temperature │ max_temperature  │
├────────────────────────┼──────────────────┼──────────────────┼──────────────────┤
│ ESTACAO_0001           │ -99.9            │ 0.1              │ 99.9             │
│ ESTACAO_0002           │ -98.3            │ -0.3             │ 97.6             │
│ ...                    │ ...              │ ...              │ ...              │
└────────────────────────┴──────────────────┴──────────────────┴──────────────────┘
```

---

## 🛠️ Tecnologias Utilizadas

- **Python 3**
- **DuckDB** – Utilizado para a consulta analítica eficiente diretamente em arquivos CSV
- **Módulos padrão do Python:** `os`, `random`, `time`

---

## 🚀 Requisitos

- Python 3.8 ou superior
- Instalar o DuckDB com:

  ```bash
  pip install duckdb
  ```

---

## 📈 Performance

- **Geração dos Dados:** A criação de 1 bilhão de registros pode demandar alguns minutos, dependendo das especificações do sistema e do disco disponível.
- **Consulta com DuckDB:** Realiza a leitura e análise do arquivo sem a necessidade de carregá-lo completamente na memória, otimizando a performance para grandes volumes de dados.

---

## 📌 Observações

- **Espaço em Disco:** Certifique-se de ter espaço suficiente (o tamanho do arquivo pode chegar a várias dezenas de GB, dependendo do formato dos dados).
- **Testes:** Para experimentos locais, é recomendável reduzir o número de registros modificando a variável `num_registros` nos scripts.

---

## 📫 Contato

Para dúvidas, sugestões ou contribuições, por favor, abra uma _issue_ no repositório ou entre em contato.

---
```
