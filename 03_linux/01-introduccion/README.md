# 📖 Introducción y Fundamentos de Linux

Linux no es solo un sistema operativo gratuito; es un núcleo (kernel) Open Source que ha revolucionado la industria IT.

## 🧠 Filosofía y Principios
Linux sigue unos principios de diseño muy claros que facilitan la automatización:

1.  **Todo es un archivo:** Incluyendo el hardware (tu ratón, disco duro o teclado son representados como archivos en `/dev`).
2.  **Programas pequeños:** Herramientas que hacen una sola cosa, pero la hacen muy bien.
3.  **Encadenamiento (Piping):** Capacidad de conectar programas pequeños para realizar tareas complejas.
4.  **Configuración en Texto:** No hay "registros" ocultos ni bases de datos binarias extrañas. La configuración se guarda en archivos de texto plano, ideales para editar y versionar.

### 🚀 ¿Por qué Linux para DevOps?
Según la documentación oficial:
* **Open Source:** Código disponible para estudiar y modificar.
* **Automatización:** La mayoría de herramientas DevOps se implementan primero en Linux.
* **Personalizable:** Puedes crear una versión mínima que solo tenga lo necesario para tu aplicación.
* **Seguro:** Arquitectura de permisos robusta.

---

## 🏗️ Arquitectura del Sistema
El sistema se organiza en capas concéntricas:

```mermaid
graph TD
    User[Usuario / Aplicaciones] --> Shell[Shell (Intérprete de Comandos)]
    Shell --> Kernel[Kernel (Núcleo)]
    Kernel --> Hardware[Hardware (CPU, RAM, Disco)]
```
* **Hardware:** Los recursos físicos.
* **Kernel:** El cerebro creado por Linus Torvalds. Gestiona el hardware.
* **Shell:** La interfaz que nos permite "hablar" con el kernel mediante comandos.

---

## 🆚 Las Dos Grandes Familias (Distros)
Aunque hay cientos de distribuciones, en el mundo empresarial/DevOps dominan dos familias. La principal diferencia es su **gestor de paquetes**.

### 📦 ¿Qué es realmente un paquete (RPM/DEB)?
Desde el punto de vista técnico, no hay mucha diferencia entre ellos. Tanto los archivos `.rpm` como los `.deb` son simplemente **archivos comprimidos (archives)** con metadatos adjuntos. Ambos contienen los ficheros del programa y las instrucciones de dónde deben instalarse, difiriendo solo en detalles sutiles de implementación.

### Tabla Comparativa
A pesar de su similitud técnica, sus ecosistemas son incompatibles:

| Familia | Sistema Operativo (Ejemplos) | Formato de Paquete | Comandos de Instalación | Enfoque |
| :--- | :--- | :--- | :--- | :--- |
| **Red Hat (RPM)** | RHEL, CentOS, Amazon Linux, Fedora | `.rpm` | `rpm`, `yum`, `dnf` | Estabilidad, Servidores Corporativos. |
| **Debian** | Ubuntu, Kali, Linux Mint | `.deb` | `dpkg`, `apt`, `apt-get` | Facilidad de uso, Desarrollo, IA. |

> **Nota:** En este curso usaremos ambas (CentOS y Ubuntu) para que aprendas a manejarte en cualquier entorno.

### Ejemplo Práctico: Instalando Google Chrome
Fíjate en cómo cambia el nombre del archivo y el comando de instalación según la familia:

| Característica | Familia Red Hat (CentOS/RHEL) | Familia Debian (Ubuntu) |
| :--- | :--- | :--- |
| **Extensión** | `.rpm` (Red Hat Package Manager) | `.deb` (Debian Software Package) |
| **Ejemplo de Archivo** | `google-chrome-stable...x86_64.rpm` | `google-chrome-stable...amd64.deb` |
| **Comando Manual** | `rpm -ivh paquete.rpm` | `dpkg -i paquete.deb` |
| **Gestor Inteligente** | `yum` o `dnf` | `apt` o `apt-get` |

> **⚠️ Nota Importante:** No solo cambian los paquetes. También encontrarás que los **nombres de servicios** a veces son distintos (ej: en Ubuntu es `apache2`, pero en CentOS es `httpd`).

---

## 📂 Estructura de Directorios (Filesystem Hierarchy)
En Linux no existen `C:\` o `D:\`. Todo empieza desde la raíz `/`.

| Directorio | Función |
| :--- | :--- |
| **`/` (Root)** | El inicio de todo. |
| **`/root`** | La casa del usuario Administrador (Superusuario). |
| **`/home`** | Donde viven los usuarios normales (ej: `/home/vagrant`). |
| **`/bin` & `/usr/bin`** | Comandos ejecutables para todos los usuarios (ej: `ls`, `cat`). |
| **`/sbin`** | Comandos de sistema (System Binaries) reservados para el admin (ej: `reboot`, `iptables`). |
| **`/etc`** | **Archivos de Configuración**. Aquí vivirá gran parte de tu trabajo DevOps. |
| **`/var`** | Datos variables: Logs, webs (`/var/www`), bases de datos. |
| **`/tmp`** | Archivos temporales (se borran al reiniciar). |
| **`/boot`** | Archivos del kernel y gestor de arranque. |
| **`/dev`** | **Devices (Dispositivos)**. Aquí están tus discos duros, terminales, etc. representados como archivos. |
| **`/proc`** | **Procesos e Info**. Información del kernel en tiempo real (CPU, RAM) como si fueran archivos de texto. |
| **`/lib`** | **Librerías compartidas** necesarias para que arranquen los programas.|
| **`/media`** / **`/mnt`** | **Puntos de montaje** para dispositivos externos (USB, Discos duros).|