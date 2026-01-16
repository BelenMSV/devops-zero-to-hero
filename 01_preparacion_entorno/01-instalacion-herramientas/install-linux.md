# 🐧 Guía de Instalación para Linux

Elige los comandos correspondientes a tu distribución (familia RedHat o familia Debian/Ubuntu).

---

## Opción A: RHEL 9 / CentOS Stream / Rocky / AlmaLinux

Estos sistemas usan el gestor de paquetes `dnf` / `yum`.

```bash
# 1. Preparar VirtualBox (requiere compilación de módulos del kernel)
sudo yum update -y
sudo yum install patch gcc kernel-headers kernel-devel make perl wget -y
sudo reboot

# --- ⚠️ IMPORTANTE: Ejecuta lo siguiente DESPUÉS de reiniciar ---

# 2. Instalar VirtualBox 7.1
# Descargar repo oficial
sudo wget http://download.virtualbox.org/virtualbox/rpm/el/virtualbox.repo -P /etc/yum.repos.d
# Instalar
sudo yum install VirtualBox-7.1 -y

# 3. Instalar Vagrant
sudo dnf config-manager --add-repo=https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo
sudo dnf install vagrant -y

# 4. Herramientas de Desarrollo (Java 17, Maven, Git)
sudo dnf install git java-17-openjdk java-17-openjdk-devel maven-openjdk17 -y
```

## Opción B: Ubuntu 24.04 LTS (y derivados)
Estos sistemas usan el gestor de paquetes apt.

```bash
# 1. Instalar VirtualBox 7.1
sudo apt update
sudo apt install curl wget gnupg2 lsb-release -y

# Añadir claves GPG de Oracle
curl -fsSL https://www.virtualbox.org/download/oracle_vbox_2016.asc | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/vbox.gpg
curl -fsSL https://www.virtualbox.org/download/oracle_vbox.asc| sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/oracle_vbox.gpg

# Añadir repositorio oficial
echo "deb [arch=amd64] http://download.virtualbox.org/virtualbox/debian $(lsb_release -sc) contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list

# Actualizar e instalar
sudo apt update
sudo apt install -y linux-headers-$(uname -r) dkms
sudo apt install virtualbox-7.1 -y

# Añadir usuario al grupo vboxusers (necesario para USBs y permisos)
sudo usermod -aG vboxusers $USER

# 2. Instalar Vagrant
wget -O- https://apt.releases.hashicorp.com/gpg| gpg --dearmor | sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install vagrant -y

# 3. Herramientas de Desarrollo
sudo apt install git openjdk-17-jdk maven -y
```
## Verificación Final
Cierra tu terminal, abre una nueva y comprueba las versiones:

```bash
# Verificar versiones (ninguno debe dar error "command not found")
vboxmanage --version
vagrant --version
java -version
mvn -version
git --version
```