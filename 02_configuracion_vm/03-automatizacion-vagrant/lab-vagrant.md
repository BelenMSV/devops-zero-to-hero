# 🧪 Laboratorio: Despliegue Automático con Vagrant

Vamos a crear la infraestructura definitiva para el curso de Linux: un servidor **CentOS** y un servidor **Ubuntu**.



## 1. Estructura de Directorios
El orden es vital. No tires todos los archivos en el Escritorio. Vamos a crear una estructura limpia.
* Abre tu terminal (Git Bash o Terminal).
* Ejecuta estos comandos para crear las carpetas:

```bash
# 1. Crear carpeta principal (puedes hacerlo en C:, D: o Desktop)
mkdir -p ~/vagrant-vms

# 2. Entrar en ella
cd ~/vagrant-vms

# 3. Crear subcarpetas para cada máquina
mkdir centos
mkdir ubuntu

# 4. Verificar estructura
ls -R
# Deberías ver: ./centos y ./ubuntu
```

---


## 2. Máquina A: CentOS Stream 9

Usaremos una "Box" (imagen) específica llamada eurolinux-vagrant/centos-stream-9.

Entra en la carpeta:

1.  Entra en la carpeta:
    ```bash
    cd ~/vagrant-vms/centos
    ```
2.  Inicializa el entorno (esto crea el archivo `Vagrantfile`):
    ```bash
    vagrant init eurolinux-vagrant/centos-stream-9
    ```
3.  Arranca la máquina (esto descargará la imagen de internet, ten paciencia):
    ```bash
    vagrant up
    ```
4.  Una vez termine, entra en ella:
    ```bash
    vagrant ssh
    ```
    *¡Felicidades! Estás dentro de tu servidor CentOS. Fíjate cómo ha cambiado el prompt de tu terminal.*
5.  Sal de la máquina (volver a tu PC):
    ```bash
    exit
    ```

---

## 3. Máquina B: Ubuntu 22.04 LTS
Ahora repetiremos el proceso para Ubuntu en su propia carpeta.

1.  Sube un nivel y entra en la carpeta de ubuntu:
    ```bash
    cd ../ubuntu
    # O usa la ruta completa: cd ~/vagrant-vms/ubuntu
    ```
2.  Inicializa con la box oficial de Ubuntu Jammy:
    ```bash
    vagrant init ubuntu/jammy64
    ```
3.  Arranca la máquina:
    ```bash
    vagrant up
    ```
4.  Verifica que funciona entrando:
    ```bash
    vagrant ssh
    ```
5.  Sal de la máquina:
    ```bash
    exit
    ```

---

## 4. Gestión del Laboratorio
Ahora tienes dos máquinas virtuales corriendo en segundo plano.

### ¿Cómo las controlo?
Desde cualquier lugar de tu terminal, puedes ver qué tienes encendido:

```bash
vagrant global-status
```

*Verás una lista con IDs, nombres, estado (running/poweroff) y la ruta de la carpeta.*

### Limpieza (Importante)
Cuando termines de estudiar por hoy, no dejes las máquinas consumiendo RAM.
1.  Ve a la carpeta de la máquina (ej: `cd ~/vagrant-vms/centos`).
2.  Apágala:
    ```bash
    vagrant halt
    ```
    *(Haz lo mismo con la de Ubuntu)*.

> **Nota:** Si en el futuro rompes una máquina haciendo pruebas, no sufras. Simplemente ejecuta `vagrant destroy` (para borrarla) y `vagrant up` (para crear una nueva idéntica en minutos). ¡Esa es la magia de Vagrant!