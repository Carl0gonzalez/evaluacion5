# ProManage DevOps Setup

Este repositorio contiene la configuración para desarrollo local con Docker Compose y despliegue en Kubernetes (AWS EKS).

## Estructura de carpetas

```
/
├── auth-service/
│   └── Dockerfile
├── project-service/
│   └── Dockerfile
├── budget-service/
│   └── Dockerfile
├── file-service/
│   └── Dockerfile
├── docker-compose.yml
├── .env.sample
├── k8s/
│   ├── namespace.yaml
│   ├── db-secret.yaml
│   ├── s3-secret.yaml
│   ├── configmap.yaml
│   ├── serviceaccount.yaml
│   ├── rolebinding.yaml
│   ├── auth-service-deployment.yaml
│   ├── project-service-deployment.yaml
│   ├── budget-service-deployment.yaml
│   ├── file-service-deployment.yaml
│   └── ingress.yaml
├── .github/
│   └── workflows/
│       └── deploy.yml
└── ARCHITECTURE_REPORT.md
```

## Desarrollo local

1. Copia `.env.sample` a `.env` y ajusta variables si es necesario.
2. Ejecuta:
   ```bash
   docker-compose up --build
   ```
3. Accede a `http://localhost:8080`.

## Despliegue en producción

1. Configura secretos en GitHub Actions (`ECR_*`, `EKS_CLUSTER_NAME`, `AWS_REGION`).
2. Empuja cambios a `main` y el pipeline se encargará de build y deploy automático.
