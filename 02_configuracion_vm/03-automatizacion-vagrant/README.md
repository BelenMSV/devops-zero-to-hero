# 🤖 Automatización con Vagrant

> "Vagrant es a las máquinas virtuales lo que un director de orquesta es a los músicos: coordina, levanta y gestiona todo con un movimiento de batuta (o comando)."

En esta sección aprenderemos a usar **Vagrant**, una herramienta de *Infraestructura como Código* (IaC) que nos permite crear y configurar entornos de desarrollo ligeros, reproducibles y portátiles.

## 🚀 ¿Por qué Vagrant?
Vimos que la creación manual es lenta y propensa a errores humanos. Vagrant soluciona esto usando:
1.  **Boxes:** Imágenes de SO pre-fabricadas (como un molde). No hay que instalar el SO paso a paso.
2.  **Vagrantfile:** Un archivo de texto que describe tu máquina (RAM, CPU, Red).
3.  **Automatización:** Con un solo comando (`vagrant up`), Vagrant descarga la imagen, crea la VM en VirtualBox y configura la red por ti.

## ⚡ Chuleta de Comandos (Cheat Sheet)
Estos son los comandos que usarás el 90% del tiempo. Ejecútalos siempre **dentro de la carpeta** donde está tu `Vagrantfile`.

| Comando | Acción |
| :--- | :--- |
| `vagrant init <box_name>` | Crea un nuevo archivo `Vagrantfile` en la carpeta actual. |
| `vagrant up` | Crea y arranca la máquina virtual (descarga la box si no existe). |
| `vagrant ssh` | Entra a la máquina virtual (loguea automáticamente). |
| `vagrant halt` | Apaga la máquina virtual (apagado ordenado). |
| `vagrant destroy` | **Borra** la máquina virtual y libera el espacio en disco. |
| `vagrant status` | Te dice si la VM está corriendo, apagada o no creada. |
| `vagrant reload` | Reinicia la VM (útil si cambiaste algo en el Vagrantfile). |
| `vagrant global-status` | Muestra TODAS las VMs Vagrant que tienes en tu PC. |

## 🛡️ Troubleshooting (Problemas Comunes)
Si al hacer `vagrant up` recibes errores extraños (ej: `VBoxHardening`, `E_FAIL`, pantallas azules):

1.  **Antivirus/Firewall:** Es la causa nº 1. Desactívalos temporalmente.
2.  **VPN:** Si estás conectado a una VPN corporativa, desconéctala (bloquean la red interna de Vagrant).
3.  **Versión de VirtualBox:** Asegúrate de tener una versión compatible (la 7.x suele ir bien, pero a veces versiones muy nuevas dan guerra con Vagrant antiguos).

👉 **¡Manos a la obra!** Ve a la [Guía de Laboratorio](./lab-vagrant.md) para crear tus máquinas.