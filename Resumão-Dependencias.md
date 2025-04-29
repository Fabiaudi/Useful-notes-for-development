# 📦 Super Resumão: Dependências Comuns em Projetos Spring Boot

## 🚀 O que são “starters” do Spring Boot?
- Starters são conjuntos prontos de dependências para iniciar rapidamente funcionalidades comuns.
- Ex: `spring-boot-starter-web` inclui tudo que você precisa para uma API REST.

---

## 📋 Dependências mais utilizadas (com descrição)

### 🌐 API REST
```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```
- Inclui Tomcat embutido, Jackson (JSON), REST controllers, etc.

### 🗄️ Acesso a banco de dados (JPA + Hibernate)
```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
```
- Integração com JPA/Hibernate, suporta repositórios e anotações como `@Entity`, `@Repository`.

### 🐬 MySQL Driver
```xml
<dependency>
  <groupId>mysql</groupId>
  <artifactId>mysql-connector-j</artifactId>
  <scope>runtime</scope>
</dependency>
```
- Driver JDBC para conexão com MySQL/MariaDB.

### 🧪 H2 Database (memória)
```xml
<dependency>
  <groupId>com.h2database</groupId>
  <artifactId>h2</artifactId>
  <scope>runtime</scope>
</dependency>
```
- Banco de dados em memória para testes ou desenvolvimento local.

### 🐇 RabbitMQ (mensageria AMQP)
```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-amqp</artifactId>
</dependency>
```
- Para envio e recebimento de mensagens via RabbitMQ (AMQP).

### ✉️ E-mail com Spring
```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-mail</artifactId>
</dependency>
```
- Suporte a envio de e-mails via SMTP.

### 🛡️ Validações
```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-validation</artifactId>
</dependency>
```
- Suporte a anotações como `@NotNull`, `@Size`, `@Email`, etc.

### 📊 Documentação Swagger (OpenAPI 3)
```xml
<dependency>
  <groupId>org.springdoc</groupId>
  <artifactId>springdoc-openapi-starter-webmvc-ui</artifactId>
  <version>2.1.0</version>
</dependency>
```
- Gera documentação interativa da API.

### 🧵 Lombok
```xml
<dependency>
  <groupId>org.projectlombok</groupId>
  <artifactId>lombok</artifactId>
  <version>1.18.30</version>
  <scope>provided</scope>
</dependency>
```
- Gera automaticamente getters/setters/construtores para classes Java.

### 🔐 Spring Security (opcional)
```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-security</artifactId>
</dependency>
```
- Para autenticação e autorização (JWT, OAuth2, Basic Auth, etc).

### 🔐 OAuth2 Resource Server / Authorization Server
```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-oauth2-resource-server</artifactId>
</dependency>
<dependency>
  <groupId>org.springframework.security</groupId>
  <artifactId>spring-security-oauth2-authorization-server</artifactId>
</dependency>
```
- Para configurar APIs protegidas com tokens JWT e autenticação OAuth2.

---

## 🧭 API Gateway
```xml
<dependency>
  <groupId>org.springframework.cloud</groupId>
  <artifactId>spring-cloud-starter-gateway</artifactId>
</dependency>
```
- Atua como **porta de entrada única** para todos os microsserviços.
- Permite:
  - Roteamento de requisições
  - Autenticação e autorização centralizada
  - Manipulação de cabeçalhos, CORS e filtros personalizados

---

## 🌐 Eureka Server vs Eureka Client

### 📡 Eureka Server
```xml
<dependency>
  <groupId>org.springframework.cloud</groupId>
  <artifactId>spring-cloud-starter-netflix-eureka-server</artifactId>
</dependency>
```
- Serviço de **descoberta e registro** de microsserviços.
- Atua como **servidor central**, onde todos os serviços se registram.
- Interface web acessível para visualizar os serviços disponíveis.

### 📲 Eureka Client
```xml
<dependency>
  <groupId>org.springframework.cloud</groupId>
  <artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
</dependency>
```
- Serviço que **se registra** no Eureka Server e **descobre** outros serviços automaticamente.
- Usado nos microsserviços que precisam se comunicar via **service discovery** ao invés de URLs fixas.

---

## 🧰 Dependências úteis para arquitetura de microsserviços

### 🔄 Config Server (centralização de propriedades)
```xml
<dependency>
  <groupId>org.springframework.cloud</groupId>
  <artifactId>spring-cloud-config-server</artifactId>
</dependency>
```
- Permite que todos os microsserviços busquem suas configurações em um único repositório remoto (como Git).

### 🌐 Feign Client (REST simplificado entre microsserviços)
```xml
<dependency>
  <groupId>org.springframework.cloud</groupId>
  <artifactId>spring-cloud-starter-openfeign</artifactId>
</dependency>
```
- Facilita chamadas HTTP entre serviços com interfaces Java + anotações.

### 🧭 Spring Cloud Sleuth + Zipkin (monitoramento e rastreabilidade)
```xml
<dependency>
  <groupId>org.springframework.cloud</groupId>
  <artifactId>spring-cloud-starter-sleuth</artifactId>
</dependency>
<dependency>
  <groupId>org.springframework.cloud</groupId>
  <artifactId>spring-cloud-starter-zipkin</artifactId>
</dependency>
```
- Adiciona identificadores únicos às requisições entre serviços.
- Permite rastrear fluxos em sistemas distribuídos via Zipkin UI.

### 📦 Spring Cloud Bus
```xml
<dependency>
  <groupId>org.springframework.cloud</groupId>
  <artifactId>spring-cloud-starter-bus-amqp</artifactId>
</dependency>
```
- Integração entre serviços usando eventos via RabbitMQ ou Kafka (útil para refresh automático de configs, por exemplo).

---

## 🧪 Testes
```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-test</artifactId>
  <scope>test</scope>
</dependency>
```
- Inclui JUnit, Mockito, Hamcrest, AssertJ para testes automatizados.

---

## 💡 Dica:
- Use o site [https://start.spring.io](https://start.spring.io) para gerar um projeto com as dependências que você precisa.

---

## 🧠 Em resumo:
> Spring Boot oferece starters prontos para quase tudo: web, banco, validação, segurança, mensageria, documentação e arquitetura em microsserviços.  
> Basta incluir no `pom.xml` e sair codando!

---