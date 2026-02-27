# Linear Algebra Matrix Multiplication Benchmark

Este proyecto es una biblioteca de álgebra lineal desarrollada en Java diseñada para la manipulación y multiplicación eficiente de matrices. El enfoque principal es el **benchmarking** de diferentes estructuras de datos para matrices, comparando el rendimiento de representaciones densas frente a diversas representaciones dispersas (sparse).

## Estructura del Proyecto

El sistema está organizado en módulos especializados para gestionar la complejidad de las operaciones matriciales:

### 1. Representaciones de Matrices (`matrix/`)
El proyecto implementa múltiples formas de almacenar matrices según su densidad de datos:
* **DenseMatrix:** Representación estándar para matrices con pocos valores cero.
* **SparseMatrix:** Clase base para matrices con alta presencia de ceros.
* **Representaciones Optimizadas:**
    * **CompressedRowMatrix (CSR):** Optimizado para acceso rápido por filas.
    * **CompressedColumnMatrix (CSC):** Optimizado para acceso rápido por columnas.
    * **CoordinateMatrix (COO):** Almacenamiento basado en ternas (fila, columna, valor).

### 2. Constructores y Carga (`matrixbuilders/` & `MatrixLoader`)
* **Builders:** Implementaciones específicas para construir matrices de forma fluida (CSR, CSC, Sparse).
* **MatrixLoader:** Capacidad para cargar matrices reales desde archivos externos con formato `.mtx` (como los archivos `1138_bus.mtx` y `bcsstk17.mtx` incluidos).

### 3. Motores de Multiplicación (`operators/matrixmultiplication/`)
El núcleo del benchmark reside en la comparación de algoritmos:
* **DenseMatrixMultiplication:** Algoritmos estándar para matrices densas.
* **SparseMatrixMultiplication:** Algoritmos optimizados que omiten operaciones con valores cero, reduciendo drásticamente el tiempo de cómputo en matrices dispersas.
* **MatrixMultiplication:** Interfaz unificada para ejecutar las operaciones.

## Ejecución y Benchmarking
El flujo de ejecución está controlado por el **Controller** y la clase **Main**, que se encargan de:
1. Cargar las matrices de prueba desde los recursos.
2. Transformar las matrices a los diferentes formatos (CSR, CSC, Dense).
3. Ejecutar la multiplicación y medir los tiempos de ejecución para comparar la eficiencia de cada formato.

## Tecnologías y Requisitos
* **Lenguaje:** Java
* **Gestión de Proyectos:** Maven (`pom.xml` incluido).
* **Formatos Soportados:** Matrix Market (`.mtx`) para la ingesta de datos de prueba.

---
Este proyecto demuestra cómo la elección de una estructura de datos adecuada (CSR vs CSC vs Dense) puede impactar críticamente en el rendimiento de los algoritmos de álgebra lineal.
