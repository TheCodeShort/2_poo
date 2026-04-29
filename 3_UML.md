[[1_poo.pdf#search=tema: Interfaces y Clases Abstractas|1_poo, p.36]]

# 1_**Clasificación y Taxonomía de los Diagramas UML**
![[1_clasi_diagram.png|697]]

**1. Diagramas de Estructura (Lo que "es")**

Representan la parte estática del sistema. Se centran en qué elementos existen y cómo se organizan físicamente o lógicamente.

- **Diagrama de clases:** El más común; muestra las clases (plantillas), sus atributos, métodos y cómo se relacionan entre sí.
- **Diagrama de objetos:** Una "foto" del sistema en un momento específico, mostrando instancias reales de las clases.
- **Diagrama de componentes:** Describe cómo se divide el sistema en módulos físicos (archivos, librerías) y sus dependencias.
- **Diagrama de implementación (despliegue):** Muestra el hardware donde se instalará el software (servidores, nodos, redes).

**2. Diagramas de Comportamiento (Lo que "hace")**

Describen las funciones del sistema y cómo cambian los datos o el estado con el tiempo.

- **Casos de uso:** Representan las funciones del sistema desde el punto de vista del usuario (el "qué", no el "cómo").
- **Diagrama de actividades:** Similar a un diagrama de flujo; muestra los pasos de un proceso de negocio o algoritmo.
- **Diagrama de estado:** Describe los diferentes ciclos de vida de un objeto (por ejemplo, un pedido que pasa de "Pendiente" a "Pagado").

**3. Diagramas de Interacción (Cómo se "comunican")**

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

# 2_ **Estructura de Relaciones y Multiplicidad en Diagramas de Clases**

cómo se conectan las entidades y cuántas instancias pueden interactuar entre sí.
![[2_relaciones_multiplicidad.png]]

1. ** La Anatomía de la Clase (Los rectángulos)**

	- **Superior:** Nombre de la clase (ej. `Usuario`, `Factura`).
	- **Media:** Atributos (características como `nombre`, `precio`).
	- **Inferior:** Métodos o funciones (acciones como `guardar()`, `calcularTotal()`).

2. ** Las Líneas de Conexión (Asociaciones)**

	Las líneas que unen los cuadros no son simples adornos; representan que una clase "conoce" a la otra.
	
	- **Asociación simple:** Una línea recta indica una relación bidireccional.
	- **Navegabilidad:** La línea con una **punta de flecha** (como se ve en la parte inferior derecha) indica que una clase conoce a la otra, pero no necesariamente al revés.

3. **El concepto crítico: Multiplicidad (Los números)**

	Indica cuántos objetos de una clase pueden estar vinculados a un objeto de la otra también le dicen cardinalidad a los números:

|Notación|Significado|Ejemplo|
|---|---|---|
|**1**|Exactamente uno|Un `DNI` pertenece a exactamente 1 `Persona`.|
|**0..***|De cero a muchos (opcional)|Un `Cliente` puede tener 0 o muchas `Compras`.|
|**1..***|Uno o muchos (obligatorio)|Un `Pedido` debe tener al menos 1 `Producto`.|
|*****|Muchos (abreviación de 0..*)|Una `Materia` puede tener muchos `Estudiantes`.|
- **¿Qué nos dice este diagrama?**
	- Al ver tantas relaciones de **1..*** y *****,estamos ante un sistema complejo con muchas dependencias. Por ejemplo, la clase central parece ser un "corazón" del sistema, ya que tiene múltiples conexiones de tipo "uno a muchos", lo que sugiere que es una entidad que coordina o agrupa a varias otras.
	
> 	**Nota técnica:** Las líneas que forman ángulos rectos (estilo ortogonal) son un estándar visual para mantener el diagrama limpio y legible cuando hay muchas conexiones cruzadas.


4. **Componentes Atómicos del Modelado Estático**. 
	![[3_componentes_atómicos.png]]


- **1. Clases:**  
    Son las "plantillas" o moldes de los objetos. En la imagen anterior, eran todos los rectángulos. Una clase define qué datos tendrá un objeto (atributos) y qué podrá hacer (métodos). Es el bloque básico de construcción.
- **2. Relaciones:**  
    Son las líneas que conectan los rectángulos en la imagen previa. Sin ellas, solo tendrías elementos aislados. Las relaciones explican cómo colaboran los objetos entre sí (por ejemplo: un "Cliente" _posee_ una "Cuenta", o un "Gato" _es un_ "Animal").
- **3. Interfaces:**  
    Este es un concepto más avanzado que no se distinguía a simple vista en la imagen anterior. Una interfaz es un "contrato". No dice _quién_ es el objeto, sino _qué es capaz de hacer_.[[1_conceptos#19_Abstracción y Interfaz]]
    - _Ejemplo:_ Una interfaz llamada `Volador` puede ser aplicada a una clase `Avión` y a una clase `Pájaro`. Ambas son cosas distintas, pero ambas "firman el contrato" de que saben volar.

---
**Diferencia Clave**
En la imagen anterior vimos **clases y relaciones**, pero las **interfaces** suelen graficarse de forma distinta (a veces como un círculo o con la palabra clave `<<interface>>`). Son fundamentales para que el software sea flexible y fácil de actualizar.

5. **Anatomía Interna y Estructura de una Clase en UML**
explicando qué debe ir dentro para que un programador pueda entenderlo y convertirlo en código real.

![[4_estructura_clase.png]]

Una clase en UML es un compartimento estandarizado. Cada sección tiene una regla específica:

1. **Nombre de la Clase (Sección Superior)**

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

2. **Atributos de la Clase (Sección Media)**

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
	
3. **Operaciones o Métodos de la Clase (Sección Inferior)**
	
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