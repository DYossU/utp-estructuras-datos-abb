# Base de Firmas de Malware - Sistema ABB 

Sistema de gestión, consulta y almacenamiento jerárquico de firmas de código malicioso basado en un **Árbol Binario de Búsqueda (ABB)** desarrollado en Java con Swing (modo Design de NetBeans) y Graphics2D. Este proyecto optimiza el registro, búsqueda, clasificación y eliminación de amenazas informáticas mediante estructuras dinámicas en memoria y persistencia plana.

---

## Características Principales

- **Estructura ABB (`ArbolFirmas`):**
  - Inserción ordenada alfabéticamente por `nombreAmenaza` utilizando `compareToIgnoreCase` con rechazo automático de claves duplicadas.
  - **Eliminación completa (3 casos):** Soporte interactivo para eliminar nodos hoja, nodos con 1 hijo y nodos con 2 hijos reemplazando por el **sucesor InOrden** (nodo mínimo del subárbol derecho).
  - **Búsqueda Principal y por Prefijo:** Búsqueda exacta $O(h)$ por nombre de amenaza y búsqueda por prefijo aprovechando la propiedad de orden del ABB.
  - **Consultas y Filtros Secundarios:** Búsqueda por `idFirma`, `tipo` de amenaza, nivel de `severidad` (1-4), coincidencia parcial o completa de `hashFirma` y conteo estadístico por severidad.
  - **Métricas Estructurales:** Cálculo recursivo de total de nodos, altura del árbol y cantidad de nodos hoja.
- **Modelo de Datos (`NodoFirma`):**
  - Almacenamiento con atributos estrictos: `idFirma` (`MW-000X`), `nombreAmenaza`, `tipo`, `severidad` (1-4), `hashFirma` (SHA-256 de 64 caracteres hexadecimales) y `fechaRegistro` (`AAAA-MM-DD`), junto con sus enlaces izquierdo y derecho.
  - Clasificación descriptiva automática según el tipo de malware (`Troyano`, `Ransomware`, `Gusano`, `Botnet`, `Spyware`).
- **Persistencia Robusta (`GestorArchivo`):**
  - Carga y validación línea por línea del archivo `firmas.csv`.
  - Verificación de formato de ID, unicidad de claves, rango de severidad, fecha ISO (`AAAA-MM-DD`) y validación hexadecimal estricta carácter por carácter (sin librerías prohibidas).
  - Creación automática de `firmas.csv` con cabecera inicial si el archivo no existe en disco.
  - Guardado automático en recorrido **PreOrden** tras cada inserción, eliminación o cierre para preservar la topología exacta del árbol.
- **Interfaz Gráfica de Usuario (Swing Design + Graphics2D):**
  - **Ventana Principal (`VentanaPrincipal`):** Navegación modular hacia registro, visualización gráfica, consultas/reportes y guardado seguro, con selector dinámico de color de fondo y botones (`JColorChooser`).
  - **Ventana de Registro (`VentanaRegistro`):** Alta de nuevas firmas con generación automática de ID secuencial (`MW-000X`) y vista previa de las características del tipo de malware seleccionado.
  - **Ventana de Visualización (`VentanaVisualizacion` + `PanelArbol`):** Dibujo jerárquico del ABB con nivel por nodo, personalización del color del lienzo y ejecución de recorridos **InOrden**, **PreOrden** y **PostOrden**.
  - **Ventana de Reportes y Gestión (`VentanaReportes`):** Panel unificado para búsquedas por criterio (`Nombre exacto`, `Prefijo`, `ID`, `Tipo`, `Severidad`, `Hash`), eliminación de firmas con confirmación y visualización de estadísticas e InOrden.
- **Cero Librerías Prohibidas:** Implementación pura sobre nodos propios sin uso de `TreeMap`, `TreeSet`, `HashMap`, `JTree`, bases de datos externas ni `MessageDigest`.

---

## Estructura del Proyecto

```text
ProyectoFirmasABB_Final/
├── firmas.csv (Generado y actualizado automáticamente en la ejecución)
├── pom.xml
└── src/
    └── main/
        └── java/
            ├── main/
            │   └── Main.java
            ├── modelo/
            │   ├── NodoFirma.java
            │   └── ArbolFirmas.java
            ├── archivos/
            │   └── GestorArchivo.java
            └── vista/
                ├── VentanaPrincipal.java / .form
                ├── VentanaRegistro.java / .form
                ├── VentanaVisualizacion.java / .form
                ├── VentanaReportes.java / .form
                └── PanelArbol.java

```

---

## Requisitos y Ejecución

### Requisitos

* **Java Development Kit (JDK) 11 o superior** (configurado para JDK 21 en `pom.xml`).
* **IDE compatible con Java** (Apache NetBeans recomendado para editar las vistas `.form` en modo *Design*, IntelliJ IDEA o VS Code).

### Instalación y Ejecución

1. Clona o descarga el repositorio en tu equipo.
2. Abre el proyecto (`ProyectoFirmasABB`) dentro de tu IDE asegurándote de respetar la estructura de paquetes (`main`, `modelo`, `archivos`, `vista`).
3. Ejecuta la clase principal `main.Main`. Al iniciar, se cargará el archivo `firmas.csv` o se creará automáticamente con su cabecera en la raíz del proyecto si aún no existe.

---

## Autores

* David Ureña
* Lis Vásquez
* Yoselin Pérez
* Oliver Oses
* Pedro Zamora
* Ethan Beltrán

```

```