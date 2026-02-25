# 👥 Gestión de Usuarios y Grupos

> "En Linux, todo es un archivo, y cada archivo tiene un usuario dueño y un grupo asociado."

Este módulo cubre cómo crear, modificar y eliminar identidades en el sistema. Es la base fundamental antes de aprender sobre permisos (`chmod`, `chown`).

---

## 1. Tipos de Usuarios en Linux
Existen tres categorías principales de usuarios en el sistema:

1. **Root (Superusuario):** UID (User ID) = 0, GID (Group ID) = 0. Tiene control absoluto. Su directorio local es `/root`.
2. **Usuarios Regulares:** UID mayor a 1000. Son los usuarios humanos que inician sesión (ej. `vagrant`, `juan`, `maria`). Tienen su carpeta en `/home`.
3. **Usuarios de Sistema/Servicio:** UID entre 1 y 999. Son cuentas creadas por programas (como `apache`, `mysql` o `sshd`) para ejecutar procesos en segundo plano. **Importante:** Se les asigna `/sbin/nologin` o `/sbin/false` como shell para impedir que alguien inicie sesión con ellos por seguridad.

---

## 2. Archivos Críticos del Sistema
Linux no usa una base de datos compleja para los usuarios; guarda todo en archivos de texto plano que puedes inspeccionar:

| Archivo | Descripción |
| :--- | :--- |
| **`cat /etc/passwd`** | Muestra todos los usuarios del sistema, sus UIDs, GIDs, directorios *home* y qué shell utilizan. (A pesar del nombre, *no* contiene las contraseñas). |
| **`cat /etc/shadow`** | Contiene las contraseñas encriptadas y las fechas de expiración. Solo el usuario root puede leer este archivo. |
| **`cat /etc/group`** | Muestra todos los grupos del sistema y qué usuarios pertenecen a ellos (como grupos secundarios). |

---

## 3. Comandos de Gestión de Usuarios (CRUD)
*Nota: Para ejecutar estos comandos necesitas ser root o usar `sudo`.*

| Comando | Descripción |
| :--- | :--- |
| **`useradd <usuario>`** | Crea un nuevo usuario. Por defecto, le creará su carpeta `/home/<usuario>` y un grupo primario con su mismo nombre. |
| **`passwd <usuario>`** | Asigna o cambia la contraseña del usuario. Si no tiene contraseña, no podrá iniciar sesión desde fuera. |
| **`userdel <usuario>`** | Elimina al usuario del sistema, **pero deja intacta su carpeta `/home`** por si necesitas recuperar sus archivos. |
| **`userdel -r <usuario>`** | Elimina al usuario y **borra por completo** su directorio `/home`. (¡Usar con precaución!). |

---

## 4. Gestión de Grupos
Agrupar usuarios facilita darles permisos a todos a la vez sobre un directorio o archivo.

| Comando | Descripción |
| :--- | :--- |
| **`groupadd <grupo>`** | Crea un nuevo grupo en el sistema (ej. `groupadd devops`). |
| **`usermod -aG <grupo> <usuario>`** | **¡Comando Estrella!** Añade un usuario existente a un grupo secundario. (`-a` de *append*, `-G` de *Group*). |
| **`groupdel <grupo>`** | Elimina el grupo especificado. |

---

## 5. Auditoría y Cambio de Identidad
Herramientas para investigar quién es quién y cambiar de cuenta en la terminal.

| Comando | Descripción |
| :--- | :--- |
| **`id <usuario>`** | Muestra el UID, GID y todos los grupos a los que pertenece el usuario. |
| **`su - <usuario>`** | Cambia de identidad en la terminal (Switch User). Si eres root, no te pedirá contraseña. El `-` asegura que cargues el entorno (*home*, variables) del nuevo usuario. |
| **`who`** | Muestra qué usuarios están conectados al sistema en este momento. |
| **`last`** | Muestra el historial de los últimos inicios de sesión en el servidor. |
| **`lsof -u <usuario>`** | Lista todos los archivos que tiene abiertos un usuario. **Tip de SysAdmin:** Ejecuta esto antes de hacer un `userdel` para asegurarte de que el usuario no está ejecutando nada crítico. |