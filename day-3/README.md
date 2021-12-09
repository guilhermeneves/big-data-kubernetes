# Data Lake

Landing Zone (CSV, XML, etc...)
Processing Zone (Converte para parquet, delta, comprimi,e tc...)

Camada Serving: pode ser clickhouse, postgres, cassandra, etc...

## Use cases Batch

- Distributed Data Store for Microservices Apps

Com microservicos, temos varios databases devido a DDD e times criando varios servicos, fica dificil dar manutencao no db e fica dificil para data analytics.

Com o yugabyteDb fica mais facil gerenciar, sendo apenas um cluster e todos os microservicos compartilhar dele.

Exemplo no Repo
apps -> ingestion-data-stores -> datastore

Data Api Random Sample
https://random-data-api.com/

Cassandra: nao recomendado para analytics, pois o CQL 'e bem limitado.

- Processing File on Data Lake using Apache Spark and Delta Lake

demos use-case-2

coreRequest=250m (trocar com core)

- Data Exploration with Apache Spark and Apache Zepelin

Apache Zepellin: Interpretador Multi source
Dremio consome muita memoria (fica muito caro)

Trino JSON extract para extrair JSON, agrupamento por duas bases.

## Airflow on Kubernetes


