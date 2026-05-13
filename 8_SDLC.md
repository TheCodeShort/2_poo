![[2_sdlc.png|697]]
# 1_**Teoría General de Sistemas (TGS)**

es la base "invisible" de cualquier software. Antes de escribir una sola línea de código en tu app, la TGS te obliga a pensar en **cómo encaja tu app en el mundo real.**

Partes clave que debes considerar de la TGS antes de empezar a crear tu app:

1. **El Objetivo del Sistema (Teleología)**

	- Un sistema no existe porque sí, existe para cumplir un fin.

		- **En tu app:** El objetivo no es solo "hacer una web", es **"Garantizar la disponibilidad de los equipos mediante un historial trazable"**. Si una función no ayuda a ese objetivo, no debería estar en el sistema.

2. **Los Límites o Fronteras (Ambiente)**

	- Debes decidir qué queda dentro y qué queda fuera.
	
		- **Consideración:** ¿Tu app se conectará con el sistema de contabilidad de la empresa? ¿O será una isla aparte? Definir la frontera te evita el "scope creep" (que el proyecto crezca sin control y nunca termines).

3. **Entropía vs. Homeostasis (El equilibrio)**

	- **Entropía:** Es el desorden natural. En tu app, la entropía es que los usuarios olviden llenar datos o que la base de datos se llene de basura.
	
	- **Homeostasis:** Es la capacidad del sistema de mantenerse estable.

	- **Aplicación:** Debes crear **validaciones**. Si un usuario intenta subir un reporte sin poner el serial del equipo, el sistema debe "defenderse" y no dejarlo pasar para evitar el desorden (entropía).

4. **Sinergia (El todo es más que las partes)**

	- Un sistema tiene sinergia si sus componentes juntos logran algo que solos no podrían.
	
		- **En tu app:** Una lista de equipos es útil. Un historial de daños es útil. Pero la **Sinergia** ocurre cuando el sistema cruza ambos y te dice: _"Ojo, este modelo de laptop siempre falla a los 6 meses"_. Eso es información que un papel suelto no te daría.

5. **Equifinalidad**

	- Dice que puedes llegar al mismo resultado por distintos caminos.
	
		- **Consideración:** Puedes generar el reporte en PDF desde el navegador o enviarlo por correo. La TGS te dice que no te cases con una sola forma; lo importante es que el **Output** (la salida) llegue a quien la necesita.
		
