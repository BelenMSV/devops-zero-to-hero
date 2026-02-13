# 📦 Gestión de Paquetes y Software

> "En Linux, raramente descargamos `.exe` de webs. Usamos repositorios oficiales seguros y gestores de paquetes."

Existen dos grandes familias en Linux, y cada una tiene sus herramientas.

| Familia | Distros | Formato Archivo | Herramienta Manual | Gestor Inteligente |
| :--- | :--- | :---: | :---: | :---: |
| **RedHat** | CentOS 7, RHEL 7 | `.rpm` | `rpm` | **`yum`** |
| **Modern RH** | CentOS 8+, Fedora | `.rpm` | `rpm` | **`dnf`** |
| **Debian** | Ubuntu, Kali, Mint | `.deb` | `dpkg` | **`apt`** |

---

## 1. Herramientas de Descarga (Previo a instalar)
Antes de instalar paquetes manuales, a veces necesitamos bajarlos de internet.

| Comando | Descripción | Ejemplo |
| :--- | :--- | :--- |
| **`wget`** | Descargar archivo desde un link. | `wget http://sitio.com/archivo.rpm` |
| **`curl -O`** | Descargar y guardar con el mismo nombre. | `curl -O http://sitio.com/archivo.rpm` |
| **`curl -o`** | Descargar y guardar con *otro* nombre. | `curl http://sitio.com/file.rpm -o mi_paquete.rpm` |

---

## 2. Familia RedHat (CentOS / RHEL / Fedora)

### A. Gestión Manual con `rpm`
Útil cuando descargas un paquete suelto y no usas repositorios.

**Instalación y Borrado**:
* `rpm -ivh paquete.rpm`: Instalar (Install, Verbose, Hash).
* `rpm -Uvh paquete.rpm`: Actualizar (Upgrade).
* `rpm -ev paquete`: Eliminar (Erase).

**Consultas (Queries)**:
Es vital saber qué tienes instalado.
* `rpm -qa`: Listar **todos** los paquetes instalados.
* `rpm -qi paquete`: Ver **información** detallada del paquete.
* `rpm -qc paquete`: Ver archivos de **configuración** del paquete.
* `rpm -qf /ruta/archivo`: ¿A qué paquete pertenece este archivo? (Muy útil).

### B. Gestores Inteligentes: `yum` y `dnf`
Resuelven las dependencias automáticamente.
* **CentOS 7:** Usa `yum`.
* **CentOS 8+:** Usa `dnf`.
* *Nota: Los comandos son 99% idénticos.*

**Comandos Clave (`yum` / `dnf`)**:

```bash
# Buscar paquetes
dnf search httpd

# Instalar (flag -y para confirmar auto)
sudo dnf install httpd -y

# Ver historial de operaciones (Muy útil para deshacer cambios)
dnf history

# Limpiar caché (si hay errores de descarga)
dnf clean all

# Instalar un grupo de herramientas (ej: Development Tools)
dnf groupinstall "Development Tools"
```
## 3. Familia Debian (Ubuntu / Kali)

### A. Gestión Manual con `dpkg`
* **Instalar:** `sudo dpkg -i paquete.deb`.
* **Problemas:** Si la instalación manual falla por falta de dependencias, ejecuta `sudo apt install -f` para que el sistema las busque y repare.

### B. Gestor Inteligente: `apt`
La herramienta estándar en Ubuntu y Debian.

* **Configuración:** La lista de repositorios se encuentra en `/etc/apt/sources.list`.

**Comandos Clave:**

```bash
# 1. Actualizar lista de repositorios (Hacer SIEMPRE primero)
sudo apt update

# 2. Buscar paquete (útil si no sabes el nombre exacto)
apt search apache2

# 3. Instalar
sudo apt install apache2 -y

# 4. Reinstalar (si un paquete se corrompió)
sudo apt reinstall apache2

# 5. Borrar paquete
sudo apt remove apache2
```
## 📄 Cheatsheet Resumen

Comparativa rápida entre los comandos de RedHat (CentOS) y Debian (Ubuntu).

| Acción | RedHat / CentOS (`dnf`/`yum`) | Ubuntu / Debian (`apt`) |
| :--- | :--- | :--- |
| **Actualizar Listas** | `dnf check-update` | `apt update` |
| **Actualizar Todo** | `dnf update` | `apt upgrade` |
| **Instalar** | `dnf install pkg` | `apt install pkg` |
| **Reinstalar** | `dnf reinstall pkg` | `apt reinstall pkg` |
| **Borrar** | `dnf remove pkg` | `apt remove pkg` |
| **Buscar** | `dnf search pkg` | `apt search pkg` |
| **Ver Historia** | `dnf history` | (ver `/var/log/apt/history.log`) |