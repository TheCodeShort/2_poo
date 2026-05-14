[[2_SDLC_sofware.pdf#search=Aplicación de pruebas de “software”|2_SDLC_sofware, p.731]]

## 1) Introducción del módulo

La introducción deja claro el propósito: estudiar los elementos necesarios para realizar pruebas de software, con foco en pruebas funcionales y no funcionales, Agile Testing e informes de resultados. También explica que, en aplicaciones web, la calidad y ausencia de errores son críticas, así que las pruebas son un pilar del proceso de desarrollo.

## 2) Realización de pruebas de software

Aquí el libro abre la parte operativa. Explica que no siempre se deben aplicar todas las pruebas posibles, sino las que mejor se ajusten al proyecto. Por eso aparece el rol del QA o líder de pruebas, que decide qué tipos de prueba son necesarios según el caso.

## 3) Tipos de pruebas

La clasificación base es sencilla: **pruebas funcionales** y **pruebas no funcionales**. A partir de ahí, el texto muestra pruebas como unitarias, integración, estrés, rendimiento y escalabilidad. El objetivo es cubrir desde el código fuente hasta la experiencia del usuario.

### 3.1 Pruebas funcionales

Estas prueban lo que el sistema **hace** para el negocio: funcionalidad, usabilidad y comportamiento esperado. Validan la aplicación contra el documento de requisitos y se relacionan con la lógica externa del producto; por eso también se entienden como pruebas de caja negra. Incluyen unitarias, regresión e interfaz, entre otras.

### 3.2 Pruebas unitarias

Aquí se valida cada unidad por separado: función, método, constructor, clase o módulo. El texto remarca que deberían ser las primeras pruebas en desarrollo y normalmente las implementan los desarrolladores. Su ventaja es que detectan errores tempranamente y reducen costos posteriores.

### 3.3 Pruebas de integración

Estas verifican que los módulos trabajen bien juntos: interfaces, bases de datos, configuración, infraestructura y comunicación entre componentes. El foco no es cada pieza aislada, sino la sinergia entre piezas. En software real, esta parte es clave porque muchos errores no nacen en el módulo, sino en su choque con otro módulo.

### 3.4 Pruebas no funcionales

Estas no prueban funciones del negocio, sino condiciones de calidad: fiabilidad, usabilidad, escalabilidad, instalación, seguridad y rendimiento. El libro las presenta como pruebas que suelen requerir automatización y que evalúan el comportamiento del sistema bajo carga o condiciones adversas.

### 3.5 Pruebas de rendimiento, carga, estrés, volumen, usabilidad y robustez

Aquí el texto afina la lupa. Las pruebas de carga simulan el volumen esperado de trabajo; las de rendimiento miden tiempos de respuesta; las de estrés empujan el sistema hasta ver su límite; las de volumen prueban con grandes cantidades de datos; las de usabilidad miden facilidad de uso; y las de robustez verifican cómo responde ante entradas incorrectas.

### 3.6 Pruebas de seguridad

La sección de seguridad busca detectar fallas y vulnerabilidades para proteger confidencialidad, integridad y disponibilidad. El módulo menciona el uso de OWASP ZAP como apoyo para probar seguridad en páginas de ejemplo. Aquí el mensaje es directo: si no pruebas seguridad, estás dejando la puerta abierta y luego sorprende que entre un problema.

## 4) Ventajas y desventajas de las pruebas

El libro explica que las pruebas mejoran calidad, experiencia del usuario y confiabilidad. Las ventajas más claras están en unitarias, integración y rendimiento: detección temprana, mejor refactorización, menos cuellos de botella y más estabilidad. Como “desventaja”, el texto señala sobre todo el costo y el tiempo necesarios para ejecutar pruebas bien hechas.

## 5) Documentos y artefactos de prueba

Esta parte es muy importante porque baja las pruebas a documentos concretos. El módulo habla de **plan de pruebas**, **casos de prueba**, **scripts de prueba**, **reporte de defectos** e **informe de resultados**. También menciona que ISO/IEC/IEEE 29119-3:2013 ofrece artefactos estandarizados para documentar procesos de pruebas.

### 5.1 Plan de pruebas

El plan de pruebas describe cómo se probará el sistema: alcance, tipos de prueba, criterios de entrada y salida, recursos, calendario, riesgos y responsabilidades. En otras palabras, es el mapa de ruta de la fase de calidad.

### 5.2 Caso de prueba

El caso de prueba define condiciones concretas con las que se verificará un requisito. El libro enumera sus elementos: identificador, nombre, descripción, orden de ejecución, requerimiento asociado, precondición, postcondición y resultado esperado. Eso permite trazabilidad y control fino.

### 5.3 Script de prueba

El script es la secuencia ejecutable de pasos que sigue el tester para comprobar un sistema. El documento destaca nombre, descripción, pasos, puntos de verificación y resultado esperado. Es el “guion” concreto de la prueba.

### 5.4 Informe de resultados

El informe de resultados resume qué se probó, qué pasó y qué falló. Incluye alcance, casos planificados, ejecutados, exitosos, fallidos, bloqueados, listado de defectos y conclusiones. El responsable principal de este documento es el gerente de pruebas.

### 5.5 Reporte de defectos

Cuando se confirma un defecto, el libro pide documentarlo con identificador, título, responsable, severidad, aplicación, descripción, método de reproducción e información adicional. Esa disciplina es la que convierte un error en algo rastreable y corregible, no en un “a veces falla”.

## 6) Agile Testing

Esta sección conecta pruebas con metodologías ágiles. El objetivo es integrar las pruebas desde el principio, no dejar la verificación para el final. El módulo explica principios de pruebas ágiles, cuadrantes, TDD, ATDD, BDD, pruebas exploratorias y automatización de regresión.

### 6.1 Cuadrantes de pruebas ágiles

Los cuadrantes organizan las pruebas según apoyen al equipo o al negocio, y según sean más técnicas o más orientadas al usuario.  
Q1: unitarias y de componente.  
Q2: funcionales, historias, prototipos y simulaciones.  
Q3: exploratorias, usabilidad, escenarios y aceptación.  
Q4: rendimiento, estrés, seguridad y robustez.

### 6.2 TDD, ATDD y BDD

El material muestra estas prácticas como formas de conectar pruebas con desarrollo:  
TDD: escribir pruebas antes o junto al código.  
ATDD: orientar el desarrollo a criterios de aceptación.  
BDD: expresar comportamiento esperado en lenguaje común entre negocio y equipo técnico.  
La lógica aquí es que la prueba deja de ser “auditoría final” y se vuelve parte del diseño.

### 6.3 Pruebas exploratorias

Son pruebas donde aprendizaje, diseño y ejecución ocurren al mismo tiempo. El tester explora el producto, formula hipótesis, prueba caminos y aprende sobre el sistema sobre la marcha. Son útiles cuando el producto ya tiene cierta madurez o cuando necesitas entender flujos reales sin depender totalmente de un guion rígido.

### 6.4 Automatización de regresión

Estas pruebas verifican que cambios nuevos no rompan funcionalidades ya existentes. El texto dice que automatizarlas ahorra tiempo, reduce errores humanos y permite repetirlas con rapidez, algo vital cuando el software ya está en producción o cambia con frecuencia.

### 6.5 Pruebas de exploración, usabilidad y aceptación

El libro diferencia usabilidad de aceptación: usabilidad busca mejorar la interacción y detectar fricción; aceptación verifica que el sistema cumpla requisitos y esté listo para liberarse. En esa misma línea coloca las pruebas exploratorias como una forma flexible y profunda de conocer el producto.

## 7) Elaboración del plan de mejora

Después de probar, el módulo no termina: ahora toca **mejorar**. El plan de mejora arranca con el diagnóstico, luego identifica áreas de mejora, selecciona acciones, organiza la planeación y hace seguimiento. La lógica es muy de gestión de calidad: probar, detectar problemas, priorizar mejoras y volver a medir.

### 7.1 Identificar el área de mejora

El texto recomienda apoyarse en fortalezas y debilidades para definir qué debe corregirse. Para eso usa herramientas como diagrama de causa-efecto, Pareto y otras técnicas de análisis de causas. No se trata de “arreglar lo que grita más fuerte”, sino de atacar la causa real.

### 7.2 Seleccionar acciones, planear y hacer seguimiento

Una vez detectadas las causas, se seleccionan acciones concretas, se planean y luego se les hace seguimiento. El espíritu del módulo es que la calidad no sea una actividad aislada, sino un ciclo: observar, corregir, verificar y repetir.

## 8) Lo que te deja esta sección

Este bloque te enseña el mapa completo de la calidad de software: **qué probar, cómo probar, cómo documentar lo probado, cómo interpretar resultados y cómo convertir hallazgos en mejora continua**. Es la parte donde el software deja de ser “funcionar” y empieza a ser “funcionar bien, con evidencia y trazabilidad”.