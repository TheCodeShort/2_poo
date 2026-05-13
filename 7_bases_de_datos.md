[[SDLC_sofware.pdf#search=Conceptos generales de bases de datos|SDLC_sofware, p.354]]
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
	

La figura [[SDLC_sofware.pdf#search=Figura 1.|SDLC_sofware, p.359]] de las llamadas telefónicas sirve para aterrizar esa idea. Ahí el autor quiere que veas que una base de datos puede representarse como una estructura **bidimensional**: columnas para atributos y filas para registros. Cada fila corresponde a una llamada concreta, y cada columna agrupa un tipo de dato específico. En otras palabras, te está entrenando para leer una tabla no como “cuadritos”, sino como una representación formal de hechos del mundo real.

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
es la extensión natural de la relacional: mientras la relacional trabaja con tablas bidimensionales, la multidimensional trabaja con **cubos** o incluso con **N dimensiones**. El autor la conecta con análisis estadístico de datos históricos y volúmenes grandes de información, y por eso la asocia con escenarios tipo bodega de datos u OLAP. La idea que te quiere transmitir no es solo “otro tipo más”, sino que hay bases pensadas para **analítica** y no para transacción diaria.

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
