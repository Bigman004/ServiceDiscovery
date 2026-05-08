### Run with Docker

```bash
docker build -t service-discovery .
docker run -p 8761:8761 service-discovery
```

---

## Registering a service

In any Spring Boot microservice that should register with this server, add the following to `pom.xml`:
it contains a ci/cd pipeline using github actions, so cloud deployment is easy

```xml
<dependency>
  <groupId>org.springframework.cloud</groupId>
  <artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
</dependency>
```

And in `application.properties`:

```properties
eureka.client.service-url.defaultZone=http://localhost:8761/eureka
spring.application.name=your-service-name
```

---

## Notes

- This server is intended to be the first service started in the microservices network
- Other services will fail to register if this server is not running
- The Eureka dashboard auto-refreshes and shows heartbeat status for all registered clients