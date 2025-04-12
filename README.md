# MVP Engenharia de Dadoos 2025 - Projeto Correlix
Este projeto representa o MVP desenvolvido no contexto da disciplina de Engenharia de Dados, integrante da pós-graduação em Análise e Ciência de Dados.


## Objetivo ##
O **Projeto Corelix** tem como objetivo identificar oportunidades estratégicas a partir da correlação entre dados relevantes, utilizando técnicas de engenharia de dados e análise exploratória. A proposta é transformar grandes volumes de informação em insights acionáveis que apoiem a tomada de decisão.


## Plataforma Utilizada ##
- Google Cloud Plataform **(GCP)**;
- SQL.


## Detalhamento ##
### 1. Bases de dados utilizdas: ###
As bases de dados utilizadas neste projeto são provenientes de um **problema de negócio real** relacionado ao setor de cobrança de uma empresa.

### 2. Coleta: ###
Como solução para coleta e armazenamento, as tabelas foram convertidas para o formato CSV e carregadas em um bucket do Google Cloud Platform (GCP).

### 3. Modelagem: ###
Para a modelagem dos dados, foi adotado o modelo dimensional do tipo **Star Schema**, utilizando o campo "contrato" como chave primária para a integração entre a tabela fato e as dimensões:
  - Tabela Fato: fato_cyber
  - Tabelas Dimensão: dim_produto, dim_bloqueio, dim_cyner

### 3.1 Catálogo Dados ###
<div align="center">
<img src="https://github.com/user-attachments/assets/bec530ab-df54-4ab4-9764-93a17eb94ae6" width="700px" />
</div>


### 4. Carga: ###
As etapas do ETL são:
- 4.1. Criação do Bucket:
<div align="center">
<img src="https://github.com/user-attachments/assets/4271ec66-9322-406b-9887-4f6f0190d8b3" width="700px" />
</div>

- 4.2. Upload Dos Dados em CSV:
<div align="center">
<img src="https://github.com/user-attachments/assets/4a71c1ac-90c2-4a94-bb83-64f9932a3b1e" width="700px" />
</div>

- *4.3. Transformação:  Não foi necessário realizar transformações nos dados, uma vez que já estavam padronizados e prontos para uso.*

- 4.4. Criação Tabelas no Data Warehouse:
 O passo a passo apresentado na imagem refere-se à criação da tabela dim_bloqueio e foi utilizado como base para estruturar as demais tabelas do modelo.
<div align="center">
<img src="https://github.com/user-attachments/assets/b0326d38-eda2-4a76-8b00-57722ad6b882" width="700px" />
</div>

- 4.5. Execução de Conciliação:
<div align="center">
<img src="https://github.com/user-attachments/assets/dd76b308-22c3-41c4-9866-107acfe00e84" width="700px" />
</div>


<div align="center">
<img src="https://github.com/user-attachments/assets/02aae33f-c60f-4ae9-aa33-8dc9207a84e5" width="700px" />
</div>

### 5. Análise: ###
- a. Qualidade dos dados:


- b. Solução do Problema:


## Autoavaliação: ##




