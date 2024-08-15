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

```bash
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
