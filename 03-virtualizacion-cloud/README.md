# ☁️ Virtualización y Cloud Computing

Este tema cubre la infraestructura: el lugar físico o virtual donde se ejecuta nuestro software. Entender la evolución desde los servidores físicos hasta la nube es clave para entender por qué usamos herramientas modernas.

---

## 1. Evolución de la Infraestructura

### 🖥️ 1. Bare Metal (On-Premise)
Es el modelo tradicional. La empresa compra sus propios servidores físicos, los instala en un rack en su oficina o data center, instala el sistema operativo y la aplicación.
* **Problema:** Es caro, lento de escalar (hay que comprar y enchufar hardware) y desperdicia recursos (si el servidor está al 10% de uso, el otro 90% se pierde).

### 📦 2. Virtualización
Gracias a un software llamado **Hipervisor** (como VMware o VirtualBox), podemos dividir un servidor físico potente en muchas "Máquinas Virtuales" (VMs).
* **Ventaja:** Aprovechamiento total del hardware.
* **Aislamiento:** Cada VM tiene su propio Sistema Operativo (Guest OS) completo.

### 🌐 3. Cloud Computing (La Nube)
La definición simplificada: *"La nube es simplemente el ordenador de otra persona"*.
Proveedores (AWS, Azure, Google Cloud) gestionan data centers gigantes y te alquilan recursos por segundos o minutos a través de Internet.
* **Concepto clave:** Pasamos de **CapEx** (Gasto de Capital - comprar hardware) a **OpEx** (Gasto Operativo - pagar por uso).

---

## 2. Modelos de Servicio en la Nube

Dependiendo de cuánto gestionas tú y cuánto gestiona el proveedor, existen tres modelos principales:

| Modelo | Significado | Analogía (Pizza) 🍕 | Ejemplo Real |
| :--- | :--- | :--- | :--- |
| **IaaS** (Infrastructure as a Service) | Te alquilan el hardware virtual (CPU, RAM, Disco). Tú instalas el SO y el software. | Te dan la cocina y el horno. Tú traes la masa y los ingredientes. | AWS EC2, Google Compute Engine. |
| **PaaS** (Platform as a Service) | Te dan el entorno listo para ejecutar código. No te preocupas del SO ni parches. | Te traen la pizza a casa. Tú solo pones la mesa y te la comes. | Heroku, Google App Engine. |
| **SaaS** (Software as a Service) | Usas el software directamente. No ves nada de lo que hay detrás. | Vas a un restaurante. Te sientas y comes. | Gmail, Dropbox, Salesforce. |

---

## 3. Concepto DevOps Clave: Pets vs Cattle 🐮

Esta es la filosofía más importante sobre infraestructura en DevOps.

### 🐶 Pets (Mascotas) - Modelo Antiguo
Tratamos a los servidores como mascotas.
* Tienen nombres únicos (ej: *Gandalf*, *Zeus*, *WebServer01*).
* Si se enferman (fallan), los "cuidamos": entramos por SSH, reiniciamos servicios, investigamos logs.
* Es un proceso manual y doloroso.

### 🐮 Cattle (Ganado) - Modelo DevOps
Tratamos a los servidores como ganado.
* Tienen números, no nombres (ej: *s-ad45-001*, *s-ad45-002*).
* Son idénticos entre sí (creados desde una plantilla/imagen).
* **Si se enferman, no los curamos.** Los eliminamos y creamos uno nuevo automáticamente en segundos.
* Esto permite la **Inmutabilidad** y la **Escalabilidad**.

---

## 4. Tipos de Nube

* **Pública:** Recursos compartidos en proveedores públicos (AWS, Azure). Barata y elástica.
* **Privada:** Infraestructura dedicada solo para una empresa (On-premise virtualizado). Más segura, pero más cara de mantener.
* **Híbrida:** Una mezcla. Ej: Datos sensibles en servidores privados, pero la web pública en AWS para aguantar picos de tráfico.