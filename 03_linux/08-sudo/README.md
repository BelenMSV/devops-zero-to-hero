# 🛡️ Sudo y Privilegios de Superusuario

> "Un gran poder conlleva una gran responsabilidad." - Principio de sudo.

El comando **`sudo`** permite a un usuario normal ejecutar comandos con privilegios de administrador (root).

## 1. Comandos Básicos
Si un usuario tiene permisos de sudo, puede convertirse en root en cualquier momento.

```bash
# Ejecutar un solo comando como root (pide tu contraseña)
sudo apt update

# Convertirse en root permanentemente (cambia el prompt de $ a #)
sudo -i
# Para salir, escribe 'exit'
```
> **Diferencia entre `su` y `sudo`**:
> * **`su - usuario`**: (Switch User) Te cambia a otro usuario. Necesitas saber la contraseña *de ese usuario*.
> * **`sudo -i`**: Te convierte en root. Necesitas saber *tu propia contraseña* (y estar en la lista de sudoers).

---

## 2. El archivo `/etc/sudoers`
Aquí es donde se define **quién** tiene permiso para usar sudo.

⚠️ **IMPORTANTE:** Nunca edites este archivo con un editor de texto normal. **Usa siempre el comando `visudo`**.
* **¿Por qué?** Porque `visudo` verifica la sintaxis antes de guardar. Si cometes un error en este archivo, puedes bloquear el acceso administrativo al sistema.

```bash
# Editar la lista de sudoers de forma segura
sudo visudo
```
## 3. Configuración de Privilegios
Dentro del archivo `/etc/sudoers`, la configuración controla quién puede hacer qué.

### A. Dar permisos a un Usuario
Para otorgar privilegios de root completos a un usuario específico (ej: `sam`), añadimos una línea debajo de la de root:

```text
# User privilege specification
root    ALL=(ALL:ALL) ALL
sam     ALL=(ALL:ALL) ALL
```
### B. Dar permisos a un Grupo
Para dar permisos a todo un grupo de usuarios, se usa el símbolo `%` delante del nombre del grupo.

```text
# Los miembros del grupo 'admin' tienen permisos totales
%admin ALL=(ALL) ALL
```
### C. Sudo sin contraseña (`NOPASSWD`)
Esta configuración es muy útil para scripts de automatización (DevOps) donde no hay un humano para escribir la clave. Permite ejecutar comandos `sudo` sin que pida la password.

```text
# El usuario 'sam' puede ejecutar sudo sin poner contraseña
sam ALL=(ALL:ALL) NOPASSWD: ALL
```
## 4. Cambiar de Usuario (`su` vs `sudo`)
Aunque parecen similares, funcionan de forma distinta.

| Comando | Descripción | Contraseña requerida |
| :--- | :--- | :--- |
| **`su - sam`** | Cambia al usuario 'sam'. | Pide la contraseña de **sam** (o la de root si quieres ser root). |
| **`sudo -i`** | Te convierte en **root**. | Pide **tu propia** contraseña. |

```bash
# Ejemplo: Cambiar de usuario actual a 'sam'
su - sam

# Ejemplo: Convertirse en root directamente (si estás en sudoers)
sudo -i
```