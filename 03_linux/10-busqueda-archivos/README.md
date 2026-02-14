# 🔍 Búsqueda de Archivos y Texto

> "En Linux no usamos el ratón para buscar carpetas. Usamos comandos de precisión."

Herramientas para encontrar archivos perdidos (`find`, `locate`) o textos específicos dentro de ellos (`grep`).

## 1. Buscar Texto dentro de Archivos (`grep`)
El comando `grep` actúa como un filtro. Busca patrones dentro del contenido de los archivos.

| Comando | Descripción |
| :--- | :--- |
| `grep "error" archivo.log` | Busca la palabra "error" dentro de `archivo.log`. |
| `grep -r "config" /etc/` | Busca "config" **recursivamente** dentro de toda la carpeta `/etc/`. |
| `grep -i "texto" archivo` | Busca sin importar mayúsculas/minúsculas (ignore case). |

---

## 2. Buscar Archivos por Nombre (`locate`)
Es la forma más rápida de encontrar un archivo, pero depende de una base de datos interna.

```bash
# Encontrar todas las rutas que contengan el nombre del archivo
locate mi_archivo.txt
```

> *Nota: Si no encuentra algo reciente, ejecuta `sudo updatedb` para actualizar su base de datos.*

---

## 3. Búsqueda Avanzada (`find`)
Es el buscador más potente. Busca en tiempo real recorriendo el disco línea por línea.

**Sintaxis:** `find [DONDE] [OPCIONES] [QUE_BUSCAR]`

### Ejemplos Prácticos
| Objetivo | Comando | Explicación |
| :--- | :--- | :--- |
| **Por Nombre** | `find /home -name "index*"` | Busca en `/home` archivos que empiecen por "index". |
| **Por Tamaño** | `find /home -size +100M` | Busca en `/home` archivos que pesen **más** de 100MB. |
| **Por Tipo** | `find . -type d` | Busca solo directorios (carpetas) en la ruta actual. |
| **Por Usuario** | `find /var -user juan` | Busca archivos que pertenezcan al usuario 'juan'. |

```bash
# Ejemplo: Buscar archivos de +10000k (10MB) en /home
find /home -size +10000k
```