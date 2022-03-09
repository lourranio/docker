# JENKINS COM DOCKER (Jenkins with Docker)

## SUMÁRIO

- [SOBRE](#sobre)
- [COMANDOS](#comandos)
- [PIPELINE](#pipeline)
- [Contributing](../CONTRIBUTING.md)

## SOBRE <a name = "sobre"></a>

Instalação de uma versao do jenkins em cima do docker

### Pre-requisitos

1. Uma maquina virtual
2. Atualizado os pacotes. Exemplo: `sudo apt update`

## COMANDOS <a name = "comandos"></a>

Usando a imagem oficial do jenkins
https://hub.docker.com/r/jenkins/jenkins

```
OPCOES
#1 Versao atualizada com jenkins/jenkins:2.332.1-lts-jdk11
  docker run --rm --name jenkins -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:2.332.1-lts-jdk11

#2 padrao com jdk8
    docker run --rm --name jenkins -p 8080:8080 -p 50000:50000 jenkins/jenkins:2.303.1-jdk8

#3 setando uma pasta padrao do jenkins "jenkins_home" com jdk8
    docker run --rm --name jenkins -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:2.303.1-jdk8

#4 setando uma pasta padrao do jenkins "jenkins_home" com jdk11
    docker run --rm --name jenkins -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:2.303.2-jdk11

```

## COMO ACESSAR

Apos a instalação é gerado uma senha (hash) no terminal. Salve essa senha.

Abra o navegador no ` http://endereco:8080`

## PIPELINE <a name = "pipeline"></a>

- A cada hora

```
pipeline {
  agent any
  triggers {
    cron 'H */1 * * *'
  }
  stages {
    stage('Hello') {
      steps {
        sh 'echo Hello World'
      }
    }
  }
}

```
