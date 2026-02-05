# 👥 Gestión de Usuarios y Grupos (Teoría)

> "En Linux, cada proceso y cada archivo tiene un dueño. Controlar a los usuarios es controlar la seguridad."

## 🧠 Conceptos Importantes
Antes de crear usuarios, debemos entender cómo los gestiona Linux internamente:

* **Acceso:** Usuarios y grupos se usan para controlar el acceso a archivos y recursos.
* **Login:** Los usuarios entran al sistema con su nombre (username) y contraseña.
* **Propiedad:** Cada archivo pertenece a un usuario y está asociado a un grupo.
* **UID (User ID):** El sistema no lee nombres, lee números. A cada usuario se le asigna un ID único.

### 📂 Archivos clave
| Archivo | Descripción |
| :--- | :--- |
| **`/etc/passwd`** | Almacena nombre de usuario, UID, directorio home, shell, etc. |
| **`/etc/shadow`** | Almacena las **contraseñas encriptadas**. |
| **`/home/username`** | Directorio personal asignado al usuario. |

---

## 🆔 Los 3 Tipos de Usuarios
En Linux existen tres categorías de usuarios según su poder y su rango de UID.

| Tipo | UID (Rango) | Ejemplo | Descripción |
| :--- | :---: | :--- | :--- |
| **Root (Super User)** | **0** | `root` | El administrador todopoderoso. Tiene control total para crear/borrar usuarios. |
| **Service (System)** | **1 - 999** | `apache`, `ssh`, `ftp` | Usuarios creados automáticamente por aplicaciones (como Apache) para ejecutar procesos en segundo plano. |
| **Regular (Normal)** | **1000 - 60000** | `imran`, `vagrant` | Usuarios humanos normales creados por el root. Tienen su propia carpeta en `/home`. |

> **Nota:** Cuando se crea un usuario normal, se generan por defecto 3 cosas:
> 1. Un directorio home (`/home/nombre`).
> 2. Un buzón de correo (`/var/spool/mail`).
> 3. Un UID y GID únicos.

---

## 🧬 Anatomía de `/etc/passwd`
Es el archivo más importante. Vamos a entender qué significa cada campo de una línea.

Ejemplo: `root:x:0:0:root:/root:/bin/bash`

1.  **`root`**: Nombre del usuario (Login name).
2.  **`x`**: La contraseña está guardada en `/etc/shadow` (es un link de seguridad).
3.  **`0`**: **UID** (User ID). Si es 0, es Superusuario.
4.  **`0`**: **GID** (Group ID). El grupo principal al que pertenece.
5.  **`root`**: Comentario (información extra sobre el usuario).
6.  **`/root`**: Directorio Home (donde aterriza al hacer login).
7.  **`/bin/bash`**: Shell por defecto (el programa que interpreta sus comandos).

---

## 👥 El archivo de Grupos (`/etc/group`)
Al igual que los usuarios, los grupos tienen su propio archivo de configuración.

Estructura: `Group name : password : GID : group members`

---

## 🔐 El archivo de secretos: `/etc/shadow`
Mientras que `/etc/passwd` es legible por todos, `/etc/shadow` solo puede leerlo el root porque contiene datos sensibles.

Cada línea tiene 9 campos separados por `:`:
1.  **Username:** Nombre del usuario.
2.  **Encrypted Password:** La contraseña cifrada. Si ves `!!` o `*`, el usuario no tiene contraseña o está bloqueado.
3.  **Last Change:** Días desde que se cambió la contraseña (contando desde 1970).
4.  **Min Days:** Días mínimos antes de poder cambiar la contraseña.
5.  **Max Days:** Días máximos antes de que la contraseña caduque (obligatorio cambiarla).
6.  **Warning:** Días de aviso antes de que caduque.
7.  **Inactive:** Días para deshabilitar la cuenta tras caducar la contraseña.
8.  **Expiry:** Fecha absoluta de caducidad de la cuenta.
9.  **Reserved:** Reservado para uso futuro.

---

## 🛠️ Comandos de Gestión (Práctica)

### 1. Crear usuario y asignar contraseña
El comando `useradd` crea el usuario, pero la cuenta está desactivada hasta que le pones contraseña.

```bash
# 1. Crear el usuario 'dino' (como root o con sudo)
sudo useradd dino

# 2. Asignarle una contraseña (te pedirá escribirla dos veces)
sudo passwd dino

# 3. Cambiar de usuario para probar (Switch User)
su - dino
```