# 🧟 Gestión de Procesos (`top`, `ps`, `kill`)

> "Si un programa se congela y no responde, no reinicies el servidor. Encuentra el proceso y mátalo."

En Linux, todo programa en ejecución es un "proceso" con un número identificador único llamado **PID** (Process ID).

## 1. Monitorizar Procesos

| Comando | Descripción |
| :--- | :--- |
| **`top`** | Muestra los procesos en **tiempo real**. Es como el "Administrador de Tareas" de Windows. Pulsa `q` para salir. |
| **`ps`** | Muestra los procesos activos en tu terminal actual. |
| **`pmap`** | Muestra el mapa de memoria de un proceso específico. |

## 2. Buscar un proceso específico
Si quieres matar un proceso, primero necesitas saber su **PID**. Usamos `ps` combinado con `grep`.

```bash
# Busca todos los procesos y filtra los que se llamen 'telnet'
ps aux | grep 'telnet'
```

## 3. Matar Procesos (`kill`)
Cuando un servicio no responde a `systemctl stop`, usamos la fuerza bruta.

| Comando | Descripción |
| :--- | :--- |
| **`kill 1234`** | Pide amablemente al proceso con PID `1234` que se cierre (usa una señal estándar). |
| **`kill -9 1234`** | Fuerza el cierre inmediato del proceso `1234` (asesinato directo, sin contemplaciones). |
| **`killall firefox`** | Cierra **todos** los procesos que tengan ese nombre exacto. |
| **`pkill fire`** | Cierra los procesos cuyo nombre **contenga** esa palabra o patrón. |

## 4. Procesos en Segundo Plano (Background / Foreground)
Si ejecutas un comando que tarda mucho, puedes pausarlo (usando `Ctrl + Z`) y mandarlo al fondo para seguir usando tu terminal.

* **`bg`**: (Background) Reanuda un proceso pausado y lo deja corriendo en el fondo (background).
* **`fg`**: (Foreground) Trae el trabajo o proceso más reciente del fondo de vuelta a tu terminal principal.
* **`fg n`**: Trae el trabajo número 'n' al frente.