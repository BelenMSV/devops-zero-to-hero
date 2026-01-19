# 🟠 Instalación Manual: Ubuntu Server 22.04

La instalación de Ubuntu es diferente a CentOS. Aquí usaremos la versión LTS (Long Term Support).

## 1. Configuración de Hardware
1.  **Nueva VM:** Nombre `ubuntuvm`. Tipo: Linux, Versión: **Ubuntu (64-bit)**.
2.  **RAM:** 2048 MB (2 GB).
3.  **CPU:** 2 CPUs.
4.  **Disco:** VDI -> Dinámico -> **25 GB** (Default).

## 2. Configuración Previa
Igual que en CentOS, ve a **Configuración**:
1.  **Storage:** Carga la ISO `ubuntu-22.04-live-server-amd64.iso`.
2.  **Network:**
    * Adaptador 1: NAT.
    * Adaptador 2: **Adaptador Puente (Bridged)** conectado a tu WiFi.

## 3. Proceso de Instalación
Inicia la VM. El asistente de Ubuntu es basado en texto.
> **Tip:** Usa las **Flechas** para moverte, **Espacio** para marcar [X] y **Enter** para confirmar.

1.  **Idioma:** English.
2.  **Keyboard:** Done.
3.  **Network Connections:** Verás dos IPs (una 10.0.x.x y otra 192.168.x.x). Esto confirma que el puente funciona. Done.
4.  **Storage:** Deja marcada la opción "Use an entire disk". Done -> Continue.
5.  **Profile Setup:**
    * Your name: `DevOps Student`
    * Server name: `ubuntuvm`
    * Username: `devops` (o tu nombre)
    * Password: Elige una contraseña.
6.  **SSH Setup (¡CRÍTICO!):** ⚠️
    * Cuando pregunte "Install OpenSSH server", marca la casilla con **Espacio** `[X]`.
    * Si no haces esto, no podrás conectarte remotamente.
7.  **Featured Server Snaps:** No marques nada. Done.

> **Al terminar:** Espera a "Install Complete!". Apaga la VM, **quita la ISO** y vuelve a encenderla.

## 4. Conexión SSH
1.  Loguéate en la VM con tu usuario `devops`.
2.  Obtén la IP: `ip addr show`.
3.  Desde tu terminal local (Git Bash):
    ```bash
    ssh devops@192.168.1.X
    ```