# 🧵 Super Resumão: Lombok com Spring Boot

## 🧠 O que é Lombok?
- **Lombok** é uma biblioteca Java que reduz a verbosidade do código.
- Gera automaticamente **getters, setters, construtores, builders, equals, hashCode**, entre outros.
- Muito útil em projetos Spring para evitar repetição de código em entidades, DTOs e modelos.

---

## ⚙️ Como funciona?
- Usa **anotações** para gerar código **em tempo de compilação**.
- O código gerado **não aparece** no fonte, mas é reconhecido pela IDE e pela JVM.

---

## 📦 Dependência no `pom.xml`
```xml
<dependency>
  <groupId>org.projectlombok</groupId>
  <artifactId>lombok</artifactId>
  <version>1.18.30</version>
  <scope>provided</scope>
</dependency>
```

---

## 🖥️ Configuração na IDE
- **IntelliJ / Eclipse / VS Code**: precisa instalar plugin "Lombok".
- Ativar a anotação no projeto se necessário:
  - Eclipse: `Enable annotation processing`
  - IntelliJ: `Settings > Build, Execution > Compiler > Annotation Processors`

---

## 🔖 Anotações Mais Usadas
| Anotação | Descrição |
|----------|-----------|
| `@Getter` | Gera todos os getters |
| `@Setter` | Gera todos os setters |
| `@ToString` | Gera `toString()` |
| `@EqualsAndHashCode` | Gera `equals()` e `hashCode()` |
| `@NoArgsConstructor` | Gera construtor sem argumentos |
| `@AllArgsConstructor` | Gera construtor com todos os campos |
| `@RequiredArgsConstructor` | Gera construtor com os campos `final` |
| `@Data` | Junta `@Getter`, `@Setter`, `@ToString`, `@EqualsAndHashCode`, `@RequiredArgsConstructor` |
| `@Builder` | Cria padrão Builder |
| `@Value` | Classe imutável (final + `@Getter` + `@AllArgsConstructor`) |

---

## 📘 Exemplo Prático
```java
@Data
@NoArgsConstructor
@AllArgsConstructor
@Builder
public class Pessoa {
    private Long id;
    private String nome;
    private int idade;
}
```
- Com essas anotações, Lombok gera:
  - Getters e Setters para todos os campos
  - `toString()`, `equals()`, `hashCode()`
  - Construtores com e sem argumentos
  - Builder pattern

---

## 💡 Boas Práticas
- Use `@Data` com cuidado em entidades JPA (pode afetar `equals/hashCode`)
- Prefira `@Getter/@Setter` individual em DTOs para controle mais fino
- Em classes imutáveis, use `@Value`
- Use `@Builder` para facilitar testes e construções complexas

---

## 🧠 Em resumo:
> Lombok economiza tempo, reduz repetição e deixa o código mais limpo.  
> Basta anotar e deixar que ele gere o resto!

---
