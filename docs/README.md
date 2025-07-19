# open-arc Documentation

## Índice
- [Arquitectura Clean](#arquitectura-clean)
- [Devcontainer](#devcontainer)
- [GitHub Actions](#github-actions)
- [Manejo de secretos en application.yaml](#manejo-de-secretos-en-applicationyaml)
- [Documentación de Endpoints](#documentación-de-endpoints)

---

## Arquitectura Clean

![Clean Architecture](https://miro.medium.com/max/1400/1*ZdlHz8B0-qu9Y-QO3AXR_w.png)

Este proyecto implementa Clean Architecture, separando claramente las responsabilidades en módulos de dominio, casos de uso, infraestructura y aplicación. Consulta el diagrama para entender la relación entre capas.

---

## Devcontainer

El proyecto soporta desarrollo en contenedores usando [devcontainer](https://containers.dev/). Esto permite un entorno de desarrollo reproducible y consistente. Para usarlo:

1. Instala la extensión "Dev Containers" en VS Code.
2. Abre el proyecto en VS Code y selecciona "Reopen in Container".
3. El entorno instalará automáticamente las dependencias necesarias.

### Ventajas
- Entorno idéntico para todos los desarrolladores.
- Aislamiento de dependencias.
- Configuración rápida para nuevos colaboradores.

---

## GitHub Actions

El repositorio incluye flujos de CI/CD usando GitHub Actions. Estos flujos automatizan:
- Compilación y pruebas del proyecto en cada push o PR.
- Análisis estático de código.
- Despliegue (si está configurado).

Los archivos de configuración se encuentran en `.github/workflows/`.

### Ejemplo de flujo:
- `build.yml`: Compila y ejecuta pruebas.
- `deploy.yml`: Despliega la aplicación (opcional).

---

## Manejo de secretos en application.yaml

Los secretos y configuraciones sensibles (como contraseñas, tokens, etc.) deben manejarse usando variables de entorno y nunca deben ser versionados directamente en `application.yaml`.

### Recomendaciones:
- Usa placeholders en `application.yaml` (por ejemplo, `${DB_PASSWORD}`).
- Define los valores reales como variables de entorno en el entorno de ejecución o en GitHub Secrets.
- Nunca subas secretos reales al repositorio.

---

## Documentación de Endpoints

A continuación se documentan los endpoints REST disponibles actualmente en el proyecto:

### API REST

- **Base URL:** `/api`

#### Ejemplo de Endpoint

- `GET /api/health`
  - **Descripción:** Verifica el estado de la API.
  - **Respuesta:**
    - `200 OK` – API operativa.

- `POST /api/ejemplo`
  - **Descripción:** Endpoint de ejemplo para crear un recurso.
  - **Body:** JSON con los datos requeridos.
  - **Respuesta:**
    - `201 Created` – Recurso creado.

> **Nota:** Para ver todos los endpoints disponibles, revisa la clase `ApiRest.java` en `infrastructure/entry-points/api-rest/src/main/java/cloud/qubits/api/`.

---

## Contribuir

1. Haz un fork del repositorio.
2. Crea una rama para tu feature o fix.
3. Haz tus cambios y abre un Pull Request.

---

## Licencia

Consulta el archivo `LICENSE` para más detalles.
