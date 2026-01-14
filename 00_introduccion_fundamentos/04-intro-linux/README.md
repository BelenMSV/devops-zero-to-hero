# 🐧 Introducción a Linux: El Sistema Operativo de la Nube

En el tema anterior aprendimos que *"La Nube es el ordenador de otra persona"*.
Pues bien, **ese ordenador, casi con total seguridad, ejecuta Linux**.

Este tema es el cimiento de todo lo que aprenderás después:
* **Docker** utiliza el Kernel de Linux para funcionar.
* **AWS/Azure** se gestionan mejor desde una terminal Linux.
* **Git** nació para crear Linux.

---

## 1. ¿Por qué Linux es el Rey en DevOps?

Mientras que Windows y macOS se diseñaron para que el usuario final haga clic en iconos bonitos, Linux domina el mundo de los servidores (el 90% de la nube pública corre en Linux) por tres pilares:

1.  **Open Source:** Es gratuito y transparente. Si algo falla, puedes ver el código para saber por qué.
2.  **Estabilidad:** Un servidor Linux puede estar años encendido sin reiniciarse.
3.  **Automatización (La clave):** Linux está pensado para ser controlado por texto. Esto permite crear "recetas" (scripts) para que las tareas se hagan solas.

---

## 2. Arquitectura: El coche por partes

Para entender cómo funciona, no necesitas ser mecánico, pero sí distinguir las partes principales:

### Arquitectura Básica
Para entender Linux, imagina un coche:

```text
+---------------------+
|   👤   USUARIO      |  <-- Tú y tus Aplicaciones
+----------+----------+
           |
           v
+----------+----------+
|   🐚    SHELL       |  <-- El Intérprete (Volante)
|  (Bash, Zsh, etc.)  |      Traduce tus órdenes
+----------+----------+
           |
           v
+----------+----------+
|   ⚙️    KERNEL      |  <-- El Núcleo (Motor)
| (Gestión Recursos)  |      Habla con el hierro
+----------+----------+
           |
           v
+----------+----------+
|   🖥️   HARDWARE     |  <-- CPU, RAM, Disco
+---------------------+
```

* **⚙️ Kernel (El Motor):** Es el corazón del sistema. Es el único que habla directamente con el hardware. Gestiona la memoria y la CPU.
* **🐚 Shell (El Volante):** Es la capa externa. Tú no hablas con el Kernel directamente; hablas con la Shell (generalmente un programa llamado `Bash`). Tú escribes un comando, la Shell lo traduce y el Kernel lo ejecuta.
* **👤 Apps (El Aire Acondicionado):** Los programas que corren encima (Servidor Web, Base de Datos, etc.).

---

## 3. El Sistema de Archivos: Un Árbol Invertido

En Windows estamos acostumbrados a las unidades (`C:\`, `D:\`). En Linux **NO existen las unidades**. Todo parte de una única raíz llamada **Root (`/`)**.

### Jerarquía Básica (Lo que debes saber)
Si te conectas a un servidor en la nube, verás estas carpetas. Es vital saber para qué sirven:

| Ruta | Significado | Analogía Windows |
| :--- | :--- | :--- |
| **`/`** | **Root**. El inicio absoluto. | `Este Equipo` |
| **`/home`** | Donde viven los usuarios. (ej: `/home/tu-usuario`). | `C:\Users` |
| **`/bin`** | **Binarios**. Aquí están los programas (los comandos `ls`, `cp`...). | `C:\Windows\System32` |
| **`/etc`** | **Configuración**. Aquí se guarda CÓMO funcionan los programas. | El Registro de Windows (pero legible). |
| **`/var`** | **Variable**. Archivos que cambian de tamaño, como los **Logs**. | `C:\ProgramData` |
| **`/tmp`** | **Temporal**. Se borra automáticamente al reiniciar. | `Temp` |

> **💡 Nota DevOps:** Cuando configures un servidor web, pasarás mucho tiempo en `/etc` (configurando) y en `/var/log` (mirando por qué no funciona).

---

## 4. Permisos: La Seguridad del Castillo

Linux es multiusuario desde su nacimiento. Para que un usuario no rompa lo que hizo otro, existe un sistema estricto de permisos basado en tres acciones:

1.  **Read (r):** Ver el archivo.
2.  **Write (w):** Modificar o borrar el archivo.
3.  **Execute (x):** Ejecutarlo (si es un programa).

### El concepto de "Root"
Hay un usuario especial llamado **`root`** (el superusuario). Es el "Dios" del sistema.
* En Windows, el Administrador te pregunta "¿Estás seguro?".
* En Linux, `root` no pregunta. Si le dices que borre todo el sistema, lo borrará sin rechistar. Por eso, en DevOps, trabajamos con usuarios normales y solo usamos poderes de root cuando es estrictamente necesario (comando `sudo`).

---

## 5. Conclusión: CLI vs GUI

¿Por qué los ingenieros DevOps aman la **Pantalla Negra** (CLI - Command Line Interface)?

* **Porque es universal:** Todos los servidores Linux se manejan igual, sin importar si estás en un ordenador de 30€ o en un superordenador de la NASA.
* **Porque es automatizable:** Lo que escribes en la terminal se puede guardar en un archivo de texto. Si guardas esos comandos, acabas de crear tu primer script de automatización.