6. **Enfoque de Sistemas**[[SDLC_sofware.pdf#search=Enfoque de sistemas|SDLC_sofware, p.8]]
	- es dejar de mirar solo "el botón" y mirar "para qué sirve el botón en el mundo real".
	
	- Para que tu app no sea "una más", el **Enfoque de Sistemas** te hace analizar estos tres puntos (que están en el PDF):

		1. **Interdependencia:** Si cambias el color a "Rojo Brillante" a las 3 de la mañana en el hospital, ¿qué pasa? Despiertas al paciente. El color (tu app) afecta al sueño (el sistema mayor).
		2. **Ambiente:** El "mundo" donde vive tu app. Si la empresa que te contrata usa tablets viejas, tu app de colores no puede ser pesada. El ambiente dicta cómo debe ser tu software.
		3. **Objetivo (Lo que quiere la empresa):** La empresa no quiere "colores", quiere **"clientes felices"**. Si tu app ayuda a que el cliente esté feliz, entonces tu sistema es exitoso.
	
	- Definir el Sistema (Poniéndole nombre y forma):
	
7.  **"Definiendo los sistemas"**, se refiere a que debes ponerle límites.
	
	- **Si tu sistema de colores es para el hospital:**
		- **Entrada:** Hora del día y estado del paciente.
		- **Proceso:** Algoritmo que elige colores suaves.
		- **Salida:** Pantalla iluminada correctamente.
		- **Límite:** La app solo controla las luces de las habitaciones, no las de los pasillos.
	
	- ==es como ponerle una "cédula de identidad" a lo que vas a construir==. No basta con decir "es una app"; tienes que definir sus características para saber cómo se va a comportar.

	- sistema se define por **cuatro elementos clave**. Vamos a verlos con tu ejemplo de la **App de Equipos**:
	
		1. Los Componentes (Las piezas)
		
			Son las partes identificables que trabajan juntas. Sin una, el sistema falla.
			
			- **En tu app:** La base de datos, el formulario de registro, el motor que genera el PDF y el usuario que mete la información.
			- _Si quitas la base de datos, las otras piezas no tienen dónde guardar nada._
		
		2. La Estructura (El orden)
		
			Es la forma en que esas piezas se conectan. No están tiradas al azar.
			
			- **En tu app:** El usuario **no** va directo al PDF. Primero pasa por el "Componente de Registro", este envía los datos a la "Base de Datos", y finalmente el "Generador de PDF" consulta esa base. Esa "escalera" de pasos es la estructura.
		
		3. Las Funciones (Lo que hacen)
		
			Es la acción que realiza cada componente para procesar las entradas.
			
			- **En tu app:** La función del formulario es **validar** (que no metan letras donde van números de serial). La función del historial es **organizar** por fechas.
		
		4. La Integración (El pegamento)
		
			Es lo que hace que todas las partes se sientan como una sola cosa y no como cuatro programas distintos. Es el sentido de unidad.
			
			- **En tu app:** Es cuando el reporte PDF muestra exactamente la foto que el técnico subió hace un mes. Todo está amarrado.
		
	- ¿Por qué esto es vital?
	
		- **Los Sistemas de Información (SI)**. Define que un software no es solo código, sino un sistema que:
			
			1. **Recibe datos** (Serial del equipo).
			2. **Almacena datos** (En el disco duro).
			3. **Procesa datos** (Calcula cuánto tiempo pasó desde el último daño).
			4. **Distribuye información** (Manda el reporte al jefe).
		
		- **En resumen:** Definir el sistema es decir: "Mi app tiene estas piezas (componentes), que se conectan así (estructura), para hacer esto (funciones) y que todo funcione como uno solo (integración)".

8. **Clasificación de los Sistemas** 

	- es fundamental porque te enseña que no todos los sistemas son iguales ni se construyen de la misma forma.

	- Saber clasificar tu sistema te sirve para elegir las herramientas de programación adecuadas. El documento los divide en tres grandes categorías principales:


	1. **Según su relación con el Medio Ambiente**
	
		Esta parte te dice qué tanto "habla" tu app con el mundo exterior.
		
		- **Sistemas Abiertos:** Intercambian materia, energía e información con el ambiente.
		    - _Tu app de equipos es un Sistema Abierto:_ Recibe datos de los técnicos, se conecta a internet y genera reportes para el jefe. Se adapta al cambio.
		- **Sistemas Cerrados:** No intercambian nada con el exterior. Son teóricos (como un experimento de física sellado al vacío). En software, casi nada es puramente cerrado.
	
	2. ***Según su Naturaleza (De qué están hechos)**
	
		- **Sistemas Concretos (Físicos):** Son las cosas que puedes tocar.
		    - _Ejemplo:_ Las laptops, herramientas y servidores donde correrá tu app.
		    
		- **Sistemas Abstractos (Conceptuales):** Son ideas, planes, hipótesis o, en nuestro caso, **el código fuente y los algoritmos**.
		    - _La magia ocurre cuando lo Abstracto (tu software) controla lo Concreto (el mantenimiento de las laptops)._
	
	3. **Según su Origen**
		
		- **Sistemas Naturales:** Creados por la naturaleza (el cuerpo humano, el clima).
		- **Sistemas Artificiales:** Creados por el hombre.
		    - _Tu app es un Sistema Artificial:_ Fue diseñado con un propósito específico por un programador.
	
	
	- ¿Para qué sirve esto en tu proyecto?
	
		- **Para definir el tipo de arquitectura.**
		
			Si clasificas tu sistema de equipos, obtienes esta "ficha técnica":
			
			1. Es un sistema **Artificial** (tú lo creas).
			2. Es un sistema **Abierto** (necesita internet y datos de usuarios).
			3. Es un sistema **Abstracto** (es software) que maneja un sistema **Concreto** (el inventario físico).
		
			**¿Ves la utilidad?** Si no sabes que tu sistema es "Abierto", podrías olvidar programar la conexión a internet o la base de datos, y tu app quedaría aislada e inútil.
			
	1. **Según su Jerarquía (La jerarquía de "las cajas")**

		Esta parte te enseña que todo sistema es parte de algo más grande y contiene cosas más pequeñas.
		
		- **Subsistema:** Son las partes internas. Son sistemas con su propio objetivo, pero que sirven al sistema mayor.
		    - _En tu app:_ El "Módulo de Reportes" o el "Sistema de Login".
		- **Sistema:** Es el protagonista, el objeto de estudio actual.
		    - _En tu app:_ La aplicación de gestión de equipos completa.
		- **Supersistema (o Suprasistema):** Es el entorno más grande que contiene al sistema.
		    - _En tu app:_ La empresa completa o la infraestructura de internet donde vive tu app.


	2. **Según su Constitución (Lo que "son")**
	
		- **Sistemas Reales o Físicos:** Cosas que existen en el mundo material, ocupan espacio y se pueden tocar.
		    - _Ejemplo:_ El servidor (la computadora física) donde guardas la información y los equipos (laptops, motores) que estás registrando.
		- **Sistemas Ideales:** Son construcciones simbólicas, como la lógica o las matemáticas.
		    - _Ejemplo:_ Los números, las fórmulas para calcular el tiempo de vida de un equipo.
		- **Abstracciones (Sistemas Abstractos):** Es el software. Son planes o ideas organizadas.
		    - _Ejemplo:_ El código fuente que escribes. No lo puedes tocar con las manos, pero existe y hace que las cosas funcionen.


	3. **Según su Origen**
	
		- **Sistemas de la Naturaleza:** Surgieron sin intervención humana (el sistema solar, una célula).
		- **Sistemas Artificiales:** Hechos por el hombre para cumplir un propósito.
		    - _En tu app:_ Es 100% artificial, creada para administrar datos.
		- **Sistemas Mixtos:** Combinan elementos naturales y artificiales.
		    - _Ejemplo:_ Una represa hidroeléctrica (usa el agua natural pero con turbinas humanas).


	4. **Según su Intercambio con el Entorno (¡Este es el más importante!)**
		
		- **Sistemas Cerrados:** No intercambian información ni energía con el exterior. Se desgastan hasta morir (entropía).
		    - _Dato:_ En software casi no existen, porque un programa que no recibe datos de nadie no sirve para nada.
		- **Sistemas Abiertos:** Son los que "viven" gracias a que reciben cosas del exterior y entregan resultados.
		    - _En tu app:_ Es **Abierta** porque necesita que un técnico le meta datos (Input) y ella entrega reportes (Output). Si cortas la comunicación con el exterior, la app "muere" funcionalmente.

9. **Análisis de los procesos a nivel de negocio**

	1. **El Levantamiento de Información (¿Qué pasa hoy?)**

		Antes de programar, debes ser un "detective". El PDF menciona que debes identificar cómo fluye la información.
		
		- **En tu app:** Imagina que vas a la oficina y ves que el técnico anota los daños en un cuaderno y luego le toma una foto para mandarla por WhatsApp. Eso que viste es el **Proceso Actual**.
		- **Por qué importa:** Si no sabes que usan WhatsApp, quizás olvides que tu app debe permitir "subir fotos" desde el celular.
		
	2. **Identificación de los Actores y Tareas**
	
		El análisis de negocio te obliga a separar quién hace qué:
		
		- **Responsabilidades:** Quién autoriza un mantenimiento, quién lo ejecuta y quién lo paga.
		- **Puntos de decisión:** Son los momentos donde el proceso puede tomar dos caminos. Por ejemplo: _"Si el arreglo cuesta más de $100, se pide aprobación al jefe; si cuesta menos, se arregla de inmediato"_. Tu software debe conocer estas reglas de negocio.
	
	3. **Análisis de "AS-IS" vs "TO-BE"**
	
		Este es un concepto técnico muy importante en el análisis:
		
		- **AS-IS (Como es):** Es el proceso actual (con errores, lento, en papel).
		- **TO-BE (Como será):** Es el proceso mejorado gracias a tu sistema (automático, rápido, con PDF).
		- **El objetivo:** Tu análisis debe demostrar que el "TO-BE" es más eficiente que el "AS-IS".
	
	4. **La Importancia de la Comunicación**
	
		El documento resalta que los analistas deben hablar con los dueños de los procesos (los empleados). Muchas veces, lo que el jefe cree que pasa es muy distinto a lo que el empleado realmente hace. El análisis de negocio busca esa **verdad única**.
		
	
	- ¿Para qué sirve esto en tu sistema de equipos?
		
		Si saltas este paso y vas directo a programar, podrías crear una app muy bonita que:
		
		1. Pide datos que nadie tiene.
		2. No genera el reporte que el jefe necesita para el presupuesto.
		3. Es más lenta que el cuaderno que usaban antes.
		
		**En resumen:** El análisis de procesos de negocio es entender la **lógica del cliente** para traducirla a **lógica de programación**.

10. **Procesos**
	![[3_flujo.png]]

	1. **Identificar procesos**
	
		Es el punto de partida. Aquí haces la lista de todo lo que sucede.
		
		- **En tu ejemplo:** Identificas que hay un proceso de "Ingreso de equipo", otro de "Reporte de falla" y otro de "Cierre de mantenimiento".
		
	2. **Determinar el equipo de trabajo**
	
		Aquí defines quiénes van a participar en el análisis. No solo eres tú como programador; necesitas a los que saben del tema.
		
		- **En tu ejemplo:** El equipo sería el jefe de sistemas, los técnicos de mantenimiento y tú. Ellos te dirán la verdad de cómo trabajan.
	
	3. **Generar el diagrama de los procesos de negocio**
	
		Es dibujar el "mapa" de cómo funcionan hoy (el proceso **AS-IS**).
		
		- **En tu ejemplo:** Dibujas: _"El técnico recibe la laptop -> busca un cuaderno -> anota el serial -> le avisa al jefe por correo"_. Es ver el camino que recorre la información.
		
	4. **Diagnóstico de cada proceso**
	
		Aquí es donde te pones crítico. Miras el diagrama anterior y buscas fallas, demoras o cuellos de botella.
		
		- **En tu ejemplo:** Te das cuenta de que el cuaderno se pierde, el correo al jefe se olvida y el historial no es fácil de consultar. **Diagnóstico:** El proceso actual es lento y poco confiable.
		
	5. **Puntos de mejora**
	
		Es la lluvia de ideas. ¿Cómo arreglamos lo que diagnosticamos mal?
		
		- **En tu ejemplo:** "Usemos una base de datos centralizada", "Que el sistema mande el correo automático", "Que se genere un PDF al instante".
	
	6. **Nuevo proceso mejorado**
	
		Aquí dibujas el nuevo mapa (el proceso **TO-BE**), pero ya con tu app incluida. Es el proceso ideal.
		
		- **En tu ejemplo:** _"El técnico escanea el serial -> la app muestra el historial -> el técnico registra la falla -> la app genera el PDF"_. ¡Mucho más eficiente!
		
	7. **Caso de estudio**
	
		Es cuando pones a prueba ese nuevo diseño en un escenario real para ver si funciona antes de terminar todo el desarrollo.
		
		- **En tu ejemplo:** Haces una prueba con una sola laptop vieja para ver si el técnico entiende la app y si el PDF sale con la información correcta.
		
11. **Caja de herramientas**
	
	![[4_caja_de_herramientas.png]]

	1. **Técnicas de recolección de datos (¿Cómo obtengo la info?)**

		Aquí es donde decides qué método usar para que la gente te cuente la verdad sobre su trabajo.
		
		- **Encuestas:** Mandas un formulario a todos los técnicos (ej: "¿Qué es lo que más les molesta del proceso actual?").
		- **Entrevistas:** Te sientas con el jefe de mantenimiento a hablar frente a frente.
		- **Focus Group:** Reúnes a varios empleados para que discutan ideas.
		- **Observación:** Te quedas callado en un rincón viendo cómo el técnico repara una laptop y anota los datos. **(Esta es la más honesta, porque ves lo que realmente hacen, no lo que dicen que hacen).**

	2. **Insumos (¿Qué información debo recolectar?)**
	
		Una vez que aplicas las técnicas anteriores, lo que buscas es obtener estos 7 elementos para entender la empresa:
		
		- **Misión/Visión/Objetivos:** ¿A qué se dedica la empresa? No es lo mismo un hospital que un taller mecánico.
		- **Roles y Organigrama:** ¿Quién manda a quién? Así sabes quién debe tener permisos de "Administrador" en tu app.
		- **Gestión Documental:** ¿Qué papeles usan hoy? (Facturas, manuales, hojas de vida de los equipos).
	
	3. **Procesos y subprocesos (¿Cómo lo aterrizo al software?)**
	
		Con todo lo anterior, ya puedes hacer una **aproximación inicial** a los detalles técnicos de tu app:
		
		- **Lugares:** ¿Desde dónde se usará la app? (En el taller, en la oficina, en la calle).
		- **Actores:** Los usuarios reales (Técnico, Jefe, Cliente).
		- **Tiempos:** ¿Cuánto tarda un reporte en ser aprobado?
		- **Costos:** ¿Cuánto se gasta la empresa hoy por no tener tu sistema?
## 1_Mas del TGS [[SDLC_sofware.pdf#search=Teoría de sistemas|SDLC_sofware, p.242]]

entra en **tres ideas encadenadas**: **diagnóstico tecnológico**, **búsqueda de soluciones** y **licencias de software**. Es como un pipeline de análisis: primero miras el estado del sistema, luego propones salidas, y después revisas qué tan legal y reutilizable es el software que vas a usar o crear.

| Sección                   | Qué dice el libro                                                                                                                                                                                  | Para qué sirve                                                    |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| **Diagnósticos**          | El diagnóstico tecnológico es una observación colaborativa entre empresa y expertos para definir necesidades y potencial tecnológico; revisa fortalezas, debilidades, brechas internas y externas. | Saber en qué estado está la empresa antes de proponer mejoras.    |
| **Soluciones**            | Propone una técnica creativa basada en preguntas para analizar el problema: describir la situación, definir el problema, analizar opciones y tomar decisiones.                                     | Generar alternativas reales en vez de quedarse con una sola idea. |
| **Licencias de software** | Explica que una licencia regula el uso y distribución del software, y empieza a clasificar tipos como copyleft, software libre, shareware y propietario.                                           | Entender qué se puede hacer legalmente con un programa.           |

### 1) Diagnósticos

El libro define el **diagnóstico tecnológico** como una actividad de observación colaborativa entre la empresa y expertos internos o externos. Su meta es identificar las **necesidades** y el **potencial tecnológico** de la empresa, viendo tanto el lado **interno** como el **externo**. Internamente se inventarían y evalúan recursos tecnológicos; externamente se revisa a competidores y la brecha frente a líderes del sector.

La idea de fondo es detectar **capacidades que ya existen** y **capacidades que faltan**. En términos simples, el diagnóstico responde:  
**“¿Qué tengo hoy y qué me hace falta para mejorar?”**

### 2) Soluciones

Después el libro pasa a una técnica de **solución creativa de problemas**. La estructura que propone es muy clara:

- describir la situación,
- definir el problema,
- analizar el problema con preguntas tipo “¿qué se puede sustituir?”, “¿combinar?”, “adaptar?”, “modificar?”, “eliminar?”, “invertir?”,
- y finalmente tomar decisiones con criterios de evaluación.

Esto no es teoría decorativa: el libro está enseñando a **abrir el problema** antes de cerrarlo con una solución. Es como cuando en programación no te lanzas a escribir una función sin antes definir entradas, salida y casos límite. Primero entiendes el problema, luego diseñas la respuesta.

### 3) Licencias de software

Luego inicia el bloque de **licencias de software**, donde el texto dice que una licencia es un **acuerdo esencial** que regula el uso y la distribución de obras intelectuales en tecnología.

Ahí aparecen varias categorías:

|              Tipo               |                                                Qué permite                                                |
| :-----------------------------: | :-------------------------------------------------------------------------------------------------------: |
|          **Copyleft**           | Protege las libertades del software libre y exige que las modificaciones mantengan condiciones similares. |
| **Software libre sin copyleft** |                           Permite modificar y redistribuir bajo otros términos.                           |
| **Software libre con copyleft** |                          Obliga a conservar las mismas condiciones de licencia.                           |
|          **Shareware**          |                          Deja usar una versión limitada o temporalmente gratis.                           |
|         **Propietario**         |                              Restringe copia, redistribución y modificación.                              |

### Lo más importante de esas páginas

El capítulo te está preparando para pensar como analista o gestor de proyectos:

```
diagnóstico → problema → alternativas → decisión → licencia correcta
```

No basta con “hacer software”; hay que saber **qué necesita la empresa**, **cómo resolverlo**, y **bajo qué condiciones legales se puede usar o distribuir el resultado**.

### 4_Normativa (**normas legales**)

Regulan el uso del software para evitar sanciones, multas y problemas de propiedad intelectual. El texto abre esa sección diciendo precisamente que, cuando se implementa un software, su uso debe regirse por una normativa que previene futuras sanciones o multas.

- ### Qué quiere decir “normativa” aquí

En este contexto, **normativa = reglas legales que debes cumplir al usar, instalar, distribuir o comercializar software**.  
O sea, el libro te está diciendo: no basta con que el software funcione; también debe ser **legal**.

- ## La idea central de la sección

El documento se enfoca en Colombia y menciona la 
**. Según el texto, esta ley obliga a las empresas a presentar un **informe de gestión** con información sobre el progreso del negocio y su estado financiero, administrativo y jurídico, y ese informe debe demostrar cumplimiento de normas relacionadas con **propiedad intelectual** y **derechos de autor**.

- ## Quién vigila eso

El libro dice que la **DIAN** puede realizar auditorías durante visitas a las empresas para verificar que el software instalado en los equipos cumpla legalmente.

- ## Qué pasa si no se cumple

La sección enumera consecuencias fuertes por incumplir la Ley 603 de 2000:

| Consecuencia                                  | Qué significa                                                                         |
| --------------------------------------------- | ------------------------------------------------------------------------------------- |
| Sanciones a administradores                   | Multas de hasta **200 SMMLV**                                                         |
| Delito patrimonial                            | Posible prisión de **2 a 5 años**                                                     |
| Infracción de derechos patrimoniales de autor | Posible prisión de **4 a 8 años**                                                     |
| Sanciones por evasión                         | La DIAN puede sancionar por evasión de impuestos derivados del uso de software ilegal |

- ## Entonces, ¿por qué está en el capítulo de licencias?

Porque la licencia de software no es solo un texto técnico: es también una **forma legal de autorizar uso, distribución o modificación**. El libro más adelante explica que una licencia es un contrato entre desarrollador y usuario donde se definen derechos y obligaciones, y que el autor decide qué permite hacer con el software.

- ## Cómo entenderlo en una frase

La sección 2.1 te está diciendo:

```
Antes de elegir o instalar software,verifica si su uso es legal,qué licencia tieney si tu empresa cumple la normativa colombiana.
```

- ## Ejemplo simple

Si una empresa instala programas sin licencia:

- puede estar violando derechos de autor,
- puede quedar expuesta a auditorías,
- y puede enfrentar sanciones legales y tributarias.

- ## Lo que el libro quiere que aprendas

No solo quiere que sepas qué es freeware, shareware o software propietario. Primero te coloca esta advertencia legal para que entiendas que **la gestión de software también tiene una dimensión jurídica**. Después de eso, ya sí entra a los tipos de licencia.

Si lo quieres resumir en una línea brutalmente clara:

**“Normativa” aquí significa las leyes que obligan a usar software con licencias válidas y a responder legalmente por su cumplimiento.**






# 2_Ingenieria de Requisitos [[SDLC_sofware.pdf#search=Validación de requisitos|SDLC_sofware, p.285]]

1. **¿Qué es la Ingeniería de Requisitos?**

	- **Como base de acuerdos:** Es crear una especificación (un documento) clara y sin errores que sirva para que todos (clientes y desarrolladores) estén de acuerdo en qué hará el sistema.
	
	- **Como proceso de descubrimiento:** No es solo sentarse a escribir; es "estudiar las necesidades" para entender qué se requiere realmente.
	
	- **Como gestión del cambio:** Los sistemas vivos cambian. La IR se encarga de que esos cambios no vuelvan loco al equipo, manteniendo la **trazabilidad** (saber de dónde viene cada idea).

> **El toque TGS:** La IR busca que el "Sistema Software" se integre con éxito en su "Supersistema" (el entorno de negocio o la empresa) [[SDLC_sofware.pdf#search=IR|SDLC_sofware, p.25]].

2. **Las 4 Etapas Clave**

	- Para que no se escape nada, el proceso se divide en cuatro pasos (pp. 26-28):
	
		1. **Elicitación (Descubrimiento):** Es la investigación de campo. Aquí hablas con el cliente para sacar a la luz las necesidades "ocultas" o implícitas.

		2. **Análisis:** Aquí es donde entra la lógica. Miras lo que recolectaste y buscas conflictos (por ejemplo, si el jefe pide algo que el empleado dice que es imposible). Se busca entender el "dominio del problema".

		3. **Especificación:** Es "pasar en limpio". Se documenta todo de forma técnica (usando estándares como el **UML** o casos de uso) para que los programadores sepan qué construir.

		4. **Validación:** Es el control de calidad. ¿Lo que escribimos es realmente lo que el usuario necesita? Si no, se corrige antes de empezar a programar (ahorrando mucho dinero).

3. **¿Qué es exactamente un "Requisito"?**

	No es solo un deseo; según el estándar IEEE, es una **condición o capacidad** que el sistema debe tener para que el usuario logre un objetivo (p. 42).
	
	Características de un buen requisito (Filtros de calidad):
	
	Para que un requisito sea útil, el documento dice que debe ser (pp. 43-44):
	
	- **Necesario:** Si lo quitas, ¿pasa algo malo? Si no, fuera.
	- **Factible:** Que se pueda hacer con el dinero y tiempo que hay.
	- **Verificable:** Debes poder probar si se cumplió o no.
	- **Rastreable:** Debes poder seguirle la pista desde que nació como idea hasta que se volvió código.

4. **Tipos de Requisitos**

	El documento los clasifica principalmente por quién los entiende (p. 44):
	
	- **Requerimientos de Usuario:** Escritos en lenguaje sencillo, para que el cliente los lea y diga "sí, eso es lo que quiero".
	- **Requerimientos de Sistema:** Mucho más técnicos y detallados, dirigidos a los desarrolladores.

Conexión con el Ciclo de Vida (SDLC)

La Ingeniería de Requisitos no vive sola; es la **Fase de Análisis** dentro del ciclo de vida del software (p. 41). Es la que "dirige" todo el proyecto. Si fallas aquí, el diseño, la programación y las pruebas también fallarán, porque estarás construyendo la cosa equivocada.

- ## Técnicas e instrumentos para elicitar requisitos [[SDLC_sofware.pdf#search=Técnicas e instrumentos para elicitar requisitos|SDLC_sofware, p.56]]

	- La elicitación de requisitos implica usar técnicas clave como la entrevista estructurada o no estructurada y la encuesta mediante cuestionarios para recopilar información detallada del cliente. Además, técnicas como la observación directa y sesiones grupales permiten identificar necesidades reales y alcanzar consensos entre los interesados. 
		
		1. **Técnicas para la Elicitacitar** 
		
			1. **Tipos de Entrevista**
			
				- El analista debe elegir el formato según lo que necesite descubrir:
	
					- **Estructuradas:** [[SDLC_sofware.pdf#search=Entrevista estructurada|SDLC_sofware, p.59]]Tienen un cuestionario rígido y definido. Son ideales para confirmar datos específicos o cuando el tiempo es muy limitado. [[SDLC_sofware.pdf#search=Entrevista Estructurada|SDLC_sofware, p.112]]
					
					- **Semiestructurada:** [[SDLC_sofware.pdf#search=Entrevista semiestructurada|SDLC_sofware, p.59]] Es un encuentro que tiene una **guía temática** (un guion base de preguntas), pero que permite al entrevistador desviarse del camino si surge un dato interesante o una necesidad que no estaba prevista.
					
					- **No estructuradas:** [[SDLC_sofware.pdf#search=Entrevista no estructurada|SDLC_sofware, p.60]] Son conversaciones abiertas. Sirven al inicio del proyecto para que el usuario hable libremente y así descubrir problemas u oportunidades que tú no habías imaginado.

				1. **El Proceso Profesional (Paso a Paso)**
				
					Para que una entrevista sea efectiva, el documento sugiere seguir este flujo:
					
					- **Preparación (Antes):** No puedes llegar en blanco. Debes leer sobre el dominio del problema (el negocio de plantas), definir los objetivos de la reunión y seleccionar a los entrevistados clave.
					- **Apertura (Inicio):** Aquí se establece la confianza. Explicas el propósito de la entrevista y por qué la opinión de esa persona es vital.
					- **Cuerpo (Desarrollo):** Es el intercambio de información. Un analista "pro" usa preguntas abiertas (¿Cómo hace esto hoy?) y cerradas (¿Necesita que el sistema envíe un correo al cliente?).
					- **Cierre (Final):** Se hace un resumen de lo hablado para confirmar que entendiste bien y se definen los siguientes pasos.
	
				2. Las 5 Reglas de Oro del Entrevistador
					
					Para que no te pase lo de "pensar que entendí y luego no era así", el texto enfatiza:
					
					1. **Escucha activa:** Deja hablar al usuario. El protagonista es él, no tu solución técnica.
					2. **Evitar tecnicismos:** Si le hablas de "bases de datos SQL" a la dueña de la tienda de plantas, la vas a bloquear. Usa su lenguaje.
					3. **Documentación inmediata:** Toma notas o graba (con permiso). La memoria es traicionera y los detalles se pierden en horas.
					4. **Confirmación:** "¿Entonces, lo que usted me dice es que si la planta no tiene stock, el sistema debe sugerir una similar?". Esto evita retrabajos.
					5. **Neutralidad:** No sugieras respuestas. Si preguntas "¿Verdad que quiere un botón rojo?", el cliente dirá que sí solo por compromiso.
				
				3. ¿Por qué es tan importante en la Elicitación?
				
					Porque es el momento donde descubres los **requisitos ocultos**. El usuario a veces asume que "es obvio" que el sistema debe hacer algo, y no lo dice. En la entrevista, mediante el cara a cara, puedes notar dudas o gestos que te indican que hay algo más que investigar.
					
			2. **Encuesta**
		
				- la **encuesta** es la técnica "hermana" de la entrevista, pero con un enfoque totalmente distinto: aquí buscas **cantidad y estadísticas**, no necesariamente profundidad emocional.
	
				- Aquí tienes la explicación completa y técnica de cómo se maneja en la ingeniería de requisitos:
	
				1. **¿Qué es y para qué sirve?**
				
					Es una técnica de recolección de datos masiva que utiliza un **cuestionario predefinido**. A diferencia de la entrevista (que es uno a uno), la encuesta te permite llegar a **cientos de personas al mismo tiempo**.
				
				2. **Su uso principal:**
				
					- Identificar tendencias o necesidades comunes en grupos grandes de usuarios.
					- Validar si una idea que surgió en una entrevista es compartida por la mayoría.
					- Obtener datos cuantitativos (números, porcentajes).
	
				3. **Tipos de Cuestionarios (El corazón de la encuesta)**
				
					El documento diferencia dos formas de preguntar:
					
					- **Cuestionario Abierto:** El usuario escribe su opinión libremente.
					    - _Ventaja:_ Descubres cosas que no esperabas.
					    - _Desventaja:_ Es una pesadilla de analizar si tienes 200 respuestas; no puedes sacar una gráfica fácil de eso.
					    
					- **Cuestionario Cerrado:** El usuario elige entre opciones (Sí/No, Selección múltiple, Escala del 1 al 5).
					    - _Ventaja:_ Es "Pro" para el análisis. Puedes decir: "El 80% de los clientes de la tienda de plantas prefiere pagar con tarjeta".
					    - _Desventaja:_ Si olvidas poner una opción importante, el usuario no te la puede decir.
	
				
				4. Pasos para una Encuesta Exitosa
				
					Hacer una encuesta no es solo mandar un link de Google Forms; requiere rigor:
					
					1. **Definir el objetivo:** ¿Qué quieres saber exactamente? (Ej: ¿Les interesa a los clientes un sistema de puntos?).
					2. **Seleccionar la muestra:** No le mandas la encuesta a todo el mundo, sino a las personas que realmente usan el sistema (Stakeholders específicos).
					3. **Diseñar las preguntas:** Deben ser cortas, claras y sin "trampas" que induzcan la respuesta.
					4. **Prueba piloto:** Antes de mandarla a 500 personas, pásasela a 2 o 3 conocidos para ver si se entiende.
					5. **Distribución y Análisis:** Se recolectan los datos y se crean gráficas para tomar decisiones basadas en datos reales, no en suposiciones.
		
	
				- **El "Pro-tip" del documento:**
				
					El texto sugiere que los cuestionarios deben ser **anónimos** para que la gente responda con total honestidad, especialmente si estás evaluando un sistema que ya existe y que a los empleados les molesta usar.
						
			2. **Observación** [[SDLC_sofware.pdf#search=Ficha de Observación|SDLC_sofware, p.114]]
			
				1. La **observación** es, quizás, la técnica más reveladora de todas porque, como dice el dicho: _"La gente dice una cosa, pero hace otra"_. En el documento (páginas 62-63), se describe como la técnica donde el analista se convierte en un "detective" para ver el proceso en vivo.

				2. **¿Qué es y por qué es necesaria?**
				
					Consiste en ver cómo los usuarios realizan sus tareas en su entorno real de trabajo. Es fundamental porque muchos usuarios tienen **conocimiento tácito**: hacen cosas tan automáticamente que olvidan mencionarlas en una entrevista o encuesta.
				
				3. **Los dos tipos principales de observación**
				
					El documento distingue dos formas de ejecutarla:
				
					- **Observación Pasiva (Shadowing):** Te sientas a un lado y miras. No interrumpes, no preguntas, solo anotas.
					    - _Uso pro:_ Sirve para medir tiempos reales y ver los errores que el usuario comete y "soluciona" por instinto (como darle tres veces a una tecla porque la pantalla se bloquea).
					    
					- **Observación Activa:** Mientras el usuario trabaja, tú le pides que explique qué está haciendo.
					    - _Uso pro:_ Es excelente para entender el "porqué" de cada acción en el momento exacto en que ocurre.
					- ![[14_tipo_observar.png]]
				
				4. **El proceso técnico: ¿Cómo se hace bien?**
				
					No es solo "mirar"; requiere un método:
					
					1. **Planificación:** Decidir qué procesos observar (ej. cómo se empaca y registra un pedido de plantas).
					2. **Preparación:** Obtener permisos (a nadie le gusta que lo vigilen sin saber por qué) y preparar una **lista de chequeo** o libreta de campo.
					3. **Ejecución:** Observar con objetividad. No debes juzgar al usuario ("lo está haciendo mal"), sino entender por qué el sistema actual lo obliga a hacerlo así.
					4. **Análisis:** Comparar lo que viste con lo que te dijeron en las entrevistas. Aquí es donde aparecen las famosas **"brechas"** (lo que el manual dice que se hace vs. lo que se hace de verdad).
				
				En resumen:
				
				La observación te permite capturar la **realidad cruda**. Mientras la entrevista te da la "teoría" del negocio, la observación te da la "práctica".
				
			3. **Sesiones grupales**
				1. **¿Qué son realmente?**

					No es una charla cualquiera; son reuniones estructuradas donde sientas en la misma mesa a personas de diferentes áreas (la dueña, el vendedor, el repartidor y el contador). El objetivo es que **todos se pongan de acuerdo** en un mismo lugar.

				2. **¿Por qué el documento dice que existen dos tipos?**
				
					El texto se enfoca en dos metodologías famosas:
					
					- **JAD (Joint Application Design - Diseño Conjunto de Aplicaciones):** Es una sesión muy formal. Hay un "facilitador" (tú, el analista) que guía la discusión para definir los requisitos del sistema rápidamente. Lo "pro" de JAD es que las decisiones se toman ahí mismo; nadie puede decir después "yo no sabía".
					- **Focus Groups:** Aquí buscas opiniones y sentimientos. Por ejemplo, reúnes a 5 clientes frecuentes de la tienda de plantas y les muestras un prototipo para ver qué les parece. No buscas decisiones técnicas, sino **reacciones y sugerencias**.
				
				3. **¿Por qué es "rara" o difícil de manejar?**
					
					Es compleja porque requiere que seas un mediador. Aquí surgen los problemas que no ves en una encuesta:
					
					- **Conflictos de interés:** El vendedor quiere que la web sea rápida, pero el contador quiere que pida mil datos para los impuestos. En la sesión grupal, esos dos tienen que pelear (en buenos términos) hasta llegar a un punto medio mientras tú tomas nota.
					- **Dinámicas de poder:** A veces el empleado no habla porque está el jefe delante. Un buen analista debe saber cómo hacer que todos opinen.
				
				4. **Elementos clave de una sesión (según el manual):**
					
					- **Facilitador:** Tú, que diriges y no dejas que se desvíen del tema.
					- **Secretario (Escribano):** Alguien que anota todo (o grabas la sesión).
					- **Participantes:** Solo la gente que realmente tiene algo que aportar.
				
				**En resumen:** Las sesiones grupales sirven para que el software no sea una colcha de retazos de opiniones sueltas, sino una **solución unificada** que todos aceptan.

- ## Herramientas para captura de requisitos
	
	1. son los artefactos que convierten lo que se descubrió en la elicitación en una representación más clara, visible y usable para el proyecto. El texto dice que sirven para capturar requisitos potenciales de un sistema nuevo o de una actualización, y presenta tres principales: **diagrama de casos de uso, historias de usuario y storyboard**.

	- ## Qué objetivo tienen
	
		- La idea no es solo “anotar cosas”, sino **capturar requisitos de forma entendible para que luego puedan analizarse, priorizarse, diseñarse y validarse**. En otras palabras, estas herramientas son el puente entre la conversación con el usuario y la documentación técnica del sistema.

	- ## Las tres herramientas principales

|Herramienta|Qué representa|Para qué sirve|
|---|---|---|
|**Diagrama de casos de uso**|Funciones del sistema y actores que las ejecutan|Identificar funcionalidades y quién interactúa con ellas|
|**Historias de usuario**|Necesidades breves vistas desde el usuario|Capturar requisitos de forma simple y ágil|
|**Storyboard**|Secuencia visual de interacción o proceso|Mostrar cómo se usará el sistema paso a paso|

1. **Diagrama de casos de uso**[[SDLC_sofware.pdf#search=Diagrama de casos de uso|SDLC_sofware, p.66]] [[SDLC_sofware.pdf#search=Diagrama de casos de uso|SDLC_sofware, p.129]]

	- El documento explica que este diagrama se usa al inicio del proyecto para visualizar **qué funcionalidades debe permitir el software** y **quiénes podrán ejecutarlas**. Sus componentes básicos son el **actor** y el **caso de uso**; el actor representa al usuario o rol, y el caso de uso representa una función del sistema. Además, no basta con dibujarlo: también debe incluirse la **documentación del caso de uso**, donde se detalla el flujo entre actor y sistema.

	- ### En simple
		
		Es como decir:
		
		```
		Actor -> hace algo -> Sistema responde
		```
	
	- ### Ejemplo del documento
	
		En el centro médico se mencionan casos como:
		
		- administrar datos de pacientes,
		- administrar tratamientos,
		- gestionar citas,
		- generar reportes.
		
	- ![[15_caos_uso.png]]

2. **Historias de usuario** [[SDLC_sofware.pdf#search=Historias de usuario|SDLC_sofware, p.202]]

	El documento dice que las historias de usuario se usan en métodos ágiles y son una **descripción breve de una funcionalidad tal como la percibe el usuario**. La estructura que propone Scrum es:
	
	```md
	Como <rol>
	Quiero <evento / acción>
	Para <funcionalidad / beneficio>	
	```
	
	- Para qué sirven
	
		Sirven para capturar necesidades de forma corta, clara y fácil de conversar con el equipo. El texto recalca que la historia no se queda sola: debe abrir una conversación para detallar solución, aclarar dudas y definir **criterios de aceptación**, que son los que luego permiten validar si la historia quedó terminada.
	
	- Ejemplo
		“Como cliente, quiero consultar productos para encontrar el que deseo comprar. 

|             Elemento             |                                                        Contenido                                                        |              Explicación              |
| :------------------------------: | :---------------------------------------------------------------------------------------------------------------------: | :-----------------------------------: |
|        **Rol (Como...)**         |                                                        Operario                                                         |    Quién necesita la funcionalidad    |
|    **Necesidad (Quiero...)**     |                                            Registrar una falla en el sistema                                            |       Acción que desea realizar       |
|     **Beneficio (Para...)**      |                                 Dejar trazabilidad del problema y notificar al técnico                                  | Valor o propósito de la funcionalidad |
| **Historia de usuario completa** | “Como operario, quiero registrar una falla en el sistema, para dejar trazabilidad del problema y notificar al técnico.” |   Historia redactada correctamente    |
|   **Criterio de aceptación 1**   |                                     El sistema debe permitir ingresar tipo de falla                                     |           Regla verificable           |
|   **Criterio de aceptación 2**   |                                  El sistema debe guardar fecha y hora automáticamente                                   |         Validación funcional          |
|   **Criterio de aceptación 3**   |                                      El sistema debe generar un número de reporte                                       |     Evidencia de registro exitoso     |
|   **Criterio de aceptación 4**   |                                        El técnico debe recibir una notificación                                         |     Resultado esperado del flujo      |
![[17_histo_ejemplo.png]]

1. **¿Qué es realmente una Historia de Usuario?**

	No es un "requisito técnico". Es una **descripción breve y simple** de una funcionalidad, contada desde la perspectiva de la persona que necesita esa mejora.
	
	El documento resalta que deben seguir la estructura de las **"3 C"**:
	
	- **Card (Tarjeta):** La frase escrita en una tarjeta física o digital.
	- **Conversation (Conversación):** Lo más importante. La tarjeta es solo una excusa para que el equipo hable con el cliente y entienda el "por qué".
	- **Confirmation (Confirmación):** Los criterios de aceptación (¿Cómo sabemos que ya quedó bien?).

2. **La estructura estándar (El "Cómo se escribe")**

	Para evitar confusiones, se usa siempre esta fórmula:
	 	
 - `Como (ROL), quiero (ACCIÓN) para (BENEFICIO)`
	
	- **Ejemplo práctico:**
	    - _Como_ Cliente de la tienda.
	    - _Quiero_ poder guardar productos en una "lista de deseos".
	    - _Para_ comprarlos después cuando tenga dinero.

3. **Los Criterios de Aceptación (La parte "confusa")**

	A menudo se confunden con la historia misma. Piensa en ellos como la **lista de verificación** del control de calidad.
	
	- _Historia:_ "Quiero una maleta para viajar".
	- _Criterios de Aceptación:_ Debe ser de color negro, tener 4 ruedas, pesar menos de 2kg y tener candado de seguridad. **Si no cumple todo eso, la historia no está terminada.**

4. **¿Cómo saber si una historia es buena? (Regla INVEST)**
	
	1. **I**ndependiente (que no dependa de otra para empezar).
	2. **N**egociable (se puede discutir el alcance).
	3. **V**aliosa (debe servirle de algo al usuario).
	4. **E**stimable (el programador debe saber cuánto tardará).
	5. **S**mall (Pequeña, que quepa en un ciclo de trabajo o Sprint).
	6. **T**estable (que se pueda probar).

---

3. **Storyboard**

	- El storyboard se presenta como un **prototipo visual**: una secuencia de imágenes que muestra cómo avanza un proceso o interacción dentro del sistema. El documento dice que permite crear vistas tempranas de manera rápida y barata, como si fuera un cómic que explica la experiencia del usuario. También resalta que ayuda a validar escenarios, es fácil de entender para el usuario y facilita incorporar cambios durante la validación.

	 - En simple
	
		- Es útil cuando quieres mostrar:
		
			- qué hace el usuario,
			- qué ve en pantalla,
			- qué pasa después,
			- cómo avanza la interacción.

	- ### Cómo van de la mano

		Estas tres herramientas no compiten; se complementan:
	
		```
		Elicitación   
		↓
		Captura inicial del requisito
		↓
		Casos de uso / Historias de usuario / Storyboard   
		↓
		Análisis y validación   
		↓
		Especificación final
		```
	
		primero entiendes el problema con técnicas como entrevista u observación, y luego usas estas herramientas para **registrar y representar** lo descubierto de forma más estructurada.
		
		- Idea clave
		
			Si la **elicitación** es “sacar la información”, estas herramientas son la forma de **dejarla bien atrapada y visible** para que el equipo no trabaje a ciegas. En términos prácticos, son la materia prima del análisis y del diseño.
			
- # Comparación 

|Aspecto|Caso de uso|Historia de usuario|Storyboard|
|---|---|---|---|
|**Qué es**|Representación de una interacción entre actor y sistema|Descripción breve de una necesidad del usuario|Secuencia visual que muestra cómo ocurre una interacción|
|**Objetivo principal**|Mostrar funcionalidades y flujo de interacción|Expresar necesidades de negocio de forma simple|Visualizar la experiencia del usuario paso a paso|
|**En qué se enfoca**|Comportamiento del sistema|Valor para el usuario|Flujo visual y experiencia|
|**Nivel de detalle**|Medio/alto|Bajo/medio|Medio|
|**Formato típico**|Actor + acciones + respuesta del sistema|“Como… quiero… para…”|Escenas o pantallas consecutivas|
|**Quién lo usa mucho**|Analistas y arquitectos|Equipos ágiles y Product Owner|UX/UI, analistas y usuarios|
|**Qué responde**|`¿Cómo interactúa el usuario con el sistema?`|`¿Qué necesita el usuario?`|`¿Cómo se verá y vivirá el flujo?`|
|**Ventaja principal**|Claridad funcional|Simplicidad y rapidez|Fácil comprensión visual|
|**Problema si se usa solo**|Puede volverse muy técnico|Puede quedar ambiguo|Puede enfocarse demasiado en interfaz|
|**Relación con requisitos**|Detalla funcionalidades|Descubre necesidades|Valida interacción y flujo|
|**Ejemplo simple**|Cliente inicia sesión y el sistema valida credenciales|“Como cliente quiero iniciar sesión para acceder a mi cuenta”|Dibujos/pantallas mostrando login → validación → panel principal|
- ![[16_herrami_captura.png]]



- ## Técnicas de análisis y especificación de requisitos [[SDLC_sofware.pdf#search=Especificación y análisis de requisitos|SDLC_sofware, p.129]]
	
	- es **ingeniería de requisitos pura**, y es la parte donde el documento deja de “capturar información” y empieza a **ordenarla, priorizarla y dejarla lista para especificarla formalmente**. El propio material la ubica después de la elicitación y antes de la especificación, y dice que aquí se trabaja el análisis de requisitos: **priorización, descomposición funcional y matriz de trazabilidad**, además de estándares para redactarlos bien.

	- ### Qué hace esta sección en el proceso completo

	```txt
	Elicitación  →  Análisis  →  Especificación  →  Validación
	(obtener)        (ordenar)     (documentar)       (confirmar)
	```

|Subtema|Para qué sirve|Idea central|
|---|---|---|
|**Priorización de requisitos**|Definir qué va primero|No todo tiene el mismo valor|
|**Clasificación de lista**|Ordenar requisitos por criterio|Ayuda a decidir rápido|
|**Puntos de historia y valor del negocio**|Ponderar esfuerzo vs valor|Muy ligado a Agile|
|**Técnica urgente**|Atender lo crítico primero|Resolver lo que bloquea|
|**MoSCoW**|Separar lo imprescindible de lo opcional|Must, Should, Could, Won’t|
|**Juicio de expertos**|Decidir con conocimiento experto|Útil, pero puede ser sesgado|
|**Matriz de priorización**|Comparar requisitos con criterios|Da un ranking objetivo|
|**Matriz de trazabilidad**|Relacionar requisitos con objetivos/entregables|Control y seguimiento|
|**Descomposición funcional**|Dividir el sistema en partes|Entender el todo por componentes|
|**IEEE 830 / IEEE 29148**|Redactar requisitos formalmente|Estructura y calidad documental|
|**Scrum / Kanban**|Especificar requisitos en ágil|Historias de usuario y backlog|
 

- ## Priorización de requisitos

	Sirve para decidir qué construir primero según valor, complejidad, dependencias y retorno de inversión. El texto insiste en que es clave para maximizar el valor entregado al cliente.
	
	### Ejemplo
	
	Si un sistema tiene:
	
	- login,
	- registro de usuarios,
	- carrito de compras,
	
	no tendría sentido priorizar el carrito si todavía no existe el registro. El documento pone exactamente esa lógica como ejemplo de dependencias.


- ## Técnica de clasificación de lista
	
	- Esta es la técnica más sencilla y directa de todas, pero también la que requiere más "carácter" por parte del analista y del cliente. Según el documento (página 78), se trata de una **priorización ordinal**.

	- Aquí te explico los puntos clave para que la entiendas a fondo:
		
		1. **¿En qué consiste?**
		
			Imagina que tienes todos los requisitos de tu tienda de materas escritos en tarjetas. La técnica de clasificación de lista consiste en poner una tarjeta sobre otra hasta formar una **columna única**.
			
			- **La regla de oro:** No puede haber dos requisitos con la misma importancia. Si tienes 10 requisitos, tendrás una lista del 1 al 10. El 1 es el más importante y el 10 el menos.
		
		2. **¿Por qué es tan efectiva? (Adiós al "Todo es urgente")**
			
			Lo que suele pasar en los proyectos es que el cliente dice: _"¡Todo es prioridad alta!"_.  
			Esta técnica elimina ese problema porque **fuerza una decisión**. Si el cliente quiere que el "Buscador" sea el #1, automáticamente el "Carrito de compras" tiene que ser el #2 o menos. No pueden compartir el trono.
		
		3. **¿Cómo se hace el proceso?**
		
			Para aplicarla en tu tienda de materas, seguirías estos pasos:
			
			1. **Reunir los requisitos:** Listas todo lo que la web debe hacer.
			2. **Comparar de a dos:** Tomas dos requisitos y preguntas: _"Si solo pudiéramos entregar uno mañana, ¿cuál salvaría el negocio?"_.
			3. **Ordenar:** Repites el proceso hasta que tengas el ranking final.

		4. **Ejemplo con tu tienda de materas:**
			
			- Si tuvieras estos tres:
			
				- A. Ver fotos de las materas.
				- B. Pagar por internet.
				- C. Recibir cupón de descuento por correo.
			
			- En la **Clasificación de Lista** quedaría así:
			
				1. **Ver fotos** (Sin fotos nadie compra, es el #1).
				2. **Pagar por internet** (Es vital, pero si hay fotos, el cliente al menos puede llamar para comprar, es el #2).
				3. **Cupón de descuento** (Es un extra, queda de #3).
			
			1. Ventajas y Desventajas
			
			- **Lo bueno:** Es muy fácil de entender y no deja dudas al programador sobre por dónde empezar.
			- **Lo malo:** En proyectos gigantes de miles de requisitos, es casi imposible hacer una lista única del 1 al 1.000 sin volverse loco.
			
			**¿Ves la diferencia?** En el paso anterior solo decíamos "esto es esencial", pero aquí le estamos dando un **puesto exacto** en la fila.

- # Técnica de puntos de historia y valor del negocio 

	- Esta técnica es la que separa a los "novatos" de los "profesionales", porque aquí dejas de usar el "yo creo" y empiezas a usar **datos y matemáticas**. Es la base de las metodologías ágiles como Scrum.

	- En esta técnica ya no solo importa qué es más importante, sino **cuánto esfuerzo cuesta hacerlo**. Se basa en una balanza de dos platos:
	
	1. El primer plato: Valor del Negocio (Business Value)
	
		Aquí el **Cliente** (la dueña de la tienda de materas) asigna un número a cada requisito.
		
		- **¿Qué mide?** Cuánto dinero le hará ganar, cuánto riesgo le quita o cuánto lo necesitan los usuarios.
		- Se suelen usar números (por ejemplo, del 1 al 100 o la escala de Fibonacci: 1, 2, 3, 5, 8, 13...).
		- _Ejemplo:_ "Pagar con tarjeta" tiene un valor de **100**. "Cambiar el color de fondo" tiene un valor de **5**.
	
	2. El segundo plato: Puntos de Historia (Esfuerzo/Complejidad)
	
		Aquí el **Equipo Técnico** (tú como programador) asigna un número al mismo requisito.
		
		- **¿Qué mide?** No mide tiempo en horas, sino **esfuerzo, dificultad y duda**. Un "8" es algo que es el doble de difícil que un "4".
		- _Ejemplo:_ "Pagar con tarjeta" es complejo por la seguridad, le das un **13**. "Cambiar el color de fondo" es una línea de código, le das un **1**.
	
	3. La Magia: El ROI (Retorno de Inversión)
	
		Aquí es donde aplicas la técnica de forma "Pro". Dividimos el **Valor** entre el **Esfuerzo**. El resultado te dice qué debes programar primero.
	
	Mira este ejemplo para tu tienda:

|Requisito|Valor (Dueña)|Puntos (Tú)|Prioridad (Valor / Puntos)|
|---|---|---|---|
|**A. Catálogo de fotos**|100|5|**20** (¡Hazlo ya!)|
|**B. Pasarela de pagos**|100|20|**5** (Importante, pero costoso)|
|**C. Chat de ayuda**|20|2|**10** (Es barato y da valor, hazlo pronto)|


**¿Qué nos dice esto?** Que aunque la pasarela de pagos es vital, el catálogo de fotos da el mismo valor y es mucho más fácil de hacer. Por lo tanto, el catálogo va de primero porque el **ROI** es mayor.


4. ¿Por qué es mejor que la lista simple?

- **Evita frustraciones:** A veces el cliente pide algo que vale "10", pero a ti te cuesta "100" de esfuerzo. Al ver los números, el cliente entiende por qué le dices que no o por qué se va al final de la lista.
- **Negociación clara:** Si el presupuesto se acaba, ya sabes que hiciste lo que daba más valor con el menor esfuerzo posible.

- # Técnica urgente
	- Esta técnica es conocida técnicamente como ==**Matriz de Urgencia e Importancia** (o Matriz de Eisenhower adaptada al software).== Es la que usas cuando el proyecto está en marcha y sientes que todo "se está quemando".

	- Según el documento, esta técnica clasifica los requisitos comparando qué tan rápido se necesitan (**Urgencia**) contra qué tanto impacto tienen (**Importancia**).
		
		Aquí tienes el desglose completo para tu tienda de materas:
		
		1. Los Cuatro Cuadrantes del "Urgente"
		
			Imagina un cuadro dividido en cuatro. Cada requisito de tus materas caerá en uno de estos:
			
			- **Cuadrante 1: Importante y Urgente (¡Fuego!)**
			    - Son cosas que si no haces hoy, el negocio se detiene o pierde dinero legalmente.
			    - _En tu tienda:_ "El botón de pagar da error y cobra doble". No puedes esperar a mañana, es **crítico**.
			    - **Acción:** Hacerlo de inmediato.
			- **Cuadrante 2: Importante pero NO Urgente (Estrategia)**
			    - Son las funciones que hacen que tu tienda sea mejor que la competencia a largo plazo. Es donde deberías pasar más tiempo.
			    - _En tu tienda:_ "Crear un sistema de fidelidad para clientes recurrentes". Es vital para el negocio, pero si no sale hoy, no pasa nada grave.
			    - **Acción:** Planificarlo y ponerle fecha.
			- **Cuadrante 3: NO Importante pero Urgente (Interrupciones)**
			    - Cosas que alguien pide con "afán" pero que no aportan valor real al objetivo de vender materas.
			    - _En tu tienda:_ "Cambiar el tipo de letra del pie de página porque a la dueña no le gusta". Ella lo quiere _ya_, pero no ayuda a vender más.
			    - **Acción:** Delegar o tratar de reducir el tiempo que le das.
			- **Cuadrante 4: Ni Importante ni Urgente (Distracciones)**
			    - Cosas que son puro "adorno".
			    - _En tu tienda:_ "Poner una música de fondo que suene cuando entran a la web". A nadie le importa y no es urgente.
			    - **Acción:** Eliminar o dejar para cuando no haya nada más que hacer.

	1. ¿Por qué es una técnica "peligrosa" si se usa mal?
	
		El documento advierte (indirectamente) que si vives solo en lo **Urgente**, el proyecto se vuelve un caos.
		
		- Un buen analista trata de que la mayoría de los requisitos estén en el **Cuadrante 2 (Importante/No Urgente)**.
		- Si todo se vuelve Urgente, es porque falló la **Ingeniería de Requisitos** al principio.
	
	2. Diferencia entre Urgencia e Importancia
	
	Este es el error más común que el documento ayuda a corregir:
	
	- **Importancia:** Tiene que ver con el **VALOR** (¿Me da dinero? ¿Cumple la ley?).
	- **Urgencia:** Tiene que ver con el **TIEMPO** (¿Se vence mañana? ¿Hay una feria de plantas el lunes y la web debe estar lista?).

	- ### **técnica llamada Matriz de Priorización por Puntos**
	
	
	- 1. El Cruce de Coordenadas (Multiplicación)

		Fíjate que tienes dos ejes:
		
		- **Vertical (Azul):** El **Valor del negocio** (del 1 al 5). ¿Qué tanto dinero o beneficio da?
		- **Horizontal (Gris):** La **Urgencia** (del 1 al 5). ¿Qué tan rápido se necesita?
		
		Los números que ves en el centro (del 1 al 25) son el resultado de **multiplicar** ambos valores. Por ejemplo:
		
		- Si un requisito tiene **Valor 5** y **Urgencia 5**, el resultado es **25** (Rojo).
		- Si tiene **Valor 2** y **Urgencia 3**, el resultado es **6** (Verde).
	
	1. El Semáforo de Prioridades (Los Colores)
	
		En lugar de "cuadrantes", esta tabla usa **niveles de calor**:
		
		- **Zona Roja (Puntaje 20-25):** Es lo que tienes que hacer **MAÑANA mismo**. Son requisitos que valen mucho y se necesitan ya.
		- **Zona Naranja/Amarilla (Puntaje 10-16):** Son requisitos importantes. Se deben programar pronto, pero no "incendian" el proyecto si esperan unos días.
		- **Zona Verde (Puntaje 1-8):** Es lo que puedes dejar para el final. Tienen poco valor o no hay prisa alguna.

		Ejemplo real con tus materas usando la Tabla 7:
		
		1. **Requisito: "Pasarela de pagos (tarjeta de crédito)"**
		    - **Valor:** 5 (Sin esto no cobras).
		    - **Urgencia:** 5 (La tienda abre el lunes).
		    - **Puntaje:** \(5 \times 5 = \mathbf{25}\) (**Rojo extremo**).
		2. **Requisito: "Galería de fotos de clientes felices"**
		    - **Valor:** 2 (Ayuda, pero no es vital).
		    - **Urgencia:** 2 (No hay prisa por lanzarlo).
		    - **Puntaje:** \(2 \times 2 = \mathbf{4}\) (**Verde tranquilo**).
		
		- ¿Por qué esta tabla es mejor que los "4 cuadrantes"?
		
			Porque te permite **comparar requisitos muy parecidos**. Si tienes dos cosas urgentes, esta tabla te ayuda a ver cuál de las dos da más dinero (valor) para decidir a cuál le dedicas tu primera hora de café.




- ## Matriz de trazabilidad
	
	1. ¿Qué es la Trazabilidad?

		Es la capacidad de seguirle el rastro a un requisito durante todo su ciclo de vida. Es decir, poder responder:
		
		- **Hacia atrás:** ¿De dónde salió este requisito? (¿De qué entrevista o de qué stakeholder?).
		- **Hacia adelante:** ¿En qué parte del software se programó esto? ¿Qué prueba de calidad lo valida?

	2. ¿Para qué sirve? (El "seguro de vida" del analista)
		
		Según el libro, tiene tres funciones críticas:
		
		1. **Control de alcance:** Asegura que el equipo esté trabajando _exactamente_ en lo que se pidió. Si hay algo en el código que no está en la matriz, es "trabajo extra" innecesario.
		2. **Análisis de impacto:** Si el cliente dice: _"Ya no quiero que las materas se paguen con tarjeta, sino solo con transferencia"_, tú miras la matriz y ves rápidamente qué otros requisitos, diseños y pruebas se ven afectados por ese cambio.
		3. **Verificación:** Sirve para demostrarle al cliente al final del proyecto que cumpliste con el 100% de lo pactado.
	
	2. ¿Cómo es la estructura de la matriz? [[SDLC_sofware.pdf#search=matriz de correlación dividida por secciones|SDLC_sofware, p.86]]
	
		Imagina una tabla de Excel muy extensa donde cada fila es un requisito. Las columnas suelen incluir:
		
		- **ID del Requisito:** (Ej: RS-001).
		- **Descripción:** (Ej: Pago con tarjeta).
		- **Fuente:** (Ej: Entrevista con la dueña).
		- **Prioridad:** (Aquí pones el resultado de las técnicas que vimos antes: MoSCoW o Urgente).
		- **Estado:** (Identificado, En desarrollo, Verificado).
		- **Entregable vinculado:** (Ej: Caso de Uso #5, Pantalla de Pago, Código en GitHub).
	- 4. Ejemplo con tu tienda de materas

|ID|Requisito|Fuente|Prioridad|Caso de Uso|Diseño (Figma)|Estado|
|---|---|---|---|---|---|---|
|**R01**|Carrito de compras|Entrevista Dueña|Must (Rojo)|CU-02|Pantalla_05|Terminado|
|**R02**|Filtro por material|Sesión Grupal|Should (Amarillo)|CU-08|Pantalla_03|En proceso|


- ## Descomposición funcional

	Sirve para partir un sistema grande en componentes más pequeños y entendibles. El documento dice que se usa para identificar y entender las partes que constituyen un todo, y sus interacciones.
	
	### En simple
	
	Es como dividir una clase grande en métodos más pequeños:
	
	- registrar,
	- validar,
	- guardar,
	- reportar.

- ## IEEE 830 y IEEE 29148

	Estos son marcos para **especificar bien** los requisitos.
	
	El documento explica que IEEE 830 propone una estructura tipo SRS con apartados como:
	
	- propósito,
	- alcance,
	- funciones del producto,
	- requisitos funcionales,
	- no funcionales,
	- restricciones,
	- interfaces, etc.
	
	Y dice que **IEEE 29148:2018** reemplaza estándares anteriores y contiene disposiciones para procesos y productos relacionados con ingeniería de requisitos durante todo el ciclo de vida. También orienta sobre cómo construir buenos requisitos y gestionar el proceso de forma iterativa.

- ## Scrum y Kanban en la especificación [[SDLC_sofware.pdf#search=Historias de usuario|SDLC_sofware, p.202]]

	En Scrum, los requisitos se describen normalmente como **historias de usuario** dentro del **product backlog**, y el equipo selecciona las historias prioritarias para cada sprint.
	
	En Kanban, el documento resalta que los requisitos se gestionan visualmente con el tablero y el flujo de trabajo, priorizando tareas según necesidades del momento y manteniendo mejora continua y flexibilidad.


# 2.1_Ciclo de vida del software

un **estándar técnico** que fija reglas, procesos y vocabulario comunes para desarrollar software de forma ordenada. El documento menciona que el ciclo de vida del software se apoya en normas como **ISO/IEC/IEEE 12207:2017** y también cita **IEEE 1074**, ambas usadas como marcos de referencia para procesos, actividades y tareas del ciclo de vida.

### Qué es el ciclo de vida del software 

El **SDLC** es el proceso para construir y hacer evolucionar software. El texto lo divide en fases: **planificación, análisis, diseño, implementación, pruebas y mantenimiento**. Cada fase produce entregables y sirve de entrada para la siguiente, como una cadena donde cada eslabón depende del anterior.

### Qué aporta la normativa

La norma no te dice “qué programa hacer”, sino **cómo estructurar el trabajo** para que sea entendible, controlable y repetible. En la práctica, sirve para:

- definir una terminología común,
- ordenar las fases,
- establecer qué actividades y tareas van en cada etapa,
- y asegurar que el producto final responda a requisitos reales.

### Entregables

| Fase           | Entregable              |
| -------------- | ----------------------- |
| Planificación  | Cronograma              |
| Análisis       | Documento de requisitos |
| Diseño         | Diagramas UML           |
| Implementación | Código fuente           |
| Pruebas        | Reporte de errores      |
| Mantenimiento  | Versión corregida       |

El **ciclo de vida del software (SDLC)** es un **flujo de trabajo estructurado** diseñado para reducir caos, errores, sobrecostos y fallos durante la creación de software. El objetivo es garantizar que el sistema:

- resuelva un problema real,
- funcione correctamente,
- sea mantenible,
- y pueda evolucionar con el tiempo.

**flujo**

Idea/Problema
      ↓
Planificación
      ↓
Análisis
      ↓
Diseño
      ↓
Implementación
      ↓
Pruebas
      ↓
Mantenimiento
      ↓
Evolución del software


|        FASE        |                PREGUNTA CENTRAL                 |                       OBJETIVO                        |                                              QUÉ SE HACE                                               |                RESULTADO / ENTREGABLE                |                 RIESGO QUE EVITA                  |
| :----------------: | :---------------------------------------------: | :---------------------------------------------------: | :----------------------------------------------------------------------------------------------------: | :--------------------------------------------------: | :-----------------------------------------------: |
| **PLANIFICACIÓN**  |       `¿Vale la pena hacer el proyecto?`        | Definir viabilidad, alcance, tiempo, costo y recursos | Estudio del problema, análisis de viabilidad, estimación de presupuesto, cronograma, recursos, riesgos | Plan del proyecto, cronograma, presupuesto, alcance  | Empezar proyectos imposibles, costosos o inútiles |
|    **ANÁLISIS**    |      `¿Qué necesita realmente el usuario?`      |           Descubrir y documentar requisitos           |     Entrevistas, observación, encuestas, casos de uso, historias de usuario, análisis del negocio      | Documento de requisitos funcionales y no funcionales |         Construir el software equivocado          |
|     **DISEÑO**     |        `¿Cómo construiremos el sistema?`        |      Crear la arquitectura técnica del software       |                 Diseño de BD, UML, interfaces, APIs, seguridad, estructura del sistema                 |      Diagramas, arquitectura, modelos técnicos       |             Programar sin estructura              |
| **IMPLEMENTACIÓN** | `¿Cómo convertimos el diseño en software real?` |            Construir el sistema funcional             |                    Programación, integración de módulos, configuración de entornos                     |          Código fuente y sistema funcional           |              Quedarse solo en teoría              |
|    **PRUEBAS**     |      `¿El sistema funciona correctamente?`      |          Detectar errores y validar calidad           |                   Testing unitario, integración, aceptación, rendimiento, seguridad                    |           Reportes de errores y validación           |           Entregar software defectuoso            |
| **MANTENIMIENTO**  |       `¿Cómo mantenemos vivo el sistema?`       |        Corregir, adaptar y mejorar el software        |                          Corrección de bugs, mejoras, adaptación tecnológica                           |              Nuevas versiones y mejoras              |          Que el software quede obsoleto           |


# 2.2_Paradigmas de los modelos de ciclo de vida del software

## ¿Qué es un paradigma?

Un paradigma es:

```
una forma de pensar y organizar el desarrollo del software
```

NO es un lenguaje.  
NO es una herramienta.  
NO es un framework.

Es un MODELO MENTAL.
- ## Paradigmas
|      Paradigma      |                 Idea central                 |
| :-----------------: | :------------------------------------------: |
|     Tradicional     |       Desarrollo lineal y estructurado       |
| Orientado a objetos | Construcción basada en objetos reutilizables |
|        Ágil         |   Desarrollo rápido, iterativo y adaptable   |

## TRADICIONAL

El documento dice que:

- es lineal,
- cada fase debe terminar antes de pasar a la siguiente,
- y se valida cada etapa antes de continuar.

- # Filosofía REAL

```
orden estricto y control fuerte
```

- # Flujo típico

```
Planificación
↓
Análisis
↓
Diseño
↓
Implementación
↓
Pruebas↓Entrega
```

- # Idea clave

NO se avanza hasta terminar la etapa anterior.

- # Ventaja

Mucho control y documentación.

Ideal para:

- bancos,
- gobierno,
- defensa,
- sistemas críticos.

---

- # Desventaja 

Si aparece un error tarde:

```
hay que regresary rehacer muchas fases
```

---

- # Problema real

Imagina:

```
6 meses programando...
```

y luego el cliente dice:

```
"eso no era lo que quería"
```

Catástrofe.

- ## Modelos asociados [[SDLC_sofware.pdf#search=Marcos de trabajos tradicionales|SDLC_sofware, p.312]]

	- ## Cascada/Waterfall (Modelo totalmente secuencial.)
		
		1. Las Fases Secuenciales 
		
			El documento muestra que para que este modelo funcione, se deben cumplir estas etapas en orden estricto:
			
			1. **Análisis de Requisitos:** Es la fase más crítica. Aquí se define **qué** debe hacer el sistema. Según el estándar que vimos (ISO 12207), si esta fase queda mal, todo lo que sigue estará mal.
			2. **Diseño del Sistema:** Aquí se define el **cómo**. Se crean los planos arquitectónicos, las bases de datos y la estructura técnica.
			3. **Implementación (Codificación):** Los programadores traducen los diseños a código real. Es la fase donde "se pica tecla".
			4. **Pruebas (Verificación):** Se busca que el software no tenga errores y que cumpla con los requisitos del paso 1.
			5. **Despliegue y Mantenimiento:** El software se entrega al cliente y se corrigen fallos que aparezcan con el uso.
			6. ![[5_model_cascada.png]]
		
		2. Características Principales (Lo que debes saber)
	
			- **Documentación pesada:** Como no puedes avanzar sin terminar la fase anterior, cada etapa debe dejar un documento firmado (por ejemplo, el documento de especificación de requisitos).
			- **Hitos claros:** Es muy fácil para un jefe de proyecto saber en qué punto está el proceso (ej. "Estamos al 100% del diseño").
			- **Rigidez:** Es su mayor debilidad. Una vez que bajas un escalón, es muy difícil y costoso "subir" para cambiar algo.

		3. ¿Cuándo se usa? (Conexión con TGS)
		
			Desde la **Teoría General de Sistemas**, este modelo es ideal para **Sistemas Cerrados** o muy estables. Se recomienda cuando:
			
			- Los requisitos son claros y **no van a cambiar**.
			- El proyecto es pequeño o sencillo.
			- Se trabaja en sectores muy regulados (como el software para un dispositivo médico o un avión) donde el orden y la documentación son vitales.

		4. La gran crítica del documento
		
			El documento señala que el mayor riesgo del modelo cascada es que **el cliente solo ve el resultado final**. Si hubo un malentendido en la fase de requisitos (la primera), el cliente se dará cuenta meses después, cuando ya se gastó todo el presupuesto. 
		

	- ## Espiral (Secuencial pero con iteraciones y análisis de riesgos.)
	
		- ¿Cómo funciona el Espiral?

			Imagina que cada vuelta del resorte (iteración) tiene **4 cuadrantes** u objetivos obligatorios. En cada vuelta, el proyecto crece en detalle:
			
			1. **Determinar Objetivos (Arriba a la izquierda):** Te sientas con el cliente. ¿Qué queremos lograr en esta vuelta? ¿Qué restricciones tenemos?
			2. **Análisis de Riesgos (Arriba a la derecha):** Esta es la parte más importante y lo que lo hace "profesional". Aquí te preguntas: _"¿Qué puede salir mal?"_. Si el riesgo es muy alto (por ejemplo, una tecnología que no conocemos), se hace un prototipo rápido para probarla antes de seguir.
			3. **Desarrollar y Probar (Abajo a la derecha):** Aquí es donde aplicas la "cascada". Escribes el código y lo verificas según lo planeado en esta vuelta.
			4. **Planificación (Abajo a la izquierda):** Revisas lo que hiciste con el cliente y planeas la siguiente vuelta del espiral.
			5. ![[6_mode_espiral.png]]

		- ¿Por qué se dice que es "Evolutivo"?
		
			Porque el software no nace de golpe. En la primera vuelta tienes un boceto; en la segunda, un prototipo funcional; en la tercera, una versión beta, y así hasta tener el producto final. **El sistema va evolucionando.**
			
			Lo que dice el documento (Puntos clave):
			
			- **Gestión de Riesgos:** Es el único modelo que pone el riesgo como prioridad. Si algo va a fallar, el modelo en espiral lo detecta temprano.
			- **Costo:** Es un modelo caro y complejo de gestionar. Se necesita gente muy experta para analizar los riesgos en cada vuelta.
			- **Flexibilidad Controlada:** A diferencia de la cascada, aquí sí puedes hacer cambios, pero solo al inicio de cada nueva vuelta.

		- Conexión con lo que ya sabes:
		
			- **TGS:** El espiral trata al software como un sistema que se retroalimenta. Cada vuelta es un ciclo de entrada-proceso-salida que mejora al anterior.
			- **Ingeniería de Requisitos:** Aquí los requisitos no se definen todos al inicio (como en cascada), sino que se van refinando y descubriendo en cada vuelta del espiral.


	- ## Prototipos (Construcción gradual mediante versiones preliminares.)
	
		- El modelo iterativo y de prototipos se agrupa en el documento para describir un proceso de desarrollo basado en ciclos de "ensayo y error guiado" . Esta metodología utiliza el prototipo como una maqueta evolutiva o desechable para obtener retroalimentación temprana del cliente, repitiendo etapas para refinar el sistema antes de la entrega final .
		
		- ![[7_mode_interativo.png]]
		
		 1. **Recolección y refinamiento de requisitos:** Aquí empieza todo (**Comienzo**). Te sientas con el cliente, pero en lugar de intentar definir el 100% del software, capturas lo más importante para empezar a "dibujar".
		2. **Diseño rápido:** No es un diseño profundo de ingeniería. Es un esquema veloz de las pantallas o funciones que el usuario va a ver.
		3. **Construcción del prototipo:** Aquí se crea la "maqueta". Puede ser algo que no funcione por detrás (sin base de datos real), pero que visualmente le muestra al cliente cómo será su sistema.
		4. **Evaluación del prototipo por el cliente:** Esta es la clave. El usuario lo prueba y dice: _"Esto sí me sirve"_ o _"No, yo me imaginaba otra cosa"_.
		5. **Refinamiento del prototipo:** Con los comentarios del cliente, ajustas la maqueta.
		6. **Producto de ingeniería:** Una vez que el cliente está feliz con el prototipo y los requisitos están claros, se construye el software de verdad, con toda la calidad técnica necesaria.
	
		7. Porque el **prototipo** es el objeto que construyes, y la **iteración** es el acto de dar vueltas en ese círculo (repetir los pasos) hasta que el cliente esté satisfecho.
	
			**Dato importante de tu imagen:**  
			Mira las flechas de **"Comienzo"** y **"Parada"**. El modelo te permite dar tantas vueltas como sea necesario hasta que el "refinamiento" sea perfecto. Solo cuando llegas a la fase de **Producto de ingeniería** es cuando el software se considera listo para salir a producción.
	
	- ## Diferencias
		1. El Modelo Cascada (El "Falso" Ciclo)

			Aunque en los libros a veces lo dibujan volviendo arriba para corregir errores, en la práctica **no es un ciclo**, es una **sentencia**.
		
			- **Diferencia clave:** Solo avanzas cuando la fase anterior está "muerta y enterrada".
			- **La trampa:** Si vuelves atrás, es porque fracasaste o hubo un error grave. No está diseñado para repetir, sino para hacerlo bien a la primera. Es como **hacer un examen**: una vez entregas la hoja, no puedes volver a pedirla para cambiar una respuesta.
		
		2. Modelo de Prototipos (Iterativo)
			
			Este se enfoca en **entender al cliente**.
			
			- **Diferencia clave:** Las vueltas que das son para **aprender**. El "código" que haces en las primeras vueltas suele ser basura (maquetas) que luego tiras para hacer el de verdad.
			- **Objetivo:** Reducir la incertidumbre. Das vueltas hasta que el cliente dice: _"¡Eso es lo que quiero!"_. Ahí te detienes y construyes. Es como **hacer un boceto** a lápiz antes de pintar el cuadro al óleo.
		
		3. Modelo Espiral (Gestor de Riesgos)
		
			Este es el más profesional y complejo.
			
			- **Diferencia clave:** Cada vuelta no es solo para aprender (como el prototipo) ni solo para avanzar (como la cascada). Cada vuelta es para **evaluar riesgos**.
			- **Objetivo:** Seguridad. En cada vuelta te preguntas: _"¿Cuánto dinero nos queda? ¿La tecnología funciona? ¿Es legal?"_. Es el único que tiene un cuadrante específico de análisis de riesgos. Es como **subir una montaña**: en cada tramo te detienes a revisar el clima, el equipo y tu salud antes de dar el siguiente paso.
			
## ORIENTADO A OBJETOS

El documento dice que se centra en:

- creación de clases,
- análisis de requisitos,
- diseño,
- y reutilización del código fuente.

- # Filosofía REAL

```
dividir el sistema en objetos reutilizables
```


- # Idea principal

En vez de pensar:

```
"todo el programa"
```

se piensa:

```
"pequeñas entidades que colaboran"
```

- # Ejemplo

Sistema hospitalario:

```
PacienteDoctorFacturaCitaMedicamento
```

Cada uno es:

- una clase,
- con atributos,
- comportamientos,
- relaciones.

- # Objetivo

```
reutilización + mantenibilidad + modularidad
```

---

- # Beneficio enorme

Puedes reutilizar objetos en otros proyectos.

Ejemplo:

```
Clase Usuario
```

Puede servir en:

- ecommerce,
- ERP,
- red social,
- sistema académico.

- # Problema que intenta resolver

El caos del software monolítico.

- # Aquí nacen conceptos gigantes:

- encapsulamiento,
- herencia,
- polimorfismo,
- abstracción.
- # Relación con Python

Python es multiparadigma…  
pero soporta muy fuerte el paradigma orientado a objetos.

```py
class Usuario:    pass
```

Eso es literalmente paradigma POO.

Aunque no tiene ciclos de vida propios, para que la POO funcione, el documento y la ingeniería sugieren dos etapas que sí viste o verás:

- **OOA (Análisis Orientado a Objetos):** Mirar el mundo real y detectar quiénes son los "actores" o "cosas" (ej: en un banco, el objeto es la "Cuenta" y el "Cliente").
- **OOD (Diseño Orientado a Objetos):** Definir cómo se van a hablar esos objetos entre ellos (usando diagramas de clases o **UML**, que seguramente viste en tus documentos).

## ÁGIL

El documento dice:

- desarrollo rápido,
- simplificación de procesos,
- interacción continua,
- cliente involucrado durante el desarrollo.

- # Filosofía REAL

```
adaptarse constantemente al cambio
```

- # Idea clave

El paradigma tradicional asume:

```
"los requisitos son estables"
```

Ágil asume:

```
"los requisitos cambiarán"
```

Y eso es MUCHO más realista.

- # Flujo ágil

```
Pequeña versión↓Retroalimentación↓Mejora↓Nueva iteración↓Más retroalimentación
```

- # En vez de esperar 1 año…

Se entregan partes funcionales rápidamente.

- # Ventajas que menciona el documento

| Ventaja                   | Significado real              |
| ------------------------- | ----------------------------- |
| Participación del usuario | El cliente corrige temprano   |
| Resultados anticipados    | Se ven avances rápido         |
| Flexibilidad              | Cambios constantes            |
| Gestión de riesgos        | Problemas detectados temprano |

- # Modelos ágiles [[SDLC_sofware.pdf#search=Marcos de trabajo ágiles|SDLC_sofware, p.321]]

	- **Scrum (El modelo de los "Sprints")**

		Es el más famoso. No se ve como una línea, sino como un círculo que se repite cada 2 o 4 semanas.
		
		- **Cómo funciona:** El trabajo se divide en piezas pequeñas llamadas **Sprints**. Al final de cada Sprint, **debes** entregar algo que funcione (un incremento del software).
		- **Roles clave:** Existe el _Product Owner_ (el que sabe qué quiere el cliente), el _Scrum Master_ (el que quita obstáculos) y el _Equipo de Desarrollo_.
		- **La clave:** Las reuniones diarias de 15 minutos (_Daily_) para sincronizarse. Es ideal para proyectos donde el cliente cambia de opinión seguido.
		
		- En Scrum, el trabajo no es un caos, sino que sigue un ritmo sagrado. Para que lo entiendas fácil, imagina que vas a organizar una fiesta (el software). Estos procesos se dividen en **"Listas de cosas" (Artefactos)** y **"Reuniones" (Eventos)**:
				
			1. **Las Listas de Tareas (Artefactos)**
				
				Antes de empezar a trabajar, necesitas saber qué vas a hacer:
				
				- **Product Backlog:** Es la "Lista de Deseos" gigante. Contiene todo lo que el cliente quiere que el sistema tenga en el futuro. Está desordenada y siempre está creciendo.
				- **Sprint Backlog:** Es el "Menú del Día". De la lista gigante anterior, el equipo elige qué puede terminar en las próximas 2 semanas. **Solo se enfocan en esto** y nada más.

			2. **Las Reuniones (Eventos)**
			
				Son los momentos donde el equipo se detiene para hablar y ajustar el rumbo:
				
				- **Sprint Planning Meeting (Planeación):** Se hace el día 1 del Sprint. El equipo decide qué tareas del _Product Backlog_ pasan al _Sprint Backlog_. Es donde se dice: _"En estas dos semanas vamos a hacer el login y el registro"_.
				- **Daily Scrum (La reunión diaria):** Dura solo **15 minutos** y se hace de pie. Se responden tres preguntas: ¿Qué hice ayer? ¿Qué haré hoy? ¿Tengo algún problema? Sirve para que nadie se quede "varado".
				- **Sprint Review (Demostración):** Se hace al final de las 2 semanas. Se le muestra al cliente el software real funcionando. El cliente dice: _"Me gusta"_ o _"Cámbienle esto"_.
				- **Sprint Retrospective (Mejora interna):** Es una reunión **solo del equipo**. No se habla del software, sino de cómo trabajaron. _"¿Peleamos mucho? ¿Nos faltó café? ¿La comunicación falló?"_. Es para mejorar como personas y como equipo para el siguiente ciclo.


			3. **¿Son métodos que aplicas mientras desarrollas?**
				
				**Sí.** Mientras los programadores están escribiendo código (el desarrollo), estas reuniones ocurren como un "reloj" para asegurar que:
				
				1. No se pierda el tiempo en cosas que el cliente no pidió.
				2. Todos sepan en qué va el otro.
				3. El software se entregue por pedacitos funcionales.
				
				**¿Ves la conexión con la TGS?** Scrum es un sistema de **Retroalimentación (Feedback)** constante. En lugar de esperar 6 meses para ver si el software funciona, te das cuenta cada 24 horas (Daily) o cada 2 semanas (Review).
		- ![[8_model_scrum.png]]

	2. **Kanban (El modelo de las "Tarjetas" y el flujo)**
	
		Este modelo nace en las fábricas de Toyota y se enfoca en la **visualización**.
		
		- **Cómo funciona:** Usas un tablero (físico o digital) con columnas: **"Por hacer", "En proceso" y "Hecho"**.
		- **La regla de oro (WIP):** No puedes tener demasiadas cosas en la columna de "En proceso". Si hay un cuello de botella, todo el equipo se detiene a ayudar ahí.
		- **Diferencia con Scrum:** No tiene tiempos fijos (Sprints), es un flujo continuo. El trabajo se va sacando a medida que hay espacio.
		- ![[9_model_kanban.png]]
	
	3. **XP - Extreme Programming (El modelo de la "Calidad Extrema")**
	
		Este se centra mucho más en la **forma de programar** que en la gestión de reuniones.
		
		- **Cómo funciona:** Lleva las buenas prácticas al extremo. Por ejemplo:
		    - **Programación en parejas:** Dos personas en un mismo teclado (uno escribe, el otro revisa).
		    - **Pruebas primero (TDD):** Antes de programar una función, escribes la prueba para ver si falla.
		    - **Entregas pequeñas:** Subir cambios al sistema varias veces al día.
		- **La clave:** El código debe ser tan limpio y simple que cualquier cambio sea fácil de hacer.
		
		1. **Tipo de desarrollo iterativo e incremental** 

			En lugar de intentar construir todo el software de una vez (como en la Cascada), XP divide el proyecto en **ciclos muy cortos** llamados iteraciones (normalmente de 1 a 2 semanas).
			
			- **Iterativo:** Repites el proceso de diseño, código y prueba una y otra vez.
			- **Incremental:** En cada ciclo añades una pequeña pieza de funcionalidad que ya sirve para algo. Así, el software va "creciendo" de forma segura. 
			
		2. **Pruebas unitarias**
	
			En XP, no se programa y luego se prueba; a menudo se usa **TDD (Test Driven Development)**.
			- Escribes una prueba pequeña (un test) para una función antes de escribir la función misma.
			- Esto garantiza que cada pequeño "ladrillo" de código funcione perfectamente desde el segundo uno y te da la confianza para cambiar cosas sin miedo a romper el resto.
		
		3. **Trabajo en equipo**
			
			XP no es para "lobos solitarios". Fomenta la comunicación constante entre todos.
			
			- Una práctica famosa es la **programación en parejas (Pair Programming)**: dos desarrolladores en una sola computadora. Uno escribe el código mientras el otro revisa la lógica en tiempo real, lo que reduce errores drásticamente. 
		
		4. **Trabajo junto al cliente**
			
			En XP, el cliente es **parte del equipo**. No es alguien a quien ves solo al principio y al final.
			
			- El cliente define qué es valioso (historias de usuario) y está presente para resolver dudas o probar avances inmediatamente. Esto evita que el equipo trabaje semanas en algo que el cliente no quería.
		
		5. **Corrección de errores**
			
			A diferencia de otros modelos donde los errores se dejan para una "fase de depuración" al final, en XP los errores **se corrigen en el momento en que se encuentran**. Las pruebas constantes y la integración continua permiten que el sistema siempre esté en un estado "saludable" y listo para funcionar
		
		6. **Reestructuración del código (Refactorización)**
		
			Es la práctica de mejorar el diseño del código **sin cambiar lo que hace**.
			
			- Si un código funciona pero es difícil de leer o está "sucio", el equipo lo limpia y lo reorganiza constantemente. Esto mantiene el sistema flexible y evita que el código se vuelva un caos imposible de mantener con el tiempo
			
		7. **El código es de todos (Propiedad Colectiva)**
		
			Nadie es "dueño" exclusivo de una parte del sistema. Cualquier desarrollador puede entrar, revisar y mejorar cualquier archivo de código.
			
			- Esto evita que el proyecto se detenga si alguien se enferma y fomenta que todos aprendan sobre todo el sistema, elevando la calidad general. 
		
		8. **El código simple es la clave**
			
			La filosofía es: **"Haz lo más sencillo que pueda funcionar hoy"**.
			
			- No intentes adivinar qué querrá el cliente dentro de un año; programa solo lo que se necesita ahora de la forma más limpia posible. La simplicidad facilita los cambios futuros y reduce el desperdicio de tiempo en funciones innecesarias.
			
		- ![[10_model_xp.png]]

## DIFERENCIA FILOSÓFICA MÁS IMPORTANTE

|Tradicional|Ágil|
|---|---|
|Predicción|Adaptación|
|Mucha planificación inicial|Evolución continua|
|Cambios costosos|Cambios esperados|
|Cliente al inicio|Cliente siempre involucrado|
|Entrega tardía|Entregas frecuentes|

# 2.3_Fase de definición de requisitos

1. Define el "Qué" antes del "Cómo"

	Imagina que vas a construir una casa. No compras ladrillos ni cemento (Desarrollo) sin antes tener los planos (Requisitos). Esta fase es la que le dice al equipo **qué** problema estamos resolviendo. Si te saltas esto, podrías terminar construyendo un puente donde el cliente necesitaba un túnel.

2. Es el punto de contacto con el Mundo Real (TGS)

	Desde la **Teoría General de Sistemas**, el software es una solución para un entorno (una empresa, un usuario). La fase de requisitos es la **interfaz** entre el cliente y los ingenieros. Es el momento en que las necesidades humanas se traducen a lenguaje técnico. Sin esta fase, el software estaría "aislado" de la realidad.

3. Evita el desperdicio de dinero

	El documento enfatiza que **corregir un error en la fase de requisitos cuesta casi nada** (solo es borrar y volver a escribir un párrafo). Pero si te das cuenta de que algo falta cuando el software ya está programado, el costo de arreglarlo es **100 veces mayor**. Por eso, por seguridad financiera, siempre debe ir primero.

- ¿Qué se hace exactamente en este "primer paso"?

	- El documento menciona que esta fase se divide en actividades críticas que ocurren antes de tocar una sola línea de código:

	- **Elicitación:** "Extraer" la información del cliente (entrevistas).
	- **Análisis:** Ver si lo que pide el cliente es posible o si hay contradicciones.
	- **Especificación:** Documentar todo formalmente.
	- **Validación:** Que el cliente firme y diga "Sí, eso es lo que quiero".

- ![[11_tabla_activi_artefac.png]]

- Para entenderla, piensa en esto como una receta de cocina:

- **Fase:** Es el momento en el que estás.
- **Actividades:** Es lo que **haces** (la acción).
- **Artefactos:** Es lo que **entregas** (el documento o resultado físico).

- El cuadro te quiere dar a entender:
	
	1. Definición del alcance del proyecto

		- **Qué significa:** Es poner los límites. Hasta dónde llega el software y qué **no** va a hacer.
		- **Por qué no tiene artefacto (en esta fila):** Porque suele ser una discusión inicial. El resultado final de esto se verá reflejado en los documentos siguientes.

	2. Identificación del negocio → Artefacto: Modelo del negocio
	
		- **Qué significa:** Antes de programar, debes entender cómo gana dinero el cliente o cómo funciona su empresa.
		- **El Artefacto:** El **Modelo del negocio** es un diagrama o documento que explica quiénes son los clientes, qué servicios ofrecen y cómo fluye la información.
	
	3. Toma de requerimientos → Artefacto: Análisis y realización de casos de uso
	
		- **Qué significa:** Aquí es donde "sacas" la información (Elicitación).
		- **El Artefacto:** Los **Casos de Uso** son fundamentales en POO. Son descripciones de cómo un usuario interactúa con el sistema (ej: "El cliente ingresa su clave y el sistema valida"). Es el plano de la funcionalidad.
	
	4. Estudio de procesos de negocio → Artefacto: Modelo de procesos y actividades
	
		- **Qué significa:** Es observar el paso a paso actual. Por ejemplo: ¿Cómo se hace una venta hoy sin el software?
		- **El Artefacto:** Un diagrama de flujo que muestra el camino que sigue la información. Esto ayuda a que el software no choque con la forma de trabajar del cliente.
	
	5. Calendarización del proyecto → Artefacto: Cronograma
	
		- **Qué significa:** Es el manejo del tiempo.
		- **El Artefacto:** El **Cronograma** (un diagrama de Gantt, por ejemplo) donde dices: "La fase de requisitos dura 2 semanas, el diseño 3", etc.

¿Cómo se une esto con lo que ya sabes?

Si elegiste un **Paradigma Ágil**, este cuadro se repite muchas veces (en cada Sprint). Si elegiste el **Tradicional**, este cuadro se hace una sola vez de forma muy profunda al principio.

En resumen: **La tabla te dice que por cada cosa que hagas (Actividad), debes dejar una prueba física de que lo hiciste (Artefacto).**

## Requisitos [[SDLC_sofware.pdf#search=Importancia de los requisitos|SDLC_sofware, p.42]]

1. **El requisito como "Capacidad"**

	Cuando la IEEE dice que es una **condición o capacidad**, se refiere a que el software debe "darle un superpoder" al usuario que antes no tenía.
	
	- _Ejemplo:_ "El usuario debe poder consultar su saldo desde el celular". Esa es la capacidad que resuelve el problema de tener que ir hasta el banco.

2. **El laberinto de las expectativas**

	Esta es la parte más difícil de la ingeniería y por eso el texto usa estos pares de palabras:
	
	- **Obvios vs. Ocultos:**
	    - _Obvio:_ El sistema debe tener un botón de "Entrar".
	    - _Oculto:_ El sistema debe encriptar la contraseña (el cliente no lo pide porque da por hecho que tú, como experto, lo harás).
	- **Conocidos vs. Desconocidos:**
	    - _Conocido:_ "Quiero que el reporte salga en PDF".
	    - _Desconocido:_ El cliente no sabe que necesita una copia de seguridad automática hasta que tú se lo mencionas.
	- **Esperados vs. Inesperados:**
	    - _Esperado:_ Que el software sea rápido.
	    - _Inesperado:_ Una función que le ahorra 3 horas de trabajo al día y que el cliente ni siquiera imaginaba que era posible.

3. **El gran reto: Comunicar expectativas**

	El texto dice que los requisitos **comunican expectativas**. Aquí es donde entra la **TGS (Teoría General de Sistemas)**:  
	Si el cliente tiene una idea en su cabeza (Expectativa) y tú escribes algo diferente en el documento de requisitos, el "sistema" resultante será un fracaso porque no habrá **entropía negativa** (orden); habrá caos.
	
	¿Por qué es importante para ti?
	
	Porque entender esto te quita la idea de que "programar es solo escribir código". Programar es, primero, **traducir** todo ese lío de cosas ocultas y esperadas en una lista clara de tareas.

> **Dato clave:** La mayoría de los proyectos de software fracasan no porque el código esté mal escrito, sino porque los requisitos **ocultos o desconocidos** nunca se descubrieron.

### Clasificación

| Clasificación                    | ¿Qué es?                                                                                                                                  | ¿Quién lo entiende?                                             | Ejemplo Práctico                                                                                                      |
| -------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **1. Requisitos de Usuario**     | Declaraciones en **lenguaje natural** sobre qué servicios se espera que el sistema proporcione. Son necesidades de alto nivel.            | El cliente, gerentes y usuarios finales (no técnicos).          | "El sistema debe permitir que los empleados soliciten sus vacaciones de forma virtual".                               |
| **2. Requisitos de Sistema**     | Descripciones detalladas de las funciones y servicios del sistema. Establecen **qué se debe implementar** con precisión.                  | Desarrolladores, analistas y arquitectos de software.           | "Al pulsar 'Enviar solicitud', el sistema validará que el empleado tenga días disponibles en la tabla `vac_balance`". |
| **3. Requisitos Funcionales**    | Describen los **servicios o funciones** que el software debe ejecutar. Son las acciones que el sistema realiza ante entradas específicas. | El equipo de desarrollo (es la guía para programar).            | "El sistema enviará un correo electrónico de notificación al jefe inmediato tras cada solicitud".                     |
| **4. Requisitos No Funcionales** | Son las **restricciones o atributos de calidad** (desempeño, seguridad, fiabilidad). No dicen qué hace, sino "cómo" debe ser.             | Arquitectos de sistema y expertos en seguridad/infraestructura. | "El sistema debe cargar cualquier página en menos de 2 segundos y soportar 500 usuarios simultáneos".                 |

![[12_requisitos.png]]

Tabla 2: Diferencias Clave para no confundirlos

|Criterio de Diferencia|Usuario vs. Sistema|Funcional vs. No Funcional|
|---|---|---|
|**Enfoque**|El de **Usuario** es el "Qué quiero"; el de **Sistema** es el "Cómo debe especificarse técnicamente".|El **Funcional** es una acción/tarea; el **No Funcional** es una propiedad/característica del sistema.|
|**Lenguaje**|**Usuario:** Informal, de negocio. **Sistema:** Formal, técnico, diagramas.|**Funcional:** Verbos de acción (Calcular, imprimir, guardar). **No Funcional:** Adjetivos de calidad (Rápido, seguro, estético).|
|**Importancia**|Sin el de **Usuario** no hay contrato; sin el de **Sistema** el programador no sabe qué codificar.|Si el **Funcional** falla, el sistema no hace la tarea. Si el **No Funcional** falla, el sistema es inusable (ej. es muy lento).|
|**Falla crítica**|Un error aquí significa que construimos el producto equivocado para el cliente.|Un error aquí puede causar que el sistema se caiga o sea hackeado fácilmente.|

**Un detalle extra del documento:** A veces los **No Funcionales** son más críticos que los Funcionales. Por ejemplo, si un sistema bancario hace bien los cálculos (Funcional) pero es fácil de hackear (No Funcional), el sistema no sirve para nada.

1. **Los Requisitos de Usuario (La visión del cliente)**

	Van al **principio**. Sirven para que el cliente firme el contrato. Se escriben como "Historias de Usuario" o párrafos sencillos. Si el cliente no entiende tu documento, esta es la parte que él debe validar.

2. **Los Requisitos de Sistema (El manual técnico)**

	Van en la **parte central**. Es la traducción técnica de los anteriores. Aquí es donde incluyes los detalles de bases de datos, protocolos y reglas de negocio complejas. Es lo que el programador lee para no cometer errores.

3. **Los Requisitos Funcionales (El "Checklist")**

	Suelen ir dentro de los requisitos de sistema, pero organizados como una **lista numerada** (RF01, RF02...). Es vital que estén así para que al final del proyecto puedas decir: "Cumplí con los 50 puntos que me pidieron".

4. **Los Requisitos No Funcionales (Las reglas del juego)**

	Van en una **sección aparte**. Son obligatorios porque definen la calidad. Aquí pones que el software debe ser seguro, que debe funcionar en Android e iOS, o que debe ser rápido. Si no los pones, el cliente podría quejarse luego de que el sistema es muy lento y tú no tendrás cómo defenderte porque "no estaba en el documento".

# 3_La fase de elicitación de requisitos

1. **El concepto: "Sacar a la luz"**

	La palabra viene del latín _elicitare_, que significa "provocar una respuesta". No es una actividad pasiva de sentarse a escuchar; es una actividad activa donde tú, como analista, debes:
	
	- **Investigar:** Entender el negocio del cliente.
	- **Observar:** Ver cómo trabajan realmente (a veces lo que dicen no es lo que hacen).
	- **Cuestionar:** Preguntar el "por qué" de cada cosa para llegar al fondo del problema.

2. **¿Por qué es tan difícil según el documento?**

	El documento menciona que en esta fase aparecen tres grandes problemas:
	
	- **Problemas de ámbito:** El cliente pide cosas imposibles o que no tienen que ver con el proyecto.
	- **Problemas de comprensión:** El cliente usa términos técnicos de su negocio (ej. "el balanceo de activos") que tú no entiendes, y tú usas términos de software que él no entiende.
	- **Problemas de volatilidad:** Los requisitos cambian porque el cliente descubre nuevas necesidades mientras hablas con él.

3. **Las técnicas que se utilizan**

	Para que la elicitación sea un éxito, no solo se hacen entrevistas. El documento sugiere varias herramientas:
	
	1. **Entrevistas:** Conversar cara a cara (pueden ser abiertas o con cuestionarios).
	2. **Encuestas:** Útiles cuando tienes cientos de usuarios y no puedes hablar con todos.
	3. **Observación (Etnografía):** Ir al puesto de trabajo del usuario y ver cómo sufre con el proceso actual.
	4. **Talleres (JAD):** Reunir a todos los jefes en una sala para que se pongan de acuerdo entre ellos (y no te den órdenes contradictorias).
	5. **Lluvia de ideas (Brainstorming):** Para proyectos innovadores donde no hay nada escrito.

4. **¿Cuál es el resultado (Artefacto)?**

	Al terminar la elicitación, el resultado suele ser una **lista de deseos cruda** o un documento de "Historias de Usuario". Todavía no es el documento técnico final, sino la materia prima para la siguiente fase (el Análisis).
	
	**En resumen:** Si la Ingeniería de Requisitos fuera un juicio, la elicitación es la etapa donde el detective interroga a los testigos y recoge pistas. Si el detective hace malas preguntas, el juicio se pierde.

### Planeacion

Antes de entrevistar, encuestar u observar, primero decides:

- **de dónde saldrá la información**,
- **quiénes participan**,
- **qué técnica conviene**,
- **cómo vas a capturar los datos**.

Es como en Python cuando primero defines la estructura de una función antes de escribirla: si no sabes qué entra, qué sale y qué pasos seguirá, terminas improvisando. La planeación es ese “encuadre” inicial que evita que la recolección de requisitos se vuelva caótica.

## Qué tareas incluye según el documento


|Tarea|Qué busca|
|---|---|
|**Identificar las fuentes**|Saber de dónde vendrán los requisitos|
|**Identificar interesados del producto**|Determinar quiénes influyen o son afectados|
|**Matriz de stakeholders**|Describir necesidades y criterios de éxito|
|**Revisar técnicas**|Elegir entrevistas, grupos focales, encuestas, prototipos|
|**Captura de interesados**|Definir cómo involucrarlos y gestionarlos|

## Qué hace cada parte

**Identificar las fuentes de requerimientos** significa ubicar quién o qué puede aportar información útil: usuarios, expertos, procesos existentes, sistemas actuales, manuales, formularios, reportes y especificaciones previas. El texto incluso clasifica esas fuentes como **primarias, secundarias y terciarias**.

**Identificar interesados del producto** es reconocer a los **stakeholders**: personas u organizaciones relacionadas con el proyecto y afectadas por sus resultados. El documento distingue **primarios** y **secundarios**, y luego muestra roles como cliente, usuario, líder de proyecto, analista, programador, QA y arquitecto.

**La matriz de stakeholders** sirve para ordenar a esos interesados según su interés e influencia, y así decidir cómo gestionarlos mejor. El documento la presenta como una herramienta para priorizar y definir estrategias de gestión.

**Revisar técnicas** significa decidir con anticipación si conviene más entrevistar, observar, encuestar o usar prototipos; el documento lo llama identificar combinaciones de técnicas.

**Captura de interesados** apunta al plan para involucrarlos de forma efectiva durante la obtención de requisitos.



![[13_roles_en_requisitos.png]]

## Qué es esa tabla

No es solo una lista de cargos. Es un **mapa de responsabilidades** dentro de la ingeniería de requisitos. Cada rol cubre una parte distinta del trabajo: negocio, uso real, negociación, análisis, codificación, calidad y diseño.

## Cómo leerla sin perderse

Piensa en esto como una cadena:

```txt
Cliente -> dice qué necesita
Usuario -> explica cómo se trabaja de verdad
Analista -> convierte eso en requisitos
Arquitecto -> define cómo se estructurará la solución
Programador -> construyeQA -> verifica que sirva
Líder de proyecto -> coordina todo el flujo
```

Eso es muy parecido a un sistema bien diseñado en programación: una función recibe datos, otra los transforma, otra valida, y al final obtienes un resultado confiable.

## ¿Eso es lo que “debería tener una empresa”?

**Sí, en cuanto a funciones. No necesariamente en cuanto a cargos separados.**

Una empresa madura debería cubrir esos roles, porque si faltan, el proyecto se vuelve débil. Pero eso **no significa** que cada rol deba ser una persona distinta. En una empresa pequeña, una sola persona puede cumplir varios roles; en una empresa grande, normalmente se separan más.

La idea del documento no es decirte “contrata exactamente 7 personas”, sino enseñarte que un proyecto serio necesita estas **responsabilidades** cubiertas.

## Qué pasa si falta alguno

- Sin **cliente**, el proyecto puede perder el enfoque de negocio.
- Sin **usuario**, el software puede quedar bonito pero inútil.
- Sin **analista**, los requisitos quedan confusos.
- Sin **arquitecto**, la solución puede quedar desordenada.
- Sin **QA**, los errores se acumulan.
- Sin **líder**, el proyecto se descontrola.

## La idea más importante

La tabla está mostrando que el software no nace del código, sino de una **colaboración organizada** entre necesidades, análisis, diseño, desarrollo y validación.

Pregunta diagnóstica: ¿quieres que ahora te explique **cada rol con un ejemplo real aplicado a un sistema de inventario o de reportes técnicos**?


# 3.1_Herramientas de modelado [[4_UML]]

es la parte donde el documento pasa de “capturar requisitos” a **representar el sistema de forma visual y formal**. El texto dice que estas herramientas se usan para crear modelos de sistemas que ya existen o que se van a desarrollar, como un **“simulacro”** del sistema, con **bajo costo y riesgo mínimo** porque se trabaja con gráficos y textos antes de construir el software real.

## Qué es, en limpio

Modelar es **dibujar y estructurar el sistema antes de programarlo**.  
Sirve para entenderlo mejor, comunicarlo entre analistas, desarrolladores y clientes, y detectar errores temprano. El documento remarca que UML es el lenguaje de modelado más conocido y utilizado actualmente, y que permite **especificar, modelar, construir y documentar** sistemas software.

## Para qué sirve

Sirve para varias cosas a la vez:

|Uso|Qué logra|
|---|---|
|**Entender el sistema**|Ver el sistema como un conjunto de partes y relaciones|
|**Comunicar ideas**|Todos leen el mismo modelo y no interpretan “a su manera”|
|**Reducir errores**|Se detectan fallos de lógica antes del código|
|**Documentar**|Queda evidencia formal del sistema|
|**Apoyar diseño y construcción**|El modelo guía lo que luego se implementa|

Eso es exactamente lo que el documento quiere enfatizar: que el modelado ayuda a **visualizar, especificar, construir y documentar** el software antes de codificarlo.

## Qué relación tiene con lo anterior

La secuencia lógica del documento es esta:

```
Elicitación → capturar requisitos → Herramientas de modelado → representar esos requisitos en modelos → Análisis / especificación → formalizar lo que el sistema debe hacer
```

O sea, la elicitación te da información; el modelado la convierte en una representación clara y técnica.

## Qué menciona el documento dentro de esta sección

El texto habla de dos grandes familias:

1. **UML (Unified Modeling Language, UML):**  [[SDLC_sofware.pdf#search=Características del Lenguaje Unificado de Modelado UML|SDLC_sofware, p.125]] Es el lenguaje gráfico de modelado más difundido. Se usa para representar sistemas orientados a objetos y sus elementos con diagramas.

2. **CASE:** Son programas y procesos guiados que ayudan a analistas, desarrolladores y diseñadores a automatizar o apoyar fases del ciclo de vida del software. Su objetivo general es **acelerar** el proceso, **automatizar** partes del trabajo y **reducir el costo** de desarrollo.

## Diferencia simple entre UML y CASE

- **UML** = el **lenguaje** para dibujar/modelar.
- **CASE** = la **herramienta software** que te ayuda a hacer esos modelos.

## Ejemplos de herramientas que menciona el documento

El documento lista varias herramientas CASE/modelado, entre ellas: **Gliffy, ArgoUML, MagicDraw, StarUML y Lucidchart**. También menciona otras como **Power Designer, Oracle Designer, Modelio, Dia, Papyrus UML** y más.

## En qué te ayuda a ti como estudiante o analista

Te ayuda a pasar de frases vagas como:

```
"el sistema debe permitir registrar reportes"
```

a algo más claro como:

- quién lo hace,
- qué pasos sigue,
- qué relaciones existen,
- qué clases, procesos o pantallas intervienen.

En otras palabras: **modelar es pensar el software como estructura, no solo como código**. Esa inferencia está alineada con lo que el documento explica sobre UML y CASE como apoyo para representar el sistema antes de codificarlo.

## Resumen en una sola línea

**Herramientas de modelado** = recursos para representar visualmente el sistema, entenderlo mejor, comunicarlo y prepararlo antes de construirlo.

# 4_Metodologías de desarrollo de software
