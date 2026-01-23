# 🖥️ Módulo 2: Virtualización y Configuración del Laboratorio

> "Antiguamente, montar un laboratorio costaba una fortuna en hardware. Hoy, puedes crear todo un centro de datos dentro de tu portátil."


En este módulo hemos pasado de la teoría a la práctica, construyendo la infraestructura que usaremos durante el resto del curso. Hemos aprendido a levantar servidores tanto "a mano" como "automáticamente".

## 🎯 Objetivos del Módulo
1.  Entender la diferencia entre **Hypervisor Tipo 1 y Tipo 2**.
2.  Aprender la terminología clave (Host, Guest, Snapshot).
3.  **Práctica Manual:** Crear una VM desde cero instalando la ISO (para entender las tripas).
4.  **Práctica Automática:** Usar **Vagrant** para desplegar infraestructura como código (IaC).

## 📜 La Regla de Oro de la Automatización
Regla crítica para DevOps:

> **"Si quieres automatizar algo, primero debes saber hacerlo manualmente."**

La automatización no es magia; es simplemente orquestar pasos que ya conoces. Por eso, en este curso primero sufriremos el proceso manual para luego disfrutar la automatización con Vagrant.

---

## 🗺️ Mapa del Módulo

| Tema | Descripción |
| :--- | :--- |
| **1. Teoría** | ¿Qué es un Hypervisor? Diferencias entre Tipo 1 (Bare Metal) y Tipo 2. <br> [📂 Ir a Fundamentos](./01-fundamentos-virtualizacion/README.md) |
| **2. Práctica Manual** | Creación de VMs paso a paso, particionado de disco y configuración de red. <br> [📂 Ir a Guía Manual](./02-creacion-manual-vms/README.md) |
| **3. Automatización (Vagrant)** | **El corazón del curso.** Cómo desplegar el laboratorio con un solo comando. <br> [📂 Ir a Guía Vagrant](./03-automatizacion-vagrant/README.md) |
| **4. Caso Especial (Apple M1/M2)** | Guía exclusiva para usuarios de Mac con chips ARM (VMware Fusion). <br> [📂 Ir a Guía Apple Silicon](./04-apple-silicon-m1-m2/README.md) |

---

## ✅ Checklist de Finalización

Antes de pasar al siguiente módulo (Linux), asegúrate de cumplir esto:

* [ ] Entiendes la diferencia entre **Host** (tu PC) y **Guest** (la VM).
* [ ] Has logrado arrancar una máquina virtual manualmente (VirtualBox).
* [ ] Has logrado arrancar el laboratorio con **Vagrant** (`vagrant up`).
* [ ] Sabes entrar a tus máquinas (`vagrant ssh`) y apagarlas correctamente (`vagrant halt`).

> **💡 Nota:** Si has completado la parte automática (Vagrant), ya puedes borrar las máquinas que creaste manualmente en el Tema 2 para liberar espacio.

---

## 🔜 Siguiente Paso: Linux
Con el laboratorio funcionando, estamos listos para ensuciarnos las manos en la terminal.