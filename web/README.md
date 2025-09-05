#  Proyecto con CI/CD usando GitHub Actions

Este repositorio implementa un flujo **DevOps** con **GitHub Actions**, utilizando contenedores Docker y despliegue automático en servidor remoto.

---

##  Pipelines disponibles

En la carpeta `.github/workflows/` se encuentran los siguientes pipelines:

- **`ci.yml`** → Validación de integración continua (linting, compilación).
- **`test.yml`** → Ejecución de pruebas unitarias y de integración.
- **`build.yml`** → Construcción de la imagen Docker y publicación en GitHub Container Registry (GHCR).
- **`deploy.yml`** → Despliegue en el servidor vía SSH y Docker.

---

## Flujo DevOps

```mermaid
flowchart TD

    A[📝 Commit / Pull Request] --> B[🔨 CI (ci.yml)]
    B --> C[🧪 Tests (test.yml)]
    C -->|✅ Pasan| D[🏗️ Build (build.yml)]
    D --> E[🚀 Deploy (deploy.yml)]
    C -->|❌ Fallan| F[🔴 Notificación de error]

    E --> G[🌍 Aplicación en servidor]
