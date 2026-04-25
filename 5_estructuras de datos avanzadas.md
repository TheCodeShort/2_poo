1. **Listas:** Colecciones lineales de elementos en las que el orden de inserción se respeta. En POO, se implementan mediante clases como ArrayList o LinkedList, cada una con características particulares (García & Mendoza, 2022).
	- Es la estructura más común. Funcionan como una fila de sillas numeradas donde el orden importa.

		- _Ejemplo en el código:_ `ArrayList` (muy usada en JAVA) o `LinkedList`.
		    
		- _Uso práctico:_ Mostrar el catálogo de productos de una tienda virtual, donde quieres mantener el orden en el que se agregaron.
		
	- **¿Cómo funciona en la vida real?**

		Piensa en un **estuche de CDs** o un **archivador**.
		
		- Cada elemento tiene una **posición** (índice).
		- En programación, siempre empezamos a contar desde el **cero (0)**.
		- Si quitas el elemento del medio, los demás se "reacomodan". 
		
		- **ArrayList (Como un estante de libros)**

			Están todos pegados. Si quieres el libro 5, vas directo a él. Pero si quieres meter un libro nuevo al principio, tienes que empujar todos los demás hacia la derecha.
			
			- **Ventaja:** Acceso instantáneo por posición.
			- **Desventaja:** Lento para añadir o quitar cosas en el medio.
		
		1. Ejemplo en Código Java ==ArrayList==
			1. ```java
			   import java.util.ArrayList; // Importamos la herramienta de listas
				import java.util.List;
				
				public class EjemploListas {
					public static void main(String[] args) {
						
						// 1. Creamos la lista (como una bolsa donde solo caben Strings)
						List<String> listaPacientes = new ArrayList<>();
				
						// 2. AGREGAR: Metemos elementos
						listaPacientes.add("Alex");    // Posición 0
						listaPacientes.add("Juan");    // Posición 1
						listaPacientes.add("Maria");   // Posición 2
				
						// 3. ACCEDER: ¿Quién está en la primera posición?
						System.out.println("El primer paciente es: " + listaPacientes.get(0));
				
						// 4. ELIMINAR: Juan se fue, lo borramos
						listaPacientes.remove(1); 
				
						// 5. TAMAÑO: ¿Cuántos quedan?
						System.out.println("Pacientes restantes: " + listaPacientes.size());
					}
				}
			   ```

		- **LinkedList (Como una cadena de tesoros)**

			Cada elemento (llamado "nodo") tiene el dato y una "mano" que agarra al siguiente. No están pegados en memoria, están unidos por direcciones.
			
			- **Ventaja:** Rapidez extrema para meter o sacar elementos (solo rompes un eslabón y enganchas el nuevo).
			- **Desventaja:** Si quieres el elemento 100, Java tiene que ir desde el 1, pasando por el 2, el 3... hasta llegar al 100. No puede "saltar" directo.
			
			
			1. **Ejemplo en código Java** ==LinkedList==
				- ```java
			  import java.util.LinkedList;
				import java.util.List;
				
				public class EjemploLinkedList {
				    public static void main(String[] args) {
				        // Solo cambia 'ArrayList' por 'LinkedList'
				        List<String> listaEnlazada = new LinkedList<>();
				
				        // ¡Los métodos son los mismos!
				        listaEnlazada.add("Paciente A");
				        listaEnlazada.add("Paciente B");
				        
				        // Pero LinkedList tiene "superpoderes" extra si usas la clase específica:
				        LinkedList<String> listaPro = new LinkedList<>();
				        listaPro.add("Medio");
				        listaPro.addFirst("Inicio"); // Método que no tiene ArrayList
				        listaPro.addLast("Final");   // Método que no tiene ArrayList
				
				        System.out.println(listaPro);
				    }
				}

				  ```


