
<h1 align="center">Configuración Rápida & Inicial para VPS</h1>

<h4 align="center">Configura tu VPS en cuestión de <u>segundos</u></h4>

<h6 align="center">Ubuntu Server 22.04 (AMD)</h2>

# TODO EN UNO

```bash
sudo apt update -y && sudo apt upgrade -y && sudo apt-get install build-essential -y && sudo apt install curl -y && curl > https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash && source ~/.profile && nvm install 16.11.0 && npm i pm2 -g && wget https://builds.openlogic.com/downloadJDK/openlogic-openjdk/11.0.16+8/openlogic-openjdk-11.0.16+8-linux-x64-deb.deb && sudo apt install ./openlogic-openjdk-11.0.16+8-linux-x64-deb.deb && sudo timedatectl set-timezone Europe/Madrid && sudo apt install ffmpeg && pm2 flush && pm2 install pm2-logrotate && pm2 set pm2-logrotate:max_size 10M && pm2 set pm2-logrotate:compress true
```

## Establecemos la fecha de horaria correcta

```bash
sudo timedatectl set-timezone Europe/Madrid
```

## Actualización de Repositorios

Actualiza la lista de repositorios de ubuntu y actualiza el kernel.

```bash
sudo apt update -y && sudo apt upgrade -y
```

## Instalación de Dependencias

Con esto podrás instalar las dependencias y evitar errores a la hora de instalar canvas u otros errores al hacer `npm i`

```bash
sudo apt-get install build-essential
```

## Instalación de Programas

Instalamos Node Version Manager para poder instalar NodeJS `18.17.1`

```bash
sudo apt install curl && curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash && source ~/.profile && nvm install 18.17.1
```

## Instalación de PM2

Instalamos el Gestor de Procesos pm2 para mantener nuestras aplicaciones 24/7 encendidas

```bash
npm i pm2 -g && pm2 startup
```

## Instalación de Java JDK

Instalamos Java para poder usar Lavalink u otros.

```bash
sudo apt install openjdk-17-jdk openjdk-17-jre
```

## Instalamos FFMPEG para poder reproducir audio

```bash
sudo apt install ffmpeg -y
```

## [OPCIONAL PERO RECOMENDADO] Tener NODE y NPM con SUDO

### SYMLINK NODE
1. Eliminar el symlink activo de NODE
```bash
sudo unlink /usr/bin/node; sudo unlink /usr/bin/npm
```
2. Establecer el nuevo symlink de NODE
```bash
whereis node
```
3.
```bash
sudo ln -s /home/$USER/.nvm/versions/node/v18.17.1/bin/node /usr/bin/node
```

4. SYMLINK NPM
```bash
sudo ln -s /home/$USER/.nvm/versions/node/v18.17.1/bin/npm /usr/bin/npm
```

## [OPCIONAL PERO RECOMENDADO] Instalar rotación de logs para limpiar los logs de pm2

```bash
pm2 flush && pm2 install pm2-logrotate && pm2 set pm2-logrotate:max_size 10M && pm2 set pm2-logrotate:compress true
```

