# 🐧 Instalación Manual: CentOS Stream 9

Sigue estos pasos rigurosamente para configurar tu primer servidor RedHat-based.

## 1. Configuración de Hardware (VirtualBox)
1.  **Nueva VM:** Nombre `centosvm`. Tipo: Linux, Versión: **Red Hat (64-bit)**.
2.  **RAM:** 2048 MB (2 GB).
3.  **CPU:** 2 CPUs.
4.  **Disco:** Crear disco virtual ahora -> VDI -> Reservado dinámicamente -> **20 GB**.

## 2. Configuración de Red y Almacenamiento
Antes de iniciar, ve a **Configuración (Settings)** de la VM:
1.  **Storage (Almacenamiento):**
    * En "Controller: IDE", selecciona el CD vacío.
    * Elige el archivo **`CentOS-Stream-9-xxx-boot.iso`** que descargaste.
2.  **Network (Red):**
    * **Adaptador 1:** Déjalo en **NAT** (por defecto).
    * **Adaptador 2:** Actívalo -> Conectado a: **Adaptador Puente (Bridged Adapter)**.
    * *Importante:* Selecciona tu tarjeta de red real (WiFi o Ethernet) en el desplegable.
3.  **System (Sistema):** En "Motherboard", cambia "Dispositivo apuntador" a **USB Tablet** (para que el ratón funcione fluido).

## 3. Proceso de Instalación
Inicia la VM (`Start`). Usa las flechas para seleccionar "Install CentOS Stream 9".

1.  **Idioma:** English (Recomendado para servidores).
2.  **Installation Destination:**
    * Haz clic en el icono del disco (20GB).
    * Selecciona "Automatic Partitioning" y pulsa **Done** dos veces.
3.  **Network & Host Name:**
    * Verifica que ambos adaptadores (eth0/eth1 o enp0s3/enp0s8) están "Connected".
    * Host Name: `centosvm` -> Apply.
4.  **Root Password:** Establece una contraseña segura (ej: `admin123`). Si es débil, pulsa Done dos veces.
5.  **Begin Installation:** Espera a que termine (10-15 min).

> **Al terminar:** NO pulses Reboot. Apaga la VM desde VirtualBox (Close -> Power off). Ve a Settings -> Storage y **retira la ISO** (Remove disk) para que no vuelva a iniciar la instalación.

## 4. Verificación
1.  Enciende la VM. Loguéate como `root` con tu contraseña.
2.  Comando clave: `ip addr show`.
3.  Busca la IP del segundo adaptador (ej: `192.168.1.X`).
4.  Desde tu PC real (Git Bash/Terminal), conéctate por SSH:
    ```bash
    ssh root@192.168.1.X
    # Acepta la huella digital (yes) y pon la contraseña.
    ```