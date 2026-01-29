# 📝 Editor VIM (Vi IMproved)

> "Si te pierdes en una isla desierta con un servidor Linux, VIM será tu única herramienta para sobrevivir."

VIM es un editor de texto en terminal. A diferencia del Notepad o Word, no usas el ratón. Todo se hace con el teclado.



## 🧠 El Concepto Clave: Los 3 Modos
VIM funciona con "modos". Si intentas escribir sin estar en el modo correcto, romperás cosas. Entender esto es vital.

| Modo | Cómo entrar | Qué hace | Cómo salir |
| :--- | :--- | :--- | :--- |
| **Command Mode** | (Por defecto al abrir) | Te mueves, copias, pegas o borras líneas. No puedes escribir texto. | Pulsa `i`, `a`, u `o` para ir a Insert. |
| **Insert Mode** | Pulsa `i` | **Aquí sí puedes escribir** normal (como en Notepad). | Pulsa `Esc` para volver a Command. |
| **Extended Mode** | Pulsa `:` (desde Command) | Para guardar (`w`), salir (`q`) o buscar. | Pulsa `Enter` tras el comando. |

---

## 🚀 Flujo de Trabajo Básico (Survival Guide)
Si solo aprendes una cosa, que sea esto. Cómo entrar, editar y salir vivo.

1.  **Abrir/Crear archivo:** `vim archivo.txt`
2.  **Entrar a editar:** Pulsa `i` (verás `-- INSERT --` abajo).
3.  **Escribir:** Escribe tu contenido.
4.  **Salir de edición:** Pulsa la tecla `Esc` (desaparece `-- INSERT --`).
5.  **Guardar y Salir:** Escribe `:wq` y pulsa `Enter`.

---

## ⌨️ Chuleta de Comandos (Cheatsheet)
Estos comandos funcionan en **Command Mode** (cuando NO estás escribiendo texto).

### 🚶 Movimiento
| Tecla | Acción |
| :--- | :--- |
| `gg` | Ir a la primera línea del archivo. |
| `G` | Ir a la última línea del archivo. |
| `w` | Saltar a la siguiente palabra (Word). |
| `b` | Saltar a la palabra anterior (Back). |
| `:20` | Ir a la línea número 20 (Extended Mode). |

### 🛠️ Edición Rápida
| Tecla | Acción |
| :--- | :--- |
| `yy` | Copiar la línea actual (Yank). |
| `p` | Pegar la línea copiada (Paste). |
| `dd` | Cortar/Borrar la línea actual. |
| `u` | Deshacer el último cambio (Undo). |
| `Ctrl + r` | Rehacer (Redo). |

### 💾 Guardar y Salir (Extended Mode)
Recuerda pulsar `Esc` antes de escribir los dos puntos `:`.

| Comando | Acción |
| :--- | :--- |
| `:w` | Guardar (Write). |
| `:q` | Salir (Quit). |
| `:wq` | Guardar y Salir. |
| `:q!` | **Salir SIN guardar** (Forzado). Úsalo si te equivocas. |
| `:set nu` | Mostrar números de línea (útil para programar). |

---

## 📥 Instalación
Aunque suele venir instalado, a veces necesitas instalar la versión completa.

```bash
# En Ubuntu/Debian
sudo apt-get install vim

# En CentOS/RedHat
sudo yum install vim
```