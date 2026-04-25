[[1_poo.pdf#search=Patrones de Diseño Orientados a Objeto|1_poo, p.42]]
Los patrones de diseño son soluciones reutilizables y probadas a problemas comunes que surgen durante el desarrollo de software orientado a objetos. Un patrón de diseño no es un fragmento de código específico, sino una guía o esquema para estructurar las clases y objetos de una manera que resuelva un problema recurrente dentro de un contexto determinado (Vázquez, 2020).

Estos patrones encapsulan las mejores prácticas de ingenieros experimentados y promueven principios fundamentales como la reutilización, el bajo acoplamiento, la cohesión y la mantenibilidad. Existen diversas clasificaciones, pero las más difundidas son las de ==creacionales, estructurales y de comportamiento==, propuestas inicialmente por el grupo conocido como los "Gang of Four" (GoF) (Ruiz & López, 2023).

Fueron formalizados en **1994** por cuatro autores conocidos como el **"Gang of Four" (GoF)** (Erich Gamma, Richard Helm, Ralph Johnson y John Vlissides). 

Publicaron el libro _Design Patterns: Elements of Reusable Object-Oriented Software_. Ellos se inspiraron en la arquitectura de edificios de Christopher Alexander, pero lo aplicaron al software.

existen patrones para otros estilos (como programación funcional), cuando la gente dice "Patrones de Diseño" casi siempre se refiere a los **Patrones de Diseño Orientados a Objetos (POO)** son soluciones estandarizadas para problemas comunes que surgen al crear objetos y hacer que interactúen entre sí

1. ==**Patrones Creacionales: "El Taller de Fabricación"**==

	**Objetivo:** Controlar **cómo se crean** los objetos.
	
	En lugar de llenar tu código de `new Clase()`, estos patrones actúan como intermediarios.
	
	- **Por qué se usan:** Porque a veces crear un objeto es complejo o necesitas asegurarte de que solo exista uno, o quieres que el sistema sea independiente de cómo se crean sus productos.
	- **En palabras simples:** Es decidir si compras un mueble ya armado, lo pides por piezas o contratas a un carpintero para que lo haga a medida.
	
	1. **Patrones de diseño**
		1. ==**Singleton:**== Garantiza que una clase tenga solo una instancia global y proporciona un punto de acceso a ella. 
			- La palabra _Singleton_ significa "único" o "solitario". Su idea es simple pero radical: **Garantizar que una clase tenga una sola instancia (un solo objeto) en todo el programa y proporcionar un punto de acceso global a ella.**
	
			- Imagina una app de IMC tienes una **Configuración** de usuario o una **Conexión a una Base de Datos**. No quieres 10 objetos de configuración gastando memoria; quieres que todos los módulos de tu programa consulten el mismo y único objeto.
		
			1. **Objetivos**
			
				- **Control total:** Evitar que alguien use la palabra `new` fuera de la propia clase.
				- **Ahorro de recursos:** No duplicar objetos pesados (como conexiones o lectores de archivos).
				- **Punto de acceso global:** Que cualquier parte del código pueda llamar a esa instancia sin tener que pasarla como parámetro de mano en mano.
			
			2. **¿Cómo se implementa en Java? (Reglas de Oro)**
			
				Para que una clase sea **Singleton**, debe cumplir tres condiciones en su código:
				
				1. **Constructor privado:** Para que nadie pueda hacer `new Clase()`.
				2. **Atributo estático privado:** Una variable de la misma clase que guardará la única instancia.
				3. **Método estático público:** El que entrega la instancia (normalmente llamado `getInstance()`).
			
			3. **Ejemplo en Java: Un Gestor de Configuración**
			
				- Imagina que quieres guardar el idioma y la moneda de tu app de IMC.
					```java
						public class Configuracion {
					    // 1. Atributo estático privado (aquí vive el único objeto)
					    private static Configuracion instancia;
					    
					    public String idioma;
					    public String moneda;
					
					    // 2. Constructor PRIVADO: ¡Nadie puede hacer 'new' desde fuera!
					    private Configuracion() {
					        this.idioma = "Español";
					        this.moneda = "COP";
					    }
					
					    // 3. Método público para obtener la instancia
					    public static Configuracion getInstance() {
					        if (instancia == null) {
					            // Solo se crea la primera vez que alguien lo pide
					            instancia = new Configuracion();
					        }
					        return instancia;
					    }
					}
					```
							
				- **¿Cómo se usa en el `Main`?**

					```java
					public class Main {
					    public static void main(String[] args) {
					        // Configuracion c = new Configuracion(); // ERROR: El constructor es privado
					        
					        // Obtenemos la única instancia
					        Configuracion config = Configuracion.getInstance();
					        System.out.println("Idioma: " + config.idioma);
					
					        // Si en otra parte del código pido la instancia...
					        Configuracion otraConfig = Configuracion.getInstance();
					        otraConfig.idioma = "Inglés";
					
					        // ¡Ambas variables apuntan al MISMO objeto!
					        System.out.println("Idioma en config original: " + config.idioma); // Imprimirá Inglés
					    }
					}
					```
			4. En el ejemplo, si cambias el idioma en `otraConfig`, automáticamente cambia en `config`, porque **son el mismo objeto en memoria**. Es como tener un solo control remoto para un televisor: no importa quién lo agarre, todos operan la misma TV.
				
				**Dato extra:** Muchos lo consideran un "Antipatrón" si se usa demasiado, porque actúa como una variable global y puede ocultar dependencias. ¡Úsalo solo cuando realmente necesites unidad absoluta!

		2. ==**Factory Method:**== Define una interfaz para crear objetos, dejando a las subclases la decisión de qué clase instanciar. 
		
			- El **Factory Method** es el patrón que quita la responsabilidad de "instanciar" (hacer el `new`) a la clase principal y se la da a una **clase especialista**: la Fábrica.

			1. **La Idea Central**

				- Imagina que vas a una pizzería. Tú no entras a la cocina a estirar la masa ni a prender el horno (no haces el `new Pizza()`). Tú simplemente le dices al mesero: _"Quiero una de Pepperoni"_. El mesero va a la **fábrica** (la cocina) y te trae el producto terminado.
				
				- En código, el Factory Method permite que tu programa pida un objeto sin saber exactamente de qué clase es, solo sabe que cumple con una interfaz.
			
			2. **Objetivos**
			
				- **Centralizar la creación:** Si mañana cambia la forma de crear un objeto, solo cambias la fábrica, no los 50 lugares donde lo usas.
				- **Desacoplamiento:** Tu `Main` no necesita conocer todas las clases hijas, solo conoce la "Fábrica" y la "Interfaz".

			3. **Ejemplo en Java: Fábrica de Notificaciones**
			
				Imagina que tu app de IMC debe avisar al paciente sus resultados. Puede ser por **Email** o por **SMS**.
				
				- **Paso A: La Interfaz (El producto)**
				
					- ```java
						 public interface Notificacion {
						     void enviar(String mensaje);
						}
					 ```

				- **Paso B: Las Clases Concretas**

					```java
					public class NotificacionEmail implements Notificacion {
					    public void enviar(String mensaje) {
					        System.out.println("Enviando Email: " + mensaje);
					    }
					}
					
					public class NotificacionSMS implements Notificacion {
					    public void enviar(String mensaje) {
					        System.out.println("Enviando SMS: " + mensaje);
					    }
					}
					```
					
			    - **Paso C: LA FÁBRICA (El corazón del patrón)**
 
					```java
						public class NotificacionFactory {
						    // Este es el "Factory Method"
						    public Notificacion crearNotificacion(String tipo) {
						        if (tipo.equalsIgnoreCase("EMAIL")) {
						            return new NotificacionEmail();
						        } else if (tipo.equalsIgnoreCase("SMS")) {
						            return new NotificacionSMS();
						        }
						        return null;
						    }
						}
					```

			4. **¿Cómo se usa en el `Main`?**

				- Aquí es donde ves la magia: el `Main` **nunca** hace `new NotificacionEmail()`.
					```java
					public class Main {
					    public static void main(String[] args) {
					        NotificacionFactory fabrica = new NotificacionFactory();
					
					        // Le pedimos a la fábrica lo que necesitamos
					        Notificacion n1 = fabrica.crearNotificacion("EMAIL");
					        n1.enviar("Tu IMC es de 24.5");
					
					        Notificacion n2 = fabrica.crearNotificacion("SMS");
					        n2.enviar("Tu cita es mañana");
					    }
					}
					```

			5. **¿Por qué es mejor que usar `new`?**

				- Imagina que en 6 meses decides que los mensajes ya no se envían por SMS, sino por **WhatsApp**.
				
					- **Sin Fábrica:** Tendrías que buscar en todo tu proyecto dónde escribiste `new NotificacionSMS()` y cambiarlo por `new NotificacionWhatsApp()`.
					- **Con Fábrica:** Solo vas a la clase `NotificacionFactory`, cambias una línea de código, ¡y listo! Todo el sistema ahora usa WhatsApp sin que el resto del programa se haya enterado.
				
				- Diferencia clave con Singleton:
				
					- **Singleton:** Te da siempre el **mismo** objeto (instancia única).
					- **Factory:** Te crea objetos **nuevos** cada vez, pero oculta la complejidad de cómo se fabrican.

		3. ==**Builder:**== Separa la construcción de un objeto complejo de su representación final (Vázquez, 2020).
		
			==es el patrón favorito cuando tienes que crear un objeto **muy complejo**, con muchos atributos, o cuando quieres que ese objeto sea **inmutable** (que no cambie después de creado)==.

			1. El Problema: El "Constructor Monstruoso"
			
				Imagina que en tu app de IMC, la clase `Paciente` empieza a crecer. Ahora tiene: nombre, edad, peso, altura, teléfono, email, dirección, historial, seguro médico...
				
				Si usas un constructor normal, tendrías algo así:  
				```java
				new Paciente("Alex", 25, 75.0, 1.75, "555-123",            "email@test.com", "Calle 123", true, "Sura");
				```
			
			2. **Es un caos:**
			
				- ¿Cuál número era el peso y cuál la edad?
				- ¿Qué pasa si el paciente no tiene email? Tienes que pasar `null` o crear 20 constructores diferentes.
				
			3. La Solución: El Builder
			
				El patrón Builder propone que la creación del objeto sea **paso a paso**, como si estuvieras armando un carro en una línea de montaje. Tú eliges qué piezas poner y al final das la orden de "construir".
				
			1. Ejemplo en Java: Creando un Paciente "Pro"
			
				La Clase con su Builder interno		
				```java
				public class Paciente {
				    // Atributos privados (sin setters para que sea inmutable)
				    private final String nombre;
				    private final double peso;
				    private final double altura;
				    private final String email; // Opcional
				
				    // El constructor es privado: solo el Builder puede usarlo
				    private Paciente(PacienteBuilder builder) {
				        this.nombre = builder.nombre;
				        this.peso = builder.peso;
				        this.altura = builder.altura;
				        this.email = builder.email;
				    }
				    // Clase interna Builder
				    public static class PacienteBuilder {
				        private String nombre;
				        private double peso;
				        private double altura;
				        private String email;
				
				        // Métodos para configurar cada atributo (retornan el mismo builder)
				        public PacienteBuilder conNombre(String nombre) {
				            this.nombre = nombre;
				            return this;
				        }
				
				        public PacienteBuilder conMedidas(double peso, double altura) {
				            this.peso = peso;
				            this.altura = altura;
				            return this;
				        }
				
				        public PacienteBuilder conEmail(String email) {
				            this.email = email;
				            return this;
				        }
				
				        // El método final que entrega el objeto real
				        public Paciente build() {
				            return new Paciente(this);
				        }
				    }
				}
				```
				
			2. ¿Cómo se usa en el `Main`? (Sintaxis Encadenada)
			
				Esta es la parte más elegante. Se lee casi como lenguaje natural:
	
				```java
				public class Main {
				    public static void main(String[] args) {
				        
				        // Creamos un paciente paso a paso
				        Paciente p1 = new Paciente.PacienteBuilder()
				                        .conNombre("Alex")
				                        .conMedidas(75.0, 1.75)
				                        .conEmail("alex@correo.com")
				                        .build();
				
				        // Si otro paciente no tiene email, simplemente no llamas al método
				        Paciente p2 = new Paciente.PacienteBuilder()
				                        .conNombre("Juan")
				                        .conMedidas(80.0, 1.85)
				                        .build();
				    }
				}
				```
			
			3. ¿Por qué es "Buenísimo"?
			
				1. **Legibilidad:** Sabes exactamente qué valor es el peso y cuál es el nombre porque el método lo dice (`conMedidas`).
				2. **Inmutabilidad:** Como el objeto se crea de un solo golpe al final (`build()`) y no tiene setters, nadie puede cambiarle el peso a "Alex" por error después de creado.
				3. **Flexibilidad:** No necesitas 10 constructores para diferentes combinaciones de datos opcionales.
		
		4. ==**Abstract Factory (La "Fábrica de Fábricas")**==

			Si el _Factory Method_ creaba un producto (como una Pizza), el **Abstract Factory** crea **familias de productos relacionados** que deben ir juntos.
			
			**La Idea:**  
			Imagina que tu app de IMC ahora tiene "Temas": un **Tema Oscuro** y un **Tema Claro**.
			
			- Si el tema es **Oscuro**, el botón debe ser negro y el texto blanco.
			- Si el tema es **Claro**, el botón debe ser blanco y el texto negro.  
			    No puedes mezclar un botón oscuro con un texto negro porque no se vería. La _Abstract Factory_ asegura que si eliges la "Fábrica Oscura", todos los componentes (botones, textos, fondos) sean oscuros.

				```java
				// Interfaz de la Fábrica Maestra
				public interface TemaUIFactory {
				    Boton crearBoton();
				    Texto crearTexto();
				}
				
				// Fábrica Concreta 1
				public class TemaOscuroFactory implements TemaUIFactory {
				    public Boton crearBoton() { return new BotonNegro(); }
				    public Texto crearTexto() { return new TextoBlanco(); }
				}
				
				// En el Main:
				TemaUIFactory fabrica = new TemaOscuroFactory(); 
				fabrica.crearBoton(); // Siempre será negro porque usamos la fábrica oscura
				```

		5. ==**Prototype (El Clonador)**==
		
			Este es el patrón más curioso. En lugar de crear un objeto desde cero con `new`, ¡lo creas **clonando** uno que ya existe!
			
			**La Idea:**  
			Imagina que crear un objeto es muy costoso (por ejemplo, requiere leer mil archivos o conectarse a un satélite). Pero ya tienes uno creado. En lugar de repetir todo el proceso pesado, le pides al objeto: _"Oye, hazme una copia exacta de ti mismo"_.
			
			**¿Cuándo se usa?**  
			Cuando el costo de crear un objeto nuevo es mayor que el de copiar uno existente.
			
			**Ejemplo en Java:**  
			Java tiene una interfaz llamada `Cloneable` para esto.
			```java
			public class ReporteIMC implements Cloneable {
			    public String titulo;
			    public List<Double> datosPesados;
			
			    // Método para clonar
			    @Override
			    public ReporteIMC clone() {
			        try {
			            return (ReporteIMC) super.clone();
			        } catch (CloneNotSupportedException e) {
			            return null;
			        }
			    }
			}
			
			// En el Main:
			ReporteIMC reporteOriginal = new ReporteIMC();
			// Cargamos datos pesados una sola vez...
		/	
			// Creamos otro reporte igual en un milisegundo
			ReporteIMC reporteCopia = reporteOriginal.clone();
			```

---
3. **Patrones Estructurales: "El Plano de Montaje"**

	**Objetivo:** Organizar **cómo se unen** las clases y los objetos para formar estructuras más grandes.
	
	Se aseguran de que, si el sistema crece, las piezas sigan encajando bien sin romperse.
	
	- **Por qué se usan:** Para que clases que no fueron diseñadas para trabajar juntas puedan hacerlo, o para agrupar objetos de forma que parezcan uno solo.
	- **En palabras simples:** Es como usar adaptadores de enchufes para un viaje o usar piezas de Lego para armar una pared sólida.

4. **Patrones de Comportamiento: "El Manual de Comunicación"**

	**Objetivo:** Gestionar **cómo se comunican** y qué responsabilidades tiene cada objeto.
	
	No se trata de cómo están armados, sino de cómo "hablan" entre ellos y cómo se reparten el trabajo.
	
	- **Por qué se usan:** Para evitar que los objetos estén "demasiado pegados" (acoplados). Si un objeto cambia, no debería obligar a todos los demás a cambiar.
	- **En palabras simples:** Es como un árbitro en un partido (Mediador) o como una fila de personas pasándose un mensaje (Cadena de responsabilidad).


