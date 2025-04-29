# 🗄️ Super Resumão: Banco de Dados no Spring Boot (MySQL + H2 + JPA)

## 🧠 O que é JPA?
- **JPA** (Java Persistence API) é uma especificação Java para mapeamento objeto-relacional (ORM).
- Permite que entidades Java sejam mapeadas para tabelas do banco de dados.
- É utilizada junto com o **Hibernate**, que é a implementação mais comum.

---

## 🧱 Estrutura Geral com Spring Boot

1. **Entity** → Classe Java que representa uma tabela (anotada com `@Entity`).
2. **Repository** → Interface que estende `JpaRepository`, responsável pelos acessos ao banco.
3. **Service** → Contém a lógica de negócio.
4. **Controller** → Recebe e responde às requisições HTTP.

---

## 🐬 Configuração com MySQL

### `application.properties`
```properties
# Banco de dados MySQL
spring.datasource.url=jdbc:mysql://localhost:3306/nomedobanco?createDatabaseIfNotExist=true&serverTimezone=America/Sao_Paulo&useSSL=false
spring.datasource.username=root
spring.datasource.password=123456
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

# JPA
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQLDialect
```

### Dependência no `pom.xml`
```xml
<dependency>
  <groupId>mysql</groupId>
  <artifactId>mysql-connector-j</artifactId>
  <scope>runtime</scope>
</dependency>
```

---

## 🧪 Configuração com H2 (banco em memória)

### `application.properties`
```properties
# Banco de dados H2
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driver-class-name=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=

# JPA
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
spring.jpa.hibernate.ddl-auto=update
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console
```

### Acesso ao console:
- Após subir o projeto, acesse: `http://localhost:8080/h2-console`
- URL do JDBC: `jdbc:h2:mem:testdb`

---

## 📦 Exemplo de Entidade
```java
@Entity
public class Cliente {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String nome;
    private String email;

    // getters e setters
}
```

---

## 📁 Exemplo de Repository
```java
public interface ClienteRepository extends JpaRepository<Cliente, Long> {
    List<Cliente> findByNome(String nome);
}
```

---

## 🛠️ Configurações importantes do JPA
- `spring.jpa.hibernate.ddl-auto`:
  - `none`: não faz nada no banco
  - `update`: atualiza o schema conforme a entidade (⚠️ útil em dev)
  - `create`: recria todas as tabelas a cada execução
  - `create-drop`: igual ao `create`, mas apaga ao finalizar a aplicação

- `spring.jpa.show-sql=true`: mostra os comandos SQL no console
- `spring.jpa.properties.hibernate.format_sql=true`: formata o SQL exibido

---

## 🧠 Boas Práticas
- Em produção, evite usar `update` ou `create-drop` → use migrações com **Flyway** ou **Liquibase**.
- Sempre defina o `dialect` correto para o banco.
- Crie um perfil separado (`application-dev.properties`, `application-prod.properties`).
- Use `@Transactional` em métodos que alteram dados.
- Evite usar `findAll()` em grandes tabelas (página ou filtro).

---

## 🎯 Em resumo:
> O Spring Boot facilita a integração com bancos como **MySQL** e **H2**, usando JPA para persistência.
> Configure o datasource, defina entidades, repositórios e acesse tudo com poucas linhas de código!

---
