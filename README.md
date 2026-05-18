# DevOps Portfolio — TP07: CI/CD

![CI/CD Pipeline](https://github.com/LucasCuevas93/devops-TP06/actions/workflows/cicd.yml/badge.svg)

Aplicación de notas con pipeline de CI/CD completo utilizando GitHub Actions.

## Estructura del Pipeline

El flujo de trabajo se divide según la rama en la que se trabaje:
* `feature/*` → Corre validaciones de código (Lint) → Ejecuta pruebas unitarias (Test).
* `develop`   → Realiza Lint → Ejecuta Test → Compila y sube la imagen (Build & Push a Docker Hub).
* `main`      → Realiza todo el flujo anterior → Ejecuta el despliegue automático (Deploy).

## Secrets Requeridos en GitHub
Para que este pipeline funcione, se configuraron los siguientes secretos en el repositorio:
* `DOCKERHUB_USERNAME`: Usuario de la cuenta de Docker Hub.
* `DOCKERHUB_TOKEN`: Token de acceso personal encriptado.

## Ejecución de Tests Localmente
Si se desea probar el comportamiento de los tests unitarios en la máquina local, ejecutar:
```bash
cd backend
pip install -r requirements.txt
pytest tests/ -v --cov=. --cov-report=term-missing
