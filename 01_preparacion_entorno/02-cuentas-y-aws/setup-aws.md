# ☁️ Configuración de AWS Free Tier

Sigue estos pasos estrictamente para asegurar tu cuenta y evitar cobros inesperados.

## 1. Crear Cuenta y Usuario Root
1.  Regístrate en [aws.amazon.com](https://aws.amazon.com). Necesitarás tarjeta bancaria.
    > **Nota internacional:** AWS realizará un cargo temporal de verificación (aprox. $1 USD o 1€) que será devuelto en unos días.
2.  Selecciona el plan **Basic Support (Free)**.

## 2. Configurar MFA (Multi-Factor Authentication) 🔐
El usuario Root es crítico. Protégelo.
1.  Entra en la consola de AWS con tu email (Root User).
2.  Ve al servicio **IAM** (Identity and Access Management).
3.  Verás una alerta de seguridad. Haz clic en **Add MFA**.
4.  Usa **Google Authenticator** en tu móvil para escanear el QR y vincularlo.

## 3. Crear tu Usuario de Trabajo (IAM Admin) 👤
**Nunca trabajes logueado como Root.**
1.  En IAM -> **Users** -> **Create User**.
2.  Nombre: `admin-devops` (o tu nombre).
3.  Dale acceso a la **Management Console**.
4.  Permisos: Selecciona "Attach policies directly" -> **AdministratorAccess**.
5.  Crea el usuario y **guarda el CSV con la contraseña**.

> **Tarea:** Cierra sesión del Root y entra con tu nuevo usuario IAM. A partir de ahora, usa SIEMPRE este usuario.

## 4. Alarma de Facturación (Billing Alarm) 💸
Esta configuración es **Global**. No importa tu país de residencia, sigue estos pasos exactos:

1.  **Región Obligatoria:** Asegúrate de estar en **N. Virginia (us-east-1)** (selecciónalo arriba a la derecha).
    > *Importante:* Los datos de facturación de AWS solo son visibles en esta región, aunque vivas en Europa o Latam.
2.  Ve a **Billing Preferences** y activa "Receive Billing Alerts".
3.  Ve a **CloudWatch** -> **Alarms** -> **Create Alarm**.
4.  Métrica: `Billing` -> `Total Estimated Charge` -> `USD`.
    > *Recomendación:* Mantén la alarma en **USD** aunque tu moneda sea el Euro. Los límites gratuitos de AWS se calculan en dólares.
5.  Condición: Mayor que **$5 USD**.
6.  Configura el envío de email y **confirma la suscripción en tu correo**.

## 5. Certificado SSL (Opcional) 🔒
Si compraste un dominio (ej: `.xyz`), puedes pedir un certificado público gratuito en **AWS Certificate Manager (ACM)**:
1.  Solicita un certificado público (`*.tudominio.xyz`).
2.  Elige validación por DNS.
3.  Crea el registro CNAME que te da AWS en tu proveedor de dominio (GoDaddy/Namecheap).