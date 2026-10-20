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
