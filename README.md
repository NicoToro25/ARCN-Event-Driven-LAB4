# ARCN-Event-Driven-LAB4

## Arquitectura Centrada en el Negocio (ARCN)

## Nicolás Toro Criollo

En este repositorio se busca solucionar el laboratorio propuesto en el link [Event Driven Lab](https://eci-arcn.github.io/Labs/event-driven-lab/)
implementando una arquitectura event-driven donde se desacoplan servicios mediante el uso de mensajería asincrónica. Tiene las siguientes características:
 
 * Se usan dos servicios principales, el **producer** que publica los eventos y **consumer** los consume.
 * Spring Boot se encarga de la lógica de los servicios.
 * RabitMQ actúa como intermediario (message broker).
 * Docker permite contener y levantar a RabbitMQ sin necesidad de instalarlo manualmente.

---

## Tecnologias utilizadas / Requisitos (estan marcados con ❗)

- Java 17+ ❗
- Maven ❗
- Spring Boot
- RabbitMQ
- Docker ❗
- GitHub Codespaces (opcional)

---

## Estructura del proyecto

```bash
.
├── docker-compose.yml
├── README.md
├── consumer-service
│   ├── Dockerfile
│   ├── pom.xml
│   └── src
│       ├── main
│       │   ├── java
│       │   │   └── com
│       │   │       └── eci
│       │   │           └── arcn
│       │   │               └── consumer_service
│       │   │                   ├── ConsumerServiceApplication.java
│       │   │                   ├── MessageListener.java
│       │   │                   ├── config
│       │   │                   │   └── RabbitMQConfig.java
│       │   │                   └── listener
│       │   └── resources
│       │       └── application.properties
│       └── test
│           └── java
│               └── com
│                   └── eci
│                       └── arcn
│                           └── consumer_service
│                               └── ConsumerServiceApplicationTests.java
└── producer-service
    ├── Dockerfile
    ├── pom.xml
    ├── src
        ├── main
        │   ├── java
        │   │   └── com
        │   │       └── eci
        │   │           └── arcn
        │   │               └── product_service
        │   │                   ├── ProductServiceApplication.java
        │   │                   ├── config
        │   │                   │   └── RabbitMQConfig.java
        │   │                   └── controller
        │   │                       └── MessageController.java
        │   └── resources
        │       ├── application.properties
        │       ├── static
        │       └── templates
        └── test
            └── java
                └── com
                    └── eci
                        └── arcn
                            └── product_service
                                └── ProductServiceApplicationTests.java
```

---

## Comandos importantes

### Clonar repo
```bash
git clone https://github.com/NicoToro25/ARCN-Event-Driven-LAB4.git
cd event ARCN-Event-Driven-LAB4
```

### Levantar RabbitMQ
```bash
docker run -d --name rabbitmq \
-p 5672:5672 \
-p 15672:15672 \
rabbitmq:3-management
```

### Acceder al panel de RabbitMQ
```bash
http://localhost:15672

Credenciales:

Usuario: guest
Contraseña: guest
```

### Ejecutar el Producer
```bash
cd producer
mvn spring-boot:run
```


### Ejecutar el Consumer
```bash
En otra terminal:

cd consumer
mvn spring-boot:run
```

### Probar el sistema
```bash
curl -X POST http://localhost:8080/event
```
