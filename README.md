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

## Agregar Plugins

No necesitas ningún programa especial. Como estamos usando **Paper** (definido en `TYPE=PAPER`), el servidor soportará plugins.

1. Inicia el servidor al menos una vez para que se creen las carpetas.
2. Ve a la carpeta `data/plugins` que se ha creado en este directorio.
3. Arrastra ahí los archivos `.jar` de los plugins que quieras instalar.
4. Reinicia el servidor:
   ```bash
   docker compose restart
   ```

## Plugins Recomendados

Estos plugins no se incluyen en el repositorio (buenas prácticas), pero puedes descargarlos y colocarlos en `data/plugins`:

### Gestión de Mundos y Lobby
- **[Multiverse-Core](https://www.spigotmc.org/resources/multiverse-core.390/)**: Para tener múltiples mundos (Lobby, SkyWars, etc.) en el mismo servidor.
- **[Multiverse-Inventories](https://www.spigotmc.org/resources/multiverse-inventories.1963/)**: Separa inventarios entre mundos (para no llevar items del lobby a los juegos).
- **[DeluxeHub](https://www.spigotmc.org/resources/deluxehub-3-professional-hub-management.49473/)**: Gestión profesional del Lobby (Scoreboard, selector de servidores, doble salto, etc).

### Minijuegos
- **[SkyWarsReloaded (Updated)](https://www.spigotmc.org/resources/skywarsreloaded-updated-recoded-1-8-1-20-4.69436/)**: El plugin clásico de SkyWars, actualizado para versiones nuevas.
- **[TNT Run Reloaded](https://www.spigotmc.org/resources/tntrun_reloaded.14357/)**: Minijuego automático de TNT Run con regeneración de arenas.

## Detener el servidor

Para detener el servidor de forma segura:

```bash
docker compose down
```
