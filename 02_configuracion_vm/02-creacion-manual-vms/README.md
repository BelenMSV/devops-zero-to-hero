# 🛠️ Estrategia de Creación Manual

Antes de usar Vagrant, vamos a crear nuestras máquinas "a la antigua usanza". Esto nos dará el conocimiento necesario para luego escribir las recetas de automatización.

## 📋 Requisitos del Laboratorio
Para completar las prácticas de este módulo necesitas:
1.  Ordenador de 64-bits con virtualización activada en BIOS.
2.  Herramientas instaladas (ver Módulo 1): VirtualBox (o VMware en Mac M1/M2) y Git Bash/Putty.
3.  Conexión a internet estable.

## 🐧 Los Sistemas Operativos (ISOs)
Trabajaremos con dos de las distribuciones Linux más populares del mercado:
* **CentOS:** La versión comunitaria de Red Hat Enterprise Linux (muy usada en servidores corporativos).
* **Ubuntu:** La distribución más popular basada en Debian.

> **Próximos pasos:** En las siguientes lecciones descargaremos las imágenes `.iso` de estos sistemas y configuraremos paso a paso el hardware virtual (CPU, RAM, Disco) para instalarlos.

# 🛠️ Creación Manual de Máquinas Virtuales

En esta sección crearemos dos servidores Linux (CentOS y Ubuntu) paso a paso. Esto nos enseñará a configurar hardware virtual, particiones y redes antes de automatizarlo.

---

## 🛑 Prerrequisitos Críticos (Solo Windows)
Si usas Windows, **DEBES** realizar estos dos pasos antes de abrir VirtualBox o fallará.

### 1. Activar Virtualización en BIOS
Debes entrar a la BIOS/UEFI de tu ordenador (F2, F12, Del o Esc al arrancar) y activar la tecnología de virtualización.
* **Intel:** Busca `Intel Virtualization Technology` o `VT-x`.
* **AMD:** Busca `SVM Mode` o `AMD-V`.
* **Estado:** Debe estar en **ENABLED**.

### 2. Desactivar Hyper-V y Conflictos
VirtualBox odia compartir el control con Windows. Busca **"Activar o desactivar las características de Windows"** en el menú Inicio y **DESMARCA** (Disable) las siguientes casillas:
* ❌ Microsoft Hyper-V
* ❌ Plataforma de Hipervisor de Windows (Windows Hypervisor Platform)
* ❌ Plataforma de máquina virtual (Virtual Machine Platform)
* ❌ Subsistema de Windows para Linux (WSL)
* ❌ Docker Desktop (si aparece como feature)

> **Reinicia tu ordenador** después de aplicar estos cambios.

---

## 📥 Descarga de ISOs
Necesitamos los discos de instalación de los sistemas operativos. Descarga estos archivos `.iso`:

| Sistema Operativo | Versión Exacta a Buscar | Link / Notas |
| :--- | :--- | :--- |
| **CentOS Stream 9** | `CentOS Stream 9` -> `x86_64` -> **`boot.iso`** | [Web Oficial](https://www.centos.org/download/) (Aprox 1GB) |
| **Ubuntu Server** | `Ubuntu Server 22.04 LTS` | [Web Oficial](https://ubuntu.com/download/server) (No descargar versión Desktop) |

---

## 🌐 Concepto Clave: Bridged Networking (Adaptador Puente)
Para que nuestras VMs se comporten como servidores reales en tu casa, usaremos el modo **"Adaptador Puente"**.