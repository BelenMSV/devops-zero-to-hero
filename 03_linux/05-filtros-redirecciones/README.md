# 🔍 Filtros y Redirecciones (grep & I/O)

> "En Linux, la información es poder, pero solo si sabes encontrarla."

Hasta ahora hemos aprendido a listar archivos. Ahora aprenderemos a **buscar texto dentro de ellos** y a manipular esa información.

## 🕵️‍♂️ El buscador: `grep`
El comando `grep` (*Global Regular Expression Print*) se usa para encontrar texto dentro de cualquier entrada de texto o archivo.

Es tu herramienta principal para filtrar información.

### 📂 El archivo de práctica: `/etc/passwd`
Para practicar, usaremos un archivo del sistema llamado `/etc/passwd`.
* **¿Qué es?** Almacena información sobre todos los usuarios del sistema.
* **¿Por qué lo usamos?** Porque es un archivo de texto largo, perfecto para probar búsquedas.

---

### 🧪 Ejercicio: Buscando usuarios
Queremos encontrar si existe el usuario "root" dentro del archivo.

* **Sintaxis:** `grep "texto_a_buscar" archivo`

```bash
# Buscar la línea que contiene la palabra "root"
grep root /etc/passwd

# Salida esperada:
# root:x:0:0:root:/root:/bin/bash
```

### 🔠 Case Sensitive (Mayúsculas y Minúsculas)
Linux es "Case Sensitive" (sensible a mayúsculas). Para Linux, `Root` es totalmente diferente a `root`.

⚠️ **Cuidado:** Si buscas "Root" (con mayúscula), probablemente no encuentres nada.
```bash
# Esto no devolverá nada porque "root" está en minúsculas en el archivo
grep Root /etc/passwd
```
### **💡 Solución**: La opción `-i` (Ignore Case)
Si quieres buscar algo sin importar si está escrito en mayúsculas o minúsculas, usa la opción `-i`.

```bash
# Ahora sí lo encontrará, ignorando mayúsculas
grep -i Root /etc/passwd
```
---

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