# 📦 Compresión y Empaquetado (`tar`, `gzip`)

> En Linux, "empaquetar" (juntar archivos) y "comprimir" (hacer que pesen menos) son dos procesos distintos, aunque solemos hacerlos a la vez.

Imagina que `tar` es meter muchas cosas en una caja de cartón, y `gzip` es usar una máquina de envasado al vacío para que ocupe menos espacio.

## 1. Empaquetar sin comprimir (`tar`)
Crea un solo archivo a partir de una carpeta, pero **no reduce su peso**.

| Comando | Descripción |
| :--- | :--- |
| **`tar cf backup.tar /home`** | **(C)reate (F)ile:** Crea un archivo `backup.tar` que contiene toda la carpeta `/home`. |
| **`tar xf backup.tar`** | **(X)tract (F)ile:** Extrae el contenido del archivo `.tar` en la carpeta actual. |

## 2. Compresión pura (`gzip`)
Comprime un archivo individual para reducir su tamaño.

| Comando | Descripción |
| :--- | :--- |
| **`gzip archivo.txt`** | Comprime el archivo. El original desaparece y se convierte en `archivo.txt.gz`. |
| **`gunzip archivo.txt.gz`** | Descomprime el archivo y lo devuelve a su estado original (comando inverso). |

## 3. Empaquetar y Comprimir a la vez (El más usado)
Este es el comando que usarás el 99% de las veces. Combina `tar` y `gzip` en un solo paso añadiendo la letra **z**.

```bash
# (C)reate (Z)ip (F)ile: Crea un archivo comprimido .tar.gz
tar czf backup.tar.gz /carpeta_a_guardar
```