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
- **OPS**: Lista de usuarios administradores (ej. `OPS=Steve,Alex`). Se añaden automáticamente al iniciar.
- **MOTD**: El mensaje que aparece debajo del nombre del servidor en la lista multijugador.

### Icono del Servidor
Para cambiar la imagen del servidor:
1. Consigue una imagen `.png`.
2. Redimensiónala para que sea **exactamente de 64x64 píxeles**.
3. Ponle el nombre `server-icon.png`.
4. Guárdala dentro de la carpeta `data/`.
5. Reinicia el servidor.

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
- **[DeluxeHub](https://www.spigotmc.org/resources/deluxehub-3-professional-hub-management.49425/)**: Gestión profesional del Lobby (Scoreboard, selector de servidores, doble salto, etc).
- **[WorldEdit](https://dev.bukkit.org/projects/worldedit)**: Herramienta esencial para pegar mapas (schematics) y editar el mundo rápidamente.

### Minijuegos
- **[SkyWarsReloaded (Updated)](https://www.spigotmc.org/resources/skywarsreloaded-updated-recoded-1-8-1-20-4.69436/)**: El plugin clásico de SkyWars, actualizado para versiones nuevas.
- **[TNT Run Reloaded](https://www.spigotmc.org/resources/tntrun_reloaded-tntrun-for-1-13-1-21-11.53359/)**: Minijuego automático de TNT Run con regeneración de arenas.

## Recursos y Mapas
- **Lobby Recomendado (Gratis)**: [Red Lobby - Free Map](https://builtbybit.com/resources/red-lobby-free-map.50601/?ref=discover)
- **[VoidGen (Fork)](https://modrinth.com/plugin/voidgen/version/2.3.4/)**: Necesario para crear mundos totalmente vacíos (útil para el Lobby o SkyWars).

### Plugins para Survival
- **[EssentialsX](https://essentialsx.net/downloads.html)**: El "kit básico" (Warps, Home, TPA, Spawn). Imperdible.
- **[GriefPrevention](https://www.spigotmc.org/resources/griefprevention.1884/)**: Para que los jugadores protejan sus casas (con la pala de oro). Es muy fácil de usar.
- **[LuckPerms](https://luckperms.net/download)**: Para crear rangos (Admin, VIP, Usuario) y gestionar permisos.
- **[Vault](https://www.spigotmc.org/resources/vault.34315/)**: Necesario para que funcionen la economía y los rangos.
- **[ViaVersion](https://www.spigotmc.org/resources/viaversion.19254/)**: Permite que entren jugadores con versiones antiguas de Minecraft (aunque tu server sea 1.21).
- **[Minepacks](https://www.spigotmc.org/resources/minepacks-backpack-plugin-recoded.19286/)**: Añade mochilas que se pueden abrir con comando o ítems, y se pueden configurar para ser crafteables.


## Detener el servidor

Para detener el servidor de forma segura:

```bash
docker compose down
```
