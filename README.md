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




## Actividad 5: Preguntas Conceptuales

5.¿Cuál es la diferencia fundamental entre Integración Continua (CI) y Entrega Continua (CD)?
R/= CI (Integración Continua): Es la práctica de integrar cambios de código frecuentemente en un repositorio compartido, seguido de la ejecución automática de pruebas y validaciones para detectar errores tempranamente. CI se enfoca en automatizar la construcción y pruebas.
CD (Entrega Continua): Extiende CI asegurando que el código siempre esté en un estado desplegable. Automatiza el proceso de despliegue a entornos de staging y producción, permitiendo lanzamientos confiables y rápidos. CD se enfoca en automatizar el despliegue.

6 ¿Qué es un GitHub self-hosted runner y cuándo sería necesario usarlo?
R/= Un self-hosted runner es un agente de ejecución que se aloja en tu propia infraestructura en lugar de usar los runners gratuitos de GitHub.
Cuándo usarlo:
Necesidad de acceder a recursos internos (red privada, VPN)
Requerimientos de hardware específicos (GPU, más RAM/CPU)
Costo: cuando se superan los límites gratuitos de GitHub Actions
Seguridad: mantener datos dentro de la organización
Software específico no disponible en runners estándar

7 ¿Cuál es el propósito de los GitHub environments? ¿Cómo se usan en workflows?
R/= Los GitHub Environments son espacios que permiten configurar protecciones y reglas específicas para despliegues.
Propósito:
Requerir aprobación manual antes de despliegues a producción
Limitar qué branches pueden desplegarse
Aislar secrets por ambiente (dev, staging, prod)

Un ejemplo de su uso en workflows es el siguiente:
deploy:
  environment: production  # Define el ambiente
  steps:
    - uses: actions/checkout@v4
    - run: deploy.sh
      env:
        API_KEY: ${{ secrets.PROD_API_KEY }}

8. ¿Que es una rollback strategy y como se implementaria en un pipeline de CD?
R/= Una rollback strategy es un plan para revertir un despliegue fallido a una versión anterior estable.
Implementación:
Blue-Green Deployment: Mantener dos entornos idénticos (blue=producción, green=nuevo). Si green falla, se mantiene blue activo.
Canary Deployment con Rollback automático: