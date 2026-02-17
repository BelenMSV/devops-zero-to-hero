# ⚙️ Gestión de Servicios (Systemd)

> "Instalar un programa no significa que esté funcionando. Tienes que encenderlo."

En Linux moderno, el encargado de arrancar, parar y gestionar los programas en segundo plano (demonios) es **Systemd**. La herramienta para controlarlo es `systemctl`.

---

## 1. El gran conflicto de nombres
Aunque el comando es el mismo para todos, los paquetes a veces tienen nombres distintos según la familia.

| Familia | Distro | Nombre del Servicio Web |
| :--- | :--- | :--- |
| **RedHat** | CentOS / Fedora | **`httpd`** |
| **Debian** | Ubuntu / Kali | **`apache2`** |

> *En los ejemplos usaremos `httpd`, pero si estás en Ubuntu cámbialo por `apache2`.*

---

## 2. Ciclo de Vida (Encender y Apagar)
Comandos para controlar el estado **actual** del servicio (sin reiniciar el PC).

| Acción | Comando | Descripción |
| :--- | :--- | :--- |
| **Iniciar** | `sudo systemctl start httpd` | Enciende el servicio ahora mismo. |
| **Parar** | `sudo systemctl stop httpd` | Apaga el servicio inmediatamente. |
| **Reiniciar** | `sudo systemctl restart httpd` | Apaga y vuelve a encender (ideal tras cambios de config). |
| **Recargar** | `sudo systemctl reload httpd` | Lee la configuración de nuevo **sin cortar** el servicio (más seguro). |
| **Estado** | `sudo systemctl status httpd` | **Vital:** Te dice si está `active (running)` o si falló (`failed`). |

---

## 3. Persistencia (Arranque Automático)
Una cosa es encenderlo hoy, y otra que se encienda solo mañana al reiniciar el servidor.

| Acción | Comando | Descripción |
| :--- | :--- | :--- |
| **Habilitar** | `sudo systemctl enable httpd` | Configura el servicio para que **inicie automáticamente** al prender el PC. |
| **Deshabilitar** | `sudo systemctl disable httpd` | Quita el arranque automático (tendrás que iniciarlo a mano). |

---

## 4. Verificaciones (`is-active`)
Comandos rápidos para scripts o comprobaciones.

```bash
# ¿Está corriendo ahora mismo? (devuelve 'active' o 'inactive')
systemctl is-active httpd

# ¿Se va a iniciar solo al reiniciar? (devuelve 'enabled' o 'disabled')
systemctl is-enabled httpd
```

## 💡 Flujo de Trabajo Típico
Cada vez que instales un servicio (Web, Base de datos, SSH), harás siempre estos 3 pasos para asegurar que funciona hoy y funcionará mañana:

1.  **`start`**: Lo enciendes para usarlo ya.
2.  **`enable`**: Lo configuras para que arranque solo si reinicias el servidor.
3.  **`status`**: Verificas que todo esté en verde (active).

```bash
# El "Combo" del SysAdmin (ejemplo con httpd):
sudo systemctl start httpd
sudo systemctl enable httpd
sudo systemctl status httpd
```