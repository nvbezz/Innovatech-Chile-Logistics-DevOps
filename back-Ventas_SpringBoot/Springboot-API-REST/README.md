# Backend Ventas - API REST Spring Boot

API REST para gestión de ventas del proyecto Innovatech Chile. Desarrollada con Spring Boot 3.4.4 y Java 17, conectada a base de datos MySQL.

## Tecnologías

- Spring Boot 3.4.4 / Java 17
- Spring Data JPA + MySQL 8.0
- SpringDoc OpenAPI 2.7.0
- Lombok, Maven

## Endpoints

| Método | Ruta | Descripción |
|--------|------|-------------|
| GET | `/api/v1/ventas` | Listar todas |
| GET | `/api/v1/ventas/{id}` | Obtener por ID |
| POST | `/api/v1/ventas` | Crear |
| PUT | `/api/v1/ventas/{id}` | Actualizar |
| DELETE | `/api/v1/ventas/{id}` | Eliminar |

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
docker build -t innovatech-backend-ventas .
docker run -p 8080:8080 \
  -e DB_ENDPOINT=localhost \
  -e DB_PORT=3306 \
  -e DB_NAME=ventas_db \
  -e DB_USERNAME=root \
  -e DB_PASSWORD=secret \
  innovatech-backend-ventas
```

Puerto: **8080** (en docker-compose se expone en el host como 8082)
