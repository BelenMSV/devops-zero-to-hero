# 💻 Información de Hardware y Diagnóstico

> "Un SysAdmin no necesita abrir la caja del servidor para saber qué procesador o cuánta RAM tiene."

Este módulo agrupa los comandos para auditar los componentes físicos de la máquina (CPU, Memoria, Discos y Periféricos).

---

## 1. CPU y Memoria RAM
Antes de instalar una aplicación pesada (como una base de datos), debes comprobar si el servidor tiene recursos suficientes.

| Comando | Descripción |
| :--- | :--- |
| **`cat /proc/cpuinfo`** | Muestra el modelo exacto, núcleos y velocidad del procesador (CPU). |
| **`cat /proc/meminfo`** | Muestra los detalles técnicos de la memoria RAM instalada. |
| **`free -m`** | Muestra la memoria RAM usada y libre en **Megabytes** (`-m`). Es el comando más rápido para ver si te quedas sin memoria. |

---

## 2. Dispositivos y Placa Base (PCI / USB)
Útil para saber si el servidor ha detectado la nueva tarjeta de red que conectaste.

| Comando | Descripción |
| :--- | :--- |
| **`lspci -tv`** | Muestra los dispositivos conectados por PCI (tarjetas de red, gráficas) en formato de árbol (`-tv`). |
| **`lsusb -tv`** | Muestra los dispositivos conectados por USB. |
| **`dmidecode`** | Extrae la información detallada del hardware directamente desde la BIOS (fabricante, números de serie, etc.). |
| **`lshal`** | Muestra una lista de todos los dispositivos del sistema con sus propiedades. |

---

## 3. Diagnóstico Profundo y Discos
Si el servidor va lento o hace cosas raras, estos comandos te ayudan a encontrar el fallo.

| Comando | Descripción |
| :--- | :--- |
| **`dmesg`** | Muestra los mensajes del Kernel. Vital para ver si hubo errores de hardware durante el arranque (boot) o al conectar un dispositivo. |
| **`cat /proc/interrupts`** | Lista el número de interrupciones por dispositivo I/O. |
| **`hdparm -i /dev/sda`** | Muestra la información de fábrica del disco duro `sda`. |
| **`hdparm -tT /dev/sda`** | Hace un **test de velocidad** de lectura en el disco duro `sda`. |
| **`badblocks -s /dev/sda`** | Escanea el disco duro en busca de sectores físicos dañados (ilegibles). ¡Muy útil si sospechas que el disco está muriendo!. |
| **`lshw`** | Muestra un resumen general de la configuración de hardware del sistema.|
| **`lsblk`** | Muestra información de los dispositivos de bloque (discos y sus particiones) en forma de árbol. ¡Es visualmente mucho más claro que `fdisk`!.|

> *Nota: Muchos de los comandos de hardware profundo (como `hdparm`, `badblocks` o `dmidecode`) requieren permisos de administrador (`sudo`).*