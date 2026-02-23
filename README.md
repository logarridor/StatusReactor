## 🔧 ¿Cómo instalar?

### 🐳 Docker Compose

```bash
mkdir statusreactor
cd statusreactor
curl -o compose.yaml https://raw.githubusercontent.com/logarridor/StatusReactor/refs/heads/main/compose.yaml
docker compose up -d
```

StatusReactor se ejecuta en todas las intefases de red (ejemplo http://localhost:3001 or http://your-ip:3001).

> [!ADVERTENCIA]
> Sistema de archivos como **NFS** **NO** son soportados. Por favor hazlo en un directorio local o volumen local.

### 🐳 Comando Docker

```bash
docker run -d --restart=always -p 3001:3001 -v statusreactor:/app/data --name statusreactor logarridor/statusreactor:2
```

StatusReactor se ejecuta en todas las intefases de red (ejemplo http://localhost:3001 or http://your-ip:3001).


```bash
docker run ... -p 127.0.0.1:3001:3001 ...
```

### 💪🏻 Sin docker

Requisitos:

- Plataformas:
  - ✅ Mejores distribuciones de Linux como Debian, Ubuntu, Fedora y ArchLinux etc.
  - ✅ Windows 10 (x64), Windows Server 2012 R2 (x64) o superiores
  - ❌ FreeBSD / OpenBSD / NetBSD
  - ❌ Replit / Heroku
- [Node.js](https://nodejs.org/en/download/) >= 20.4
- [Git](https://git-scm.com/downloads)
- [pm2](https://pm2.keymetrics.io/) - Para ejecutar StatusReactor en segundo plano

```bash
git clone https://github.com/logarridor/StatusReactor.git
cd StatusReactor
npm run setup

# Option 1. Try it
node server/server.js

# (Recommended) Option 2. Run in the background using PM2
# Install PM2 if you don't have it:
npm install pm2 -g && pm2 install pm2-logrotate

# Start Server
pm2 start server/server.js --name StatusReactor
```
StatusReactor se ejecuta en todas las intefases de red (ejemplo http://localhost:3001 or http://your-ip:3001).

Comandos utiles PM2

```bash
# Ver monitor de activdad de PM2
pm2 monit

# Si quieres agregarlo al startup
pm2 startup && pm2 save
```