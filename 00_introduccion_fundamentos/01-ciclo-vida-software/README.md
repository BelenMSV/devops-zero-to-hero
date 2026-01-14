# 🔄 Ciclo de Vida del Software (SDLC) y Metodologías

Este tema cubre los fundamentos de cómo se construye el software, desde la concepción de la idea hasta su mantenimiento, y cómo han evolucionado las metodologías de trabajo hasta llegar a la necesidad de DevOps.

---

## 1. SDLC (Software Development Life Cycle)

El **SDLC** (Ciclo de Vida de Desarrollo de Software) es el proceso estructurado que utilizan los equipos para diseñar, desarrollar y probar software de alta calidad.

> **Nota:** DevOps no elimina estas fases; lo que hace es optimizar cómo se ejecutan (más rápido y automatizado).

### Las 7 Fases del SDLC
El desarrollo de software suele pasar por estas etapas, independientemente de la metodología:

1.  **📊 Requisitos:** Definir qué quiere el cliente y qué problema se resuelve.
2.  **📅 Planificación:** Estimar costes, recursos y tiempos.
3.  **📝 Diseño:** Arquitectura del sistema, bases de datos y prototipos.
4.  **💻 Desarrollo:** La escritura del código (coding).
5.  **🧪 Testing (Pruebas):** Verificar que no hay errores (bugs) y cumple los requisitos.
6.  **🚀 Despliegue (Deploy):** Poner el software en producción para el usuario final.
7.  **🔧 Mantenimiento:** Corregir errores post-lanzamiento y añadir mejoras.

---

## 2. Evolución de las Metodologías

Para gestionar las fases del SDLC, existen diferentes modelos de trabajo. Los dos más importantes para entender la historia de DevOps son **Cascada** y **Ágil**.

### 🌊 Modelo en Cascada (Waterfall)
Es el enfoque tradicional y lineal. Una fase no comienza hasta que la anterior ha terminado por completo.

* **Flujo:** Requisitos → Diseño → Código → Test → Deploy.
* **Problema:** Es muy rígido. Si detectas un error en la fase de Testing, volver a la fase de Diseño es muy costoso y lento.
* **Entrega:** El cliente ve el producto final solo al terminar todo el proyecto (meses o años).

### 🏃 Modelo Ágil (Agile)
Nació para solucionar la rigidez de Waterfall. Se basa en un **enfoque iterativo e incremental**.

> **💡 El Ciclo de Vida Iterativo**
>
> El desarrollo se divide en bloques pequeños y en cada bloque se aborda una funcionalidad concreta (Ej: gestión de usuarios, inicio de sesión, registro).
>
> * **Cada bloque incluye sus propias fases** de diseño, codificación y pruebas.
> * Al terminar el bloque, esa funcionalidad ya aporta valor y puede ser entregada.

* **Iteraciones (Sprints):** Ciclos cortos de trabajo (2-4 semanas).
* **Feedback:** El cliente ve avances constantemente y puede pedir cambios sobre la marcha.

---

## 3. Otros Modelos Relevantes

Aunque Waterfall y Agile dominan la conversación, existen otros enfoques que aportaron conceptos clave a la ingeniería moderna:

### 🏭 Lean Software Development
Adaptado del sistema de producción de Toyota. Su objetivo no es solo "ir rápido", sino **eliminar desperdicios** (todo aquello que no aporta valor al cliente).
* **Concepto clave para DevOps:** Si una tarea es repetitiva y manual (como desplegar un servidor a mano), es un "desperdicio". Por eso automatizamos.

### 🌀 Modelo en Espiral
Combina la idea iterativa con un enfoque fuerte en el **Análisis de Riesgos**.
* **Concepto clave:** En cada vuelta de la espiral, se evalúan los peligros del proyecto. Esto es el antecesor de pensar en seguridad desde el principio (*Shift-Left Security*).

---

## ⚔️ Comparativa: Waterfall vs Agile

| Característica | Waterfall (Cascada) | Agile (Ágil) |
| :--- | :--- | :--- |
| **Enfoque** | Lineal y secuencial | Iterativo y cíclico |
| **Flexibilidad** | Baja (Difícil hacer cambios) | Alta (Cambios bienvenidos) |
| **Entrega de Valor** | Al final del proyecto (Big Bang) | Continua y gradual |
| **Pruebas** | Al final de todo el desarrollo | En cada iteración/bloque |
| **Relación con DevOps** | Genera silos entre equipos | **Es la base cultural de DevOps** |

---

## 📚 Conclusión
Entender el paso de Waterfall a Agile es clave. **DevOps es la evolución natural de Agile**: mientras Agile agilizó el desarrollo (Dev), DevOps lleva esa agilidad también a las operaciones y el despliegue (Ops).