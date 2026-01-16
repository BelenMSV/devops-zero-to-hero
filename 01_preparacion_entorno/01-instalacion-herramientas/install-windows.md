# 🛠️ Guía de Instalación para Windows

En este curso NO descargaremos instaladores `.exe` manualmente. Usaremos **Chocolatey**, un gestor de paquetes profesional para Windows.

## 1. Instalar Chocolatey
1.  Abre **PowerShell** como Administrador.
2.  Ejecuta este comando para verificar la política de ejecución:
    ```powershell
    Get-ExecutionPolicy
    ```
    *(Si devuelve `Restricted`, ejecuta `Set-ExecutionPolicy AllSigned` y acepta con S).*
3.  Copia y pega este bloque para instalar Chocolatey (es el comando oficial obtenido de chocolatey.org):
    ```powershell
    Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
    ```
4.  Una vez termine, **cierra y vuelve a abrir PowerShell** para que reconozca el comando `choco`.

> **⚠️ Troubleshooting:** Si la instalación se queda congelada, desactiva tu antivirus (ej: McAfee) durante 15 minutos.

## 2. Instalar el Pack de Herramientas
Copia todo este bloque y pégalo en PowerShell (Admin). Instalará todo lo necesario de una vez.

```powershell
# Virtualización y Entorno
choco install virtualbox -y
choco install vagrant -y
choco install git -y

# Lenguajes y Build Tools
choco install corretto17jdk -y
choco install maven -y

# Cloud y Editor
choco install awscli -y
choco install vscode -y
```
## 3. Verificación Final

Para asegurarte de que todo está listo para trabajar, cierra la terminal, abre una nueva (puede ser PowerShell o Git Bash) y ejecuta estos comandos:

```powershell
# Verificar versiones (no deben dar error)
vagrant --version
java -version
mvn -version
git --version
aws --version
```
Si todos devuelven un número de versión, ¡estás listo!