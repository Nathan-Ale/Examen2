# Proyecto con CI/CD Pipeline

## Evidencia de Deployment

### Pipeline CI
![CI Pipeline](screenshots/ci-pipeline.png)

### Pipeline CD
![CD Pipeline](screenshots/cd-pipeline.png)

### Deployment exitoso a Vercel
https://mi-proyecto.vercel.app

## Configuración del Proyecto

### Prerrequisitos
- Node.js 16.x o superior
- Docker y Docker Compose

### Ejecutar localmente
```bash
# Instalar dependencias
npm install

# Ejecutar tests
npm test

# Levantar con Docker Compose
cd docker
docker-compose up