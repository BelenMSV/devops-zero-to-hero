# 💻 Tema 1: Herramientas Locales (On-Premise)

En esta sección prepararemos "la fábrica" en tu propio ordenador. Antes de subir a la nube, necesitamos un entorno local robusto para desarrollar y probar nuestras aplicaciones.

---

## 📦 El Stack Tecnológico

Estas son las herramientas que instalaremos y su función en el curso:

### 1. Infraestructura y Virtualización
* **VirtualBox / VMware:** Es el "motor" que simula el hardware. Nos permite crear ordenadores virtuales aislados dentro de tu sistema principal.
    * *Nota:* En Mac con chip Apple Silicon usaremos VMware Fusion Player.
* **Vagrant:** Es el "director de orquesta". En lugar de crear máquinas haciendo clics manualmente, usaremos Vagrant para definir y levantar entornos idénticos con una sola línea de código.

### 2. Desarrollo y Código
* **Git:** El sistema de control de versiones. Es nuestra "máquina del tiempo" para guardar y compartir código.
* **Java 17 (OpenJDK):** El lenguaje de programación base que usaremos para la aplicación de ejemplo.
* **Maven:** La herramienta que compila y empaqueta el código Java.
* **VSCode:** El editor de código recomendado (incluido en los scripts de Windows y Mac).

---

## ⚠️ Requisito Previo Crítico (Hardware)
Para que la virtualización funcione, **debes tener la Virtualización activada en la BIOS/UEFI** de tu ordenador.

* En procesadores Intel se llama **VT-x** o **Virtualization Technology**.
* En procesadores AMD se llama **AMD-V** o **SVM Mode**.

> **Si no activas esto en la BIOS:** La instalación funcionará, pero cuando intentes arrancar una máquina virtual te dará un error crítico y no iniciará.

---

## 🚀 Guías de Instalación por Sistema Operativo

Hemos automatizado el proceso lo máximo posible. Selecciona tu sistema:

| Sistema Operativo | Guía de Instalación |
| :--- | :--- |
| **🪟 Windows** | [📂 Ver Guía paso a paso](./install-windows.md) |
| **🍎 macOS** | [📂 Ver Guía paso a paso](./install-mac.md) |
| **🐧 Linux** | [📂 Ver Guía paso a paso](./install-linux.md) |

> **✅ Verificación:** Al terminar la instalación, es **obligatorio** cerrar la terminal, abrir una nueva y ejecutar los comandos de verificación incluidos al final de cada guía (como `vagrant --version` o `java -version`) para asegurar que todo está listo.