## Integração e Sincronização de Dados Entre SQL Server e Elasticsearch Usando KNIME


### Índice

- [Introdução](#introdução)
- [Tecnologias Utilizadas](#tecnologias-utilizadas)
- [Pré-requisitos](#pré-requisitos)
- [Configuração do Ambiente](#configuração-do-ambiente)
- [Instruções de Uso](#instruções-de-uso)




## Introdução

O objetivo final desse pipeline no pode ser a transformação e a sincronização de dados entre um banco de dados SQL Server e o Elasticsearch. Especificamente, você está processando dados no SQL Server com etapas de filtragem, ordenação, e manipulação, e, em seguida, realizando consultas e operações no Elasticsearch, para indexação dos dados 




## Tecnologias Utilizadas

- **Docker**: Utilizado para empacotar e distribuir as aplicações em contêineres, garantindo que elas funcionem em qualquer ambiente.
- **SQL Server**: Banco de dados relacional usado para armazenar dados estruturados.
- **KNIME**: Plataforma de análise de dados utilizada para processar, transformar e modelar os dados.
- **Elasticsearch**: Motor de busca e análise utilizado para indexar e realizar buscas nos dados processados.



## Pré-requisitos

- Docker instalado ([instruções de instalação](https://docs.docker.com/get-docker/))
- SQL Server instalado e configurado ([instruções de instalação](https://docs.microsoft.com/pt-br/sql/database-engine/install-windows/install-sql-server?view=sql-server-ver15))
- KNIME instalado ([download](https://www.knime.com/downloads))
- Elasticsearch instalado ([instruções de instalação](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html))


## Configuração do Ambiente

### 1. Clone o repositório

````
git clone https://github.com/italobaracho/integracao_server_knime_elastic.git
cd integracao_server_knime_elastic


## Instrução de uso

version: '3'
services:
  sqlserver:
    image: mcr.microsoft.com/mssql/server:2019-latest
    environment:
      SA_PASSWORD: "YourStrong@Passw0rd"
      ACCEPT_EULA: "Y"
    ports:
      - "1433:1433"

  elasticsearch:
    image: docker.elastic.co/elasticsearch/elasticsearch:7.17.10
    environment:
      - discovery.type=single-node
    ports:
      - "9200:9200"
      - "9300:9300"


docker-compose up -d
````



### 7. **Instruções de Uso**
- Passos para rodar e utilizar o projeto.


## Instruções de Uso


- Microsoft SQL Server Connector:

Função: Estabelece uma conexão com o SQL Server.
Instruções: Configure as credenciais e parâmetros de conexão (endereço do servidor, nome do banco de dados, usuário e senha).

- DB Query Reader:

Função: Executa uma query SQL na base conectada.
Instruções: Escreva a query SQL desejada para extrair os dados necessários do banco de dados.

- Column Filter:

Função: Filtra as colunas do dataset para manter apenas aquelas que são relevantes.
Instruções: Selecione as colunas que você deseja manter no dataset.

- Row Filter:

Função: Filtra as linhas do dataset com base em uma condição específica.
Instruções: Defina a condição (ex.: manter apenas registros onde a data é maior que uma certa data).
 
- Joiner:

 Função: Faz uma junção entre dois datasets.
 Instruções: Configure as colunas para a junção (escolha a chave primária ou de ligação entre as tabelas/datasets).

- Send Email:

Função: Envia um e-mail com os dados ou informações desejadas.
Instruções: Configure o servidor de e-mail, remetente, destinatário(s), assunto e corpo do e-mail. Anexe os dados ou inclua-os no corpo do e-mail, conforme necessário.

String Manipulation:

Função: Modifica strings (textos) dentro das colunas.
Instruções: Defina as regras de manipulação, como substituir, concatenar ou alterar o formato dos textos.
Column Filter (segunda instância):

Função: Novamente filtra as colunas do dataset.
Instruções: Selecione as colunas finais que serão usadas na próxima etapa.
Sorter:

Função: Ordena os dados com base em uma ou mais colunas.
Instruções: Escolha as colunas e a ordem (crescente ou decrescente) para a ordenação.
POST Request:

Função: Envia uma requisição POST para uma API com os dados processados.
Instruções: Configure a URL da API, os cabeçalhos e o corpo da requisição (normalmente em JSON).
### Executando o KNIME

- Abra o KNIME.
- Importe o workflow [instruções para importar workflows].
- Execute o workflow para processar os dados.

### Inserção e Busca de Dados no Elasticsearch

- Use o node `POST Request` para carregar os dados no Elasticsearch.
- Use a interface do Elasticsearch ou o comando curl para realizar buscas nos dados:

```bash
https://localhost:9200/seu_indice/_doc

