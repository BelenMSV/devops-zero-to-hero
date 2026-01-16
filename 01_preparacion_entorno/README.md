# 🛠️ Módulo 1: Preparación del Entorno

> "Antes de empezar el viaje, hay que hacer las maletas."

Este módulo cubre la instalación de herramientas y la creación de cuentas necesarias para el curso. Sigue los pasos en orden para tener tu laboratorio listo.

---

## 📍 Tema 1: Herramientas Locales (On-Premise) 💻
*(Carpeta: `01-instalacion-herramientas`)*

Dependiendo de tu sistema operativo, hemos preparado guías específicas para instalar **VirtualBox, Vagrant, Git, Java 17, Maven y VSCode** usando la terminal (como un profesional).

| Tu Sistema Operativo | Archivo de Instalación |
| :--- | :--- |
| **Windows** | [📂 Ir a Guía Windows](./01-instalacion-herramientas/install-windows.md) (vía Chocolatey) |
| **macOS** | [📂 Ir a Guía macOS](./01-instalacion-herramientas/install-mac.md) (vía Homebrew) |
| **Linux** | [📂 Ir a Guía Linux](./01-instalacion-herramientas/install-linux.md) (Ubuntu/RHEL) |

---

## ☁️ Tema 2: Cuentas y Nube (Cloud)
*(Carpeta: `02-cuentas-y-aws`)*

En esta fase configuramos todos los servicios externos. Necesitamos registrarnos en plataformas de terceros y configurar nuestra nube en Amazon.

### Parte A: Plataformas SaaS (Signups)
Regístrate gratuitamente en estos servicios para poder alojar tu código y contenedores:

#### A. GitHub (Código)
1.  Ve a [github.com](https://github.com) y crea una cuenta gratuita.
2.  Verifica tu correo electrónico.
3.  *Opcional:* Si te pregunta, selecciona el plan "Free" y rol de estudiante/profesor.

#### B. Docker Hub (Imágenes)
Es el registro donde subiremos nuestros contenedores.
1.  Ve a [hub.docker.com](https://hub.docker.com).
2.  Regístrate (Sign up) con el plan gratuito (Personal).

#### C. SonarCloud (Calidad de Código)
1.  Ve a [sonarcloud.io](https://sonarcloud.io).
2.  Selecciona **Log in** o **Sign up**.
3.  **Importante:** Elige entrar **"With GitHub"** para vincular ambas cuentas.

#### D. Dominio Web (Opcional) 🌐
Se recomienda comprar un dominio para prácticas de producción (SSL, DNS), aunque es opcional.
* **Truco de ahorro:** Busca dominios con extensiones **`.xyz`** en registradores como GoDaddy o Namecheap. Suelen costar ~$1-2 USD el primer año.
* Asegúrate de seleccionar duración **1 año** en el carrito para ver el precio real bajo.

### Parte B: Infraestructura en AWS (IaaS)
El paso final y más crítico es configurar tu cuenta de Amazon Web Services con las medidas de seguridad y alertas de facturación adecuadas. Como es un proceso delicado (seguridad y pagos), tiene su propia guía detallada donde configuraremos la cuenta, el usuario IAM y las alertas de facturación.

👉 **[Ir a Guía de Configuración AWS](./02-cuentas-y-aws/setup-aws.md)**