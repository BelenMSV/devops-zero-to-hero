# 🗂️ Tipos de Archivos y Enlaces

> "En Linux, todo es un archivo. Pero no todos los archivos son iguales."

Cuando ejecutas `ls -l`, la primera letra de cada línea te dice qué tipo de objeto estás viendo. Es vital saber leer esto.

## 🆔 Identificando Tipos de Archivos
Fíjate en el **primer carácter** de la columna de permisos.

| Carácter | Tipo de Archivo | Descripción |
| :---: | :--- | :--- |
| **`-`** | **Regular file** | Archivos normales (texto, imágenes, ejecutables, data). |
| **`d`** | **Directory** | Directorios (carpetas). Contienen listas de otros archivos. |
| **`l`** | **Link** | Enlaces simbólicos (accesos directos) que apuntan a otro sitio. |
| **`b`** | **Block file** | Dispositivos de bloque (Discos duros, USBs) en `/dev`. |
| **`c`** | **Character file** | Dispositivos de caracteres (Terminales, impresoras) en `/dev`. |
| **`s`** | **Socket** | Archivo especial para comunicación entre procesos (redes). |
| **`p`** | **Pipe** | Tubería con nombre para pasar datos entre procesos. |


---

## 🔗 Enlaces Simbólicos (Symbolic Links)
Un **Soft Link** (enlace simbólico) es exactamente igual que un "Acceso Directo" en Windows. Es un archivo pequeño que apunta a la ruta de otro archivo real.

### ¿Para qué sirven en DevOps?
Imagina que tienes una configuración en `/var/www/html/app/config/settings.yaml` y quieres editarla cómodamente desde tu carpeta personal. Creas un link y listo.

### Comando `ln -s` (Soft Link)
* **Sintaxis:** `ln -s <archivo_real> <nombre_del_link>`

### Comando `ln` (Hard Link)
* **Sintaxis:** `ln <archivo_real> <nombre_del_link>`

Si ejecutas el comando sin la `-s` (`ln archivo.txt enlace`), crearás un **Hard Link** (enlace duro). A diferencia de los Soft Links, los enlaces duros son copias exactas a nivel de disco (apuntan al mismo inodo). Si borras el archivo original, el Hard Link sigue funcionando y conservando los datos. *(Nota: no se pueden hacer Hard Links de directorios).*

```bash
# 1. Crear un archivo real para probar
touch archivo_original.txt

# 2. Crear un enlace simbólico (acceso directo) que apunte a él
ln -s archivo_original.txt mi_acceso_directo

# 3. Verificar (Fíjate en la 'l' al principio y la flecha '->')
ls -l
# Salida esperada:
# -rw-rw-r-- 1 vagrant vagrant 0 ... archivo_original.txt
# lrwxrwxrwx 1 vagrant vagrant 20 ... mi_acceso_directo -> archivo_original.txt
```
### Borrado de enlaces simbólicos
Otro pequeño detalle vital para evitar desastres: cuando un novato quiere borrar el enlace simbólico `logdir` que habéis creado en el ejercicio, a veces usa el autocompletado del tabulador y ejecuta `rm logdir/` (con la barra al final). Dependiendo del sistema, esto puede dar error. Para borrar un enlace a un directorio, siempre es `rm logdir` (sin barra final).

> **⚠️ Nota:** Si borras el archivo original, el enlace se rompe (se queda "huérfano") y dejará de funcionar.

### 🧪 Ejercicio Práctico
Vamos a crear un acceso directo en nuestra carpeta actual que nos lleve directamente a la carpeta de logs del sistema (`/var/log`), tal como se ve en el laboratorio.

```bash
# 1. Estamos en nuestra carpeta de prácticas
pwd
# /home/vagrant/linux-practices

# 2. Creamos el enlace 'logdir' que apunta a '/var/log/'
ln -s /var/log/ logdir

# 3. Verificamos con ls -l
ls -l
# Salida esperada:
# lrwxrwxrwx 1 vagrant vagrant ... logdir -> /var/log/
```
Fíjate en dos cosas:

1. La línea empieza por `l` (indicando que es un Link).
2. Al final aparece una flecha `->` indicando a dónde apunta realmente.

Si ahora haces `cd logdir`, ¡mágicamente estarás viendo el contenido de `/var/log`!