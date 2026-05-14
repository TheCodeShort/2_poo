[[2_SDLC_sofware.pdf#search=Conceptos generales de bases de datos|SDLC_sofware, p.354]]
# 1_Conseptos 

una base de datos es un **almacén de información** que se crea para guardar grandes volúmenes de datos de forma organizada y poder recuperarlos con facilidad. Desde ahí, el texto te prepara para ver bases de datos como una solución pensada para cumplir necesidades de información reales de una organización, no como un archivo suelto ni como una hoja aislada.

La intención del autor es que entiendas una diferencia clave: en sentido amplio, hasta Excel, una lista de contactos o un conjunto de archivos organizados pueden parecer bases de datos; pero en **desarrollo de software** el término se usa con más rigor para hablar de información almacenada en grandes cantidades, estructurada y administrada por un **Sistema de Gestión de Bases de Datos**. Ese matiz es importante porque después todo el módulo se apoya en esa idea: no basta con guardar datos, hay que **administrarlos bien**.

Luego entra el concepto que suele pasar desapercibido y que en realidad es la columna vertebral del diseño: los **metadatos**. El documento te está diciendo que una base de datos no solo guarda información, sino también una descripción precisa de esa información: qué es cada dato, cómo se interpreta, qué tipo tiene y cómo debe almacenarse. A eso se le relaciona con el **diccionario o catálogo de datos**, que es básicamente la ficha técnica de la base de datos. Sin metadatos, los datos existen; con metadatos, los datos se vuelven diseñables, verificables y mantenibles.

- ## Los **metadatos** 
- 
	son técnicamente definidos como **"datos sobre los datos"**. En el contexto de las bases de datos, son la información oculta que describe cómo está estructurada, organizada y gobernada tu base de datos.
	
	Sin los metadatos, tu motor de base de datos solo vería un montón de texto y números sin sentido.
	
	🗺️ **El Diccionario de Datos: El hogar de los metadatos**
	
	En las bases de datos relacionales, los metadatos se agrupan en un componente llamado **Diccionario de Datos** (o catálogo del sistema). Este almacena de forma automática:
	
	- **Estructuras:** Nombres de tablas, nombres de columnas y sus tipos de datos (entero, texto, fecha).
	- **Restricciones:** Cuáles columnas son Llaves Primarias (PK), cuáles son Llaves Foráneas (FK) y qué valores son obligatorios (`NOT NULL`).
	- **Seguridad:** Qué usuarios tienen permisos para ver, editar o borrar tablas específicas.
	- **Rendimiento:** Qué índices existen para acelerar las búsquedas de información.
	
	💡 Ejemplo práctico para entenderlo
	
	Imagina una tabla llamada `Clientes`.
	
	- **Los Datos:** `1`, `Juan Pérez`, `juan@email.com`, `2026-05-12`.
	- **Los Metadatos:**
	    - La primera columna se llama `id`, es de tipo `INT` y es una `PRIMARY KEY`.
	    - La segunda columna se llama `nombre`, es de tipo `VARCHAR(100)` y no puede estar vacía.
	    - La tercera columna debe validar que el texto tenga un formato de correo electrónico.
	
	🚀 ¿Por qué son tan importantes?
	
	- **Garantizan la integridad:** Evitan que un usuario guarde un texto en una columna destinada a fechas o números.
	- **Permiten la automatización:** Los frameworks modernos (ORMs) leen los metadatos para mapear automáticamente tus tablas en clases de programación (POO).
	- **Optimizan consultas:** El motor de la base de datos consulta los metadatos para decidir el camino más rápido y eficiente para ejecutar un `SELECT`.
	- **Independencia de datos:** Permiten cambiar los datos reales sin alterar la estructura general del sistema.
	

La figura [[2_SDLC_sofware.pdf#search=Figura 1.|SDLC_sofware, p.359]] de las llamadas telefónicas sirve para aterrizar esa idea. Ahí el autor quiere que veas que una base de datos puede representarse como una estructura **bidimensional**: columnas para atributos y filas para registros. Cada fila corresponde a una llamada concreta, y cada columna agrupa un tipo de dato específico. En otras palabras, te está entrenando para leer una tabla no como “cuadritos”, sino como una representación formal de hechos del mundo real.

El ejemplo también te enseña algo más profundo: antes de diseñar, debes definir el **significado** de cada campo. Por eso aparecen nombres como `calldate`, `src`, `dst`, `duration` y `disposition`, junto con sus tipos `TIMESTAMP`, `VARCHAR(25)`, `TIME`, etc. El mensaje oculto es este: en bases de datos, el diseño correcto empieza preguntando “¿qué representa este dato?” y “¿qué forma técnica necesita para almacenarse?”. Eso separa la lógica del negocio del almacenamiento físico.

El objetivo pedagógico de esta sección es dejarte listo para el resto del módulo. Si entiendes bien esta parte, después podrás comprender sin perderte el **modelo entidad-relación**, las **claves**, la **normalización** y las **reglas de integridad**. Si esta base falla, todo lo demás se vuelve memorización vacía; si la entiendes, cada tema posterior encaja como pieza de un sistema.

# 2_Tipos de datos y restricción de no nulidad

**estructura interna real**. El foco ya no es “qué es una base de datos”, sino **cómo se describe formalmente lo que guarda**: primero con metadatos, luego con diccionario de datos, y después con tipos de dato y restricciones. Ese es el salto importante: pasar de la idea conceptual a la definición técnica de cada campo.

La primera enseñanza fuerte es esta: **una base de datos necesita describirse a sí misma**. Por eso aparecen los **metadatos** y el **diccionario o catálogo de datos**. El documento te está diciendo que no basta con guardar información; también hay que dejar claro qué significa cada dato, cuál es su tipo, cuánto ocupa y para qué sirve dentro del sistema. En el ejemplo de llamadas telefónicas, la tabla no solo guarda valores, sino que cada columna tiene una explicación técnica: `calldate`, `src`, `dst`, `duration` y `disposition`. Además, el material remarca algo clave: hay una separación entre la **lógica del dato** y su **almacenamiento físico**, porque la descripción del campo no es lo mismo que el tipo y el tamaño con los que se guarda.

 **el tipo de dato no es un adorno**, sino una regla de control. Por eso compara varios SGDB: Oracle, PostgreSQL, MySQL y SQL Server. La idea no es memorizar marcas, sino entender que cada motor maneja nombres distintos para cosas equivalentes: por ejemplo, cadenas, textos, enteros, fechas y horas. El mensaje de fondo es que el diseño de una base de datos siempre debe respetar el motor donde vivirá, porque los tipos definen cómo se guarda y cómo se valida la información.

La siguiente capa es la más técnica y la más útil: la **restricción de longitud** y la **restricción de no nulidad**. Cuando el texto pone `src VARCHAR(25)`, te está diciendo que ese campo admite texto, pero con un máximo de 25 caracteres. Cuando luego agrega `NOT NULL`, el sentido cambia: ya no solo importa el formato, sino que el dato pasa a ser **obligatorio**. En otras palabras, el campo no puede quedar vacío. El material incluso aclara que algunos sistemas resumen eso como `NN`. Aquí el autor te está enseñando que una base de datos bien diseñada no solo guarda datos; también impone reglas para evitar basura, vacíos y ambigüedad.

La intención pedagógica de todo este bloque es muy precisa: que aprendas a pensar cada columna como una pieza con tres decisiones obligatorias: **qué representa, qué tipo tiene y si es obligatoria o no**. Eso es exactamente lo que después te permite construir tablas serias y consistentes. Si lo llevas a una analogía de programación, es como declarar una variable sin dejarla “a la suerte”: defines su tipo, su capacidad y si puede quedarse en `None`. Esa disciplina evita errores desde el diseño, no después del desastre.

En resumen, esta sección te está diciendo: **antes de modelar relaciones o normalizar, aprende a definir bien cada dato**. Si entiendes eso, todo lo que viene después encaja mucho mejor.

# 3_Tipo de bases de datos

**las bases de datos no son todas iguales y no se eligen por moda, sino por la forma en que organizan la información y por el tipo de problema que resuelven**. El autor abre la sección diciendo que las bases de datos han evolucionado con distintos modelos y que algunos rinden mejor que otros según la aplicación. O sea: aquí no te están dando una lista para memorizar, te están enseñando a **pensar en estructura** antes de diseñar.

## 1_**base de datos jerárquica:**
El texto la describe como una estructura en árbol, donde unas relaciones dependen de otras. La idea que te quiere transmitir es que aquí la información se navega de arriba hacia abajo, como si partieras de una raíz y luego fueras abriendo ramas. El ejemplo que usa es LDAP, que se aplica a directorios de usuarios, dispositivos, nombres, contraseñas y direcciones dentro de una red. El mensaje oculto es: este tipo sirve cuando la estructura es muy ordenada y la búsqueda sigue rutas bastante definidas.

- Una **base de datos LDAP** (Lightweight Directory Access Protocol o _Protocolo Ligero de Acceso a Directorios_) no es una base de datos relacional común con tablas y filas. En realidad, ==es un **servicio de directorio estructurado en forma de árbol jerárquico**, diseñado específicamente para buscar y consultar información de manera extremadamente rápida==
- Su función principal en el mundo real es actuar como una **guía telefónica corporativa centralizada**. Se utiliza principalmente para gestionar la **autenticación (iniciar sesión) y autorización (permisos)** de usuarios, dispositivos y aplicaciones en una red empresarial. 

- 🌳 ¿Cómo se organiza la información en LDAP?

La información se organiza en un Árbol de Información de Directorio (DIT). Cada entrada se identifica de manera única mediante una ruta llamada **DN (Distinguished Name)**, que funciona igual que una ruta de archivos en tu computadora:
- `dn: cn=Juan Perez,ou=Desarrollo,dc=miempresa,dc=com`
    - **dc (Domain Component):** El dominio base (`miempresa.com`).
    - **ou (Organizational Unit):** El departamento o carpeta (`Desarrollo`).
    - **cn (Common Name):** El objeto o persona específica (`Juan Perez`).
    
Cada objeto (como el usuario Juan Pérez) contiene **atributos** con sus respectivos valores (como `mail: juan@empresa.com`, `userPassword: password123`, `telephoneNumber: 555-1234`).

⚙️ ¿Para qué se utiliza exactamente?

1. **Single Sign-On (SSO):** Permite que un empleado use la misma contraseña para entrar a su computadora, al correo electrónico corporativo, al sistema de recursos humanos y al CRM.
2. **Gestión de recursos de red:** Almacenar la ubicación y los permisos de impresoras, servidores y carpetas compartidas en una red.
3. **Control de Accesos:** Validar de inmediato si un usuario pertenece al grupo "Administradores" antes de permitirle realizar un cambio en el sistema.

🛠️ Ejemplos de software que usan LDAP

- **Microsoft Active Directory (AD):** El servicio de gestión de identidades más usado en empresas del mundo; utiliza LDAP para comunicarse.
- **OpenLDAP:** Una de las implementaciones de código abierto más populares para entornos Linux. 

- ![[18_db_jerarquica.png]]


## 2_ **base de datos en red**. 
Aquí el texto sube el nivel de complejidad: ya no hay una sola ruta limpia como en un árbol, sino varias conexiones posibles entre registros. Lo que te está diciendo el autor es que los datos pueden relacionarse por más de un camino, y eso da más flexibilidad, pero también más complejidad de lectura y mantenimiento. Si lo llevas a una analogía de Python, la jerárquica se parece más a un **diccionario anidado**; la de red se parece más a un **grafo**, donde un nodo puede conectar con varios nodos por distintos caminos.
- Una **base de datos en red** ==es un modelo de organización de datos que se creó a finales de los años 60 para superar las limitaciones del modelo jerárquico tradicional== (el cual solo permitía relaciones de padre a hijo).

	A diferencia del modelo relacional moderno que usa tablas, este modelo organiza la información mediante un esquema de **grafos**, donde los datos son nodos y las relaciones son punteros físicos (flechas) que los conectan.
	
	🔑 La regla de oro: Relaciones de muchos a muchos
	
	La gran revolución de la base de datos en red es que **un registro hijo puede tener múltiples padres**
	
	- **En el modelo jerárquico (Árbol):** Un estudiante solo podría pertenecer a una carrera. Si tomaba materias de otra, el dato se tenía que duplicar.
	- **En el modelo en red (Grafo):** El nodo `Estudiante` puede conectarse al mismo tiempo con el nodo `Profesor A`, el nodo `Materia: Bases de Datos` y el nodo `Facultad de Ingeniería`.


	💡 Ejemplo práctico de estructura
	
	Imagina un sistema universitario estructurado en red:
	
	- **Nodos Principales (Padres):**
	    - `Curso: Programación`
	    - `Curso: Matemáticas`
	- **Nodos Secundarios (Hijos que comparten padres):**
	    - El `Estudiante: Carlos` está conectado mediante un puntero físico a _Programación_ y a _Matemáticas_.
	    - La `Estudiante: Ana` está conectada únicamente a _Programación_.
	
	Para encontrar qué materias cursa Carlos, el motor de la base de datos sigue el enlace físico directo desde el registro de Carlos hasta sus respectivos cursos.

	
	📈 Ventajas del modelo en red
	
	- **Acceso ultra rápido:** Al usar punteros físicos directos en el disco duro (direcciones de memoria), buscar un registro conectado a otro es casi instantáneo.
	- **Cero redundancia:** No es necesario duplicar datos para representar relaciones complejas de muchos a muchos.
	- **Integridad de datos:** Los enlaces aseguran que no queden registros "huérfanos" fácilmente.
	
	
	📉 Desventajas (Por qué ya casi no se usa)
	
	- **Extrema complejidad:** Diseñar y modificar la base de datos es muy difícil. Si quieres añadir un nuevo tipo de dato, debes reprogramar manualmente los punteros de miles de registros.
	- **Poca flexibilidad:** No puedes hacer consultas improvisadas (como un `SELECT` moderno). Para buscar un dato, debes conocer de memoria la ruta exacta de enlaces físicos para llegar a él.
	- **Dependencia del programador:** Las consultas se escribían en lenguajes de bajo nivel (como COBOL), incrustando la navegación física dentro del código de la aplicación.
	
	
	🛠️ Estándar y ejemplos reales
	
	Este modelo fue estandarizado por el consorcio **CODASYL** (Conference on Data Systems Languages). Su implementación comercial más famosa fue **IDMS** (Integrated Database Management System), muy utilizado en grandes computadoras centrales (_mainframes_) bancarias y gubernamentales durante los años 70 y 80.
	- ![[19_db_red.png]]
## 3_**base de datos relacional**
El texto la presenta como la más extendida en la industria y la más usada, aunque también la más compleja de aprender, porque después todo lo demás se construye sobre este modelo. El autor aclara que se basa en **tablas**, como la de llamadas telefónicas, y en la relación entre tablas. Es decir, la información deja de pensarse como archivos sueltos y pasa a verse como un sistema de relaciones controladas. En términos de programación, sería pasar de una lista desordenada de objetos a un conjunto de estructuras conectadas por claves.

- Las **Bases de Datos Relacionales (BDR)** representan el modelo más utilizado en el mundo del software actual. Desarrollado por Edgar F. Codd en IBM durante 1970, este modelo resolvió la complejidad y rigidez de las bases de datos en red y jerárquicas [1].

	Su principio fundamental es que **los datos se organizan en tablas de dos dimensiones (filas y columnas)** y las relaciones entre los datos se establecen mediante el propio contenido de estas tablas, eliminando los complejos punteros físicos de memoria .
	
	- 🧱 Los Componentes Esenciales
	
	- Para entender una base de datos relacional, debes dominar sus cuatro conceptos estructurales básicos:
	
	- **Tablas (o Relaciones):** Es la estructura base. Cada tabla representa una entidad del mundo real (por ejemplo: `Clientes`, `Productos`, `Facturas`).
	- **Columnas (Campos o Atributos):** Definen las características que tendrá cada registro. Cada columna tiene asignado un tipo de dato estricto (Texto, Entero, Fecha) definido en sus metadatos.
	- **Filas (Registros o Tuplas):** Representan a un elemento único y específico dentro de la tabla (por ejemplo, el cliente "Juan Pérez" con ID 45).
	- **Claves (o Llaves):** Son las herramientas de identificación y unión:
	    - **Llave Primaria (Primary Key - PK):** Un campo (o conjunto de campos) cuyo valor es único para cada fila y no puede repetirse ni ser nulo. Identifica unívocamente al registro (ej. la cédula de ciudadanía o un ID numérico autoincremental).
	    - **Llave Foránea (Foreign Key - FK):** Es una columna en una tabla que hace referencia directa a la Llave Primaria de **otra tabla**. Es el mecanismo matemático que une y relaciona ambas tablas.
	
	🔗 ¿Cómo se conectan las tablas? (El Concepto de Relación)
	
	Imagina que tienes una tienda en línea. En lugar de meter toda la información en una sola hoja de cálculo gigante (lo cual duplicaría el nombre y teléfono del cliente en cada compra que haga), el modelo relacional separa la información estratégicamente:
	
	1. Creas una tabla **`Clientes`** con las columnas: `ID_Cliente` (PK), `Nombre`, `Telefono`.
	2. Creas una tabla **`Pedidos`** con las columnas: `ID_Pedido` (PK), `Fecha`, `Total`, y añades la columna **`ID_Cliente` (FK)**.
	
	Cuando el cliente Juan (`ID_Cliente = 5`) realiza tres compras, la tabla `Pedidos` registrará tres filas diferentes, pero todas tendrán en su columna `ID_Cliente` el número `5`. El motor de la base de datos sabe interpretar esa coincidencia y conecta ambas entidades de forma instantánea al consultar.
	

	🚀 Ventajas del Modelo Relacional
	
	- **Flexibilidad de Consulta:** Permite hacer preguntas complejas improvisadas al sistema mediante lenguaje SQL (ej. _"Muéstrame todos los clientes de Bogotá que compraron más de $100,000 en el último mes"_). No necesitas conocer una ruta de navegación física preestablecida.
	- **Independencia de los Datos:** Cambiar la estructura de una tabla o la ubicación física de los archivos en el servidor no rompe los programas que consumen la base de datos.
	- **Integridad Referencial:** El motor impide errores graves de lógica; por ejemplo, no te dejará borrar un cliente de la tabla `Clientes` si ese cliente todavía tiene pedidos registrados en la tabla `Pedidos`.
	- **Garantía ACID:** Cumplen estrictamente con cuatro propiedades (Atomicidad, Consistencia, Aislamiento y Durabilidad) que aseguran que las transacciones financieras o críticas se completen perfectamente o se cancelen por completo ante un fallo, evitando corrupción de datos.
	
	🛠️ Los Motores Relacionales más Populares
	
	- **Open Source:** MySQL, PostgreSQL, MariaDB, SQLite.
	- **Comerciales / Empresariales:** Oracle Database, Microsoft SQL Server.
	- ![[20_db_relacional.png]]

## 4_Bases de datos con estructura multidimensiona 
es la extensión natural de la relacional: mientras la relacional trabaja con tablas bidimensionales, la multidimensional trabaja con **cubos** o incluso con **N dimensiones**. El autor la conecta con análisis estadístico de datos históricos y volúmenes grandes de información, y por eso la asocia con escenarios tipo bodega de datos u OLAP. La idea que te quiere transmitir no es solo “otro tipo más”, sino que hay bases pensadas para **analítica** y no para transacción diaria. ^043760

- Las **Bases de Datos Multidimensionales (BDM)** están diseñadas específicamente para el análisis masivo de datos y la inteligencia de negocios (Business Intelligence) [1].

	A diferencia de las bases de datos relacionales tradicionales (diseñadas para registrar transacciones del día a día como ventas o registros), las multidimensionales se estructuran para **responder preguntas de negocio complejas en segundos** [1].
	
	
	🎲 El Concepto Clave: El Cubo OLAP
	
	En lugar de organizar la información en tablas planas de dos dimensiones (filas y columnas), este modelo organiza los datos en **Cubos OLAP** (OnLine Analytical Processing) 
	
	Imagina un dado o un cubo en tercera dimensión (o más) donde la información se interconecta de forma inmediata. Un cubo multidimensional se compone de dos elementos fundamentales:
	
	1. **Métricas (o Hechos):** Son los valores numéricos cuantitativos que el negocio quiere medir (por ejemplo: `Unidades Vendidas`, `Ingresos Totales`, `Costos`).
	2. **Dimensiones:** Son los criterios o filtros mediante los cuales se quieren analizar las métricas (por ejemplo: `Tiempo` [año/mes/día], `Geografía` [país/ciudad], `Producto` [categoría/nombre]).
	
	
	💡 Ejemplo práctico de consulta
	
	En una base de datos relacional (SQL) estándar, si el Director de Ventas pregunta: _"¿Cuántos smartphones vendimos en Bogotá durante el tercer trimestre de 2025 y cómo se compara con Medellín?"_, el servidor tendría que buscar, filtrar y sumar millones de filas de varias tablas en tiempo real, lo cual consume mucho tiempo y cómputo.
	
	En una **Base de Datos Multidimensional**, el sistema ya tiene las respuestas precalculadas y almacenadas en los cruces de las dimensiones del cubo:
	
	- **Dimensión 1 (Producto):** Smartphones.
	- **Dimensión 2 (Geografía):** Bogotá / Medellín.
	- **Dimensión 3 (Tiempo):** Q3 2025.
	
	El sistema simplemente va a la coordenada exacta del cubo y extrae el dato numérico precalculado instantáneamente.
	

	🛠️ Los Modelos de Diseño Más Comunes
	
	Para construir estas estructuras multidimensionales sobre sistemas de almacenamiento, se suelen utilizar dos arquitecturas lógicas principales:
	
	- **Esquema en Estrella (Star Schema):** Hay una gran tabla central de "Hechos" (métricas) conectada directamente a múltiples tablas periféricas de "Dimensiones". Visualmente parece una estrella.
	- **Esquema en Copo de Nieve (Snowflake Schema):** Es una variante del esquema en estrella, pero aquí las tablas de dimensiones se descomponen y normalizan en subtablas más pequeñas (por ejemplo, la dimensión _País_ se conecta a _Región_, y esta a _Ciudad_).
	
	🚀 Ventajas de las Bases de Datos Multidimensionales
	
	- **Velocidad de Respuesta Extraordinaria:** Las consultas analíticas complejas tardan milisegundos porque los datos agregados ya están calculados de antemano.
	- **Análisis Intuitivo para Humanos:** Es la estructura perfecta para alimentar herramientas visuales como Power BI, Tableau o Excel (Tablas Dinámicas), permitiendo a los gerentes hacer _Drill-Down_ (navegar desde el total del año hasta el detalle del día) con un clic.
	- **Independencia de los Sistemas de Operación:** Al estar separadas en un almacén de datos (Data Warehouse), los análisis pesados de los directivos no ralentizan la aplicación web ni la base de datos transaccional que usan los clientes para comprar.
	- ![[21_db_multidim.png]]
	
	
## 5_Bases de datos con estructura orientada a objetos
La **orientada a objetos** aparece como una base donde la información se representa en forma de **objetos**, alineada con el paradigma de programación orientada a objetos. Aquí el documento está haciendo un puente conceptual entre el mundo de las bases de datos y el de la POO: ya no piensas solo en filas y columnas, sino en entidades con comportamiento y estructura más cercana a objetos del software. El texto la incluye para que entiendas que el modelo de almacenamiento también puede seguir la lógica de la programación orientada a objetos.

- Las **Bases de Datos Orientadas a Objetos (BDOO)** nacieron para resolver la desconexión existente entre el código de programación moderno y el almacenamiento tradicional.

	En lugar de desarmar un objeto de tu código para guardarlo en filas y columnas (como en el modelo relacional), este modelo **almacena los objetos directamente en el disco duro con su estructura, estado y comportamiento intactos**.
	

	💥 El Problema que Resuelven: La "Desadaptación Impedancia"
	
	Cuando programas usando POO , creas clases con atributos, métodos y herencia. Si usas una base de datos relacional (como MySQL), te ves obligado a transformar esos objetos en tablas planas mediante un software intermedio (llamado ORM, como Hibernate o Entity Framework). Esto consume recursos y tiempo de desarrollo.
	
	Las bases de datos orientadas a objetos eliminan este intermediario. El objeto de tu lenguaje de programación (Java, C#, Python) se guarda exactamente con el mismo formato en la base de datos.
	
	🧩 Componentes y Conceptos Clave
	
	El modelo hereda de forma estricta los conceptos de la Programación Orientada a Objetos:
	
	- **Identificador de Objeto (OID):** A diferencia de la Clave Primaria (PK) relacional, que depende de los datos (como una cédula o un correo), el `OID` es un código único e invisible generado automáticamente por el sistema para identificar de forma unívoca al objeto en memoria o disco.
	- **Encapsulamiento:** El registro no solo guarda los datos (atributos), sino que también almacena o conoce los métodos (funciones) que operan sobre ellos.
	- **Herencia:** Si tienes una clase padre `Vehículo` y una clase hijo `Auto`, la base de datos entiende de forma nativa que un registro de `Auto` hereda todas las propiedades de `Vehículo`.
	- **Polimorfismo:** Permite almacenar diferentes tipos de objetos derivados en una misma colección y responder correctamente según el tipo específico al ser consultados.
	
	💡 Ejemplo Práctico de Almacenamiento
	
	Imagina que estás desarrollando un videojuego de rol (RPG):
	
	```
	Clase Personaje {
	    Atributos: ID, Nombre, Nivel, Coordenadas (X, Y)
	    Objetos anidados: Inventario [Espada, Escudo, Poción]
	    Métodos: atacar(), usarItem()
	}
	```
	
	- **En una Base de Datos Relacional:** Necesitarías al menos tres tablas conectadas (`Tabla_Personajes`, `Tabla_Inventarios`, `Tabla_Items`) y reconstruir el objeto cada vez usando operaciones de unión (`JOIN`).
	- **En una Base de Datos Orientada a Objetos:** El bloque de memoria completo que representa al personaje, junto con su lista de inventario interna, se guarda directamente como un único elemento continuo en el disco.
	
	🚀 Ventajas Principales
	
	- **Rendimiento en Estructuras Complejas:** Al no requerir costosas operaciones de unión (`JOIN`) entre tablas planas, el acceso a datos altamente jerárquicos o anidados es extremadamente rápido.
	- **Compatibilidad Total con el Código:** No necesitas traducir tipos de datos ni usar frameworks ORM complejos. Programas y almacenas usando los mismos conceptos.
	- **Soporte de Datos Ricos:** Manejan de forma nativa tipos de datos complejos como geometría 3D, archivos multimedia, mapas GIS o estructuras de ingeniería de manera eficiente.

	📉 Desventajas (Por qué no sustituyeron al modelo relacional)
	
	- **Falta de Estándar Universal:** A diferencia de SQL, que funciona casi igual en cualquier motor relacional, las BDOO no lograron consolidar un lenguaje de consultas único y universalmente aceptado (aunque existieron intentos como OQL).
	- **Complejidad en Consultas Simples:** Hacer un reporte general de datos masivos (ej. _“calcular el promedio de nivel de todos los personajes inscritos en el último mes”_) resulta más ineficiente que en una base de datos estructurada por columnas o tablas.
	- **Comunidad Reducida:** El ecosistema de herramientas de respaldo, seguridad y administración es significativamente menor comparado con la madurez del mundo SQL.
	
	
	🛠️ Ejemplos de Motores Orientados a Objetos
	
	- **db4o** (Database for Objects - muy popular en entornos Java/.NET).
	- **ObjectDB** (Especializado en persistencia nativa de Java).
	- **ObjectStore** y **Versant** (Utilizados en sistemas industriales y de telecomunicaciones de alta complejidad).
	- ![[22_db_poo.png]]

Lo más importante de esta parte no es solo la definición de cada tipo, sino el criterio que te obliga a desarrollar: **cada modelo tiene un ámbito de aplicación distinto**. El texto remata diciendo que las jerárquicas van mejor para consultas puntuales, las relacionales son fuertes para garantizar calidad de datos y evitar repetición, y las multidimensionales sirven para análisis estadístico de grandes volúmenes. Aunque eso ya roza la siguiente parte del documento, el sentido de esta sección es claro: **elige la estructura según el problema, no al revés**.





# 4_Clasificación de bases de datos [[2_SDLC_sofware.pdf#search=Clasificación de bases de datos|SDLC_sofware, p.366]]

ya no te habla de la **forma** de la base de datos, sino de la **naturaleza de los datos que guarda**. Esa es la lógica de esta sección. El autor te está diciendo que una base de datos no solo se clasifica por su estructura interna, sino también por el tipo de información que almacena y por el uso que le vas a dar. Por eso introduce una tabla de clasificación con criterios como **variabilidad de los datos** y **contenido**.

1. La primera división es la más importante: **bases de datos estáticas** y **dinámicas**. 
	
	- ## 1_ bases de datos estáticas
		guardan datos históricos que ya no se modifican; sirven para estudiar el comportamiento de la información a través del tiempo. El texto incluso aclara que normalmente se llaman **bodegas de datos** y que muchas se almacenan en cubos para análisis, lo que conecta con el concepto **OLAP** [[7_bases_de_datos#^043760]]. La idea que te quiere transmitir el autor es que aquí la prioridad no es operar el negocio en el momento, sino **analizarlo**.
	
	- ## 2_**bases de datos dinámicas**
		sí cambian todo el tiempo: permiten agregar, borrar, actualizar y consultar registros en cualquier momento. El documento las relaciona con sistemas **transaccionales**, como un sistema de facturación, y allí aparece **OLTP**. El mensaje es claro: si el negocio vive de operaciones diarias, necesitas una base que soporte cambios constantes; si vives de análisis histórico, necesitas una base más orientada a consulta y acumulación.

1. La segunda división ya no depende de si los datos cambian o no, sino de **qué tipo de contenido guardan**. Ahí aparecen las **bases de datos documentales** y las **deductivas**. 

	- ## 1_bases de datos documentales 
		 permiten indexación a texto completo y búsquedas más potentes; el autor está pensando en información textual grande, donde buscar por contenido importa más que recorrer filas sueltas.

	- ## 2_**bases de datos deductivas**
		van un paso más allá: no solo almacenan hechos, sino que permiten hacer **inferencias** y sacar conclusiones a partir de reglas. El texto las llama también **bases de datos lógicas**, porque se apoyan en lógica matemática. La idea pedagógica aquí es que la base de datos no siempre es una caja pasiva de almacenamiento; en algunos casos también puede comportarse como un sistema que **razona** sobre lo almacenado.

# 5_Modelo entidad relación

Aquí el autor entra en la **columna vertebral del diseño de bases de datos**: el **Modelo Entidad–Relación**. No te está diciendo todavía cómo crear tablas en SQL; te está enseñando **cómo pensar el mundo real antes de convertirlo en tablas**. La idea central es esta: una base de datos relacional no se modela directamente desde cero, sino que primero se abstrae el problema en tres niveles: **conceptual**, **lógico** y **físico**. Ese orden existe para ir ocultando complejidad paso a paso y no diseñar a ciegas.

La primera frase importante de esta sección es que el modelo E-R nace de una **percepción del mundo real**. Eso significa que el autor quiere que entiendas que una base de datos no empieza en la tabla, sino en los objetos y relaciones que existen fuera del software. Por eso pone como ejemplos cosas como **persona** y **cuenta bancaria**: son objetos del mundo real que pueden distinguirse unos de otros. A eso le llama **entidades**.

## **entidad** 
 es “algo” que existe y que puede identificarse de forma separada de otros “algos”. El texto lo explica con claridad: cada persona es una entidad, y cada cuenta bancaria también puede ser una entidad. Lo importante no es solo que existan, sino que sean **distinguibles**. Esa distinción es clave porque después cada entidad podrá convertirse en una tabla, y cada instancia en una fila o registro.

## **atributos**
Aquí el autor te está diciendo que una entidad por sí sola es demasiado abstracta; necesitas describirla. Por eso una persona puede tener nombres, apellidos, edad e identificación, y una cuenta bancaria puede tener número de cuenta, saldo y fecha de creación. O sea: los atributos son las **propiedades** que hacen que una entidad sea útil dentro del sistema. En términos prácticos, son los futuros campos de la tabla.

## **relaciones**
que para el documento son la parte más importante porque conectan las entidades entre sí. El ejemplo clásico es la relación **titular** entre persona y cuenta. El mensaje profundo es este: en un sistema real, los datos no viven aislados; viven conectados. Una persona no se guarda por separado de sus cuentas como si no existiera vínculo alguno. El modelo E-R precisamente existe para representar esas conexiones antes de pasarlas al modelo relacional.

En este tramo el documento ya no está hablando solo del **modelo entidad–relación como dibujo**, sino de cómo ese dibujo empieza a convertirse en **tablas reales**. La idea central es: primero entiendes que una entidad puede representarse como tabla, luego que una fila de esa tabla se llama **tupla**, y después que para poder relacionar tablas sin repetir información necesitas **claves**.

 - ### tupla
	  El texto te está diciendo que una tupla es el conjunto completo de atributos de una fila; en lenguaje simple, una fila de la tabla. Eso importa porque el autor quiere que dejes de pensar en “dibujitos de entidades” y empieces a pensar en **registros concretos**. Es como en Python cuando pasas de imaginar una clase a mirar el objeto ya instanciado con sus valores reales.

- ### **principio de unicidad**
	Aquí el mensaje es muy serio: en una tabla no deben existir filas repetidas con exactamente los mismos valores. ¿Por qué? Porque si repites filas, repites información y la base se vuelve redundante. El documento insiste en que, aunque una persona pueda tener varias cuentas bancarias, no tiene sentido copiar los mismos datos de la persona en cada cuenta; lo correcto es relacionar tablas, no duplicar datos. Ese es el paso mental que el autor quiere que hagas.

- ### **claves**
	El texto te explica que, como no deben existir filas iguales, cada registro debe poder identificarse de manera inequívoca por uno o varios atributos. En el ejemplo, `identificación` sirve para la tabla **persona** y `numero_cuenta` sirve para la tabla **cuenta**. El subrayado en el diagrama no es decoración: significa “este atributo identifica de forma única a la entidad”.

	Después el documento complica el ejemplo a propósito: imagina que el banco es internacional. Ahí te muestra por qué una sola clave ya no basta en todos los casos. Puede existir el mismo número de identificación en países distintos, así que `identificación` sola deja de ser suficiente; por eso aparece la idea de usar `identificación + país` como **clave compuesta**, o usar el **correo** si la regla del negocio garantiza que no se repite. Ese tramo te enseña que una clave no se elige por capricho técnico, sino por la realidad del negocio.

- ### **clave candidata**, **superclave** y **clave primaria**
	La **superclave** es cualquier conjunto de uno o más atributos que identifica de forma única una entidad; por eso `id_persona` es superclave, y también lo sería `identificación + país` o `correo` si cumplen unicidad
	
	La **clave candidata** es una superclave que además está lista para competir por ser la clave principal
	
	La **clave primaria** es la clave candidata que el diseñador elige como identificador principal de la tabla.
	
	Lo importante aquí no es memorizar tres nombres, sino entender la jerarquía lógica:  
	**superclave** = puede identificar;  
	**clave candidata** = puede ser elegida;  
	**clave primaria** = fue elegida.  
	Eso es como tener varios nombres posibles para una variable y decidir cuál se vuelve el nombre oficial del módulo porque es el más limpio y estable.

	el texto dice que el enfoque más recomendado es crear un **atributo identificador artificial** como `id_persona`. ¿Por qué? Porque reduce la complejidad del diseño y facilita relacionar tablas. Esa es una decisión de arquitectura de datos: a veces conviene usar una clave natural del negocio, pero muchas veces conviene una clave surrogate para que el sistema sea más simple y robusto.

## Diagrama [[2_SDLC_sofware.pdf#search=Entidad relación persona cuenta bancaria|SDLC_sofware, p.370]]
- rectángulos para entidades
- elipses para atributos
- rombos para relaciones 
- líneas para conectar todo
Eso no es solo dibujo académico; es un lenguaje visual para que el analista pueda comunicar la estructura del sistema sin ambigüedad. Si entiendes esa gramática, lees un diagrama E-R como lees código bien estructurado.

## modelo relacional 
**convierte las entidades en tablas**. Por eso después muestra que la entidad persona termina siendo una tabla persona, y la entidad cuenta termina siendo una tabla cuenta. Cada fila representa un objeto concreto del mundo real. Ahí está el puente entre lo conceptual y lo técnico: primero entiendes la realidad, luego la conviertes en estructura de datos.


# 6_Normalizacion 

**normalizar no es “poner más reglas por capricho”**; es **ordenar el modelo para que las tablas queden bien separadas, sin repetir datos y sin mezclar información que no depende de la misma clave**. El documento lo define como el procedimiento para convertir el modelo entidad–relación en modelo relacional, es decir, en tablas y relaciones. Sus dos principios rectores son la **no redundancia** y la **dependencia coherente**.

La idea de fondo es esta: cuando una base de datos está mal normalizada, empiezas a repetir datos y después cada cambio se vuelve una pesadilla. El texto usa el ejemplo de la tabla `persona` y la tabla `empleado`: los datos comunes de clientes o personas quedan en `persona`, mientras que lo exclusivo del empleado se mueve a `empleado`. Eso evita que, por ejemplo, el correo de una persona se copie innecesariamente en muchas filas donde no aporta nada nuevo. En lenguaje de arquitectura, estás separando responsabilidades; en lenguaje de Python, estás evitando guardar la misma información en varias listas cuando bastaría una estructura principal y relaciones limpias.

Luego aparece un concepto clave que el documento llama **dependencia incoherente**. Esto pasa cuando un dato aparece en una tabla donde no pertenece lógicamente. El ejemplo del texto es muy claro: buscar el **correo** de un cliente en `persona` sí tiene sentido, pero buscar allí el **salario** del empleado no lo tiene, porque el salario depende de la tabla `empleado`. La enseñanza aquí es brutalmente práctica: cada atributo debe vivir en la tabla de la que realmente depende. Si no, la ruta para encontrarlo se daña y el mantenimiento se complica.

## Las **tres formas normales**
No las pone como teoría abstracta, sino como reglas de limpieza del modelo:

- ### **primera forma normal (1FN) - Atomisidad**
	- elimina grupos de repetición y obliga a que cada conjunto de datos relacionados esté en una tabla independiente. También exige identificar cada conjunto con una **clave primaria**. En términos simples: una celda no debe contener listas escondidas ni columnas repetidas del mismo tipo.
	
	- Cada celda debe contener un solo valor. No se permiten listas de datos en un solo campo (por ejemplo, no puedes tener un campo llamado `Teléfonos` que guarde `"555-1234, 555-5678"` juntos; deben ir en filas o registros separados).

- ### **segunda forma normal (2FN)**
	- pide crear tablas independientes para conjuntos de valores que se aplican a varios registros, y luego conectarlas con una **clave foránea**. Aquí el mensaje es: si un dato se repite para muchos registros y no depende de cada fila individualmente, sácalo a otra tabla. Eso reduce duplicación y mejora el control.
	
	- Ya cumpliendo la 1FN, exige que todos los datos que no sean la "llave" (ID) dependan completamente de la llave principal de esa tabla

- ### **tercera forma normal (3FN)**
	- elimina los campos que no dependen de la clave. Este es el punto más fino: no basta con que el dato esté en una tabla adecuada; también debe depender **directamente** de la clave de esa tabla y no de otro atributo intermedio. Es la forma de cortar dependencias indirectas que después generan inconsistencias.

	- Ya cumpliendo la 2FN, elimina las dependencias transitivas. Esto significa que un dato que no es llave tampoco debe depender de _otro_ dato que no sea llave (por ejemplo: la `Categoría_Producto` depende del `Producto`, no directamente de la `Compra`; por eso el producto debe ir en su propia tabla)

El texto también aclara que existen una **cuarta forma normal (BCNF)** y una **quinta forma normal**, pero que no se tratan aquí porque suelen agregar complejidad sin aportar valor práctico en este contexto. Esa frase te dice algo importante: el documento no busca que te conviertas en teórico puro, sino que aprendas lo necesario para diseñar bien en escenarios reales.

Es **separar, ordenar y depurar la estructura de datos para que el sistema no se rompa por redundancia ni por dependencias mal puestas**. Sin esta parte, lo que viene después —dependencias funcionales, diseño relacional e integridad— queda débil.

![[23_db_normalizacion.png]]

# 7_Dependencias funcionales

Esta sección te está llevando al punto donde el diseño de bases de datos deja de ser “dibujar tablas” y pasa a ser **razonar dependencias**. El autor arranca diciendo que una dependencia funcional es una restricción que generaliza el concepto de clave; o sea, no solo identifica un registro, sino que establece **qué atributo determina a cuál otro**. En términos simples: si conozco el valor de `Y`, entonces siempre puedo conocer el mismo valor de `X`. Esa es la lógica que sostiene la normalización y el paso correcto al modelo relacional.

El ejemplo de la ferretería. El documento te da una sola relación “grande” con **proveedores, productos y precios**, y te obliga a descubrir qué cosas se repiten y qué cosas realmente dependen de otras. Ahí aparece la primera pista: `nit_proveedor` se repite cuando cambian `correo`, `nombres` y `teléfono`, así que esos atributos determinan al proveedor. Después, `codigo_producto` determina al producto. Y el precio no depende solo del proveedor ni solo del producto, sino de la combinación **proveedor + producto**. Ese es el corazón del ejemplo.

La parte más importante es esta: el autor quiere que entiendas que **no toda columna depende de una sola clave**. Algunas dependen de una clave simple, pero otras necesitan una **clave compuesta**. Por eso el texto dice que para cada proveedor y producto existe un precio distinto. En otras palabras, el precio no pertenece únicamente al proveedor ni únicamente al producto; pertenece a la relación entre ambos. Esa idea es crítica porque evita que metas el precio en la tabla equivocada y luego termines repitiéndolo o contradiciéndolo.

La tabla de dependencias funcionales lo resume de forma muy clara: `nit_proveedor` depende de `correo`, `nombres` y `teléfono`; `codigo_producto` depende de `producto`; y `precio` depende de `nit_proveedor` junto con `codigo_producto`. El documento te está enseñando a leer la información como una red de determinaciones, no como un bloque plano de columnas. Si una columna depende de otra, significa que esa segunda columna “manda” sobre la primera dentro de la lógica del negocio.

La definición formal lo deja cerrado: un atributo `X` depende funcionalmente de `Y` si a todo valor de `Y` le corresponde siempre el mismo valor de `X`. La palabra clave aquí es **siempre**. Si cambias `Y` y `X` también cambia de manera consistente, entonces hay dependencia funcional. Si no ocurre así, no existe esa dependencia. Ese criterio es el que después se usa para separar tablas bien normalizadas y evitar redundancia.

Después el texto hace el puente hacia el modelo entidad–relación: te dice que estas dependencias pueden representarse allí, porque un proveedor puede suministrar muchos productos y un producto puede ser ofrecido por muchos proveedores, y en cada combinación aparece un precio. Ahí el autor te está mostrando una relación **muchos a muchos** con un atributo propio de la relación. Cuando esa relación pasa al modelo relacional, aparece una tabla intermedia `provee` y en esa tabla se agrega el atributo `precio`. Esa es una regla estructural clave: si el dato pertenece a la relación entre dos entidades, no debe quedarse en una sola de ellas.

El bloque de “diseño relacional” cierra la idea con tres caminos posibles para llegar a las tablas. La opción más didáctica es pasar del diagrama entidad–relación al relacional; la opción más analítica es partir de una tabla grande y descubrir dependencias funcionales para descomponerla; y la tercera es diseñar de forma ad hoc y verificar luego si se cumple la forma normal deseada. El documento aclara que, en la práctica, con más experiencia, se usan mucho las opciones 2 y 3. Eso te revela la intención real del tema: no memorizar una receta, sino aprender a **descomponer correctamente** la información.


La idea central de toda esta sección es esta: **las dependencias funcionales te dicen cómo romper una tabla grande en tablas correctas, sin duplicar datos y sin poner atributos donde no pertenecen**. Si entiendes eso, ya estás pensando como diseñador relacional y no como alguien que solo copia columnas.


# 8_ Definición formal de dependencia funcional

Aquí el documento deja de hablar “a nivel humano” y pasa a una regla precisa. La idea formal es esta: un atributo `X` depende funcionalmente de otro atributo o conjunto de atributos `Y` si, para cada valor de `Y`, siempre corresponde el mismo valor de `X`. Esa palabra es la clave: **siempre**. No es una coincidencia, no es una tendencia, es una relación estable dentro del modelo de datos.

Lo que el autor quiere que entiendas es que una dependencia funcional no es solo “dos columnas relacionadas”. Es una forma de decir que una columna **determina** a otra. En el ejemplo de proveedores, productos y precios, el documento muestra que `nit_proveedor` determina los datos del proveedor, `codigo_producto` determina el producto, y el precio depende de la combinación `nit_proveedor + codigo_producto`. Esa última parte es crucial: hay datos que no dependen de una sola columna, sino de una **clave compuesta**.

Eso sirve para descubrir dónde vive cada dato. El precio no debe meterse dentro de proveedor ni dentro de producto, porque no pertenece a uno solo; pertenece a la relación entre ambos. En lógica de programación sería como una función que no recibe un parámetro, sino dos, y solo con ambos puede devolver un resultado correcto. Si cambias una entrada, la salida esperada sigue una regla fija; eso es dependencia funcional.

El documento también te muestra que estas dependencias se pueden representar en el modelo entidad–relación y después trasladarse al relacional. Cuando la relación `provee` pasa a tablas, aparece una tabla intermedia `provee` con el atributo adicional `precio`. Esa es la enseñanza fuerte: si un dato depende de la relación entre dos entidades, el diseño correcto no lo deja “pegado” a una sola de ellas.

# 9_Diseño relacional

Aquí el texto ya no solo analiza dependencias; ahora te dice **cómo usar esa información para construir el esquema final de tablas**. Primero aclara que la normalización encaja dentro de un proceso general de diseño de bases de datos, y propone tres caminos para llegar al modelo relacional. 

- **opción 1** es convertir directamente el diagrama entidad–relación en diagrama relacional **opción 2** consiste en partir de una tabla grande, detectar dependencias funcionales y desde ahí obtener tablas y claves; 
- **opción 3** es hacer un diseño ad hoc y después comprobar que cumpla la forma normal deseada.

La intención del autor aquí es muy práctica: no quiere que te cases con un único camino. De hecho, dice que en la vida real, cuando ya hay más experiencia, las opciones 2 y 3 son las más usadas. Eso significa que el diseño relacional no es una receta fija, sino una decisión de ingeniería basada en cómo llega el problema. Es como en Python: a veces partes de clases bien definidas, a veces limpias una estructura ya existente, y otras veces diseñas el sistema desde la necesidad concreta.

Después el documento comienza un ejemplo grande con una **biblioteca escolar**. Ese ejemplo no está puesto para entretenerte; está ahí para mostrarte cómo se traduce un problema real en entidades y relaciones. El problema incluye publicaciones, ejemplares, estudiantes, préstamos, editoriales, autores, temas, códigos ISBN, estado del ejemplar, fecha de préstamo y devolución. La enseñanza es que un problema real llega mezclado, y el trabajo del diseño relacional consiste en separarlo en piezas lógicas.

El autor te hace notar algo muy importante con el caso de autor y estudiante: una relación uno a uno no siempre se debe llevar de forma mecánica a tablas separadas si una de las entidades no aporta atributos propios suficientes. En el ejemplo, si `autor` solo termina siendo prácticamente igual a `persona`, entonces no conviene dejarlo como tabla aislada; es mejor relacionar la publicación directamente con `persona`. Esa es una lección de diseño fino: no crear tablas por inercia, sino por necesidad real del modelo.

En resumen, esta parte te quiere enseñar dos cosas distintas pero conectadas: primero, a **descubrir reglas de dependencia entre atributos**; segundo, a **usar esas reglas para construir tablas correctas, sin redundancia y sin entidades vacías**. La lógica del documento es: detectar → analizar → convertir → verificar.


# 10_Reglas de Integridad, borrado y edición

Aquí el documento cambia de fase: ya no está construyendo el modelo, sino **protegiéndolo**. La intención de esta sección es mostrar que, aunque ya hayas normalizado y distribuido los datos en tablas, todavía falta asegurar que lo que entra a la base de datos sea **válido, coherente y consistente**. El autor lo dice explícitamente: ahora hay que garantizar que los datos que se van a insertar sean correctos, y para eso existen las **restricciones de integridad**.

## 1_**criterio de nulidad**. 

Aquí el texto te está diciendo que `NULL` no es lo mismo que `0` ni que una cadena vacía; `NULL` significa **ausencia de información**. Eso puede pasar porque el dato se desconocía al momento de insertar la fila o porque, para ese registro, ese atributo no aplica. La idea que quiere dejarte clara el autor es que la base de datos no solo guarda valores, también debe saber manejar la **falta de valor** de forma correcta, porque eso afecta consultas, validaciones y diseño.

## 2_**integridad de entidad**

Esta parte es muy estricta: ningún atributo que haga parte de la **clave primaria** puede ser nulo. La razón es lógica: una clave primaria existe para identificar de manera única una fila, y si permites nulos en ella, rompes su capacidad de identificar. El documento insiste en la palabra **irreducible**: una clave primaria no puede perder parte de sus componentes sin dejar de identificar correctamente la tupla. En resumen, aquí el autor te está diciendo que la identidad de cada registro debe estar completa, no a medias.

## 3_**integridad referencial**

El texto la explica con el caso de `persona` y `estudiante`: la tabla `estudiante` depende de `persona`, por lo que no puedes tener un estudiante que apunte a una persona inexistente. Si eso pasara, la base tendría “datos basura” o inconsistencia. El documento quiere que entiendas que una clave foránea no es un dato decorativo; es un vínculo que debe apuntar a algo real en la tabla referenciada.

## 4_**reglas de borrado**.

 Aquí te está mostrando qué debe hacer el sistema cuando intentas eliminar una fila que es referenciada por otra tabla. Las opciones son: 
 
- **restringir** la eliminación
- **cascada** para borrar también los registros dependientes 
- **poner null** en la clave foránea si el campo lo permite, o usar un 
- **valor por defecto**. La lógica de fondo es que borrar un registro no puede romper la relación con las demás tablas; por eso el SGBD necesita una política clara para actuar.

## 5_**reglas de edición**o actualización

La pregunta es parecida a la anterior, pero ahora el problema no es borrar, sino cambiar el valor de la clave primaria que otras tablas usan como referencia. El autor vuelve a darte las mismas salidas: restringir, cascada, poner null o valor por defecto. El mensaje técnico es que una modificación en una clave referenciada puede propagarse o bloquearse según la política de integridad que el sistema adopte.


# 11_Lenguajes de los sistemas administradores de bases de datos

Aquí la idea del documento es muy simple, pero la empaqueta en cuatro bloques.  
**SQL** es el lenguaje que usan los SGBD relacionales para ejecutar las operaciones sobre la base de datos, y el texto lo divide en **DDL, DML, DCL y TCL**.

```
SQL = el lenguaje de trabajo del SGBD
┌───────────────────────────────┬──────────────────────────────┐
│ BLOQUE                        │ PARA QUÉ SIRVE│
├───────────────────────────────┼──────────────────────────────┤
│ DDL                           │ Definir la estructura        │
│ DML                           │ Manipular los datos          │
│ DCL                           │ Controlar permisos           │
│ TCL                           │ Controlar transacciones      │└───────────────────────────────┴──────────────────────────────┘
```

## 1) DDL — Definición de la estructura

El documento lo presenta como el conjunto de sentencias para **crear, alterar y eliminar tablas**. También aclara que aquí entran otros objetos como **vistas, índices y disparadores**. En el ejemplo del texto, se crea la tabla `persona` con `CREATE TABLE` y luego se elimina con `DROP TABLE`.

```
DDL→ define la forma de la base→ crea / cambia / elimina estructuras
```

Ejemplo mental: es como diseñar la “cáscara” del sistema antes de meter información.


## 2) DML — Manipulación de datos

Aquí el texto cambia de enfoque: ya no habla de la estructura, sino de los **datos dentro de las tablas**. DML sirve para **insertar, consultar, editar y borrar** registros. El ejemplo mostrado usa `INSERT`, `UPDATE` y `DELETE` sobre la tabla `persona`.

```
DML→ trabaja con los registros→ inserta / consulta / modifica / borra
```

Ejemplo mental: la tabla ya existe; ahora estás metiendo o corrigiendo la información.


## 3) DCL — Control de acceso

El texto dice que este bloque lo usan los administradores para **crear usuarios y conceder o revocar privilegios**. En el ejemplo aparece `GRANT`, dando permisos a un usuario sobre una base de datos y una tabla específicas.

```
DCL→ controla quién puede hacer qué→ permisos / privilegios
```

Ejemplo mental: no todos los usuarios deberían poder borrar o modificar datos.

## 4) TCL — Control de transacciones

Aquí el documento lo define como un grupo pequeño de sentencias que permite tratar operaciones DML **en bloque**, garantizando que se ejecuten **todas o ninguna**. Esa es la idea esencial: evitar que una operación quede a medias y la base quede inconsistente.

```
TCL→ controla bloques de cambios→ todo se confirma o todo se revierte
```

Ejemplo mental: si una compra exige varios pasos, la transacción evita que se guarde solo una parte.

## La lectura correcta de esta sección

El autor te está entrenando para pensar así:

```
1. Primero diseño la base  → DDL2. Luego lleno y cambio datos → DML3. Después controlo permisos → DCL4. Por último aseguro coherencia en bloque → TCL
```

Eso es lo que realmente quiere que veas: **SQL no es un solo conjunto de comandos; es un sistema de control dividido por intención**.![[24_db_reglas_sql.png]]