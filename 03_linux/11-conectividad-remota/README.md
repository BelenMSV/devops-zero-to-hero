# 🔌 Conectividad Remota y Transferencia de Archivos

> "Como administradores, rara vez estamos físicamente delante del servidor. Trabajamos en remoto."

Este módulo cubre cómo entrar a otros ordenadores (`ssh`) y cómo enviarles archivos (`scp`, `rsync`).

## 1. Login Remoto (SSH vs Telnet)

### A. SSH (`Secure Shell`)
Es el estándar para conectarse de forma segura (encriptada).

| Comando | Descripción |
| :--- | :--- |
| **`ssh user@host`** | Conectarse al servidor `host` usando el usuario `user`. |
| **`ssh -p 2222 user@host`** | Conectarse a un puerto específico (si no es el 22 por defecto). |

### B. Telnet
Es un protocolo antiguo y **no seguro** (la contraseña viaja en texto plano). Solo se usa para probar si un puerto está abierto, nunca para trabajar.

```bash
# Conectar por telnet (¡Evitar para login!)
telnet host
```

## 2. Copiar Archivos: SCP (`Secure Copy`)
`scp` es el primo hermano de `ssh`. Usa el mismo túnel seguro, pero en lugar de abrir una terminal, solo sirve para **transportar archivos** de un lado a otro.

**La Regla de Oro:** Siempre es `scp [ORIGEN] [DESTINO]`.

### Casos de Uso
**1. Subir un archivo (De mi PC -> al Servidor)**
```bash
# "Copia file.txt y déjalo en la carpeta /tmp del servidor remoto"
scp file.txt root@192.168.1.50:/tmp
```
**2. Bajar un archivo (Del Servidor -> a mi PC)**
```bash
# "Ve al servidor, agarra index.html y tráelo aquí (el punto . significa aquí)"
scp root@192.168.1.50:/www/index.html .
```
**3. Copiar una carpeta entera**
Igual que con el comando `cp`, necesitamos el flag `-r` (recursivo) para carpetas.
```bash
scp -r carpeta_local root@192.168.1.50:/home/backup
```

## 3. Sincronización Inteligente: Rsync
Imagina que tienes un archivo de 10GB y solo has cambiado una frase.
* **SCP:** Copiaría los 10GB de nuevo (lento).
* **Rsync:** Detecta el cambio y solo envía ese pedacito (rápido y eficiente).

Es la herramienta favorita para hacer **Backups**.

**Flags Vitales (`-avz`):**
* **`-a` (Archive):** "Déjalo todo igual". Mantiene los permisos, fechas y dueños originales del archivo.
* **`-v` (Verbose):** "Cuéntame qué haces". Muestra el progreso en pantalla.
* **`-z` (Zip):** "Comprime". Comprime los datos antes de enviarlos para ahorrar internet.

```bash
# Sincronizar carpeta local con remota
# Esto asegura que /backup/ en el servidor sea idéntico a /home/apps
rsync -avz /home/apps root@servidor:/backup/
```
## 💡 Resumen Rápido

| Acción | Herramienta | ¿Cuándo usarla? |
| :--- | :--- | :--- |
| **Entrar al servidor** | `ssh` | Para trabajar en la terminal remota. |
| **Copiar archivo rápido** | `scp` | Para mover archivos sueltos puntualmente. |
| **Hacer Backup** | `rsync` | Para mover grandes cantidades de datos o mantener carpetas sincronizadas. |

---

## 4. Instalación y Requisitos
La mayoría de estas herramientas vienen pre-instaladas. Sin embargo, si obtienes el error `command not found`, instálalas así:

### Verificar si los tengo instalados
```bash
# Preguntar al sistema dónde está el programa
which ssh
which rsync
```
### Instalar si faltan

**En Ubuntu / Debian:**
```bash
sudo apt update
sudo apt install openssh-client rsync -y
# Telnet (solo si es estrictamente necesario, no recomendado)
sudo apt install telnet -y
```

**En CentOS / RedHat:**
```bash
sudo dnf install openssh-clients rsync -y
# Telnet (solo si es estrictamente necesario, no recomendado)
sudo dnf install telnet -y
```