2. **Pilas (Stacks - LIFO):** Estructuras de tipo LIFO (Last In, First Out) que permiten apilar y desapilar elementos. Se utilizan en la implementación de algoritmos recursivos, control de llamadas o deshacer acciones.

	- El primero en entrar es el primero en salir). Piensa en la fila del banco: el primero que llega es el primero en ser atendido.
    
    - _Uso práctico:_ Una cola de impresión. Si mandas a imprimir 3 documentos, la impresora los saca en el orden exacto en que los recibió. También existen las _Priority Queues_, donde alguien puede "colarse" si tiene mayor urgencia.
        
	- **Conjuntos (Sets):** Son como un club exclusivo: **no admiten duplicados**.
	    
	    - _Uso práctico:_ Imagina que quieres registrar los números de documento (cédulas) de los usuarios. No pueden existir dos personas con la misma cédula. Un `HashSet` rechazaría automáticamente cualquier intento de guardar una cédula repetida, haciéndolo muy eficiente.
	
	- Para entender las **Pilas**, olvida los estantes y las cadenas. Imagina una **pila de platos** o una **pila de libros**:

		1. Solo puedes poner un plato **arriba** de todos.
		2. Si quieres sacar un plato, solo puedes agarrar el que está **arriba**.
		3. Si quieres el plato que está al fondo, ¡tienes que sacar todos los de arriba primero!

	- Los 3 comandos básicos en Java

		En las pilas no hablamos de "añadir" o "quitar", usamos nombres especiales:
		
		- **`push` (Empujar):** Pones un elemento arriba de la pila.
		- **`pop` (Sacar):** Sacas el elemento de arriba (y desaparece de la pila).
		- **`peek` (Vistazo):** Miras qué hay arriba, pero no lo quitas. 
		
	- 2. **Ejemplo en código Java** ==Stack==
		- ```java
		  import java.util.Stack;
			
			public class EjemploPila {
			    public static void main(String[] args) {
			        // Creamos la pila de pesos
			        Stack<Double> historialPesos = new Stack<>();
			
			        // 1. PUSH: El paciente se pesa varias veces en el mes
			        historialPesos.push(80.5); // Primero en entrar (Fondo)
			        historialPesos.push(79.0); 
			        historialPesos.push(78.2); // Último en entrar (Cima)
			
			        // 2. PEEK: ¿Cuál es el peso actual? (Sin borrarlo)
			        System.out.println("Peso actual: " + historialPesos.peek()); // 78.2
			
			        // 3. POP: El paciente dice "me equivoqué", borramos el último
			        double pesoBorrado = historialPesos.pop(); 
			        System.out.println("Eliminamos el peso: " + pesoBorrado);
			
			        // Ahora el peso que quedó arriba es el anterior
			        System.out.println("Nuevo peso actual: " + historialPesos.peek()); // 79.0
			    }
			}
		 ```
	- **Deque**
		- El nombre **`Deque`** (se pronuncia "deck") significa _Double Ended Queue_ (Cola de doble final). Es como una "Pila Superpoderosa" o una "Cola Flexible".

			La gran diferencia es que en un `Deque` puedes meter y sacar cosas **por ambos lados** (por arriba y por abajo).
		
		1. ¿Por qué se usa en lugar de `Stack`?
		
			Java recomienda usar `Deque` (específicamente la implementación `ArrayDeque`) porque la clase `Stack` vieja es un poco lenta y pesada. `Deque` es más moderna, rápida y versátil.
		
		2. Ejemplo en código: Usándolo como Pila
			
			Aquí tienes cómo se vería tu historial de pesos usando `ArrayDeque`. Fíjate que los métodos cambian un poquito para ser más descriptivos:
			```java
			import java.util.ArrayDeque;
			import java.util.Deque;
			
			public class EjemploDeque {
			    public static void main(String[] args) {
			        // Creamos el Deque (el motor es un ArrayDeque)
			        Deque<Double> historial = new ArrayDeque<>();
			
			        // --- COMPORTAMIENTO DE PILA (LIFO) ---
			        
			        // 1. Agregar arriba (en lugar de push)
			        historial.push(90.0);
			        historial.push(85.5);
			        historial.push(82.0); // Este queda arriba
			
			        // 2. Ver el de arriba
			        System.out.println("Último peso: " + historial.peek()); // 82.0
			
			        // 3. Sacar el de arriba
			        historial.pop(); 
			
			        // --- ¿POR QUÉ ES MEJOR? (Flexibilidad) ---
			        
			        // Puedes agregar algo directamente al fondo sin sacar lo de arriba
			        historial.addLast(100.0); 
			        
			        // O sacar el peso más viejo de todos (el del fondo)
			        Double pesoInicial = historial.removeLast();
			        
			        System.out.println("Historial restante: " + historial);
			    }
			}
			/**
			- **Para el frente:** => `addFirst()`, `removeFirst()`, `peekFirst()`.
- **Para el final:** => `addLast()`, `removeLast()`, `peekLast()`.
			*/			
			```

