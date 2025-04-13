# MVP Engenharia de Dadoos 2025 - Projeto Correlix
Este projeto representa o MVP desenvolvido no contexto da disciplina de Engenharia de Dados, integrante da pós-graduação em Análise e Ciência de Dados.

## Objetivo ##
O **Projeto Correlix** tem como objetivo validar a integridade dos dados entre a tabela fato e a dimensão Cyner, garantindo que todos os clientes que estão aptos a serem cobrados estejam devidamente registrados na tabela Cyner, a fim de evitar falhas no processo de cobrança e garantir a inclusão de 100% dos contratos válidos.

## Plataforma Utilizada ##
- Google Cloud Plataform **(GCP)**;
- SQL.

## Detalhamento ##
### 1. Bases de dados utilizdas: ###
As bases de dados utilizadas neste projeto são provenientes de um **problema de negócio real** relacionado ao setor de cobrança de uma empresa do segmento de Telecomunicações.

### 2. Coleta: ###
Para a coleta e armazenamento dos dados, foi utilizada a plataforma **Google Cloud Platform (GCP)**, aproveitando seus serviços gerenciados e escaláveis.
As bases de dados, originalmente extraídas de sistemas internos da empresa (relacionadas ao setor de cobrança), foram exportadas em formato CSV, garantindo compatibilidade e facilidade de manipulação inicial.

### 3. Modelagem: ###
Para a modelagem dos dados, foi adotado o modelo dimensional do tipo **Star Schema**, por sua simplicidade e desempenho em consultas analíticas.

Estrutura do Esquema Estrela:
- **Tabela Fato:**
  - fato_cyber (PK = "Contrato").

- **Tabelas Dimensão:**
  - dim_produto (FK = "Contrato");
  - dim_bloqueio (FK = "Contrato");
  - dim_cyner (FK = "Contrato");

### 3.1 Catálogo Dados ###
<div align="center">
<img src="https://github.com/user-attachments/assets/bec530ab-df54-4ab4-9764-93a17eb94ae6" width="700px" />
</div>

### 4. Carga: ###
Como solução de armazenamento, foi criado um bucket no Google Cloud Storage, estruturado em pastas para organização por data e categoria de dado. Essa organização segue boas práticas de data lake, facilitando versionamento e governança. 

As etapas são:
- 4.1. Criação do Bucket: 
<div align="center">
<img src="https://github.com/user-attachments/assets/4271ec66-9322-406b-9887-4f6f0190d8b3" width="700px" />
</div>

- 4.2. Upload Dos Dados em CSV: Durante o MVP, os arquivos CSV foram carregados manualmente no bucket.
<div align="center">
<img src="https://github.com/user-attachments/assets/4a71c1ac-90c2-4a94-bb83-64f9932a3b1e" width="700px" />
</div>

- *4.3. Transformação:  Não foi necessário realizar transformações nos dados, uma vez que já estavam padronizados e prontos para uso.*

- 4.4. Criação Tabelas no Data Warehouse:
 O passo a passo apresentado na imagem refere-se à criação da tabela dim_bloqueio e foi utilizado como base para estruturar as demais tabelas do modelo.
<div align="center">
<img src="https://github.com/user-attachments/assets/b0326d38-eda2-4a76-8b00-57722ad6b882" width="700px" />
</div>

Resultado criação demais tabelas:
<div align="center">
<img src="https://github.com/user-attachments/assets/77ffa5b4-cee2-4cc5-93bd-2e8e52273253" width="700px" />
</div>

- 4.5. Execução de Conciliação:
Nessa fase, foi utilização a linguegm SQL no Big Query para relacionar as informações:
<div align="center">
<img src="https://github.com/user-attachments/assets/dd76b308-22c3-41c4-9866-107acfe00e84" width="700px" />
</div>

<div align="center">
<img src="https://github.com/user-attachments/assets/02aae33f-c60f-4ae9-aa33-8dc9207a84e5" width="700px" />
</div>

### 5. Análise: ###
- Qualidade dos dados e Solução do Problema:
  - A partir de uma análise preliminar, comparando os dados da tabela fato com a dimensão Cyner, observa-se na imagem abaixo que **39,6 mil contratos não estão presentes na dimensão Cyner**, ou seja, não estão aptos para cobrança.
<div align="center">
<img src="https://github.com/user-attachments/assets/3f71268c-cfa4-4c09-a6c4-1cabffef3f21" width="700px" />
</div>

  - Ao investigar a **dimensão de bloqueio**, foi identificado que todos os contratos não aptos *estão associados a bloqueios* do tipo "No Dunning" ou "Migração Indevida". Assim, **a ausência desses contratos na dimensão Cyner é justificada**.
<div align="center">
<img src="https://github.com/user-attachments/assets/0f3a4199-a7fc-4f18-9f81-9396927ed96e" width="700px" />
</div>

  - *Conclusão: A análise demonstrou que, do total de 104.610 contratos, apenas **64.923 estão aptos para cobrança**, o que representa cerca de **62% da base total**. Os 39.687 contratos restantes (38%) não estão presentes na dimensão Cyner, o que à primeira vista poderia indicar uma falha de qualidade nos dados. No entanto, ao investigar a dimensão de bloqueio, identificou-se que todos os contratos não localizados estão vinculados a bloqueios específicos, como **"No Dunning"** e **"Migração Indevida"**, que os tornam inelegíveis para cobrança. Portanto, **a ausência desses 39,6 mil contratos na dimensão Cyner não representa uma falha nos dados, mas sim um reflexo coerente das regras de negócio**.
Esse cruzamento entre a tabela fato e a dimensão Cyner **demonstra consistência nas informações e confirma que os contratos foram corretamente excluídos da base de cobrança**, conforme critérios operacionais.*

## Autoavaliação: ##
Durante o desenvolvimento do Projeto Correlix, tive a oportunidade de aplicar na prática diversos conceitos de engenharia de dados, como modelagem dimensional (Star Schema), uso do Google Cloud Platform e manipulação de grandes volumes de dados usando SQL no BigQuery. Foi especialmente valioso compreender a importância do relacionamento entre tabelas fato e dimensão para garantir a integridade dos dados e a confiabilidade das análises.

Um dos maiores desafios foi garantir que os dados estivessem bem organizados desde o armazenamento até o cruzamento final, o que exigiu atenção redobrada à consistência dos arquivos CSV e à padronização das chaves de relacionamento. Além disso, utilizar joins e funções analíticas para validar regras de negócio (como os bloqueios de cobrança) foi uma etapa essencial para entender como os dados representam os processos reais da empresa.

Acredito que o projeto contribuiu significativamente para minha evolução na área, especialmente no que diz respeito à visão crítica sobre qualidade de dados e construção de pipelines analíticos.

Se fosse recomeçar, faria uma etapa mais robusta de documentação desde o início e buscaria automatizar mais processos, como a carga de dados no bucket.

Como principal lição, levo a importância de alinhar dados com regras de negócio. Não basta os dados estarem "certos" tecnicamente — eles precisam refletir a realidade e gerar valor. Esse projeto me fez enxergar melhor o papel estratégico da engenharia de dados em decisões corporativas.
