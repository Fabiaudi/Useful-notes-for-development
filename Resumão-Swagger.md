# 🔍 Super Resumão: Swagger / OpenAPI com Spring Boot

## 📘 O que é Swagger?
- **Swagger** (atualmente conhecido como **OpenAPI**) é uma especificação para documentar APIs REST.
- Com ele, você gera automaticamente uma **documentação interativa** dos endpoints do seu sistema.
- É amplamente usado em projetos Spring Boot para testes e comunicação entre times.

---

## ✅ Benefícios do Swagger
- Documentação automática e atualizada
- Interface web para testar endpoints
- Facilidade de integração entre frontend e backend
- Reduz dependência de ferramentas externas como Postman

---

## 📦 Dependência no `pom.xml`
Para Spring Boot 3+:
```xml
<dependency>
  <groupId>org.springdoc</groupId>
  <artifactId>springdoc-openapi-starter-webmvc-ui</artifactId>
  <version>2.1.0</version>
</dependency>
```

---

## 🔧 Configuração (opcional)
Com a dependência acima, já funciona **automaticamente**. Mas é possível configurar o título, descrição, versão:

### `application.properties`
```properties
springdoc.api-docs.enabled=true
springdoc.swagger-ui.enabled=true
springdoc.swagger-ui.path=/swagger-ui.html
```

### Classe de configuração personalizada (opcional):
```java
@Configuration
public class SwaggerConfig {

    @Bean
    public OpenAPI customOpenAPI() {
        return new OpenAPI()
            .info(new Info()
                .title("Pet API")
                .description("API de cadastro de pets")
                .version("1.0"));
    }
}
```

---

## 🌐 Acessando o Swagger
- Com o projeto rodando, acesse:
  ```
  http://localhost:8080/swagger-ui.html
  ```
- Ou a documentação em JSON:
  ```
  http://localhost:8080/v3/api-docs
  ```

---

## 🧷 Anotações Úteis no Controller
```java
@Tag(name = "Pets", description = "Operações com pets")
@RestController
@RequestMapping("/pets")
public class PetController {

    @Operation(summary = "Lista todos os pets")
    @ApiResponses(value = {
        @ApiResponse(responseCode = "200", description = "Sucesso"),
        @ApiResponse(responseCode = "500", description = "Erro interno")
    })
    @GetMapping
    public List<Pet> listar() {
        return petService.listarTodos();
    }
}
```

### Principais anotações:
| Anotação | Uso |
|----------|-----|
| `@Tag` | Define categoria no Swagger UI |
| `@Operation` | Título e resumo do endpoint |
| `@ApiResponse` | Documenta os códigos de resposta |
| `@Parameter` | Documenta parâmetros da URL ou query |
| `@Schema` | Descreve campos nos DTOs |

---

## 💡 Boas Práticas
- Documente os principais endpoints da API
- Use `@Operation` para clareza no Swagger UI
- Crie exemplos nos DTOs com `@Schema(example = "valor")`
- Mantenha a documentação concisa e objetiva
- Organize os endpoints por `@Tag`

---

## 🧠 Em resumo:
> Swagger (OpenAPI) deixa sua API mais profissional, testável e compreensível.  
> Basta adicionar a dependência e anotar os controllers para ter uma documentação interativa completa!

---