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