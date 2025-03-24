# Postgres MCP SERVER

### docker compose
```bash
---
services:
  postgres:
    image: postgres:15.8
    container_name: postgres-test
    restart: unless-stopped
    environment:
      POSTGRES_PASSWORD: asim
      POSTGRES_USER: asim
      POSTGRES_DB: test
    ports:
      - "5432:5432"
    networks:
      - postgres
    volumes:
      - postgres_data:/var/lib/postgresql/data

  pgadmin:
    image: dpage/pgadmin4:latest
    container_name: pgadmin
    restart: unless-stopped
    environment:
      PGADMIN_DEFAULT_EMAIL: admin@example.com
      PGADMIN_DEFAULT_PASSWORD: admin
    ports:
      - "8080:80"
    networks:
      - postgres
    depends_on:
      - postgres

networks:
  postgres:
    driver: bridge

volumes:
  postgres_data:
```