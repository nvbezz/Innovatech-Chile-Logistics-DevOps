# Backend Despachos - API REST Spring Boot

API REST para gestión de despachos del proyecto Innovatech Chile. Desarrollada con Spring Boot 3.4.4 y Java 17, conectada a base de datos MySQL.

## Tecnologías Utilizadas

- Spring Boot 3.4.4 / Java 17
- Spring Data JPA + MySQL 8.0
- SpringDoc OpenAPI 2.7.0
- Lombok, Maven

## Endpoints

| Método | Ruta | Descripción |
|--------|------|-------------|
| GET | `/api/v1/despachos` | Listar todos |
| GET | `/api/v1/despachos/{id}` | Obtener por ID |
| POST | `/api/v1/despachos` | Crear |
| PUT | `/api/v1/despachos/{id}` | Actualizar |
| DELETE | `/api/v1/despachos/{id}` | Eliminar |

Swagger disponible en `/swagger-ui.html`.

## Variables de entorno

```
DB_ENDPOINT   host de la base de datos
DB_PORT       puerto MySQL (3306)
DB_NAME       nombre de la base de datos
DB_USERNAME   usuario
DB_PASSWORD   contraseña
```

## Ejecución local

```bash
mvn spring-boot:run
```

## Docker

```bash
docker build -t innovatech-backend-despachos .
docker run -p 8081:8081 \
  -e DB_ENDPOINT=localhost \
  -e DB_PORT=3306 \
  -e DB_NAME=despachos_db \
  -e DB_USERNAME=root \
  -e DB_PASSWORD=secret \
  innovatech-backend-despachos
```

Puerto: **8081**
