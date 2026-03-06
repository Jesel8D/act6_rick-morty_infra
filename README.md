# act6_rick-morty_infra

> **Capa de Infraestructura** — Arquitectura SOA | Proyecto Rick & Morty

Configuración de infraestructura local del proyecto. Levanta un contenedor de **PostgreSQL 15** y un proxy inverso **Nginx** para el Frontend usando Docker Compose.

##  Rol en la Arquitectura SOA

```
[Docker Compose]
  ├── PostgreSQL 15  → usado por Persistence Microservice (local)
  ├── Nginx          → proxy inverso del Frontend (local)
  └── Frontend       → contenedor del build de Next.js
```

##  Tecnologías

- Docker & Docker Compose
- PostgreSQL 15 (Alpine)
- Nginx (Alpine)

##  Levantar en local

```bash
# 1. Crear el archivo de variables de entorno
cp .env.example .env
# Edita .env con tus credenciales deseadas para PostgreSQL

# 2. Levantar todos los contenedores
docker compose up -d

# 3. Para detenerlos
docker compose down
```

> La base de datos queda disponible en `localhost:5432`.

## Producción

En producción, la infraestructura es reemplazada completamente por servicios administrados:
- **PostgreSQL** → Neon.tech (Serverless, Free Tier)
- **Nginx** → Eliminado (Vercel y Render proveen HTTPS/proxy propios)
