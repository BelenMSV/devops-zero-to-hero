# 🔒 Permisos y Propiedad de Archivos

> "En Linux, todo es un archivo, y todo archivo tiene un dueño y unos permisos."

Seguridad básica: Decidir quién puede leer, escribir o ejecutar un archivo.

## 1. Ver Permisos (`ls -l`)
Para ver los permisos usamos el listado largo `ls -l`.

Ejemplo de salida: `-rwxr-xr-x`

Esto se divide en 4 partes:
1.  **Tipo:** El primer carácter. `-` es archivo, `d` es directorio.
2.  **Usuario (Owner):** Los siguientes 3 (`rwx`). Lo que puede hacer el dueño.
3.  **Grupo (Group):** Los siguientes 3 (`r-x`). Lo que pueden hacer los miembros del grupo.
4.  **Otros (Others):** Los últimos 3 (`r-x`). Lo que puede hacer el resto del mundo.

### Significados
| Símbolo | Significado | Valor Octal | Descripción |
| :---: | :--- | :---: | :--- |
| **`r`** | **Read** | **4** | Leer el archivo o listar la carpeta. |
| **`w`** | **Write** | **2** | Modificar/Borrar el archivo o crear archivos en la carpeta. |
| **`x`** | **Execute** | **1** | Ejecutar como programa o entrar (`cd`) en la carpeta. |
| **`-`** | **Sin permiso** | **0** | Acceso denegado. |

---

## 2. Cambiar Propiedad (`chown` y `chgrp`)
Solo el usuario `root` puede cambiar el dueño de un archivo.

* **`chown`** (Change Owner): Cambia el usuario dueño.
* **`chgrp`** (Change Group): Cambia el grupo dueño.

```bash
# Cambiar el dueño del archivo a 'usuario'
sudo chown usuario archivo.txt

# Cambiar el grupo del archivo a 'admin'
sudo chgrp admin archivo.txt

# Cambiar dueño Y grupo a la vez (usuario:grupo)
# La opción -R lo hace recursivo (para carpetas enteras)
sudo chown -R usuario:admin /var/www/html
```
## 3. Cambiar Permisos (`chmod`)
El comando es **`chmod`** (Change Mode). Hay dos formas de usarlo.

### A. Método Simbólico (Letras)
Es más intuitivo para humanos.

* **Quién:** `u` (user), `g` (group), `o` (other), `a` (all).
* **Acción:** `+` (añadir), `-` (quitar), `=` (asignar exacto).
* **Permiso:** `r`, `w`, `x`.

```bash
# Dar permiso de ejecución (x) a todo el mundo (a)
chmod a+x script.sh

# Quitar permiso de escritura (w) y ejecución (x) a 'otros' (o)
chmod o-wx archivo_secreto.txt

# Dar lectura (r) al usuario, grupo y otros
chmod ugo+r notas.txt
```
### B. Método Numérico (Octal)
Es el método rápido y profesional. Se basa en sumar los valores (`r=4`, `w=2`, `x=1`).

**Cálculo:**
* Si quieres **Lectura (4) + Escritura (2)** = **6**.
* Si quieres **Lectura (4) + Ejecución (1)** = **5**.
* Si quieres **Todo (4+2+1)** = **7**.

Debes poner 3 números: Uno para el Usuario, otro para el Grupo, otro para Otros.

**Ejemplos Comunes:**

| Código | Descripción | Uso Típico |
| :---: | :--- | :--- |
| **`777`** | `rwx rwx rwx` (Todo para todos). | ⚠️ Peligroso. Solo pruebas. |
| **`755`** | `rwx r-x r-x` (Yo todo, los demás leen y ejecutan). | Scripts, Programas. |
| **`644`** | `rw- r-- r--` (Yo leo/escribo, los demás solo leen). | Archivos de texto, configs. |
| **`600`** | `rw- --- ---` (Solo yo leo/escribo). | Claves privadas SSH (`id_rsa`). |

```bash
# Ejemplo de la imagen: Dueño (rw- = 6), Grupo (r-- = 4), Otros (--- = 0)
chmod 640 myfile
```
---

## 4. 🚑 Troubleshooting (Errores Comunes)

### "Permission denied" al ejecutar scripts
Es el error número 1 en Linux. Creas un script, intentas ejecutarlo y pasa esto:

```bash
./mi_script.sh
# Salida: -bash: ./mi_script.sh: Permission denied
```
**¿Por qué?**
Por seguridad, Linux crea los archivos nuevos **sin permiso de ejecución** (normalmente `644` o `rw-r--r--`).

**Solución:**
Debes darle el permiso `x` (execute) explícitamente:
```bash
chmod +x mi_script.sh
./mi_script.sh
# ¡Ahora funciona!
```