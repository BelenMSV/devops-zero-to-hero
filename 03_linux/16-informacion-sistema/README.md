# 🖥️ Información del Sistema y Usuarios

> "La regla de oro al entrar a un servidor nuevo: Mira a tu alrededor antes de tocar nada."

Este módulo agrupa los comandos esenciales para auditar el sistema operativo, el hardware, el tiempo de actividad y los usuarios conectados.

---

## 1. Identificar el Sistema (¿Dónde estoy?)
Estos comandos te dicen qué versión de Linux estás usando y cómo se llama la máquina en la red.

| Comando | Descripción |
| :--- | :--- |
| **`uname -a`** | Muestra toda la información del sistema Linux (kernel, arquitectura, nombre). |
| **`uname`** | Muestra solo la información básica del kernel. |
| **`cat /etc/redhat_release`** | Muestra qué versión exacta de RedHat/CentOS está instalada. |
| **`hostname`** | Muestra el nombre del sistema (host). |
| **`hostname -i`** | Muestra la dirección IP asignada a ese host. |

---

## 2. Tiempo y Estado (¿Desde cuándo está encendido?)
Es vital saber si un servidor lleva meses estable o si se reinició hace 5 minutos por un error.

| Comando | Descripción |
| :--- | :--- |
| **`uptime`** | Muestra cuánto tiempo lleva el sistema encendido y la carga de trabajo (load). |
| **`last reboot`** | Muestra el historial de las últimas veces que el sistema se reinició. |
| **`date`** | Muestra la fecha y hora actual del servidor. |
| **`cal`** | Muestra un calendario del mes actual en la terminal. |

---

## 3. Usuarios (¿Quién más está aquí?)
Si vas a reiniciar un servicio o apagar la máquina, primero asegúrate de que no haya otro compañero trabajando.

| Comando | Descripción |
| :--- | :--- |
| **`whoami`** | Te dice con qué usuario estás logueado actualmente (útil si cambias mucho de sesión). |
| **`w`** | Muestra quién más está conectado (online) al servidor en este momento y qué están haciendo. |
| **`finger user`** | Muestra información detallada sobre un usuario específico en el sistema. |

```bash
# Ejemplo de rutina rápida al entrar a un servidor:
whoami
hostname
uptime
w
```