3. **Colas (Queues):** Estructuras FIFO (First In, First Out) útiles para gestionar procesos en espera, tareas de impresión o mensajes en sistemas distribuidos. Variantes como PriorityQueue permiten ordenamientos adicionales.
	-   Piensa en la fila del banco: el primero que llega es el primero en ser atendido.

		- _Uso práctico:_ Una cola de impresión. Si mandas a imprimir 3 documentos, la impresora los saca en el orden exacto en que los recibió. También existen las _Priority Queues_, donde alguien puede "colarse" si tiene mayor urgencia.
		- Imagina la fila de un banco o la fila para entrar al cine:
			1. La gente llega y se pone al **final** de la fila.
			2. El cajero atiende únicamente al que está al **principio**.
			3. Nadie puede colarse (en teoría) ni salir por el medio.
			
		1. **Los comandos en Java**

			A diferencia de la Pila, aquí los nombres cambian para reflejar que es una fila:
			
			- **`add` / `offer`:** Llegas a la fila y te pones al final.
			- **`poll`:** El primero de la fila sale porque ya lo atendieron (se elimina).
			- **`peek`:** Miras quién es el siguiente en ser atendido, pero no lo sacas.
			- **Un detalle de "Modularidad":**  
				Nota que en el código usé `Queue<String> lista = new LinkedList<>();`. Aquí aplicamos de nuevo el **Diseño Orientado a Interfaces**: `Queue` es la interfaz (el contrato) y `LinkedList` es la clase que hace el trabajo sucio.
			
			1. **Ejemplo en código Java** ==Queue==
				- ```java
			   import java.util.LinkedList;
				import java.util.Queue;
				
				public class EjemploCola {
				    public static void main(String[] args) {
				        // Usamos LinkedList porque implementa la interfaz Queue
				        Queue<String> filaPacientes = new LinkedList<>();
				
				        // 1. LLEGAN PACIENTES (Se forman al final)
				        filaPacientes.add("Paciente 1: Carlos");
				        filaPacientes.add("Paciente 2: Adriana");
				        filaPacientes.add("Paciente 3: Pepe");
				
				        // 2. PEEK: ¿A quién le toca ahora?
				        System.out.println("Siguiente en turno: " + filaPacientes.peek()); // Carlos
				
				        // 3. POLL: Atendemos a Carlos y sale de la fila
				        String atendido = filaPacientes.poll();
				        System.out.println("Atendiendo a: " + atendido);
				
				        // 4. ¿Quién quedó de primero ahora?
				        System.out.println("Ahora el turno es de: " + filaPacientes.peek()); // Adriana
				    }
				}
				```


