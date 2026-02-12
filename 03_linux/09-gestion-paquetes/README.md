# 📦 Gestión de Paquetes y Software

> "En Linux, raramente descargamos `.exe` de webs. Usamos repositorios oficiales seguros y gestores de paquetes."

Existen dos grandes familias en Linux, y cada una tiene sus herramientas.

| Familia | Distros | Formato Archivo | Herramienta Manual | Gestor Inteligente |
| :--- | :--- | :---: | :---: | :---: |
| **RedHat** | CentOS, RHEL, Fedora | `.rpm` | `rpm` | **`yum`** (o `dnf`) |
| **Debian** | Ubuntu, Kali, Mint | `.deb` | `dpkg` | **`apt`** |

---

## 1. RedHat / CentOS (RPM y YUM)

### A. Instalación Manual (`rpm`)
Podemos descargar un archivo `.rpm` e instalarlo manualmente.
* Comando: `rpm -ivh paquete.rpm` (Install, Verbose, Hash).

**El Problema de las Dependencias:**
Si intentas instalar un paquete complejo (como `httpd`) con `rpm`, fallará si te faltan librerías previas. Es el infierno de las dependencias.

### B. La Solución: YUM (`Yellowdog Updater Modified`)
YUM resuelve las dependencias automáticamente. Sabe qué librerías faltan, las baja y las instala por ti.

* **Configuración:** Los repositorios (de dónde bajar cosas) están en `/etc/yum.repos.d/`.

**Comandos Clave de YUM**:

```bash
# Actualizar todos los paquetes del sistema
sudo yum update

# Instalar un programa (y sus dependencias automáticamente)
# -y responde "yes" a todo
sudo yum install httpd -y

# Eliminar un programa
sudo yum remove httpd -y

# Ayuda y lista de opciones
yum --help
```
## 2. Debian / Ubuntu (DPKG y APT)

### A. Instalación Manual (`dpkg`)
Si tienes un archivo `.deb` descargado (ej: con `wget`), lo instalas así:

```bash
# Descargar un paquete .deb
wget [http://archive.ubuntu.com/ubuntu/pool/universe/t/tree/tree_1.7.0-3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/tree/tree_1.7.0-3_amd64.deb)

# Instalar manualmente
sudo dpkg -i tree_1.7.0-3_amd64.deb
```
### B. La Solución: APT (`Advanced Package Tool`)
Es el equivalente a YUM pero para la familia Debian/Ubuntu. Es la forma estándar y recomendada de trabajar.

* **Configuración:** La lista de repositorios (de dónde descargar el software) está en el archivo `/etc/apt/sources.list`. Este archivo es el mapa que usa el sistema para saber dónde buscar actualizaciones o programas nuevos.

```bash
# Ver la lista de fuentes (repositorios)
cat /etc/apt/sources.list

# Ver la ayuda y opciones del comando
apt --help
```
> **Nota:** El flujo de trabajo típico con APT es:
> 1. `sudo apt update` (Actualiza la lista de paquetes disponibles).
> 2. `sudo apt install nombre_paquete` (Instala el programa y sus dependencias).

**Comandos Clave de APT**:

```bash
# 1. Actualizar la lista de repositorios (Hacer siempre antes de instalar)
sudo apt update

# 2. Buscar un paquete (Ej: buscar 'apache2')
# Muy útil si no sabes el nombre exacto del programa
apt search apache2

# 3. Instalar un programa
# En Ubuntu, el servidor web se llama 'apache2' (en CentOS era 'httpd')
sudo apt install apache2 -y
```