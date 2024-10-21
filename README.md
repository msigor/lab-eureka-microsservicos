Peço desculpas pelo equívoco. Você está correto, e agradeço por apontar isso. Vou fornecer o README completo em formato Markdown adequado:
# API Gateway para Microserviços

## Visão Geral

Este projeto implementa um API Gateway utilizando Spring Cloud Gateway para gerenciar e rotear requisições para uma arquitetura de microserviços. O gateway atua como um ponto de entrada único para todos os microserviços, proporcionando roteamento inteligente, balanceamento de carga e uma camada adicional de segurança.

## Tecnologias Utilizadas

- Spring Boot 2.x
- Spring Cloud Gateway
- Spring Cloud Netflix Eureka Client
- Docker
- Maven

## Pré-requisitos

- JDK 11 ou superior
- Maven 3.6 ou superior
- Docker (opcional, para containerização)

## Configuração e Execução

### Executando Localmente

1. Clone o repositório:
   ```bash
   git clone https://github.com/seu-usuario/api-gateway.git
   cd api-gateway 


2. Compile o projeto:
  mvn clean package


3. Execute o aplicativo:
  java -jar target/api-gateway-0.0.1-SNAPSHOT.jar



O API Gateway estará disponível em http://localhost:8080.
## Usando Docker

1. Construa a imagem Docker:
  docker build -t api-gateway .


2. Execute o container:
  docker run -p 8080:8080 api-gateway



## Estrutura do Projeto

src/main/java/com/seudominio/apigateway/: Contém o código-fonte Java
src/main/resources/: Contém arquivos de configuração
application.yml: Configurações principais do Spring e rotas do Gateway



## Configuração de Rotas
As rotas são configuradas no arquivo application.yml. Exemplo:
spring:

```bash
spring:
  cloud:
    gateway:
      routes:
        - id: user-service
          uri: lb://USER-SERVICE
          predicates:
            - Path=/users/**
        - id: task-service
          uri: lb://TASK-SERVICE
          predicates: 
```


## Integração com Eureka
O API Gateway está configurado para se registrar no Eureka Server e descobrir outros serviços automaticamente. Certifique-se de que o Eureka Server esteja em execução e acessível.

## Segurança
O projeto inclui configuração básica de segurança usando JWT. Para personalizar ou estender a segurança, modifique a classe SecurityConfig.

## Monitoramento
Endpoints de monitoramento estão disponíveis através do Spring Boot Actuator:

Health check: http://localhost:8080/actuator/health
Métricas: http://localhost:8080/actuator/metrics
Prometheus: http://localhost:8080/actuator/prometheus

## Docker Compose
Um arquivo docker-compose.yml está incluído para facilitar a execução de todo o ecossistema de microserviços. Para iniciar todos os serviços:
docker-compose up -d
