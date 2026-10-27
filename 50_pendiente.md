```table-of-contents
title: Conceptos POO
minDepth: 1
maxDepth: 6
listStyle: number
```
# 1_🗺️ Plan de Estudio Detallado: De la Teoría al Mundo Laboral

## 1Arquitectura de Software: El Patrón MVC

- **Lo que debes estudiar a fondo:** **Separación de Responsabilidades (Separation of Concerns).**
- **Detalle de los conceptos:**
    - Qué es el **Modelo** (capa de datos y lógica de negocio), la **Vista** (la interfaz con la que interactúa el usuario) y el **Controlador** (el puente que coordina ambas).
    - Cómo se comunican entre sí sin depender rígidamente (bajo acoplamiento).
- **Términos técnicos para buscar:** _Model-View-Controller (MVC)_, _Desacoplamiento de software_, _Capas de abstracción_.

## 2_Paradigmas Modernos: Programación Orientada a Eventos y Reactiva

- **Lo que debes estudiar a fondo:** Cómo las aplicaciones modernas "escuchan" al usuario de forma pasiva.
- **Detalle de los conceptos:**
    - El **Bucle de Mensajes (Message Loop / Event Loop):** El ciclo infinito que corre de fondo capturando los clics o movimientos del mouse.
        
    - **Manejadores de Eventos (Event Handlers / Callbacks):** Funciones o bloques de código que se disparan solo cuando ocurre una acción específica.
    - **Flujos de Datos (Streams):** Cómo reaccionar a eventos inmediatos (como escribir tecla por tecla) usando programación reactiva.
- **Términos técnicos para buscar:** _Event-Driven Architecture_, _Event Handlers_, _Reactive Programming (Rx)_, _Asynchronous Streams_.

## 3_Rendimiento y Concurrencia: Gestión de Hilos (Multi-threading)

- **Lo que debes estudiar a fondo:** **La regla de oro de las interfaces de usuario (UI): Jamás bloquear la pantalla.**
- **Detalle de los conceptos:**
    - **Hilo Principal (UI Thread / Main Thread):** Es el hilo único encargado de dibujar los botones y animaciones. Si le das una tarea pesada, la app se congela.
    - **Hilos Secundarios (Background Threads):** Rutas alternas en el procesador para enviar tareas pesadas (descargas, consultas a bases de datos).
    - **Programación Asíncrona:** El arte de iniciar una tarea pesada en el fondo y "esperar" a que termine sin congelar el sistema.
- **Términos técnicos para buscar:** _Multithreading_, _Asincronía (Async/Await)_, _UI Thread vs Background Thread_, _Concurrency_.

## 4_Seguridad de Aplicaciones: Protección de la Superficie de Atque

- **Lo que debes estudiar a fondo:** No confiar jamás en lo que el usuario escribe en la pantalla.
- **Detalle de los conceptos:**
    - **Superficie de Ataque:** Entender que la interfaz gráfica (formularios, inputs) es la primera línea de exposición ante un atacante.
    - **Sanitización de Entradas (Input Sanitization):** Filtrar, limpiar y remover caracteres peligrosos (como código malicioso o scripts) antes de procesarlos.
    - **Validación de Datos:** Asegurar que si esperas un número, el usuario envíe un número y no texto.
- **Términos técnicos para buscar:** _Input Sanitization_, _Data Validation_, _Inyección de Código (SQL Injection / XSS)_, _Attack Surface_.

## 5_Ciclo de Vida de Componentes de Software

- **Lo que debes estudiar a fondo:** Los estados por los que pasa una ventana o componente desde que nace hasta que muere.
- **Detalle de los conceptos:**
    - **Inicialización (Initialize / Construct):** Creación del objeto en memoria.
    - **Carga (Load / Mount):** El momento justo antes de mostrarse donde se preparan los datos iniciales.
    - **Estados Intermedios de Cierre (Closing vs Closed):** Entender la diferencia entre interceptar y cancelar una acción en proceso (`Closing`) versus limpiar recursos cuando la acción ya terminó (`Closed`).
- **Términos técnicos para buscar:** _Component Lifecycle_, _Lifecycle Hooks_, _Event Interception_.

# 2_🗺️ Plan de Estudio Detallado:
## 1_Gestión de Memoria (Estática vs. Dinámica)

