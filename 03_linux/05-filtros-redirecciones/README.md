# 🔍 Filtros, Lectura y Redirecciones

> "En Linux, la información es poder, pero solo si sabes encontrarla y leerla."

Hasta ahora hemos aprendido a listar archivos. Ahora aprenderemos a **leer su contenido**, buscar texto dentro de ellos y manipular esa información.

## 📖 Comandos de Lectura (Viewers)
A veces los archivos son enormes (miles de líneas). No podemos simplemente volcarlos en pantalla. Necesitamos herramientas para "paginar" o ver trozos.

### 1. Paginación: `less` y `more`
Se usan para ver archivos largos página por página.

* **`less`**: Es el estándar moderno. Muestra el contenido y te deja navegar.
* **`more`**: Es la versión antigua ("exactly same like less" pero con menos funciones).

**Teclas de navegación en `less`**:
| Tecla | Acción |
| :--- | :--- |
| `Enter` | Bajar línea por línea. |
| `d` | Bajar página (Down). |
| `b` | Subir página (Back). |
| `/` | Buscar una palabra dentro del archivo. |
| `v` | Entrar en modo edición (`vi`) al vuelo. |
| `q` | Salir (Quit). |

```bash
# Ver un archivo largo cómodamente
less /etc/passwd
```
### 2. Vistas Parciales: `head` y `tail`
A veces solo te interesa el principio o el final.

* **`head`**: Muestra las primeras 10 líneas (la cabeza).
* **`tail`**: Muestra las últimas 10 líneas (la cola).

```bash
# Ver el principio del archivo
head /etc/passwd

# Ver el final del archivo
tail /etc/passwd
```

## 🕵️‍♂️ El buscador: `grep`
El comando `grep` (*Global Regular Expression Print*) se usa para encontrar texto dentro de cualquier entrada de texto o archivo.

Es tu herramienta principal para filtrar información.

### 📂 El archivo de práctica: `/etc/passwd`
Para practicar, usaremos un archivo del sistema llamado `/etc/passwd`.
* **¿Qué es?** Almacena información sobre todos los usuarios del sistema.
* **¿Por qué lo usamos?** Porque es un archivo de texto largo, perfecto para probar búsquedas.

---

## 🧪 Ejercicios de Búsqueda

### A. Búsqueda básica 
Queremos encontrar si existe el usuario "root" dentro del archivo.

* **Sintaxis:** `grep "texto_a_buscar" archivo`

```bash
# Buscar la línea que contiene la palabra "root"
grep root /etc/passwd

# Salida esperada:
# root:x:0:0:root:/root:/bin/bash
```

### B. Case Sensitive (Mayúsculas y Minúsculas)
Linux es "Case Sensitive" (sensible a mayúsculas). Para Linux, `Root` es totalmente diferente a `root`.

⚠️ **Cuidado:** Si buscas "Root" (con mayúscula), probablemente no encuentres nada.
```bash
# Esto no devolverá nada porque "root" está en minúsculas en el archivo
grep Root /etc/passwd
```
* **💡 Solución**: La opción `-i` (Ignore Case)
Si quieres buscar algo sin importar si está escrito en mayúsculas o minúsculas, usa la opción `-i`.

```bash
# Ahora sí lo encontrará, ignorando mayúsculas
grep -i Root /etc/passwd
```
### C. Búsqueda Inversa (`-v`)
¿Y si quieres ver todo **EXCEPTO** una palabra específica? Usa la opción `-v`.

```bash
# Mostrar todas las líneas que NO contengan "nologin"
grep -v nologin /etc/passwd
```
---

## ✂️ Manipulación de Texto (`cut` y `sed`)
A veces no basta con buscar, necesitamos recortar datos o reemplazar palabras.

### 1. Cortar columnas (`cut`)
Sirve para extraer columnas específicas de un archivo delimitado (como un CSV o `/etc/passwd`).

* **`-d`**: Delimitador (qué carácter separa las columnas, ej: `:`, `,`, `espacio`).
* **`-f`**: Field (qué número de columna quieres).

```bash
# Ejemplo: Extraer solo los nombres de usuario (columna 1) de /etc/passwd
# El delimitador es ':'
cut -d ":" -f 1 /etc/passwd
```

### 2. Buscar y Reemplazar (`sed`)
`sed` (Stream Editor) permite modificar el texto al vuelo. 
> ⚠️ **Nota**: Por defecto solo modifica la salida en pantalla, no cambia el archivo original.

* Sintaxis: `sed 's/buscar/reemplazar/g' archivo`

```bash
# 1. Creamos un archivo de prueba
echo "Welcome to Kernel Tech" > ktfile

# 2. Reemplazamos "Tech" por "Technologies"
sed 's/Tech/Technologies/g' ktfile

# Salida: Welcome to Kernel Technologies
# (Si haces 'cat ktfile', verás que el original sigue igual)
```

---
---

## 🔦 Búsqueda de Archivos (`find`)
A diferencia de `grep` (que mira dentro de los archivos), el comando `find` se usa para buscar la **ubicación de archivos o carpetas** en el sistema.

Es similar al buscador de archivos de Windows.

* **Sintaxis:** `find <ruta_donde_buscar> <opciones>`

```bash
# Ejemplo de la imagen: Buscar el archivo 'newtools.txt' dentro de la carpeta home
find /home/vagrant/ -name newtools.txt

## 🔀 Redirecciones de Entrada/Salida (I/O)
Normalmente, el resultado de un comando sale por la pantalla (stdout). Podemos redirigir ese resultado para guardarlo en un archivo.

### 1. Sobrescribir (`>`)
Guarda la salida en un archivo.
⚠️ **¡CUIDADO!** Si el archivo ya existe, **borra su contenido anterior** y escribe lo nuevo.

```bash
# Busca "root" y guarda el resultado en un archivo nuevo
grep root /etc/passwd > resultado_busqueda.txt

# Comprobamos el contenido del nuevo archivo
cat resultado_busqueda.txt
```

### 2. Añadir / Append (`>>`)
Agrega la salida al final del archivo sin borrar lo que ya existía.

```bash
# Añadimos una línea de fecha al final del archivo anterior
date >> resultado_busqueda.txt
```

## ⛓️ Tuberías (`|` Pipes)
El operador `|` (pipe) es la magia de Linux. Toma la salida del comando de la izquierda y la mete como entrada al comando de la derecha.

**Filosofía**: Unir herramientas pequeñas para hacer tareas complejas.

```bash
# Ejemplo: Leer el archivo y pasárselo a grep
# (El resultado es igual a grep normal, pero ilustra el flujo)
cat /etc/passwd | grep root

# Ejemplo Útil: Contar cuántas líneas tienen la palabra "false"
# 1. grep busca las líneas
# 2. wc -l las cuenta (Word Count -lines)
grep false /etc/passwd | wc -l
```