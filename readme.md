[![Docker](https://img.shields.io/badge/docker-v20.10.2+-yellow.svg)](https://www.docker.com)
[![Docker-compose](https://img.shields.io/badge/docker_compose-v1.28.4+-yellow.svg)](https://docs.docker.com/compose/)
[![Grafana](https://img.shields.io/badge/grafana-Lataest-orange.svg)](https://grafana.com)
[![Mysql](https://img.shields.io/badge/mysql-v5.7-orange.svg)](https://www.mysql.com)
![Dependencies](https://img.shields.io/badge/dependencies-up%20to%20date-brightgreen.svg)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://opensource.org/licenses/MIT)


## Projet
---
## Etape 1 : Instalation des prérequis
### Connexion au seveur
```bash
ssh user@IpDuServeur
```


### Git clone
```bash
git clone https://github.com/CLOATRE-Erwan/Grafana-mysql_docker.git
```


### Docker-compose
```bash
pip install docker-compose
```

## Etape 2 : Up
```bash
cd Grafana-mysql_docker
```
```bash
docker-compose up -d
```
Contenu du docker-compose.yml
```bash
version: '2'
services:

  # simple myself setup
  mysql:
    image: mysql:5.7
    container_name: mysqldb
    ports:
      - "3306:3306"
    volumes:
      - ./mysql:/docker-entrypoint-initdb.d
    environment:
      MYSQL_ROOT_PASSWORD: 1234
      MYSQL_DATABASE: CRKI

  # grafana used for graphing mysql data
  grafana:
    image: grafana/grafana
    container_name: grafana
    ports:
      - '80:3000'
    volumes:
      - ./grafana/provisioning/datasource:/etc/grafana/provisioning/datasources
      - .//grafana/provisioning/dashboard:/etc/grafana/provisioning/dashboards
 ```

## Etape 3 : Resultats


![Drag Racing](img/graph.png)