- **Qué debiste haber estudiado:** La diferencia entre cómo el sistema operativo maneja la memoria a nivel de compilación frente a tiempo de ejecución (_runtime_).
- **Explicación sencilla:**
    - **Memoria Estática:** Es como reservar las mesas de un restaurante con meses de anticipación. El tamaño se define al compilar el código y no cambia durante la ejecución del programa.
    - **Memoria Dinámica:** Es como añadir mesas a un evento sobre la marcha a medida que van llegando los invitados. Se solicita y se libera directamente mientras el programa ya está corriendo, adaptándose al volumen de datos en tiempo real.

2. Notación Big O (Complejidad Temporal)

- **Qué debiste haber estudiado:** Métricas de rendimiento de algoritmos y análisis de eficiencia en el peor de los casos.
- **Explicación sencilla:** Es la forma en que los programadores miden qué tan "rápido" o "lento" se volverá un algoritmo a medida que crecen los datos:
    - **Complejidad \(O(1)\) (Constante):** El algoritmo tarda lo mismo con 1 dato que con 1 millón de datos. Es un acceso instantáneo y el escenario ideal.
    - **Complejidad \(O(n)\) (Lineal):** Si los datos se duplican, el tiempo de ejecución se duplica. Ocurre cuando tienes que revisar los elementos uno por uno de principio a fin (búsqueda secuencial), lo que genera riesgos de cuellos de botella.

3. Estructuras de Datos Lineales y No Lineales

- **Qué debiste haber estudiado:** Clasificación de estructuras de almacenamiento según la forma en que sus nodos se interconectan.
- **Explicación sencilla:**
    - **Estructuras Lineales:** Los elementos forman una fila recta, uno detrás del otro (como Arreglos, Listas, Pilas y Colas).
    - **Estructuras No Lineales:** Los elementos se conectan de formas más complejas. Un solo dato puede ramificarse a muchos otros, creando jerarquías (como los **Árboles**) o redes interconectadas (como los **Grafos**).

4. Estructuras de Datos Específicas y sus Reglas

- **Qué debiste haber estudiado:** El comportamiento y propósito técnico de los contenedores de datos estándar:
    - **Arreglo (Array):** Colección de tamaño fijo que almacena estrictamente datos _homogéneos_ (todos los elementos son del mismo tipo) uno al lado del otro en memoria contigua.
    - **Conjunto (Set):** Una colección diseñada específicamente para guardar valores únicos; por definición matemática interna **no permite elementos duplicados**.
    - **Pila (Stack):** Se rige por el principio **LIFO** (_Last In, First Out_). El último dato en entrar es obligatoriamente el primero en salir (como una pila de platos sucios).
    - **Cola (Queue):** Se rige por el principio **FIFO** (_First In, First Out_). El primer dato en entrar es el primero en salir (como la fila de un banco).
    - **Cola de Prioridad (PriorityQueue):** Modifica la cola tradicional. Aquí los elementos no salen por orden de llegada, sino por un atributo de "peso" o nivel de relevancia asignado.
    - **HashMap (Tablas Hash):** Estructura que logra accesos ultra rápidos \(O(1)\) convirtiendo una clave en una dirección de memoria exacta mediante un algoritmo matemático llamado **Función Hash**.

5. Inmutabilidad y Colecciones de Solo Lectura

- **Qué debiste haber estudiado:** Diseño de software seguro y protección del estado de la memoria.
- **Explicación sencilla:** Configurar datos para que su valor quede "grabado en piedra" una vez creados. Al implementar colecciones inmutables o de solo lectura, impides que otras partes del código alteren los datos accidentalmente, garantizando la estabilidad del sistema frente a modificaciones externas en la memoria.

6. Genéricos (Generics)

- **Qué debiste haber estudiado:** Seguridad de tipos (_Type Safety_) en lenguajes de programación fuertemente tipados.
- **Explicación sencilla:** Es una forma de crear estructuras flexibles pero seguras. En lugar de hacer una lista que acepte cualquier cosa (corriendo el riesgo de mezclar textos con números y romper el programa en ejecución), los genéricos te permiten especificar: _"Esta lista contendrá estrictamente este tipo de dato"_. El compilador valida esto y previene errores de compatibilidad antes de que el programa sea distribuido.