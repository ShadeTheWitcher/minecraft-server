# Minecraft Server (Docker)

Este proyecto levanta un servidor de Minecraft utilizando la imagen de [itzg/minecraft-server](https://github.com/itzg/docker-minecraft-server).

## Requisitos

- Docker
- Docker Compose

## Cómo iniciar

1. Abre una terminal en esta carpeta.
2. Ejecuta el siguiente comando para descargar la imagen e iniciar el servidor en segundo plano:

   ```bash
   docker compose up -d
   ```

3. El servidor estará disponible en `localhost:25565`.

## Ver Logs

Para ver lo que está pasando en la consola del servidor (y ver cuando termine de iniciarse):

```bash
docker compose logs -f
```

(Presiona `Ctrl + C` para salir de los logs)

## Configuración Básica

Puedes editar el archivo `docker-compose.yml` para cambiar la configuración:

- **EULA**: Debe estar en `TRUE` para aceptar la licencia de Mojang.
- **VERSION**: Por defecto es `LATEST`. Puedes poner una específica como `1.20.4`.
- **TYPE**: Está configurado como `PAPER` para mejor rendimiento. Puedes cambiarlo a `VANILLA`, `FORGE`, etc.
- **MEMORY**: Memoria RAM asignada (ej. `2G`, `4G`).
- **ONLINE_MODE**: `TRUE` para solo usuarios Premium. `FALSE` para permitir usuarios no-premium.

## Datos

Todos los datos del mundo, configuración y plugins se guardarán en la carpeta `./data` que se creará automáticamente.

## Detener el servidor

Para detener el servidor de forma segura:

```bash
docker compose down
```