4. **Conjuntos (Sets):** Colecciones que no permiten duplicados. Implementaciones como HashSet o TreeSet ofrecen eficiencia en las operaciones de búsqueda y manipulación de elementos únicos (Hernández & Baquero, 2023). 

	- Un **Set** es como una bolsa donde echas cosas, pero con una regla mágica: **No se permiten repetidos.**

		Si intentas meter a "Adriana" dos veces, la bolsa simplemente ignora la segunda entrada. Es la estructura perfecta cuando quieres asegurar que algo sea **único**.
		
		1. ¿Cómo funciona en la vida real?
		
			Imagina una **lista de invitados** a una fiesta. No importa cuántas veces alguien intente anotarse, solo puede aparecer una vez en la lista final. O piensa en los **números de cédula** dos personas no pueden tener el mismo número.
		
		1. **Ejemplo en Código Java** ==Set==
			- ```java
			  import java.util.HashSet;
				import java.util.Set;
				
				public class EjemploSets {
				    public static void main(String[] args) {
				        // Creamos el conjunto de IDs de pacientes
				        Set<String> idsPacientes = new HashSet<>();
				
				        // 1. AGREGAR
				        idsPacientes.add("1020");
				        idsPacientes.add("3040");
				        idsPacientes.add("1020"); // ¡Ojo! Estamos repitiendo el ID
				
				        // 2. COMPROBAR EL TAMAÑO
				        // Aunque intentamos meter 3, solo habrá 2.
				        System.out.println("Total de pacientes únicos: " + idsPacientes.size()); 
				
				        // 3. BUSCAR: Es súper rápido saber si alguien ya está
				        if (idsPacientes.contains("1020")) {
				            System.out.println("El paciente ya está registrado.");
				        }
				
				        // 4. ELIMINAR
				        idsPacientes.remove("3040");
				    }
				}
			  ```

	- **Sin Duplicados:** La lista te deja tener 50 "Adrianas". El Set solo una.
	- **Sin Orden (Normalmente):** El `HashSet` no te garantiza que los elementos salgan en el mismo orden en que los metiste. Los guarda "donde quepan" para ser más rápido.
	- **Búsqueda Veloz:** En una lista de 1 millón de nombres, buscar a "Adriana" toma tiempo. En un Set, Java sabe exactamente en qué rincón de la memoria está, ¡es casi instantáneo!
	
	- En Java, el más usado es el `HashSet`.
		- **HashSet:** El más rápido, pero desordenado.
		- **TreeSet:** (Aquí se une con el concepto de Árboles). Guarda los elementos **ordenados** (por ejemplo, de la A a la Z), pero es un poquito más lento que el HashSet

5. **Mapas (Maps):** Asociaciones clave-valor también conocidos como Diccionarios que permiten almacenar pares de datos. Ejemplos comunes incluyen HashMap, TreeMap y LinkedHashMap, fundamentales para implementar diccionarios, índices y caches (García & Mendoza, 2022). 
	- _Uso práctico:_ Imagina un casillero. La _Clave_ es el número de tu carnet, y el _Valor_ es tu mochila. Si le das el número de carnet al mapa (`HashMap`), te devuelve tus datos instantáneamente sin tener que buscar uno por uno. Es vital para relacionar usuarios con sus sesiones activas.
	- Si el **Set** era una bolsa de elementos únicos, el **Mapa** es como una **agenda telefónica** o un **casillero de gimnasio**.
		
	- La regla aquí es el concepto de **Clave/Valor**:
		
		- **La Clave (Key):** Es el identificador único (como el número de cédula o el nombre del contacto). No se puede repetir.
		- **El Valor (Value):** Es la información que guardas dentro (como el objeto `Persona` con su peso y altura).
		
		1. ¿Por qué es la "Estructura Maestra"?
		
			Porque te permite encontrar a **"Adriana"** (el valor) al instante si conoces su **ID** (la clave), sin tener que recorrer una lista, ni vaciar una pila, ni esperar en una cola.
		
		1. **Ejemplo en Código Java** ==Map==
			- ```java
			  import java.util.HashMap;
				import java.util.Map;
				
				public class EjemploMapas {
				    public static void main(String[] args) {
				        // Map<Clave, Valor> -> Map<Cédula, Objeto Persona>
				        Map<String, String> agendaPacientes = new HashMap<>();
				
				        // 1. PUT: Guardar (Clave, Valor)
				        agendaPacientes.put("1020", "Adriana (IMC: 22.5)");
				        agendaPacientes.put("3040", "Juan (IMC: 28.1)");
				        agendaPacientes.put("5060", "Pepe (IMC: 24.0)");
				
				        // 2. GET: Buscar directamente por la clave
				        String datos = agendaPacientes.get("1020");
				        System.out.println("Datos recuperados: " + datos);
				
				        // 3. ¿Qué pasa si meto la misma clave otra vez?
				        agendaPacientes.put("1020", "Adriana - DATOS ACTUALIZADOS"); 
				        // ¡El valor viejo se sobrescribe! La clave es única.
				
				        // 4. ELIMINAR
				        agendaPacientes.remove("5060");
				
				        // 5. REVISAR SI EXISTE
				        if (agendaPacientes.containsKey("3040")) {
				            System.out.println("Juan está en el sistema.");
				        }
				    }
				}
			```
			
