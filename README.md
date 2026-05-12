# Innovatech Chile - Sistema de Logística y Ventas

Sistema web para gestión de despachos y ventas. Compuesto por un frontend React y dos APIs Spring Boot independientes, cada una con su propia base de datos MySQL.

## Arquitectura

- **Frontend** (React + Nginx): puerto 80
- **Backend Despachos** (Spring Boot): puerto 8081
- **Backend Ventas** (Spring Boot): puerto 8082
- **DB Despachos** (MySQL 8.0): puerto 3306
- **DB Ventas** (MySQL 8.0): puerto 3307

Los servicios se comunican a través de una red interna Docker.

## Tecnologías

- React 18, Vite 5, TailwindCSS 3
- Spring Boot 3.4.4, Java 17
- MySQL 8.0
- Docker, Docker Compose
- GitHub Actions, AWS EC2

## Estructura del repositorio

```
proyecto-semestral/
├── docker-compose.yml
├── front_despacho/
├── back-Despachos_SpringBoot/Springboot-API-REST-DESPACHO/
├── back-Ventas_SpringBoot/Springboot-API-REST/
└── .github/workflows/
```

## Pre-requisitos

- Docker y Docker Compose instalados
- Git

## Ejecución local

Crear un archivo `.env` en la raíz con las variables listadas más abajo, luego:

```bash
docker-compose up -d
```

- Frontend: http://localhost
- API Despachos: http://localhost:8081/api/v1/despachos
- API Ventas: http://localhost:8082/api/v1/ventas

## Variables de entorno (.env)

```
MYSQL_DESPACHOS_ROOT_PASSWORD=
DB_DESPACHOS_NAME=
DB_DESPACHOS_USER=
DB_DESPACHOS_PASSWORD=

MYSQL_VENTAS_ROOT_PASSWORD=
DB_VENTAS_NAME=
DB_VENTAS_USER=
DB_VENTAS_PASSWORD=
```

## Pipeline CI/CD

Los workflows en `.github/workflows/` se activan al hacer push a la rama `deploy`. Cada workflow detecta cambios por path, construye la imagen Docker, la sube a Docker Hub y despliega en la instancia EC2 correspondiente via SSH.

Secrets requeridos en GitHub:
- `DOCKERHUB_USERNAME`, `DOCKERHUB_TOKEN`
- `EC2_FRONTEND_HOST`, `EC2_BACKEND_HOST`, `EC2_SSH_KEY`, `EC2_USERNAME`
- `DB_ENDPOINT`, `DB_PORT`, `DB_NAME`, `DB_USERNAME`, `DB_PASSWORD`

## Despliegue en AWS EC2

Se usan dos instancias EC2: una pública para el frontend (puerto 80 abierto) y una para los backends (puertos 8081 y 8082 accesibles desde el frontend). Los security groups deben restringir el acceso según corresponda.

## Endpoints

**Despachos** — `GET /POST /PUT /{id} /DELETE /{id}` en `/api/v1/despachos`

**Ventas** — `GET /POST /PUT /{id} /DELETE /{id}` en `/api/v1/ventas`

## Persistencia de datos

Se usan named volumes (`mysql-despachos-data`, `mysql-ventas-data`) en lugar de bind mounts. Esto hace que el proyecto funcione igual en cualquier máquina sin depender de rutas del sistema host.

## Autores

- Yaquelin Rugel
- Yeider Catari
