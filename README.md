# MVP Engenharia de Dadoos 2025 - Projeto Correlix
Este projeto representa o MVP desenvolvido no contexto da disciplina de Engenharia de Dados, integrante da pós-graduação em Análise e Ciência de Dados.


## Objetivo ##
O **Projeto Corelix** tem como objetivo identificar oportunidades estratégicas a partir da correlação entre dados relevantes, utilizando técnicas de engenharia de dados e análise exploratória. A proposta é transformar grandes volumes de informação em insights acionáveis que apoiem a tomada de decisão.


## Plataforma Utilizada ##
- Google Cloud Plataform.


## Detalhamento ##
### 1. Bases de dados utilizdas: ###
As bases de dados utilizadas neste projeto são provenientes de um **problema de negócio real** relacionado ao setor de cobrança de uma empresa.

### 2. Coleta: ###
Como solução para coleta e armazenamento, as tabelas foram convertidas para o formato CSV e carregadas em um bucket do Google Cloud Platform (GCP).
2. Coleta e Upload Bucket GCP.png


### 3. Modelagem: ###
Para a modelagem dos dados, foi adotado o modelo dimensional do tipo **Star Schema**, utilizando o campo "contrato" como chave primária para a integração entre a tabela fato e as dimensões:
  - Tabela Fato: fato_cyber
  - Tabelas Dimensão: dim_produto, dim_bloqueio, dim_cyner

    + Catálogo de Dados*****

### 4. Carga: ###
As etapas do ETL são:


### 5. Análise: ###
- a. Qualidade dos dados:


- b. Solução do Problema:


## Autoavaliação: ##