5. **Arbol:** Los **Árboles** no son solo "otra forma de guardar datos", sino que son la **estrategia de búsqueda** más eficiente que existe. Se les llama "motor" porque muchas estructuras (como el `TreeSet` o el `TreeMap`) los usan por dentro para que todo sea veloz.

	Imagina que estás buscando una palabra en un diccionario físico de 1,000 páginas:
	
	- **Forma Lista:** Empiezas en la página 1, luego la 2... hasta la 1,000. (Muy lento).
	- **Forma Árbol:** Abres el libro por la mitad. ¿Tu palabra empieza con una letra mayor o menor a la que viste? Si es mayor, descartas 500 páginas de un solo golpe. Repites el proceso y en solo **10 saltos** encuentras tu palabra entre 1,000.
	
	1. ¿Cómo es la estructura?
	
		Se llama árbol porque tiene una **Raíz** (el nodo principal) y de ahí salen **Ramas** (hijos).  
		En un **Árbol Binario de Búsqueda** (el más común), la regla es:
	
		- Los valores **menores** van a la **izquierda**.
		- Los valores **mayores** van a la **derecha**.
	
	1. Ejemplo visual
	
		Si insertas los números de identificación: **50, 20, 70, 10, 30**.
		```text
	      50 (Raíz)
	     /  \
	   20    70
	  /  \
	 10  30
		```
		Si buscas el **30**:

		1. Miras el 50: "¿30 es menor?". Sí, vas a la izquierda.
		2. Miras el 20: "¿30 es mayor?". Sí, vas a la derecha.
		3. **¡Lo encontraste!** Solo hiciste 2 comparaciones en lugar de 5.

	1. ¿Por qué es el "Motor"?
	
		Cuando usas un `HashMap` o un `HashSet` en Java, si hay demasiados datos, Java deja de usar una lista simple y convierte todo internamente en un **Árbol** para que, aunque tengas millones de pacientes, encontrarlos tome milisegundos.
		
	2. ¿Cuándo lo usarías tú directamente?
		
		Casi nunca programarás un árbol desde cero (a menos que sea para un examen), pero usas su lógica cuando necesitas que tus datos estén **siempre ordenados automáticamente**:
		```java
		import java.util.TreeSet;
		// Un Set que usa un Árbol por dentro
		TreeSet<Integer> edades = new TreeSet<>();
		edades.add(40);
		edades.add(10);
		edades.add(25);
		
		System.out.println(edades); // Imprime: [10, 25, 40] -> ¡Se ordenó solo!
		```
		

6. Colecciones genéricas: Permiten trabajar con estructuras de datos parametrizadas por tipo, garantizando la seguridad en tiempo de compilación al evitar errores de tipo en tiempo de ejecución (Vázquez, 2020). 

	- ==son la forma que tiene Java de decir: _"Esta bolsa es solo para un tipo de cosa"_==.

		Antes, en las versiones muy viejas de Java, las listas eran como "bolsas negras" donde podías meter cualquier cosa: un String, un número y un objeto `Persona` juntos. El problema era que al sacar algo, no sabías qué era y el programa solía romperse (errores de ejecución).
		
		Las **Genéricas** llegaron para dar orden y seguridad usando los símbolos **`< >`** (llamados "diamante").
		
		1. ¿Cómo se ven?
		
		- **Sin genéricos (Peligroso):** `List lista = new ArrayList();` (Cualquier cosa entra).
		- **Con genéricos (Seguro):** `List<Persona> lista = new ArrayList<>();` (Solo entran objetos `Persona`).
		
		1. ¿Por qué son importantes para tu modularidad?
		
		2. **Seguridad de Tipo (Type Safety):**  
		    Si declaras `List<Double> pesos`, e intentas meter el nombre "Alex" (`pesos.add("Alex")`), **IntelliJ te marcará un error rojo antes de que des Play**. Esto evita errores cuando tu app esté funcionando.
		3. **No necesitas "Castear" (Convertir):**  
		    Al sacar un elemento, Java ya sabe exactamente qué es.
		    - **Antes:** Tenías que decirle: `Persona p = (Persona) lista.get(0);`
		    - **Ahora:** Simplemente pones: `Persona p = lista.get(0);`
		4. **Código más limpio:**  
		    Cualquier programador que lea tu código sabrá de inmediato qué contiene esa colección sin tener que adivinar.
		
		5. Ejemplo rápido en tu proyecto
		
		Cuando crees tu lista de pacientes, lo harás así:	
	```java
	// "List" es la colección, "<Paciente>" es el genérico
	List<Paciente> listaDeConsultorio = new ArrayList<>();
	
	listaDeConsultorio.add(new Paciente("Alex", 75.0, 1.75)); 
	// Si intentas agregar un número aquí, Java no te dejará.
	```

