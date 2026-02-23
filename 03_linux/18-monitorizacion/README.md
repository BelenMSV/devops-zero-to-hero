# 📊 Monitorización y Rendimiento (Estadísticas)

> "Cuando el servidor va lento, no reinicies a ciegas. Usa las estadísticas para encontrar al culpable: ¿Es la CPU, la RAM, el Disco o la Red?"

Este módulo contiene las herramientas clave para analizar el rendimiento del sistema en tiempo real y cazar cuellos de botella.

---

## 1. CPU y Memoria (Rendimiento General)
El primer paso cuando algo va lento es mirar el procesador y la memoria RAM.

| Comando | Descripción |
| :--- | :--- |
| **`top`** | Muestra y actualiza en tiempo real los procesos que más CPU consumen. |
| **`mpstat 1`** | Muestra estadísticas detalladas relacionadas con los procesadores/núcleos. |
| **`vmstat`** | Muestra estadísticas de la memoria virtual (swap) y del sistema. ¡Una herramienta de rendimiento súper útil!. |
| **`free -m`** | Muestra la cantidad de RAM usada y libre en Megabytes. De uso diario. |

---

## 2. Discos e I/O (Entrada/Salida)
Si la CPU está bien, quizás el disco duro no da abasto leyendo y escribiendo datos.

| Comando | Descripción |
| :--- | :--- |
| **`iostat 2`** | Muestra estadísticas de Entrada/Salida (I/O) de los discos. El "2" hace que se actualice cada 2 segundos. |

---

## 3. Red y Tráfico (Análisis de Paquetes)
Cuando el problema es la conexión, los administradores se ponen el sombrero de detectives para inspeccionar los paquetes de red.

| Comando | Descripción |
| :--- | :--- |
| **`tcpdump -i eth1`** | Captura y muestra todos los flujos de paquetes que pasan por la interfaz de red `eth1`. |
| **`tcpdump -i eth0 'port 80'`** | Monitoriza todo el tráfico web (HTTP) que pasa por el puerto 80 en la interfaz `eth0`. |

---

## 4. Auditoría de Archivos y Seguimiento Continuo
A veces necesitas saber qué está haciendo un programa exactamente o ver cómo cambian los datos en vivo.

| Comando | Descripción |
| :--- | :--- |
| **`lsof`** | Lista todos los archivos que están abiertos actualmente por los procesos activos (¡Uno de los comandos favoritos de los SysAdmins!). |
| **`lsof -u testuser`** | Lista solo los archivos que han sido abiertos por un usuario específico (`testuser`). |
| **`tail -n 500 /var/log/syslog`** | Muestra los últimos 500 mensajes de los logs del kernel/sistema. |
| **`watch df -h`** | Ejecuta el comando `df -h` repetidamente para que puedas ver cómo cambia el espacio libre del disco continuamente. |