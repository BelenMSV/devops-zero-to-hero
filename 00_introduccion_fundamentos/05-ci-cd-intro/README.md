# 🔄 Introducción a CI/CD: La Fábrica de Software

En el desarrollo tradicional, unir el código de todos los programadores era una pesadilla. En DevOps, convertimos ese proceso manual en una **cadena de montaje automatizada**.

Este tema cierra el módulo de fundamentos explicando **cómo** movemos el código desde el ordenador del desarrollador hasta el servidor final.

---

## 1. El Problema: "Integration Hell" (El Infierno de la Integración)

En el modelo antiguo (Waterfall), el flujo de trabajo solía ser así:
1.  Un equipo trabaja durante **3 o 4 semanas** escribiendo código en sus ordenadores de forma aislada.
2.  El último día, intentan juntar (integrar) todo el trabajo en el servidor central.
3.  💥 **Resultado:** Cientos de conflictos de código, archivos sobrescritos y bugs inesperados.
4.  Se pierde más tiempo arreglando la integración que programando nuevas funciones.

> **La Solución:** En lugar de integrar una vez al mes, **integramos varias veces al día**.

---

## 2. ¿Qué es CI? (Continuous Integration)

Es una práctica automatizada donde los desarrolladores envían sus cambios a un repositorio central (como GitHub) frecuentemente. Cada cambio dispara un **Proceso Automático**.

### El Flujo de CI
El objetivo es detectar fallos **temprano** (Fail Fast).

```text
+-------------+      +--------------+      +--------------+      +--------------+
| 💻  DEV     | ---> | 📦  REPO     | ---> | ⚙️  BUILD    | ---> | ✅  TEST     |
| (Escribe)   |      | (Almacena)   |      | (Compila)    |      | (Verifica)   |
+-------------+      +--------------+      +--------------+      +--------------+
      ^                                            | (Si falla)
      |                                            v
      +------------------------------------ 🚨 NOTIFICACIÓN
                                           (Al Dev para que arregle)
```
1.  **Code Commit:** El desarrollador sube cambios al repositorio.
2.  **Build:** Un servidor de CI toma el código y lo compila.
3.  **Test:** Se ejecutan pruebas automáticas para asegurar que nada se rompió.
4.  **Feedback:** Si algo falla, el sistema avisa inmediatamente. Si todo sale bien, genera un **Artefacto**.

---

## 3. Concepto Clave: El Artefacto 📦

El resultado final del proceso de CI no es "código suelto", sino un paquete cerrado y listo para usar llamado **Artefacto**.

* Es un archivo comprimido o binario que contiene la aplicación.
* **Formatos comunes:**
    * Java: `.jar` o `.war`
    * Windows: `.exe` o `.dll`
    * Web: `.zip` o `.tar.gz`
    * Moderno: Imagen de Docker.

> **Regla de Oro:** "Build once, deploy anywhere". Generas el artefacto **una sola vez** y ese mismo archivo exacto es el que viaja a Pruebas y luego a Producción. Nunca recompilamos en producción.

---

## 4. ¿Qué es CD? (Continuous Delivery / Deployment)

Una vez tenemos el artefacto (el paquete de software), ¿qué hacemos con él? Aquí entra la segunda parte de la sigla.
Es crucial entender que en el mundo moderno, **desplegar no es solo copiar y pegar archivos** en un servidor.

### 🏗️ Las Capas de un Despliegue Real
Un proceso de despliegue completo debe orquestar varias tareas antes de que la aplicación pueda correr. No basta con mover el código, también hay que preparar el terreno:

1.  **Aprovisionamiento (Provisioning):** Crear la infraestructura si no existe (servidores, balanceadores, bases de datos).
    * *Herramientas:* Terraform, AWS CloudFormation.
2.  **Gestión de Configuración:** Instalar dependencias, parches de seguridad, configurar el Firewall y las redes.
    * *Herramientas:* Ansible, Chef, Puppet.
3.  **Despliegue de la App:** Finalmente, mover el artefacto, detener la versión antigua y arrancar la nueva.
    * *Herramientas:* Jenkins, GitHub Actions, Octopus Deploy.

### 🚦 Diferencia entre Delivery y Deployment

Aunque las siglas son las mismas (CD), existen dos grados de automatización:

* **Continuous Delivery (Entrega Continua):** Todo el proceso de construcción y pruebas es automático. El artefacto queda listo en un entorno de "Staging" (Pre-producción). El paso final a Producción requiere **aprobación manual** (un humano pulsa un botón para confirmar).
* **Continuous Deployment (Despliegue Continuo):** Automatización total. Si el artefacto pasa los tests automáticos, se despliega directo a los usuarios en Producción **sin intervención humana**.
---

## 5. Resumen del Ciclo

Para que el negocio funcione rápido y seguro:
1.  **Dev** hace commit.
2.  **CI** compila, testea y empaqueta el **Artefacto**.
3.  **CD** toma el artefacto y lo despliega en el servidor (Cloud/Linux).