7. Comparación de estructuras: La elección entre estructuras tradicionales y colecciones modernas depende de factores como la eficiencia, la legibilidad y la compatibilidad con algoritmos avanzados.
	1. es el ==proceso de analizar cuál es la mejor forma de organizar tus datos basándote en dos factores: **tiempo** (qué tan rápido es el programa) y **memoria** (cuánto espacio ocupa)==. 

		No existe una estructura "perfecta", sino una "adecuada" para cada situación. Por ejemplo, un **ArrayList** es excelente para leer datos rápidamente por su posición, pero un **HashMap** es superior si necesitas buscar un elemento específico sin recorrer toda la lista. 
		
		Tabla Comparativa de Estructuras en Java
		
		Esta tabla resume cómo se comportan las herramientas que hemos visto según la tarea que necesites realizar
		
|Estructura|¿Permite Repetidos?|¿Mantiene el Orden?|¿Para qué es mejor?|Desventaja principal|
|---|---|---|---|---|
|**ArrayList**|Sí|Sí (por índice)|Leer datos rápido por posición.|Lenta al borrar en el medio.|
|**LinkedList**|Sí|Sí|Insertar/Borrar en los extremos.|Lenta para buscar el elemento #500.|
|**HashSet (Set)**|**No**|No|Asegurar que los datos sean únicos.|No sabes en qué orden saldrán.|
|**TreeSet (Set)**|**No**|**Sí (ordenado)**|Mantener datos ordenados siempre.|Más lenta que el HashSet.|
|**HashMap (Map)**|Claves: No|No|Buscar información usando un ID.|Usa más memoria que una lista.|
|**Stack (Pila)**|Sí|LIFO (Inverso)|Deshacer acciones o retroceder.|Solo accedes al último que entró.|
|**Queue (Cola)**|Sí|FIFO (Llegada)|Gestionar turnos y procesos.|Solo accedes al primero que llegó.|

- ¿Cómo elegir? (El criterio de "Big O")
	En programación profesional se usa la **Notación Big O** para comparar la eficiencia: 
	
	- **O(1) (Constante):** Es la más rápida. No importa si tienes 10 o 10 millones de datos, tarda lo mismo (ej. `get` en un ArrayList o `put` en un HashMap).
	
	- **O(n) (Lineal):** El tiempo crece según la cantidad de datos (n). Si tienes 1,000 datos, podría tardar 1,000 pasos (ej. buscar a alguien en una lista común).

8. ==Importante==
	1. 1. **Lo de la izquierda (`List`, `Set`, `Map`):** Es el **RANGO** o la **FUNCIÓN**. Define qué "promete" hacer el objeto. Si dices `List`, prometes que los datos tendrán un orden y un índice.
	2. **Lo de la derecha (`new ArrayList`, `new LinkedList`):** Es el **MOTOR** o la **ESTRATEGIA**. Define cómo se organiza la memoria internamente para cumplir esa promesa.
	
	3. **Los "Superpoderes" :**
		
		Cuando eliges el motor de la derecha, estás eligiendo qué superpoder será más fuerte:
		
		- Si eliges `new ArrayList<>`, el superpoder es **VELOCIDAD DE LECTURA** (encuentra el índice 500 al instante).
		- Si eliges `new LinkedList<>`, el superpoder es **AGILIDAD DE CAMBIO** (mete o saca elementos en el medio sin despeinarse).
		- Si eliges `new TreeSet<>`, el superpoder es **ORDEN AUTOMÁTICO** (él mismo acomoda los números o letras mientras los vas metiendo).
		
		- Un ejemplo visual para tu código:
		```java
		// "Prometo que será una LISTA, y hoy quiero que el motor sea un ARRAY"
		List<Paciente> lista = new ArrayList<>(); 
		
		// Pero si mañana tu app de IMC tiene miles de pacientes y borras muchos...
		// ¡Solo cambias el motor y el resto del código sigue igual!
		List<Paciente> lista = new LinkedList<>(); 
		```
