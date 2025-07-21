# Cómo lanzar la aplicación OpenArc

## 1. Lanzar la app usando Docker (desde el devcontainer)

Asegúrate de estar en el devcontainer y que Docker esté disponible (Docker-in-Docker). Ejecuta:

```bash
# Construye la imagen Docker desde la carpeta deployment
cd /workspaces/open-arc

docker build -t openarc-app deployment/

# Lanza el contenedor exponiendo el puerto 8080

docker run -p 8080:8080 openarc-app
```

## 2. Lanzar la app directamente con Gradle

Si prefieres no usar Docker, puedes lanzar la app usando Gradle:

```bash
cd /workspaces/open-arc/applications/app-service
./gradlew bootRun
```

## 3. Acceder al único endpoint disponible

Una vez la app esté corriendo (por Docker o Java), accede al endpoint desde tu navegador o con `curl`:

```
http://localhost:8080/api/usecase/path
```

Ejemplo usando curl:

```bash
curl http://localhost:8080/api/usecase/path
```

La respuesta esperada es:

```
Open Arc Rocks!!!
```

---

Para abrir la URL en el navegador del host desde el devcontainer, puedes usar:

```bash
"$BROWSER" http://localhost:8080/api/usecase/path
```
