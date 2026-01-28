# ⌨️ Comandos Básicos de Navegación

> "Antes de correr, hay que aprender a caminar. En Linux, caminar es saber dónde estás y cómo moverte."

En esta sección practicaremos los comandos fundamentales para interactuar con el sistema de archivos.

> **Nota sobre el prompt**: En los ejemplos verás `[vagrant@localhost ~]$.` Esto es porque estamos usando la máquina virtual de Vagrant. En un entorno real o en tu propio PC, aquí aparecería tu nombre de usuario (ej: `[juan@mi-pc ~]$`).


## 📍 ¿Dónde estoy? (`pwd`)
En una interfaz gráfica siempre ves la carpeta abierta. En la terminal, necesitas preguntar.
* **Comando:** `pwd` (Print Working Directory).
* **Resultado:** Te muestra la ruta absoluta de tu ubicación actual.

```bash
[vagrant@localhost ~]$ pwd
/home/vagrant
```

## 📂 Crear Carpetas (`mkdir`)
Para organizar nuestro trabajo, crearemos directorios (carpetas).
* **Comando:** `mkdir <nombre>` (Make Directory).

```bash
# Crea una carpeta llamada 'linux-practices' en tu directorio actual
[vagrant@localhost ~]$ mkdir linux-practices
```

## 🚶 Moverse por el sistema (`cd`)
El comando `cd` (Change Directory) es tus "piernas" en Linux.
* **`cd nombre_carpeta`**: Entra en una carpeta.
* **`cd ..`**: Retrocede un nivel (vuelve a la carpeta padre).
* **`cd` (sin nada)**: Te lleva directo a tu casa (`/home/usuario`).

```bash
# Entramos en la carpeta que acabamos de crear
[vagrant@localhost ~]$ cd linux-practices

# Verificamos que hemos cambiado de sitio
[vagrant@localhost linux-practices]$ pwd
/home/vagrant/linux-practices
```

## 👁️ Listar contenido (`ls`)
Para ver qué hay dentro de una carpeta.

* **`ls`**: Listado simple.
* **`ls -l`**: Listado detallado (permisos, dueño, tamaño).
* **`ls -a`**: Muestra archivos ocultos (los que empiezan por punto .).

```bash
# 1. Creamos más carpetas para probar
mkdir testdir
mkdir devopsdir
mkdir vpdir

# 2. Listamos para verlas
ls
# Salida esperada: devopsdir testdir vpdir
```

## 📄 Crear archivos vacíos (`touch`)
A veces necesitamos crear un archivo rápidamente para pruebas sin abrir un editor.

* **Comando**: `touch <nombre_archivo>`

```bash
# Creamos tres archivos a la vez
touch file2 file3 file4

# Comprobamos que están ahí junto con los directorios
ls
# Salida esperada: devopsdir file2 file3 file4 testdir vpdir
```

## 🧭 Concepto: Rutas Absolutas vs Relativas
Es vital entender la diferencia al moverte:

| Tipo | Descripción | Ejemplo |
| :--- | :--- | :--- |
| **Absoluta** | La dirección completa desde la raíz `/`. Funciona estés donde estés. | `/home/vagrant/linux-practices/file2` |
| **Relativa** | La dirección desde donde estás parado ahora mismo. | `file2` (si ya estás dentro de la carpeta). |

> **Ejercicio:** Intenta ir a la carpeta `/tmp` usando la ruta absoluta (`cd /tmp`) y luego vuelve a tu casa usando solo `cd`.

---

## 📋 Copiar Archivos y Carpetas (`cp`)
Para duplicar contenido usamos `cp` (Copy).
* **`cp origen destino`**: Copia un archivo.
* **`cp -r origen destino`**: Copia una carpeta entera (recursivo).

```bash
# Copiar un archivo a una carpeta
cp file2 testdir/

# Copiar una carpeta entera (necesita -r)
# Esto crea una copia de 'testdir' dentro de 'vpdir'
cp -r testdir/ vpdir/
```

## 🚚 Mover y Renombrar (`mv`)
En Linux, "mover" y "renombrar" son el mismo comando: mv (Move).

1. Si mueves de A a B (carpeta), se mueve.
2. Si mueves de A a A (con otro nombre), se renombra.

```bash
# MOVER: Mueve la carpeta 'devopsdir' dentro de 'vpdir'
mv devopsdir/ vpdir/

# RENOMBRAR: Cambia el nombre de 'file3' a 'file_renamed'
mv file3 file_renamed
```

## 🗑️ Borrar contenido (`rm`)
⚠️ ¡Cuidado! En la terminal no hay "Papelera de Reciclaje". Lo que borras, desaparece para siempre.

* **`rm archivo`**: Borra un archivo.
* **`rm -r carpeta`**: Borra una carpeta y su contenido.
* **`rm -rf carpeta`**: Borra carpeta a la fuerza sin preguntar (peligroso).

```bash
# Borrar un archivo simple
rm file2

# Borrar una carpeta y todo su contenido
rm -rf testdir/
```