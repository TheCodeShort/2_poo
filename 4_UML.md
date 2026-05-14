[[1_poo.pdf#search=tema: Interfaces y Clases Abstractas|1_poo, p.36]]
# Para tener un ejemplo de diagrama de flujo pagina => 352

[[2_SDLC_sofware.pdf#search=Diagramas de flujo|SDLC_sofware, p.497]]

[[2_SDLC_sofware.pdf#search=Ejemplo estructura de control secuencial|SDLC_sofware, p.511]]
# 1_**Clasificación y Taxonomía de los Diagramas UML**
![[1_clasi_diagram.png|697]]

1. ==**Diagramas de Estructura (Lo que "es")**== [Pagina 351 ejemplo] [[2_SDLC_sofware.pdf#search=Vistas estáticas|SDLC_sofware, p.446]]
	Representan la parte estática del sistema. Se centran en qué elementos existen y cómo se organizan físicamente o lógicamente.
	
	- **Diagrama de clases:[[2_SDLC_sofware.pdf#search=Diagramas de clase|SDLC_sofware, p.214]]** El más común; muestra las clases (plantillas), sus atributos, métodos y cómo se relacionan entre sí, es una abstracción de un objeto de la vida real. Se representa como un rectángulo dividido en **tres partes**:
	
	- **Diagrama de objetos:** Una "foto" del sistema en un momento específico, mostrando instancias reales de las clases.
	
	- **Diagrama de componentes:** Describe cómo se divide el sistema en módulos físicos (archivos, librerías) y sus dependencias. [[2_SDLC_sofware.pdf#search=Diagrama de componentes|SDLC_sofware, p.450]]
		
		- El documento dice que el diagrama de componentes muestra una **perspectiva estática** del sistema y pertenece a los diagramas estructurales. Representa cómo se organiza el software en términos de componentes lógicos o físicos, como bibliotecas, módulos, paquetes y capas. Además aclara que normalmente se construye después del diagrama de clases.

		 **Qué elementos usa**
		
		```
		COMPONENTE
		→ unidad lógica del sistema
		→ está por encima de las clases
		
		INTERFAZ
		→ punto de comunicación entre componentes
		
		DEPENDENCIA
		→ un componente necesita a otro para trabajar
		
		PAQUETE
		→ agrupa componentes relacionados
		```
		
		La idea central aquí no es infraestructura física, sino **arquitectura interna del software**. Este diagrama te dice cómo se reparte el sistema en partes y qué parte depende de cuál.
		
		### Cómo entenderlo rápido
		
		```
		Sistema
		 ├─ interfaz de usuario
		 ├─ lógica de negocio
		 ├─ base de datos
		 └─ servicios externos
		```
		
		Eso te ayuda a ver el software como módulos que cooperan, no como un bloque gigante.
		

		## Lo que el autor quiere que aprendas con esta sección
		
		No quiere que memorices iconos. Quiere que aprendas a leer el sistema en dos niveles:
		
		```
		nivel 1: infraestructura
		nivel 2: arquitectura interna
		```
		
		Ese salto es muy importante porque un sistema bien hecho no solo tiene código; también tiene una forma clara de distribuirse y de separarse en partes.
	
	- **Diagrama de despliegue (implementación):** Muestra el hardware donde se instalará el software (servidores, nodos, redes).[[2_SDLC_sofware.pdf#search=Diagrama de despliegue|SDLC_sofware, p.447]]
		
		- un diagrama de UML que representa la **arquitectura física** del sistema, tanto en hardware como en software, junto con sus conexiones. O sea: aquí ya no estás mirando “qué hace el sistema”, sino **dónde se ejecuta** y **qué piezas físicas o lógicas participan en su ejecución**.

		  **Qué elementos usa**
			
			```
			NODO
			→ puede ser hardware o software
			→ se dibuja como un cubo
			
			ARTEFACTO
			→ cosas producidas por el desarrollo
			→ bibliotecas, archivos, ejecutables
			
			ASOCIACIÓN DE COMUNICACIÓN
			→ línea que une nodos
			→ muestra por dónde se conectan
			
			DISPOSITIVO
			→ nodo especial
			→ por ejemplo, un servidor
			
			ESPECIFICACIÓN DE DESPLIEGUE
			→ reglas o configuración para poner un artefacto dentro de un nodo
			```
			
			La idea profunda es esta: el diagrama de despliegue te ayuda a responder preguntas como **“¿en qué servidor corre esto?”, “¿qué archivo se instala ahí?”, “¿cómo se conectan los nodos?”**. Es un mapa de infraestructura del sistema.

		 **Cómo entenderlo rápido**
		
		```
		Aplicación   
		↓
		se instala en   
		↓
		Servidor / nodo   
		↓
		se conecta con   
		↓
		otros nodos o dispositivos
		```
		
		En analogía simple: es como mirar un edificio y ver en qué piso está cada cosa, qué cable va a dónde y qué máquina hace qué trabajo.

2. ==**Diagramas de Comportamiento (Lo que "hace")**==

	Describen las funciones del sistema y cómo cambian los datos o el estado con el tiempo.
	
	- **Casos de uso:** Representan las funciones del sistema desde el punto de vista del usuario (el "qué", no el "cómo").
	
	- **Diagrama de actividades:** Similar a un diagrama de flujo; muestra los pasos de un proceso de negocio o algoritmo.
		- ![[33_diagr_actividad.png]]
	
	- Los Componentes (Lo que verás en los dibujos)

		Para entender los diagramas de esas páginas, debes conocer estos símbolos básicos:
		
		- **Círculo Sólido (●):** El Inicio. Solo hay uno por diagrama.
		- **Rectángulo Redondeado:** Representa una **Actividad** (una tarea que el sistema o el usuario hace). Ej: "Validar tarjeta".
		- **Flechas:** Indican el orden o la dirección del flujo.
		- **Rombo (♦):** Un punto de **Decisión**. De aquí salen dos flechas (ejemplo: ¿Hay stock? Sí / No).
		- **Barras Gruesas (Sincronización):** Se usan para mostrar tareas que pasan al mismo tiempo (Paralelismo). se llaman técnicamente **Fork** (Bifurcación) y **Join** (Unión).
		- **Círculo con borde (○):** El Final del proceso	
		
		- **Ejemplo =>** [[2_SDLC_sofware.pdf#search=Ejemplo de diagrama de actividades|SDLC_sofware, p.212]]
		

	- **Diagrama de estado:** Describe los diferentes ciclos de vida de un objeto (por ejemplo, un pedido que pasa de "Pendiente" a "Pagado").

3.  **Diagramas de Interacción (Cómo se "comunican")**

	Son una subcategoría del comportamiento, pero se enfocan específicamente en el intercambio de mensajes entre objetos.
	
	- **Diagrama de secuencia:** Se centra en el orden cronológico de los mensajes (el tiempo fluye de arriba hacia abajo).
	- **Diagrama de colaboración/comunicación:** Similar al de secuencia, pero se organiza alrededor de los objetos y sus enlaces, no del tiempo.
	- **Diagrama de tiempo:** Analiza el comportamiento de los objetos en periodos de tiempo muy precisos (crítico en sistemas de tiempo real).

**4. En la columna de Estructura (Faltan 3)**

- **Diagrama de Perfil:** Permite extender UML para dominios específicos (por ejemplo, crear símbolos propios para modelar sistemas médicos o aeroespaciales).
- **Diagrama de Estructura Compuesta:** Explica la estructura interna de una clase compleja, incluyendo sus "puertos" y "conectores".
- **Diagrama de Paquetes:** Se usa para organizar los elementos del modelo en grupos o carpetas (paquetes) y ver las dependencias entre ellos a gran escala.

**5. En la columna de Interacción (Falta 1)**

- **Diagrama de Visión General de Interacción:** Es una mezcla entre un diagrama de actividades y uno de secuencia. Sirve para ver el flujo general de varias interacciones juntas.


---

> **Dato clave:** En la práctica profesional, no se usan todos a la vez. El **Diagrama de Clases**, el de **Casos de Uso** y el de **Secuencia** suelen ser el "núcleo duro" de cualquier desarrollo.

# 2_ **Diagramas de Clases Estructura de Relaciones y Multiplicidad**

cómo se conectan las entidades y cuántas instancias pueden interactuar entre sí.

![[2_diagra_clases.png]]

	
## ==**1_Relaciones entre clases**==
- Las relaciones entre las diferentes clases indican cómo interactúan los objetos pertenecientes a esas clases
### **2_Asociacion (Las Líneas de Conexión)**

| Elemento      | Qué significa           |
| ------------- | ----------------------- |
| Nombre        | contexto de la relación |
| Rol           | función de cada clase   |
| Navegabilidad | dirección               |
| Multiplicidad | cantidad                |
- Las líneas que unen los cuadros no son simples adornos; representan que una clase "conoce" a la otra.

	- **Asociación:[[2_SDLC_sofware.pdf#search=Asociaciones|SDLC_sofware, p.217]]** Una línea recta indica una relación bidireccional, las conexiones entre clases
		- ![[34_clases_asociacion.png]]
		- ![[34_1_clases_asociacion.png]]



**Multiplicidad:** Indica cuántos objetos de una clase pueden estar vinculados a un objeto de la otra también le dicen cardinalidad a los números

| Notación | Significado                  | Ejemplo                                         |
| -------- | ---------------------------- | ----------------------------------------------- |
| **1**    | Exactamente uno              | Un `DNI` pertenece a exactamente 1 `Persona`.   |
| **0..*** | De cero a muchos (opcional)  | Un `Cliente` puede tener 0 o muchas `Compras`.  |
| **1..*** | Uno o muchos (obligatorio)   | Un `Pedido` debe tener al menos 1 `Producto`.   |
| *****    | Muchos (abreviación de 0..*) | Una `Materia` puede tener muchos `Estudiantes`. |

**Nota técnica:** Las líneas que forman ángulos rectos (estilo ortogonal) son un estándar visual para mantener el diagrama limpio y legible cuando hay muchas conexiones cruzadas.

### **3_Herencia** [[2_SDLC_sofware.pdf#search=Herencia|SDLC_sofware, p.221]]
va de lo **general** a lo **específico**, o sea, de **superclase** a **subclase**. La define como una relación especial de asociación donde la subclase hereda **atributos** y **comportamientos** de la superclase. También aclara que esta relación lleva implícito el sentido **“es un / es una”**, por lo que no se le asigna nombre ni multiplicidad.

- Para qué sirve en un diagrama de clases

	Sirve para **evitar repetir información** y para mostrar una jerarquía clara del dominio. En vez de dibujar varias clases casi iguales, el modelo coloca lo común en una clase más general y deja en las subclases solo lo particular. El libro dice que en herencia pueden existir varios niveles y que cada nivel tiene su superclase y sus subclases. [[2_SDLC_sofware.pdf#search=Ejemplo de herencia múltiple|SDLC_sofware, p.224]]

### 4_Agregación
es una relación del diagrama de clases que expresa un **todo formado por partes**, pero con una diferencia clave: **las partes pueden existir por separado**. No es una unión fuerte; es una relación de pertenencia “suave”. El texto la presenta como un tipo de asociación donde la clase agregada representa el todo y las ot1ras clases son sus componentes.

- ### Qué está diciendo el libro, en limpio

| Punto                              | Explicación                                                                                                     |
| ---------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| **Qué es**                         | Una relación entre una clase “todo” y varias clases “parte”.                                                    |
| **Qué significa**                  | El todo contiene componentes, pero esos componentes no dependen totalmente de él para existir.                  |
| **Cómo se dibuja**                 | Línea con un **rombo vacío** en el lado de la clase agregada.                                                   |
| **Dónde se pone la multiplicidad** | En el lado de los componentes.                                                                                  |
| **Qué tan fuerte es**              | Más débil que la composición.                                                                                   |
| **Para qué sirve**                 | Modelar estructuras donde algo está formado por otras cosas, pero esas cosas pueden cambiar o sobrevivir solas. |

| Computador de Escritorio clase agregada                              | **Torre** puede contener                                               |
| -------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| - monitor,<br>- torre,<br>- teclado,<br>- ratón,<br>- dos parlantes. | - discos duros,<br>- memorias,<br>- procesador,<br>- tarjeta de video. |

Lo importante aquí es que esos componentes **pueden ser parte de otras clases** y pueden **sustituirse fácilmente**, por eso la relación no es muy fuerte.

#### Cómo entenderlo de verdad

Piensa así:

```
Computador de escritorio   
		├── Monitor   
		├── Torre   
		├── Teclado   
		├── Ratón   
		└── Parlantes
```

La relación dice:

- el computador **tiene** partes,
- pero si cambias el teclado o el monitor, el computador sigue siendo el mismo tipo de objeto,
- y esas partes pueden existir en otro contexto.

Eso es lo que la hace **agregación** y no composición.

#### ¿Para qué sirve en un diagrama de clases?

Sirve para representar un modelo del mundo real donde:

- una entidad agrupa otras,
- las partes no están “atadas de por vida” al todo,
- y el sistema necesita mostrar esa relación sin exagerarla como si fuera dependencia total.
[[2_SDLC_sofware.pdf#search=jemplo de relación de Agregación|SDLC_sofware, p.226]]

### 5_Composición
**Composición** es la versión **más fuerte** de la relación todo-parte dentro del diagrama de clases un tipo particular de agregación donde los componentes **no pueden pertenecer a más de una composición**; es decir, son **exclusivos** del todo al que pertenecen. Además, señala que se representa con un **rombo negro relleno** en el lado de la clase que hace de “todo”. [[2_SDLC_sofware.pdf#search=Ejemplo de relación de Composición|SDLC_sofware, p.227]]

- ### Qué significa realmente

La idea central es esta:

```
si destruyes el todo,las partes dejan de existir como parte de ese todo
```

Eso la diferencia totalmente de la agregación.


- ### Lo que dice el libro, traducido a lenguaje claro

|Aspecto|Composición|
|---|---|
|**Tipo de relación**|Todo-parte fuerte|
|**Dependencia**|Muy alta|
|**Existencia de las partes**|Dependen del todo|
|**Pertenencia**|Exclusiva|
|**Símbolo UML**|Rombo negro relleno|
|**Idea mental**|“Si el todo desaparece, la parte también”|

---

- ### Ejemplo simple

Piensa en una **Casa** y sus **Habitaciones**.

```
Casa ├── Habitación 1 ├── Habitación 2 └── Habitación 3
```

Aquí la relación es de composición porque:

- una habitación forma parte de esa casa,
- no tiene sentido modelarla como parte viva de otra casa al mismo tiempo,
- si la casa se elimina, esas habitaciones dejan de existir dentro de ese modelo.

Eso encaja con la definición del libro: componentes exclusivos de la composición.

---

- ### Ejemplo más cercano a software

Un **Pedido** y sus **Detalles de pedido**.

- El pedido es el todo.
- Los detalles son las partes.
- Si eliminas el pedido, los detalles ya no tienen sentido por sí solos dentro del sistema.

Eso es composición.

---

- ### Cómo no confundirla con agregación

|Relación|¿La parte puede vivir sola?|Ejemplo|
|---|---|---|
|**Agregación**|Sí|Computador y teclado|
|**Composición**|No|Casa y habitaciones|

La agregación es más flexible; la composición es más estricta. El libro presenta justamente esta diferencia al decir que en agregación los componentes pueden sustituirse con facilidad, mientras que en composición la exclusividad de pertenencia es la característica distintiva.

---

- ### Qué está intentando enseñarte el documento

No está solo enseñando símbolos UML. Está enseñándote a pensar así:

```
¿Esta parte depende de ese todo?¿Puede existir sola?¿Puede pertenecer a varios todos?
```

Si la respuesta es:

- **sí puede existir sola** → agregación,
- **no puede existir sola** → composición.

Ese es el filtro mental correcto.
## 2_**Componentes Atómicos del Modelado Estático**. 
- ![[3_componentes_atómicos.png]]


- **1. Clases:**  
    Son las "plantillas" o moldes de los objetos. En la imagen anterior, eran todos los rectángulos. Una clase define qué datos tendrá un objeto (atributos) y qué podrá hacer (métodos). Es el bloque básico de construcción.
- **2. Relaciones:**  
    Son las líneas que conectan los rectángulos en la imagen previa. Sin ellas, solo tendrías elementos aislados. Las relaciones explican cómo colaboran los objetos entre sí (por ejemplo: un "Cliente" _posee_ una "Cuenta", o un "Gato" _es un_ "Animal").
- **3. Interfaces:**  
    Este es un concepto más avanzado que no se distinguía a simple vista en la imagen anterior. Una interfaz es un "contrato". No dice _quién_ es el objeto, sino _qué es capaz de hacer_.[[1_Conceptos_poo#19_Abstracción y Interfaz]]
    - _Ejemplo:_ Una interfaz llamada `Volador` puede ser aplicada a una clase `Avión` y a una clase `Pájaro`. Ambas son cosas distintas, pero ambas "firman el contrato" de que saben volar.

---
**Diferencia Clave**
En la imagen anterior vimos **clases y relaciones**, pero las **interfaces** suelen graficarse de forma distinta (a veces como un círculo o con la palabra clave `<<interface>>`). Son fundamentales para que el software sea flexible y fácil de actualizar.

### **Anatomía Interna y Estructura de una Clase en UML**
explicando qué debe ir dentro para que un programador pueda entenderlo y convertirlo en código real.

 - **Superior:** Nombre de la clase (ej. `Usuario`, `Factura`).
 - **Media:** Atributos (características como `nombre`, `precio`).
- **Inferior:** Métodos o funciones (acciones como `guardar()`, `calcularTotal()`).


![[4_estructura_clase.png]]

![[2_1_diagra_clases.png]]

Una clase en UML es un compartimento estandarizado. Cada sección tiene una regla específica:

1. ==**Nombre de la Clase (Sección Superior)**==

	- Es el identificador único.
	- **Regla de oro:** Siempre se escribe en **Sustantivo** y en **Singular** (ej. `Factura`, no `Facturas` ni `ImprimirFactura`).
	- Suele usarse la convención _PascalCase_ (Primera letra de cada palabra en mayúscula).
	-  excepciones técnicas que podrías encontrar:
		1. Estereotipos (Las "Etiquetas")
		
			A veces verás palabras entre comillas angulares sobre el nombre, así: `<<interface>>`. Esto sirve para avisar que esa clase no es una clase normal, sino un tipo especial (como una interfaz o una clase abstracta).
			
		2. Paquetes (La "Ruta")
		
			Si el sistema es gigante, a veces se pone el nombre del grupo al que pertenece arriba del nombre de la clase. Por ejemplo:  
			`Administracion::Personal`  
			Esto indica que la clase `Personal` está dentro del módulo de `Administracion`.
		
		3. Propiedades de la Clase
		
			En casos muy específicos, se puede indicar si la clase es **Abstracta** (poniendo el nombre en _cursiva_). Una clase abstracta es una que no se puede "crear" directamente, sino que sirve de base para otras (por ejemplo, `Personal` podría ser abstracta y de ella derivan `Medico` y `Enfermero`).

2. ==**Atributos de la Clase (Sección Media)**==

	- Son las características o datos que definen al objeto (su estado).
	- **Ejemplo:** Si la clase es `Coche`, los atributos serían `color`, `marca`, `modelo`, `velocidadActual`.
	- En un diagrama real, aquí también se indica el **tipo de dato** (ej. `precio: Float`) y la **visibilidad** (+ para público, - para privado).
	
	- **Ejemplo:**
		- 1. **El Formato Estándar**
	
			La forma correcta de escribir un atributo en UML 2.0 en adelante es:
	
			**`visibilidad nombreAtributo : tipoDeDato = valorInicial`**
			
			- **Visibilidad:** Se indica con un símbolo (+ para público, - para privado, # para protegido).
			- **Nombre:** Se escribe primero, empezando en minúscula (convención _camelCase_).
			- **Tipo de dato:** Se pone **DESPUÉS** del nombre, separado por **dos puntos (:)**.
			- **Valor inicial:** Es opcional; se usa si quieres que el dato empiece con algo específico.
			4. Ejemplo práctico: Clase `Medicamento`

		2. **Si estuviéramos modelando de un hospital, la sección de atributos se vería así:**
			
			- `- nombre : String` (Un texto para el nombre del remedio)
			- `- miligramos : Integer` (Un número entero para la dosis)
			- `- requiereReceta : Boolean` (Un valor de verdadero/falso)
			- `- precio : Double = 0.0` (Un número con decimales que empieza en cero)
		
		
		3. **¿Va algo más?**
		
			Aparte del nombre y el tipo, hay tres cosas "extra" que podrías ver o necesitar:
			
			1. **Multiplicidad (Arreglos):** Si un atributo guarda una lista de cosas, se pone entre corchetes.
			    - Ejemplo: `componentes : String [1..*]` (Significa que el medicamento tiene una lista de uno o más componentes).
			    
			2. **Atributos Estáticos (Subrayados):** Si ves un atributo subrayado, significa que ese valor es compartido por todos los objetos de esa clase (ej. `iva : Double`).
			
			3. **Atributos Derivados (/):** Si empieza con una barra inclinada, significa que el valor se calcula a partir de otros.
			    - Ejemplo: `/edad : Integer` (No se guarda la edad, se calcula restando la fecha actual de la fecha de nacimiento).
		
		4. Recuerda siempre este orden: **¿Quién lo ve?  Nombre : ¿Qué es?**  
			`- stock : Integer`
	
3. ==**Operaciones o Métodos de la Clase (Sección Inferior)**==
	
	- También llamados **Métodos**. Es el comportamiento del objeto (lo que puede hacer).
	- **Ejemplo:** Para el `Coche`, las operaciones serían `acelerar()`, `frenar()`, `encender()`.
	- Representan las funciones que transforman o utilizan los atributos de la sección media.
	
	1. **El Formato Estándar**

		En UML, una operación se escribe así:

	   **`visibilidad nombreMetodo (parámetro : tipo) : tipoRetorno`**
	
		- **Visibilidad:** Igual que en los atributos (`+`, `-`, `#`). La mayoría de los métodos suelen ser **públicos (`+`)** porque son la forma en que otros objetos interactúan con la clase.
		- **Nombre del método:** Se escribe en _camelCase_ (ej. `calcularDosis`). **Importante:** A diferencia de las clases, aquí usamos **verbos** porque indican una acción.
		- **Parámetros (entre paréntesis):** Son los datos que el método necesita para trabajar. Se escriben igual que los atributos (`nombre : tipo`). Si no necesita nada, los paréntesis van vacíos `()`.
		- **Tipo de Retorno:** Se pone al final, después de dos puntos. Es el resultado que nos devuelve la función tras ejecutarse.

	2. **Ejemplo: Clase `Medicamento`**
	
		Siguiendo con tu ejemplo del hospital, así se vería la tercera sección:
		
		- `+ actualizarStock(cantidad : Integer)` : No devuelve nada, solo cambia el inventario.
		- `+ aplicarDescuento(porcentaje : Double) : Double` : Recibe un número y nos devuelve el precio final calculado.
		- `+ verificarVencimiento() : Boolean` : No recibe datos, pero nos responde con un "Sí" o "No" (True/False).

	2. **¿Qué más puede aparecer en esta sección?**
	
		Además de la firma básica, podrías encontrar:
		
		1. **Métodos Abstractos (en cursiva):** Indica que el método está definido pero no programado aún (se programará en las clases hijas).
		2. **Constructores:** A veces verás un método con el mismo nombre de la clase, como `+ Medicamento()`. Su función es "crear" el objeto desde cero.
		3. **Niveles de Abstracción:** Al igual que en los atributos, si un método está **subrayado**, significa que es **Estático** (se puede usar sin necesidad de crear un objeto de esa clase).



       ![[6_visibile.png]]  
# 3_**Tipología de Vínculos y Semántica de Relaciones en UML**

 cuatro tipos de conexiones fundamentales que definen cómo una clase depende, contiene o hereda de otra. Es el mapa de "comportamiento social" de los objetos.
![[7_relaciones.png]]

1. **Agregación (Rombo Blanco)**

	Representa una relación de "todo y sus partes", pero con un **vínculo débil**.
	
	- **Concepto:** Una clase contiene a la otra, pero ambas pueden existir por separado.
	- **Ejemplo Hospital:** Una `SalaDeEspera` tiene `Sillas`. Si el hospital cierra la sala, las sillas siguen existiendo y pueden llevarse a otro lado.
	- **En código:** Si eliminas el objeto "Padre", el objeto "Hijo" **no** se destruye.
		![[13_agregacion.png]]

2. **Composición (Rombo Negro)**

	Es una relación de "todo y sus partes" con un **vínculo fuerte** y vital.
	
	- **Concepto:** La parte es propiedad exclusiva del todo. Si el "todo" desaparece, la "parte" también.
	- **Ejemplo Hospital:** Un `Hospital` tiene `Pisos`. Si destruyes el edificio del hospital, los pisos dejan de existir físicamente.
	- **En código:** El objeto "Hijo" tiene el mismo ciclo de vida que el "Padre". Si borras uno, borras ambos.![[14_composicion.png]]![[14_1_composicion.png]]

3. **Herencia / Generalización (Flecha de Triángulo Vacío)**

	Representa la relación "es un tipo de". Es la base de la reutilización de código.
	
	- **Concepto:** Una clase hija hereda todos los atributos y métodos de la clase madre, pero añade los suyos propios.
	- **Ejemplo Hospital:** Un `Cirujano` **es un** `Médico`. El cirujano tiene todo lo que tiene un médico, más sus habilidades específicas de quirófano.
	- **Visual:** La flecha siempre apunta hacia la clase "Madre" (la más general).
	- ![[16_herencia.png]]
	

4. **Dependencia (Flecha Discontinua)**

	Es la relación más débil y temporal de todas.
	
	- **Concepto:** Una clase utiliza a otra momentáneamente para realizar una tarea, pero no la "posee".
	- **Ejemplo Hospital:** Un `Médico` usa un `Termómetro` para tomar la temperatura. El médico no "es" un termómetro, ni el termómetro "es parte" del médico; solo lo necesita un momento.
	- **En código:** Suele aparecer cuando una clase recibe a otra como un parámetro dentro de un método.
	- ![[15_dependencia.png]]
	

 5. **La Asociación Binaria: El Vínculo Base entre Objetos**
 
    ![[8_asociación_binaria.png]]
	- **1. ¿Qué es una Relación Binaria?**  
		    Se llama así porque conecta exactamente a **dos** clases (bi-). Es el tipo de relación más común. Indica que un objeto de la clase "Padre" tiene una referencia o sabe de la existencia de un objeto de la clase "Hijo".
	- **2. El peso de los nombres (Padre e Hijo):**  
	    Aquí hay un detalle importante. Aunque la imagen usa estos nombres, en UML una línea recta simple **no siempre significa herencia**.
	    - Si fuera **Herencia**, debería tener la flecha de triángulo que vimos antes.
	    - Al ser solo una línea, nos dice que hay una **conexión estructural**. Por ejemplo: un `Padre` (clase) posee un `Hijo` (clase) como un dato dentro de su sección de atributos.
	- **3. La Ausencia de Flechas (Bidireccionalidad):**  
	    Cuando la línea no tiene puntas de flecha en ningún extremo (como en esta imagen), se asume que es **bidireccional**.
	    - El Padre conoce al Hijo.
	    - El Hijo conoce al Padre.
	    - Ambos pueden enviarse mensajes entre sí.

6. **La Relación Ternaria: Coordinación de Múltiples Entidades**
	 Pasamos de conexiones entre dos elementos a una relación donde tres piezas deben encajar al mismo tiempo para que la lógica tenga sentido. La **Ternaria** se utiliza cuando una acción o evento no puede explicarse simplemente uniendo dos clases; requiere de una tercera para estar completa.
    ![[9_relacion_ternaria.png]]
	 
	 **1. El Concepto de "Grado 3":**  
	    En UML, el "grado" de una relación es el número de clases que participan. Aquí el grado es 3. La línea que se une en el centro indica que las tres clases están amarradas a un mismo contexto: una **Venta** o **Transacción**.
	
	 **2. La Lógica de Interdependencia:**  
	    El diagrama nos dice que para que exista un registro válido, necesitas obligatoriamente a los tres:
		    - No hay venta si hay **Vendedor** y **Producto** pero no hay **Cliente**.
		    - No hay venta si hay **Cliente** y **Producto** pero no hay un **Vendedor** que procese.
		    - No hay venta si hay **Vendedor** y **Cliente** pero no se intercambia un **Producto**.
		    
	**3. Representación Visual:**  
	    Aunque en esta imagen las líneas se unen en un punto simple, en el estándar UML oficial avanzado, este tipo de relación suele representarse con un **rombo grande en el centro** donde convergen las tres líneas. Esto ayuda a no confundirla con simples líneas cruzadas.


	**¿Cómo se aplica a tu ejemplo del Hospital?**
	
	Este es el ejemplo perfecto para situaciones complejas en tu hospital. Imagina una **Cita Médica**:
	1. **Clase 1:** Médico.
	2. **Clase 2:** Paciente.
	3. **Clase 3:** Consultorio.
	
	Si quieres registrar la cita, necesitas saber qué médico atendió a qué paciente y en qué lugar físico ocurrió. Si quitas cualquiera de los tres, la información de la "Cita" queda incompleta. Eso se dibuja exactamente como esta imagen.
	
	**¿Tiene relación con las anteriores?**
	
	**Sí.** Es la evolución de la "Asociación Binaria" que vimos justo antes. Mientras que la binaria es una charla entre dos personas, la ternaria es una **reunión de tres**.
	
 	 >**Nota para tu aprendizaje:** Las relaciones ternarias son más difíciles de programar, por lo que los analistas de sistemas intentan evitarlas a menos que sean estrictamente necesarias para la lógica del negocio.

7. **Asociación Dual o Múltiple: Roles Diferenciados entre Clases**
	Esto ocurre cuando una misma pareja de clases interactúa en contextos distintos y cada conexión tiene un significado semántico único.
	![[10_relacion_doble.png]]
	
	**1. El Concepto de Roles:**  
	    En UML, cuando hay más de una línea entre dos clases, es obligatorio ponerle un **nombre a la relación** (o rol) para no confundirlas. En tu imagen, los roles son:
	    - **Capital:** Define una jerarquía administrativa específica.
	    - **Pertenece:** Define una relación de ubicación o contenedor general.
	 **2. Diferenciación de Lógica:**
	    - **Línea Superior (Capital):** Es una relación **1 a 1**. Un país solo tiene una ciudad capital, y esa ciudad solo es capital de un país. Es una relación restrictiva y especial.
	    - **Línea Inferior (Pertenece):** Es una relación de **1 a muchos**. Muchas ciudades pertenecen al mismo país. Es una relación de inclusión general.
	**3. ¿Por qué no usar una sola línea?**  
	    Si usáramos una sola línea, el sistema no sabría distinguir entre una ciudad cualquiera (como Rosario) y la ciudad principal (como Buenos Aires). Al duplicar la línea, permitimos que el objeto `País` tenga un atributo especial llamado `capital` que apunta a una única `Ciudad`.
	
	**¿Cómo se aplica a tu ejemplo del Hospital?**
	
	Este concepto es vital para tu modelo del hospital. Imagina las clases **`Médico`** y **`Paciente`**:
	
	1. **Relación 1 (Tratamiento):** El médico atiende al paciente (relación profesional estándar).
	2. **Relación 2 (Seguimiento):** El médico es el "Médico de Cabecera" del paciente (un vínculo más permanente y de mayor responsabilidad).
	
	Si un médico atiende a 50 personas, pero solo es médico de cabecera de 5, necesitas **dos líneas** para que el software pueda llevar ese control por separado.

8. **Asociación Reflexiva: Autorelación e Interacción entre Instancias**. 

	La **Relación Reflexiva** (o recursiva) ocurre cuando una línea de asociación sale de una clase y vuelve a entrar en la **misma clase**. Esto no significa que un objeto se relacione con "sí mismo" (aunque podría), sino que un objeto de esa clase se relaciona con **otro objeto de su misma especie**.![[11_relacion_flexiba.png]]
	
	- **1. El Concepto de Instancia:**  
	    Para entender esto, imagina que la clase es el molde "Persona". En el mundo real, tenemos dos objetos creados con ese molde: _Juan_ y _María_. La línea "Pareja" indica que _Juan_ (objeto A) está vinculado con _María_ (objeto B). Ambos son de la clase **Persona**.
	- **2. El Rol de la Relación:**  
	    En la imagen, la palabra **"Pareja"** es el rol. Indica la función que cumple un objeto respecto al otro dentro de la misma clase. Sin este nombre, no sabríamos por qué una persona está conectada con otra.
	- **3. Importancia en la Jerarquía:**  
	    Este tipo de relación es la que permite crear estructuras complejas como árboles genealógicos o jerarquías laborales sin necesidad de crear cientos de clases diferentes.

		**¿Cómo se aplica a tu ejemplo del Hospital?**
		
		Este concepto es perfecto para resolver problemas de organización interna. Imagina la clase **`Empleado`**:
		
		1. **Relación de Supervisión:** Un `Empleado` (el Jefe) supervisa a otros `Empleados` (los Subordinados).
		    - No necesitas una clase "Jefe" y una clase "Subordinado" porque, al final del día, ambos son empleados con sueldo, legajo y horario.
		    - Simplemente dibujas una **flecha reflexiva** sobre la clase `Empleado` con el rol "Supervisa".
		2. **Relación de Reemplazo:** Un `Médico` puede tener asignado a otro `Médico` como "Suplente" en caso de emergencia. Es una relación entre dos objetos de la misma clase.
		
		**¿Tiene relación con las anteriores?**
		
		**Sí.** Es el caso especial de la **Asociación Binaria** que vimos hace poco. La diferencia es que, mientras la binaria unía dos rectángulos distintos, esta es una línea que "da la vuelta" sobre el mismo rectángulo.
		
      > **Dato técnico:** En estas relaciones es vital la **Multiplicidad**. Por ejemplo, en el caso de "Pareja", la multiplicidad en ambos extremos suele ser **0..1**, ya que una persona puede estar soltera o tener exactamente una pareja.
      
# 4_**Cardinalidad y Multiplicidad en la Asociación de Clases**
Esta imagen explica cómo cuantificar la relación entre dos entidades. Es el "contrato de cantidad" que dicta cuántos objetos pueden participar en una interacción.
![[12_cardinalidad.png|585]]


1. **Cardinalidad (o Multiplicidad):**  
    Son los números o letras (`1` y `n`) situados en los extremos de la línea.
    - **El `1` en Empresa:** Indica que, en este modelo, un empleado pertenece a **exactamente una** empresa. No puede trabajar en dos a la vez según este diagrama.
    - **La `n` en Empleado:** Representa "muchos". Indica que una empresa puede tener un número indefinido de empleados contratados.
    
	    1. Los Números Fijos

			- **`1` (Uno exactamente):** Solo puede haber un objeto vinculado. Ni cero, ni dos. (Ejemplo: Un `País` tiene exactamente `1` `Capital`).
			- **`0` (Cero):** Se usa rara vez solo, generalmente es parte de un rango. Indica que no hay relación.
			- **`n` o `m` (Número específico):** A veces verás un número como `4`. (Ejemplo: Un `Coche` tiene exactamente `4` `Ruedas`).
			
			---
			
		2. Los Rangos (Mínimo .. Máximo)
		
			Esta es la forma más común porque define límites:
			
			- **`0..1` (Cero o uno):** Es opcional. El objeto puede existir sin el otro, o tener máximo uno. (Ejemplo: Una `Persona` puede tener `0` o `1` `Cónyuge`).
			- **`1..1` (Uno y solo uno):** Es lo mismo que poner solo `1`. Es obligatorio y único.
			- **`1..*` (Uno a muchos):** Es obligatorio. Debe haber al menos uno, pero no hay límite máximo. (Ejemplo: Un `Pedido` debe tener al menos `1` `Producto`).
			- **`0..*` (Cero a muchos):** Es totalmente flexible. Puede no haber nada o haber miles.
		
			---
			
		1. Los Signos Especiales
		
			- **`*` (El Asterisco):** Es la abreviatura de `0..*`. Significa "muchos" sin restricciones. Es el que más verás en programación.
			- **`..` (Puntos suspensivos):** Se usan para separar el valor mínimo del máximo.
			- **`,` (Coma):** Se usa para listas discretas. Si ves `2, 4, 6`, significa que la relación solo puede ser de 2, 4 o 6 objetos, nada más.

2. Rangos Personalizados

	UML te permite ser muy específico si el negocio lo requiere:
	
	- **`2..4`:** De dos a cuatro. (Ejemplo: Un `Trío Musical` puede tener de `2` a `4` `Integrantes` si aceptan invitados).
	- **`5..*`:** Mínimo cinco, máximo infinito.
	
	- **2. Nombre de la Asociación (`-Contrata-`):**  
	    UML permite colocar un verbo en medio de la línea para explicar la naturaleza de la relación. En este caso, el verbo "Contrata" aclara que el vínculo es de tipo laboral y no, por ejemplo, de subcontratación o consultoría externa.
	    
	- **3. Dirección de la Lectura:**  
	    Aunque no tiene flecha, el nombre entre guiones indica una lectura lógica: _"La Empresa contrata n Empleados"_. Esto ayuda a que personas que no son programadores entiendan el diagrama rápidamente.

# 5_**Variaciones y Estereotipos de Clase**
Aparte de la **Interfaz**, el estándar UML define otros "tipos" de clases especiales para organizar mejor el software:
![[17_estereotipos.png|239]]

**1. Clase Abstracta**

Es similar a la interfaz pero puede tener algo de código real.

- **Identificación:** El nombre de la clase se escribe en _cursiva_ o se usa el estereotipo `<<abstract>>`.
- **Uso:** Sirve como una "base" incompleta. Por ejemplo, en tu hospital, `Personal` sería una clase abstracta porque nadie es "solo personal"; eres o `Médico` o `Enfermero`.

**2. Clase de Enumeración (`<<enumeration>>`)**

Se usa para listas de valores fijos que no cambian.

- **Estructura:** Solo tiene el nombre y una lista de valores en la sección de atributos.
- **Ejemplo Hospital:** `<<enumeration>> Especialidad` con los valores: `Pediatría`, `Traumatología`, `Cardiología`.

**3. Clase de Utilidad (`<<utility>>`)**

Es una clase que no crea objetos, sino que solo contiene herramientas o cálculos matemáticos.

- **Ejemplo:** Una clase llamada `CalculadorImpuestos` que solo tiene fórmulas.

**4. Los Estereotipos de Análisis (El "Trío Dinámico")**

Cuando se diseña la arquitectura de un sistema, se usan tres tipos específicos para separar responsabilidades:

|Estereotipo|Icono Alternativo|Función|
|---|---|---|
|**`<<boundary>>`**|Círculo con línea (L)|**Frontera:** La pantalla o interfaz que ve el usuario.|
|**`<<control>>`**|Círculo con flecha arriba|**Control:** El "cerebro" que procesa la lógica entre la pantalla y los datos.|
||Círculo con línea abajo|**Entidad:** El objeto que guarda la información (como la Base de Datos).|


# 6_Modelo de análisis 
- ![[18_modelo_analisis.png]]

# 7_Herramientas CASE
significa **Computer Aided Software Engineering**, o sea, **Ingeniería de Software Asistida por Computadora**. El texto dice que son un conjunto de herramientas que automatizan tareas de desarrollo y buscan ofrecer un sistema integrado que conecte y automatice las fases del ciclo de vida del software.

## 1) Qué es CASE, en limpio

CASE no es un diagrama ni una metodología. Es un **ecosistema de herramientas** para apoyar el desarrollo de software. El documento insiste en que antes muchas tareas eran manuales, pero que la ingeniería de software moderna necesita herramientas más sofisticadas para responder a las exigencias actuales. Además, resalta que CASE ayuda a integrar la calidad desde la fase de diseño, antes de construir el producto.

|Tipo|Nombre|Para qué se usan|
|---|---|---|
|**Integradas**|**I-CASE**|Cubren todo el ciclo de vida; también las llaman CASE de trabajo en equipo|
|**Alto nivel**|**U-CASE / Front-end**|Apoyan análisis y diseño|
|**Bajo nivel**|**L-CASE / Back-end**|Apoyan construcción e implementación|
|**Juegos de herramientas**|**Tools-Case**|Automatizan una tarea específica; son herramientas independientes|
## 4) Qué significa cada categoría

### I-CASE

El libro dice que son las más completas: abarcan **todos los aspectos del ciclo de vida**. O sea, sirven para acompañar el proyecto desde lo inicial hasta lo final.

### U-CASE

Son las de **alto nivel** y se usan en las etapas tempranas: **análisis y diseño**. Aquí encajan los diagramas, el modelado y la especificación.

### L-CASE

Son las de **bajo nivel** y ayudan en construcción e implementación, cuando ya se está programando o armando el sistema.

### Tools-Case

Son herramientas más específicas, una sola actividad o tarea. El libro las describe como el tipo más simple, útil para automatizar un trabajo puntual.

## 5) Qué herramientas menciona el libro

El material lista varias herramientas CASE usadas en distintos ámbitos. Entre las más citadas están:

- **ERwin**
- **ArgoUML**
- **Easy Case**
- **Oracle Designer**
- **Power Designer**
- **System Architect**
- **SNAP**
- **Gliffy**
- **MagicDraw**
- **Lucidchart**
- **Papyrus UML**
- **Modelio**
- **StarUML**
- **Dia**
- **MonoUML**