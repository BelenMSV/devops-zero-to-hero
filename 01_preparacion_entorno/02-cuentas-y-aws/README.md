# ☁️ Tema 2: Cuentas y Servicios Cloud

En este tema nos enfocaremos en **registrar y configurar** los servicios externos necesarios para el ciclo de vida DevOps. A diferencia de las herramientas locales del Tema 1, estos servicios viven en la nube y son esenciales para alojar código, imágenes y desplegar infraestructura.

---

## 📋 1. Plataformas SaaS (Software as a Service)

Necesitas crear cuentas gratuitas en los siguientes servicios. Sigue las instrucciones específicas para asegurar que eliges los planes correctos (Free Tier).

### 🐙 A. GitHub (Control de Versiones)
Aquí alojaremos el código fuente de nuestros proyectos y colaboraremos.
* **Web:** [github.com](https://github.com)
* **Plan:** Selecciona el plan **"Free"**.
* **Acción:** Regístrate y **verifica tu correo electrónico** (obligatorio).
* *Tip:* Si eres estudiante, puedes aplicar al [GitHub Student Developer Pack](https://education.github.com/pack), aunque no es obligatorio para el curso.

### 🐳 B. Docker Hub (Registro de Contenedores)
Es el almacén público donde subiremos las imágenes de Docker que construyamos.
* **Web:** [hub.docker.com](https://hub.docker.com)
* **Plan:** Selecciona el plan **"Personal"** (Gratuito).
* **Acción:** Crea un **Docker ID** (usuario). Recuérdalo bien, ya que lo usaremos frecuentemente en la terminal para descargar y subir imágenes.

### 🔍 C. SonarCloud (Calidad y Seguridad)
Herramienta que analizará nuestro código en busca de errores, bugs y vulnerabilidades de seguridad.
* **Web:** [sonarcloud.io](https://sonarcloud.io)
* **Acción Crítica:** No te registres con email/password. Usa el botón **"Log in with GitHub"**.
* **Por qué:** Esto vinculará ambas cuentas automáticamente y permitirá que SonarCloud escanee tus repositorios de GitHub sin configuración extra.

### 🌐 D. Dominio Web (Opcional pero Recomendado)
Para la práctica final, desplegar una web con un dominio real (ej: `tu-nombre.xyz`) da un toque muy profesional (HTTPS, DNS).
* **Proveedores:** Namecheap, GoDaddy, Porkbun.
* **Estrategia de ahorro:** Busca extensiones baratas como **`.xyz`**, **`.online`** o **`.site`**. Suelen costar **~$1-2 USD** el primer año.
* **Importante:** Asegúrate de que la renovación automática esté controlada o desactivada si no quieres mantenerlo el año siguiente.

---

## 🏗️ 2. Infraestructura Cloud: AWS (IaaS)

Esta es la parte más crítica del módulo. Configuraremos una cuenta en **Amazon Web Services** para crear máquinas virtuales y redes en la nube.

⚠️ **Advertencia:** AWS pide tarjeta de crédito. Hemos creado una guía estricta para configurar **Alertas de Facturación** y **Seguridad (MFA)** para evitar sustos.

### Contenido de la Guía AWS:
1.  **Alta en Free Tier:** Registro seguro.
2.  **Seguridad MFA:** Proteger al usuario Root.
3.  **Usuario IAM:** Crear un administrador seguro para trabajar.
4.  **Billing Alarm:** Configurar aviso si el gasto supera los $5 USD.

👉 **[Abrir Guía Detallada de Configuración AWS](./setup-aws.md)**