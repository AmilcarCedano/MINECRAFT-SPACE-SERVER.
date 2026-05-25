# 🚀 Minecraft Space Server

> Despliega tu servidor de Minecraft en la nube — en órbita.

![Minecraft](https://img.shields.io/badge/Minecraft-1.21.1-brightgreen?style=flat-square&logo=minecraft)
![Docker](https://img.shields.io/badge/Docker-ready-blue?style=flat-square&logo=docker)
![Java](https://img.shields.io/badge/Java-21-orange?style=flat-square&logo=openjdk)
![License](https://img.shields.io/badge/license-MIT-purple?style=flat-square)

---

## ✨ Características

- 🚀 **Despliegue rápido** — servidor listo en minutos con un solo comando
- 🐳 **Dockerizado** — sin dependencias locales, corre en cualquier plataforma
- ⚙️ **Configurable** — RAM, versión, modo de juego y dificultad por variables de entorno
- 🛡️ **Backups automáticos** — tu mundo se guarda cada hora
- 📡 **Consola remota** — administra el servidor desde cualquier lugar
- ☁️ **Cloud-ready** — compatible con Railway, Render, Fly.io, y VPS

---

## ⚡ Quick Start

```bash
# 1. Clona el repositorio
git clone https://github.com/tu-usuario/minecraft-space-server.git
cd minecraft-space-server

# 2. Copia y configura las variables de entorno
cp .env.example .env

# 3. Lanza el servidor
docker compose up -d

# 4. Revisa los logs
docker compose logs -f minecraft
```

Conéctate desde Minecraft con: `localhost:25565`

---

## 🔧 Configuración

Copia `.env.example` a `.env` y ajusta los valores:

```env
# Versión del servidor
MC_VERSION="1.21.1"

# Recursos asignados
MC_MEMORY="2G"

# Modo de juego: survival, creative, adventure, spectator
GAMEMODE="survival"

# Dificultad: peaceful, easy, normal, hard
DIFFICULTY="normal"

# Máximo de jugadores
MAX_PLAYERS="20"

# EULA de Mojang (obligatorio)
EULA="TRUE"
```

---

## 📁 Estructura del proyecto

```
minecraft-space-server/
├── docker-compose.yml      # Orquestación del servidor
├── Dockerfile              # Imagen base
├── .env.example            # Variables de entorno de ejemplo
├── scripts/
│   ├── start.sh            # Script de arranque
│   └── backup.sh           # Script de backups automáticos
├── config/
│   └── server.properties   # Configuración de Minecraft
└── data/                   # Mundo generado (creado automáticamente)
```

---

## 🐳 Docker Compose

```yaml
services:
  minecraft:
    build: .
    ports:
      - "25565:25565"
    environment:
      - EULA=${EULA}
      - MC_VERSION=${MC_VERSION}
      - MC_MEMORY=${MC_MEMORY}
      - GAMEMODE=${GAMEMODE}
      - DIFFICULTY=${DIFFICULTY}
      - MAX_PLAYERS=${MAX_PLAYERS}
    volumes:
      - ./data:/data
    restart: unless-stopped
```

---

## ☁️ Despliegue en la nube

### Railway

1. Haz fork de este repositorio
2. Conecta tu cuenta de GitHub en [Railway](https://railway.app)
3. Crea un nuevo proyecto desde el repo
4. Añade las variables de entorno en el panel
5. Despliega 🚀

### Fly.io

```bash
fly launch
fly secrets set EULA=TRUE MC_VERSION=1.21.1 MC_MEMORY=2G
fly deploy
```

### VPS (Ubuntu/Debian)

```bash
# Instala Docker
curl -fsSL https://get.docker.com | sh

# Clona y despliega
git clone https://github.com/tu-usuario/minecraft-space-server.git
cd minecraft-space-server
cp .env.example .env && nano .env
docker compose up -d
```

---

## 🛡️ Backups

El script `scripts/backup.sh` crea una copia del mundo cada hora en `backups/`.

Para activar los backups automáticos en Linux:

```bash
# Añade al crontab
crontab -e

# Ejecutar backup cada hora
0 * * * * /ruta/al/proyecto/scripts/backup.sh
```

---

## 📡 Comandos útiles

```bash
# Ver estado del servidor
docker compose ps

# Ver logs en tiempo real
docker compose logs -f minecraft

# Consola del servidor (comandos de Minecraft)
docker attach minecraft-space-server-minecraft-1

# Detener el servidor
docker compose down

# Reiniciar
docker compose restart
```

---

## 🤝 Contribuir

1. Haz fork del repositorio
2. Crea una rama: `git checkout -b feature/mi-mejora`
3. Haz tus cambios y commit: `git commit -m "feat: añadir mi mejora"`
4. Push: `git push origin feature/mi-mejora`
5. Abre un Pull Request

---

## 📄 Licencia

MIT © [tu-usuario](https://github.com/tu-usuario)

---

<div align="center">
  ⛏ <i>Built with redstone & rockets</i> 🚀
</div>
