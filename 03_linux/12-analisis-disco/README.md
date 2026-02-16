# 💾 Análisis de Disco y Almacenamiento

> "La regla #1 del SysAdmin: Nunca dejes que el disco se llene al 100% o el servidor dejará de funcionar."

En este módulo aprenderás a diagnosticar problemas de espacio y gestionar discos.

## 1. ¿Cuánto espacio libre queda? (`df`)
El comando `df` (Disk Free) te da una visión general de todas las particiones del sistema.

| Comando | Descripción |
| :--- | :--- |
| `df` | Muestra el espacio en bloques de 1K (difícil de leer). |
| **`df -h`** | (Human Readable) Muestra el tamaño en **MB** o **GB**. ¡Usa siempre este! |
| `df -i` | Muestra los **Inodos** libres (a veces el disco tiene espacio, pero se agotan los "ficheros permitidos"). |

```bash
# Ver estado del disco en formato legible
df -h
```
## 2. ¿Qué está ocupando tanto espacio? (`du`)
Si `df` te dice que el disco está lleno, usas `du` (Disk Usage) para encontrar al culpable (qué carpeta pesa más).

| Comando | Descripción |
| :--- | :--- |
| `du` | Muestra el peso de cada archivo individualmente (demasiada información). |
| `du -sh` | (Summary Human) Muestra solo el peso **total** de la carpeta actual en GB/MB. |
| `du -sh *` | Muestra el peso de cada carpeta/archivo en el directorio actual (ideal para comparar). |

```bash
# Ejemplo: Estoy en /var y quiero ver qué carpeta pesa más
cd /var
sudo du -sh *
```

## 3. Discos y Particiones (`fdisk`)
Herramienta administrativa para ver los discos físicos conectados (discos duros, USBs, volúmenes virtuales).

> *Nota: Requiere permisos de administrador (`sudo`).*

```bash
# Listar todos los discos y particiones detectados
sudo fdisk -l
```
## 4. Montar Discos (`mount`)
En Linux, cuando conectas un USB o disco nuevo, a veces no aparece automáticamente. Tienes que "montarlo" en una carpeta para poder acceder a él.

**Sintaxis:** `mount [DISPOSITIVO] [CARPETA_DESTINO]`

```bash
# 1. Crear una carpeta donde aparecerá el contenido (Punto de montaje)
sudo mkdir /mnt/usb

# 2. Enlazar el dispositivo (ej: /dev/sdb1) a esa carpeta
sudo mount /dev/sdb1 /mnt/usb

# 3. Desmontarlo cuando termines (importante antes de desconectar)
sudo umount /mnt/usb
```

## 💡 Resumen de Emergencia
Si el servidor va lento o da error de "No space left on device", sigue estos pasos para liberar espacio rápidamente:

1.  **`df -h`**: Revisa si alguna partición está al 100% (usualmente `/` o `/var`).
2.  **`cd /`**: Ve a la raíz (o a la partición que esté llena).
3.  **`du -sh *`**: Mira qué carpeta pesa más (ej: si `/var` pesa 50GB, entra ahí con `cd var` y repite el comando para ver qué subcarpeta es la culpable).
4.  **`rm`**: Borra lo que sobre (logs viejos, backups antiguos, caché).