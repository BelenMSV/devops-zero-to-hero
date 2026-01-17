# 📚 Fundamentos de Virtualización

La virtualización permite que un solo ordenador físico haga el trabajo de múltiples ordenadores, ejecutando varios Sistemas Operativos (SO) en paralelo.

## 🆚 Antes vs. Ahora

| Modelo Tradicional (Bare Metal) | Virtualización |
| :--- | :--- |
| 1 Servidor = 1 Servicio (Aislamiento) | 1 Servidor Físico = Múltiples VMs |
| Recursos infrautilizados (se compra RAM de sobra "por si acaso") | Recursos compartidos y optimizados |
| Alto coste (CAPEX/OPEX) | Coste reducido y despliegue rápido |

## 🧠 Conceptos Clave
Es vital dominar esta terminología:

* **Host OS:** El sistema operativo de tu máquina física (donde estás leyendo esto).
* **Guest OS:** El sistema operativo que instalas *dentro* de la máquina virtual.
* **Hypervisor:** El software que hace posible la magia. Se sienta entre el hardware y las VMs.
* **Snapshot:** Una "foto" del estado de la VM que sirve como copia de seguridad instantánea.

## 🏗️ Tipos de Hypervisor


### Tipo 1: Bare Metal (Nativo)
Se instala directamente sobre el hardware, sin sistema operativo intermedio.
* **Uso:** Centros de datos, producción, servidores empresariales.
* **Ejemplos:** VMware ESXi, Microsoft Hyper-V (en modo servidor), Xen.
* **Ventaja:** Máximo rendimiento y acceso directo al hardware.

### Tipo 2: Hosted (Alojado)
Se instala como un programa más sobre tu sistema operativo (Windows/Mac/Linux).
* **Uso:** **Este curso**, laboratorios personales, pruebas.
* **Ejemplos:** **Oracle VirtualBox**, VMware Workstation/Fusion.
* **Funcionamiento:** Hardware -> Host OS -> Hypervisor -> VMs.

> **Nota:** En este curso usaremos un Hypervisor Tipo 2 (VirtualBox o VMware Fusion en Mac Silicon) para simular un entorno complejo sin gastar dinero.