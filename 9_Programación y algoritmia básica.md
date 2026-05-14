[[2_SDLC_sofware.pdf#search=rogramación y algoritmia básica|SDLC_sofware, p.457]]

## Introducción a la algoritmia

Aquí el documento te dice que la programación y la construcción de software se basan en aplicar una secuencia correcta de pasos. También te presenta las **cuatro fases clave** del trabajo algorítmico: **análisis, diseño, implementación y validación**. La idea es que no saltes directo a codificar; primero entiendas el problema y luego lo conviertas en una solución verificable. Piensa en esto como una función de Python bien hecha: no solo corre, sino que además está pensada para recibir algo, procesarlo y devolver algo útil.

- ### Definición de algoritmo

	La sección define algoritmo como un **conjunto ordenado y finito de operaciones** que permite resolver un problema. El documento explica además que una computadora hace operaciones simples, pero en gran cantidad; por eso un problema grande debe dividirse en procesos pequeños y manejables. Aquí está la base de todo: si no puedes dividir el problema, tampoco puedes automatizarlo bien.

## Pensamiento algorítmico

Esta parte muestra que un mismo problema puede resolverse de varias maneras, pero todas comparten algo: una **secuencia ordenada de pasos**. El ejemplo del cuadrado [[2_SDLC_sofware.pdf#search=Figura 2. Pensamiento lógico y procedimental|SDLC_sofware, p.466]] dibujado de formas distintas sirve para demostrar que no importa tanto el camino exacto, sino que el proceso tenga lógica. Las fases mentales que propone el material son:

**entender el problema
hacer un plan
ejecutar el plan 
revisar el resultado**

Esto es muy parecido a depurar un script: primero entiendes qué falla, luego pruebas una ruta, la ejecutas y revisas si realmente resolvió el error.

## Solución de problemas y programación

Aquí el documento baja la idea de algoritmo a ejemplos cotidianos, como **apagar una computadora** o **cargar un celular**, para mostrar que un algoritmo no tiene que ser matemático para ser válido: solo debe ser claro, secuencial y útil. Después define tres propiedades importantes de un algoritmo: 

**realizable** (termina), 
**comprensible** (se entiende qué hacer) 
**preciso** (si repites los datos, obtienes el mismo resultado).

En términos prácticos, esto evita “algoritmos zombi” que nunca terminan o que hacen cosas distintas cada vez que los ejecutas.

 - #### **Fases para elaborar un programa de computador**
	
	El PDF aquí conecta la teoría con el proceso real de desarrollo: **análisis del problema, diseño del algoritmo, traducción a un lenguaje de programación y depuración**. O sea, primero piensas, luego estructuras, después codificas y finalmente corriges. Esta parte es importante porque deja claro que un programa bueno no nace del teclado; nace del razonamiento.

## Análisis del problema: formular claramente el problema

En esta subsección el documento te obliga a hacer las preguntas correctas antes de resolver nada: 

- qué tan claro está el problema
- qué palabras no entiendes
- si ya existe algo parecido 
- qué información sí importa

El ejemplo del celular de don Juan muestra cómo transformar una situación real en un problema computable. Esta etapa es vital porque si formulas mal el problema, el algoritmo puede ser perfecto… para resolver otra cosa.

- ### Precisar elementos de entrada

	Aquí aprendes a separar la **información necesaria** de la irrelevante
	
	- identificar **datos de entrada**
	- detectar la **incógnita**
	- reconocer si hacen falta datos adicionales
	
	También te recuerda que a veces necesitas entender el contexto del problema, por ejemplo si hay componentes financieros, numéricos o de otro dominio. Esto es como definir bien los parámetros de una función: si pides variables equivocadas, la función no falla por culpa de Python; falla por culpa de la entrada mal pensada.

- ### Precisar resultados esperados

	Esta parte te enseña a definir con exactitud **qué salida debe producir el algoritmo** y en qué formato: pantalla, diagrama, orden específico, etc. Parece obvio, pero no lo es; muchos errores de programación vienen de no saber exactamente qué debe devolver el sistema. Aquí el material te entrena para cerrar el ciclo: entrada clara, proceso claro, salida clara.

## Desarrollo de la creatividad: elementos, modelos, fases y objetivos

Esta sección introduce la **espiral creativa de Resnick**: [[2_SDLC_sofware.pdf#search=Figura 4. Espiral del Pensamiento Creativo diseñada por el Dr. Mitchel Resnick|SDLC_sofware, p.473]] imaginar, crear, jugar, compartir, reflexionar e imaginar otra vez. El mensaje de fondo es que resolver algoritmos también requiere creatividad, no solo técnica. En programación esto es oro puro: un buen desarrollador no solo escribe instrucciones, también encuentra formas mejores de pensar el problema y mejorar la solución con cada iteración.

## Lógica matemática

### **proposición**: 
una oración que solo puede ser **verdadera o falsa**, pero no las dos a la vez. El texto distingue entre proposiciones simples válidas, como “la tierra es plana” o “-17 + 38 = 21”, y enunciados que no cuentan como proposición lógica, como un saludo o una orden, porque no tienen valor de verdad. Esa distinción es clave: en programación, no toda frase sirve como condición; solo las que pueden evaluarse.

### **conectores lógicos**
El documento explica tres operadores básicos: 

**AND (∧)** o conjunción, que exige que ambas proposiciones sean verdaderas
**OR (∨)** o disyunción, que resulta verdadera si al menos una lo es 
**NOT (¬)** o negación, que invierte el valor lógico. 

El material pone ejemplos cotidianos para que entiendas que esto no es solo teoría de pizarrón, sino la materia prima de los `if`, validaciones y filtros en código.

### **tablas de verdad**
cómo se evalúa cada operador con valores **V/F** o **1/0**, y deja claro que cada conector tiene su propia tabla. 

Para conjunción, solo sale verdadero cuando ambas entradas lo son
para disyunción, basta con una verdadera 
para negación, el valor se invierte

Si esto no se entiende bien, después un condicional en un programa puede quedar como una puerta con bisagras rotas: parece cerrar, pero deja pasar todo.

- #### **proposiciones condicionales**
	expresadas como **p → q**, leídas como “si p, entonces q”. El documento lo trabaja con ejemplos que muestran cómo una condición implica otra, y usa tablas de verdad para ver cuándo la implicación es verdadera o falsa. Aquí ya estás entrando al corazón de la lógica de decisión que luego usarás en estructuras condicionales.

	- **bicondicional** **p ↔ q**, que significa “p si y solo si q”. Esta idea sirve para expresar equivalencia lógica: la proposición es verdadera cuando ambas partes coinciden en verdad o falsedad. Es un concepto fino, pero muy útil cuando quieres modelar reglas donde dos condiciones deben alinearse exactamente.

### tres resultados globales de las tablas de verdad

**tautología:** Una tautología siempre da verdadero
**contradicción:** una contradicción siempre da falso 
**contingencia:** una contingencia depende de los valores asignados

Esto es oro puro para programación, porque te enseña a distinguir entre una regla que siempre se cumple, una que nunca se cumple y una que depende del contexto.

En resumen, estas páginas te están entrenando para esto: **convertir lenguaje natural en lógica formal**. Primero aprendes a identificar qué enunciados sí pueden evaluarse, luego a combinarlos con operadores y finalmente a verificar si la expresión lógica completa tiene sentido. Es el puente entre hablar de problemas y escribir condiciones correctas sin dispararte al pie.


## Metodología de algoritmos

- Aquí el documento te enseña que un algoritmo no es solo una lista de pasos bonitos; es una solución que debe pasar por 

	**análisis
	diseño
	implementación 
	validación**

- La lógica del bloque es: 

	- **primero entiendes el problema**
	- **luego diseñas la secuencia**
	- **después la traduces** 
	- **finalmente verificas que haga lo correcto**

- El texto insiste en que la solución debe ser

	- **realizable
	- comprensible 
	- precisa**

Eso significa que el algoritmo debe terminar, debe poder ser entendido por quien lo lea, y debe dar el mismo resultado si se ejecuta con los mismos datos.

## Pruebas de escritorio o trazas

Esta parte es la “radiografía” del algoritmo. muestra que las pruebas de escritorio sirven para simular la ejecución paso a paso y comprobar si la lógica realmente funciona. Normalmente se hacen en una tabla donde se van registrando las variables, condiciones y salidas conforme avanza el pseudocódigo. En el ejemplo del número, su cuadrado y su cubo, se ve claramente cómo el valor entra, se procesa y luego se refleja en las salidas. La idea es detectar errores antes de programar; es decir, corregir la idea antes de que el error se vuelva código.

## Diagramas de flujo

los **diagramas de flujo**, que son la versión gráfica del algoritmo. El documento explica que donde en pseudocódigo usas frases o instrucciones, en el diagrama usas figuras. También resalta que un diagrama de flujo ayuda a ver con claridad la secuencia, el inicio, el procesamiento y el final. En el ejemplo del número entero, el flujo es simple: pedir dato, leer dato, mostrar dato. En el ejemplo del cuadrado y el cubo, ya se ve cómo el diagrama organiza el cálculo y la salida de resultados.

## Uso de identificadores y palabras reservadas

cómo nombrar bien las cosas. Te dice que los identificadores deben ser 

- **descriptivos 
- **nemotécnicos**
- **sin tildes**
- **sin símbolos raros** 
- **sin palabras reservadas**.

También explica que 

una variable es un contenedor de datos que puede cambiar
una constante conserva su valor

Además aparecen los **contadores**, que son variables que se incrementan con un valor constante, y se menciona que los nombres deben ayudar a entender el propósito del dato, no a ocultarlo. Esto es importantísimo porque muchos errores no nacen de la lógica, sino de nombres mal puestos que vuelven el algoritmo un pantano.

## Operadores y jerarquía en los operadores

Este tramo también comienza a preparar el terreno para programar expresiones correctas. El material clasifica los operadores en 

- **aritméticos
- alfanuméricos
- relacionales 
- lógicos** 

Luego explica su **jerarquía de evaluación**: 

- **primero paréntesis**
- **después signos**
- **potencias** 
- **raíces**
- **multiplicación y división**
- **después suma y resta** 

más adelante concatenación, relacionales y operadores lógicos. El ejemplo de la expresión matemática muestra que la computadora no resuelve “como uno cree”, sino siguiendo una prioridad estricta. Esa prioridad es la razón por la que una expresión mal escrita puede dar un resultado inesperado aunque “se vea bien”.

## 6) Estructura secuencial

es la forma más básica de resolver un problema en programación: una instrucción después de la otra, sin decisiones ni repeticiones. El documento la presenta como una línea de flujo donde las acciones se ejecutan en orden. El ejemplo del área de un triángulo rectángulo muestra el patrón completo: pedir base y altura, calcular el área y mostrar el resultado. Aquí ya ves el esqueleto real de un programa simple: entrada, proceso y salida.

