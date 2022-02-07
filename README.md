# Docker Jenkins

Docker jenkins support

* jenkins:2.333
* java:jdk11

## How to use?

```bash
mkdir -p data/jenkins

## docker-compose.yml

version: '3.7'

services:
  jenkins:
    build: ./docker
    image: dylanops/jenkins:2.333-jdk11
    container_name: jenkins
    restart: always
    environment:
      - JENKINS_SLAVE_AGENT_PORT=5001
    ports:
      - "8080:8080"
      - "5001:5001"
    volumes:
      - "./data/jenkins:/var/jenkins_home"
    networks:
      - app

networks:
  app:
    driver: bridge

docker-compose up -d

```