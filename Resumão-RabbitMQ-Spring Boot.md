# 🐇 Super Resumão: RabbitMQ + Spring Boot

## 📌 O que é RabbitMQ?
- RabbitMQ é um **message broker** que permite **comunicação assíncrona** via **filas**.
- Ideal para sistemas distribuídos, escaláveis, resilientes e desacoplados.

---

## 🔄 Comunicação Síncrona vs Assíncrona

### Síncrona:
- Serviço A espera a resposta do B (ex: HTTP).
- ✅ Simples de implementar
- ❌ Alto acoplamento / Sensível a falhas

### Assíncrona:
- A envia mensagem à fila; B processa depois.
- ✅ Desacoplamento / Resiliência / Escalabilidade
- ❌ Mais complexa / Difícil de debugar

---

## 🚀 Vantagens de usar filas (RabbitMQ)
- 🔗 Desacoplamento
- 🔁 Persistência de mensagens
- 💪 Alta disponibilidade
- 📦 Escalabilidade horizontal (vários consumers)
- ⚙️ Tolerância a falhas

---

## 🧱 Componentes do RabbitMQ

| Componente     | Função                                                                 |
|----------------|------------------------------------------------------------------------|
| **Producer**       | Responsável por **enviar** mensagens. Não sabe quem vai recebê-las.                        |
| **Exchange**       | É o **correio**: decide **para qual fila** enviar a mensagem baseada na routing key.       |
| **Routing Key**    | É o **endereço da carta**: string usada para rotear a mensagem.                           |
| **Binding**        | Liga a exchange à fila com base em uma routing key.                                       |
| **Queue**          | Armazena a mensagem até que um consumer a leia.                                          |
| **Consumer**       | É quem **consome/processa** as mensagens da fila. Pode haver mais de um.                 |
| **Virtual Host**   | Partições isoladas de recursos dentro do RabbitMQ.                                       |
| **Connection**     | Conexão TCP entre app e RabbitMQ.                                                        |
| **Channel**        | Subconexões lógicas (eficientes e reutilizáveis).                                        |

---

## 💡 Analogia Completa
Imagine o RabbitMQ como o sistema de **correios**:

- **Producer**: quem escreve e envia a carta.
- **Exchange**: agência dos correios que recebe a carta.
- **Routing Key**: o CEP/endereço.
- **Binding**: as regras internas da agência que definem para onde a carta vai.
- **Queue**: caixa de correio onde a carta espera.
- **Consumer**: o destinatário que lê a carta.

---

## 📬 Tipos de Exchanges
- **Direct**: Roteia com base em routing key exata
- **Topic**: Usa padrões com `*` e `#`
- **Fanout**: Envia para todas as filas vinculadas
- **Headers**: Usa cabeçalhos ao invés de routing keys

---

## 🛠️ Configuração Básica (Spring Boot)

### Dependência no `pom.xml`
```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-amqp</artifactId>
</dependency>
```

### `application.properties` (Producer e Consumer)
```properties
spring.rabbitmq.host=localhost
spring.rabbitmq.port=5672
spring.rabbitmq.username=guest
spring.rabbitmq.password=guest

broker.exchange.name=pet_events
broker.routingkey.created=pet.created
broker.queue.name=queue_created
```

---

## 🧩 Configuração do Producer

### `RabbitMQConfig.java`
```java
@Configuration
public class RabbitMQConfig {

    @Value("${broker.exchange.name}")
    private String exchange;

    @Bean
    public TopicExchange topicExchange() {
        return new TopicExchange(exchange, true, false);
    }

    @Bean
    public MessageConverter jsonConverter() {
        return new Jackson2JsonMessageConverter();
    }
}
```

### `Producer.java`
```java
@Component
public class EventProducer {

    @Autowired
    private RabbitTemplate rabbitTemplate;

    @Value("${broker.exchange.name}")
    private String exchange;

    @Value("${broker.routingkey.created}")
    private String routingKey;

    public void publish(GenericEventDTO event) {
        rabbitTemplate.convertAndSend(exchange, routingKey, event);
        System.out.println("Mensagem enviada!");
    }
}
```

---

## 📥 Configuração do Consumer

### `RabbitMQConfig.java`
```java
@Configuration
public class RabbitMQConfig {

    @Value("${broker.exchange.name}")
    private String exchange;

    @Value("${broker.queue.name}")
    private String queue;

    @Value("${broker.routingkey.created}")
    private String routingKey;

    @Bean
    public Queue createdQueue() {
        return new Queue(queue, true);
    }

    @Bean
    public TopicExchange topicExchange() {
        return new TopicExchange(exchange);
    }

    @Bean
    public Binding binding() {
        return BindingBuilder.bind(createdQueue()).to(topicExchange()).with(routingKey);
    }

    @Bean
    public Jackson2JsonMessageConverter jsonConverter() {
        return new Jackson2JsonMessageConverter();
    }
}
```

### `Consumer.java`
```java
@Component
public class EventConsumer {

    @Autowired
    private EventService eventService;

    @RabbitListener(queues = "${broker.queue.name}")
    public void receive(GenericEventDTO event) {
        eventService.process(event);
    }
}
```

---

## ✅ Boas Práticas
- ✔️ Use mensagens **idempotentes** (evite duplicidade)
- ✔️ Utilize **ACK/NACK** para confirmar o processamento
- ✔️ Configure **DLQs (Dead Letter Queues)** para falhas
- ✔️ Centralize logs e monitore via interface web
- ✔️ Prefira JSON com conversores adequados (Jackson)
- ✔️ **Separe bem as responsabilidades**:
  - O **Producer só envia** mensagens → não sabe quem consumirá.
  - O **Consumer só consome** e **processa** a lógica da mensagem.
  - O **Exchange não armazena**, só **redireciona**.

---

## 📌 Termos Importantes
- `ACK` → mensagem processada com sucesso
- `NACK` → falha ao processar
- `DLQ` → fila de descarte de mensagens com erro

---

## 🧠 Em resumo:
> RabbitMQ permite enviar mensagens de forma assíncrona e resiliente.  
> O Producer envia para a Exchange com uma Routing Key.  
> A Exchange roteia para a Queue.  
> O Consumer lê da fila e processa.  
> Cada componente tem sua responsabilidade clara e isolada!

---
