# Sistema de Gestión de Firmas de Malware (ABB en Java)

Proyecto académico desarrollado para **Estructuras de Datos** en la **Universidad Tecnológica de Panamá (UTP)**, enfocado en la gestión y visualización de firmas mediante un Árbol Binario de Búsqueda (ABB).

## Propósito del proyecto
Aplicar estructuras de datos jerárquicas (ABB) para organizar, registrar, consultar y generar reportes sobre firmas de malware, complementado con una interfaz gráfica en Java y persistencia en archivos.

## Estructura del proyecto
* `pom.xml`: Configuración de dependencias y compilación del proyecto Maven.
* `src/main/java/main/Main.java`: Punto de entrada de la aplicación.
* `src/main/java/modelo/`: Lógica del árbol (`ArbolFirmas.java`) y estructura del nodo (`NodoFirma.java`).
* `src/main/java/archivos/GestorArchivo.java`: Manejo de lectura/escritura de datos en archivos.
* `src/main/java/vista/`: Interfaz gráfica y paneles de visualización (`VentanaPrincipal`, `VentanaRegistro`, `VentanaReportes`, `VentanaVisualizacion`, `PanelArbol`).

## Ejecución
1. Abre el proyecto en tu IDE compatible con Maven (Apache NetBeans, VS Code o IntelliJ IDEA).
2. Compila el proyecto y ejecuta la clase `main.Main`.

## Licencia
Este proyecto se distribuye bajo la licencia **MIT**. Consulta el archivo `LICENSE` para más detalles.
