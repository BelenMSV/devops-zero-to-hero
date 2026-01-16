# 🍎 Guía de Instalación para macOS

Usaremos **Homebrew**, el estándar de la industria para instalar software en Mac.

## 1. Instalar Homebrew
1.  Abre la Terminal.
2.  Ve a [brew.sh](https://brew.sh) y copia el comando de instalación.
3.  Pégalo en tu terminal y sigue las instrucciones (te pedirá contraseña).
4.  **Importante:** Si al terminar la instalación te pide ejecutar comandos `echo` y `eval` para configurar el PATH, hazlo inmediatamente.

## 2. Instalar el Pack de Herramientas
Ejecuta estos comandos en tu terminal.

### Para Macs con chip Intel:
```bash
brew install --cask virtualbox
brew install --cask vagrant
brew install git awscli openjdk@17 maven
brew install --cask visual-studio-code
```
### Para Macs con chip Apple Silicon (M1, M2, M3):
**⚠️Nota: VirtualBox no funciona bien en arquitectura ARM.Usaremos VMware.**

1.  Instala VMware Fusion (versión Player gratuita para uso personal) descargándolo de la web de VMware.

2.  Resto de herramientas (vía Brew):
```bash
brew install --cask vagrant
brew install git awscli openjdk@17 maven
brew install --cask visual-studio-code
```
## 3. Verificación Final
Cierra la terminal, abre una nueva y comprueba que todo responde correctamente:

```bash
# Verificar versiones (no deben dar error)
vagrant --version
java -version
mvn -version
git --version
aws --version
```
Si todo devuelve una versión, ¡estás listo!