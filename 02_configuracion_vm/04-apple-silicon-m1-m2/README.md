# 🍎 Guía Especial: Mac con Apple Silicon (M1/M2/M3)

> **¡ATENCIÓN!** Esta guía es **EXCLUSIVA** para usuarios de Mac con chips ARM (M1, M2, M3).

La arquitectura ARM no es compatible con VirtualBox. Usaremos **VMware Fusion** y **Vagrant** con un plugin especial.

---

## 🛠️ Fase 1: Instalación de Herramientas
Sigue estos pasos en orden estricto desde tu terminal.

### 1. Instalar Rosetta 2
Necesario para la traducción de binarios.
```bash
/usr/sbin/softwareupdate --install-rosetta --agree-to-license
```

### 2. Instalar Vagrant
```bash
brew install vagrant
```
### 3. Instalar VMware Fusion (Broadcom)
1.  Crea una cuenta en el [Portal de Soporte de Broadcom](https://support.broadcom.com).
2.  Descarga **VMware Fusion 13 Pro** (o superior).
3.  Durante la instalación, selecciona la licencia **"Personal Use"** (gratuita).

### 4. Permisos de Accesibilidad (Crítico)
1.  Abre **Ajustes del Sistema** -> **Privacidad y Seguridad** -> **Accesibilidad**.
2.  Busca **VMware Fusion** y **ACTIVA** el interruptor.

### 5. Plugins de Conexión
Ejecuta estos dos comandos para que Vagrant pueda hablar con VMware:
```bash
# 1. Instalar la utilidad de sistema (Utility)
brew install --cask vagrant-vmware-utility

# 2. Instalar el plugin de Vagrant
vagrant plugin install vagrant-vmware-desktop
```
---

## 🏗️ Fase 2: Configuración de las Máquinas

### A. Máquina Ubuntu (ARM)
Crea la carpeta `~/Desktop/vms/ubuntu` y dentro un archivo `Vagrantfile` con este contenido exacto:

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "spox/ubuntu-arm"
  config.vm.box_version = "1.0.0"
  config.vm.network "private_network", ip: "192.168.56.11"
  
  config.vm.provider "vmware_desktop" do |vmware|
    vmware.gui = true
    vmware.allowlist_verified = true
  end
end
```
### B. Máquina CentOS (ARM)
Crea la carpeta ~/Desktop/vms/centos y dentro un archivo Vagrantfile con este contenido:
```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "bandit145/centos_stream9_arm"
  config.vm.network "private_network", ip: "192.168.56.12"
  
  config.vm.provider "vmware_desktop" do |vmware|
    vmware.gui = true
    vmware.allowlist_verified = true
  end
end
```
> **Nota:** Para **arrancar** las máquinas, **usa vagrant up dentro de cada carpeta**.