8. **For-Each (o For mejorado)**
	1. El `for` clásico (`for i=0...`) tiene un problema: **es muy manual**. Tienes que gestionar el índice `i`, revisar que no te pases del tamaño (`size`) y luego sacar el objeto con `get(i)`. Es fácil equivocarse y que el programa explote.

		El **For-Each** dice: _"Java, tú sabes cuántos elementos hay, solo dame el objeto de cada vuelta"_.
		
		- **Más legible:** Se lee como "Para cada **Paciente p** dentro de **lista**...".
		- **Más seguro:** Es imposible que te pases del índice (no hay `IndexOutOfBoundsException`).
		
		- **La lógica del For-Each**

			Se escribe así: `for (Clase nombreVariable : nombreColeccion)`
			
			1. **Clase:** El tipo de dato que hay dentro (ej: `Paciente`).
			2. **nombreVariable:** El nombre que tú quieras darle al objeto en esa vuelta (ej: `p`).
			3. ==**:**== Significa "dentro de" o "de la".
			4. **nombreColeccion:** Tu lista o array.
		
		1. ¿Cuántos tipos de `for` hay?
		
			En Java moderno usamos principalmente **3 formas** de recorrer cosas:
		
			1. **El Clásico (`for` con índice):**
				1. ```java
				   for (int i = 0; i < lista.size(); i++) {
				    System.out.println(lista.get(i));
				}
				// Úsalo solo si necesitas saber la posición (ej: "Borrar solo los pares").
		       	```
		       
			   2. **El For-Each:**
			       1. ```java
					 for (Paciente p : lista) {
					    // Aquí puedes hacer DE TODO sin errores raros:
					    if (p.getPeso() > 100) {
					        System.out.println("Alerta con " + p.getNombre());
					    }
					    // Puedes usar 'break' para detenerte o 'return'
					}
					// Es el estándar para leer datos.
			       ```
			    - **Por qué evita errores:** Porque Java gestiona el inicio y el fin de la lista por ti.
				- **Por qué es mejor que la Lambda:** Si hay un error dentro del `if`, el **Debugger** de IntelliJ se detendrá exactamente en esa línea y podrás ver cuánto vale el peso de `p` en ese momento.

			3. **El `forEach` con Lambda (Nivel avanzado):**  Es una sola línea de código que se usa mucho en Java moderno:
				1. ```java
				   (nombre de mi lista).forEach(p -> System.out.println(p.getNombre()));
				   
				   (nombre de la lista).stream()                  // 1. Ponemos los datos en la cinta
					.filter(p -> p.getNombre().equals("Maria")) // 2. El filtro saca a las que no se llamen Maria
					.forEach(p -> System.out.println(p));        // 3. Al final, mostramos lo que quedó

					```
					Efectivamente, al igual que el operador ternario, el `forEach` con Lambda (`->`) puede volverse un dolor de cabeza si se abusa de él.

					- **¿Cuándo falla?** No es que el programa se rompa, sino que se vuelve **imposible de depurar (debuggear)**. Si pones mucha lógica dentro de esa línea y algo falla, IntelliJ no te dirá exactamente qué parte de la línea falló. Además, dentro de una Lambda no puedes usar `break` ni `continue`, lo cual te quita control.
					
					- **Regla de oro:** Úsalo solo para tareas ultra simples, como imprimir algo (`System.out::println`). Para lógica de negocios (como calcular IMC y validar datos), el **For-Each normal** (el de los dos puntos `:`) es mucho mejor.
					
					- si quiero poner algo de lógica compleja es difícil de hacer y se vuelve complejo con el tiempo