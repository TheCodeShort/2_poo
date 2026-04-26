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
			
			1. **Ejemplo en Java: Un Gestor de Configuración**
			
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
			2. En el ejemplo, si cambias el idioma en `otraConfig`, automáticamente cambia en `config`, porque **son el mismo objeto en memoria**. Es como tener un solo control remoto para un televisor: no importa quién lo agarre, todos operan la misma TV.
				
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
			
		
			// Creamos otro reporte igual en un milisegundo
			ReporteIMC reporteCopia = reporteOriginal.clone();
			```

---
2. ==**Patrones Estructurales: "El Plano de Montaje"**==
	- en el catálogo oficial de la _Gang of Four_ hay **7 patrones estructurales**, pero así como en los creacionales, hay **3 que son los pilares** que verás en todos lados. 
	
	- **Objetivo:** Organizar **cómo se unen** las clases y los objetos para formar estructuras más grandes se aseguran de que, si el sistema crece, las piezas sigan encajando bien sin romperse.

		- **Por qué se usan:** Para que clases que no fueron diseñadas para trabajar juntas puedan hacerlo, o para agrupar objetos de forma que parezcan uno solo.
		- **En palabras simples:** Es como usar adaptadores de enchufes para un viaje o usar piezas de Lego para armar una pared sólida.
	
	- ==**ADAPTER (Adaptador):**== Su objetivo es hacer que dos interfaces que no tienen nada que ver entre sí puedan trabajar juntas. (Como un convertidor de enchufe).
		
		1. La Idea Central

			Imagina que tienes una aplicación de IMC que funciona con **Kilogramos y Metros**. De repente, te piden integrar una librería externa (o una báscula importada) que solo entrega el peso en **Libras** y la altura en **Pulgadas**.
			
			Tu código no entiende esas medidas. Tienes dos opciones: o cambias todo tu código (mala idea), o creas un **Adapter** que reciba los datos en libras/pulgadas y se los entregue a tu sistema convertidos a kg/metros.

		2. Objetivos
		
			- **Compatibilidad:** Permitir que clases con interfaces incompatibles colaboren.
			- **Reutilización:** Usar clases viejas o externas sin tener que modificar su código original.


		3. Ejemplo en Java: El Adaptador de Medidas

			- **Paso A: Lo que tu sistema espera (La Interfaz)**

			```java
			public interface SistemaLocal {
			    void registrarPesoKG(double peso);
			}
			```


			- **Paso B: La clase "Vieja" o "Externa" (Lo que no encaja)**

			```java
			public class BasculaAmericana {
			    public void setWeightLbs(double weight) {
			        System.out.println("Peso recibido en Libras: " + weight);
			    }
			}
			```


			- **Paso C: EL ADAPTER (El puente)**  
				El adaptador implementa tu interfaz pero por dentro usa la clase que no encaja.

			```JAVA
			public class BasculaAdapter implements SistemaLocal {
			    private BasculaAmericana bascula;
			
			    public BasculaAdapter(BasculaAmericana bascula) {
			        this.bascula = bascula;
			    }
			
			    @Override
			    public void registrarPesoKG(double pesoKG) {
			        // Convertimos KG a Libras para que la bascula americana entienda
			        double libras = pesoKG * 2.20462;
			        bascula.setWeightLbs(libras);
			    }
			}
			```

			- ¿Cómo se usa en el `Main`?

			```JAVA
			public class Main {
			    public static void main(String[] args) {
			        // Tenemos el objeto que no encaja
			        BasculaAmericana viejaBascula = new BasculaAmericana();
			
			        // Usamos el adaptador para que parezca un "SistemaLocal"
			        SistemaLocal miSistema = new BasculaAdapter(viejaBascula);
			
			        // Ahora puedo usar mis métodos de siempre, y el adaptador hace la magia
			        miSistema.registrarPesoKG(70.0); 
			    }
			}
			```



		4. ¿Por qué es "Modularidad Perfecta"?

			Porque tu programa principal sigue creyendo que habla con un sistema de Kilogramos. Si mañana cambias la báscula por una de **Piedras** (medida antigua), solo creas otro Adaptador y el resto de tu código no se mueve ni una coma.
			
			**Diferencia clave con otros:**
			
			- El **Adapter** cambia la interfaz de un objeto para que se vea como otra.
			- El **Decorator**  no cambia la interfaz, sino que le agrega "capas" de funcionalid


	- ==**DECORATOR (Decorador):**== Su objetivo es añadirle funciones a un objeto de forma dinámica sin cambiar su clase original. (Como ponerle accesorios a un personaje de un juego).
	
		1. **La Idea Central**

			Imagina que tienes un café básico. Si quieres añadirle leche, no creas una clase nueva llamada `CafeConLeche`. Si luego quieres azúcar, no creas otra llamada `CafeConLecheYAzucar`. ¡Terminarías con mil clases!
			
			El patrón **Decorator** te permite "envolver" tu objeto original en "capas" de funcionalidades nuevas. Es como una cebolla: el núcleo es el objeto básico y cada capa añade algo especial.
		
		2. **El Objetivo**
		
			- **Añadir responsabilidades dinámicamente:** Puedes poner y quitar funciones en tiempo de ejecución.
			- **Evitar la "Explosión de Clases":** En lugar de tener una clase para cada combinación posible, tienes piezas pequeñas que se combinan entre sí.

		3. Ejemplo en Java: Reporte de IMC con "Extras"

			Imagina que tu sistema genera un reporte de texto simple, pero a veces quieres que ese reporte tenga un **Borde** elegante o una **Firma Digital**.
			
			- **Paso A: La Interfaz (El componente base)**

			```JAVA
			public interface Reporte {
				String leerContenido();
			}
			```

			- **Paso B: El Objeto Básico (Lo que vamos a decorar)**

			```JAVA
			public class ReporteSimple implements Reporte {
			    @Override
			    public String leerContenido() {
			        return "Informe de IMC: 24.5 - Saludable.";
			    }
			}
			```

			- **Paso C: El Decorador Maestro (La base para los adornos)**  
				Esta clase es clave: implementa la interfaz y _contiene_ un objeto de la interfaz.

			```JAVA
			public abstract class ReporteDecorator implements Reporte {
			    protected Reporte reporteDecorado; // El reporte que estamos envolviendo
			
			    public ReporteDecorator(Reporte reporte) {
			        this.reporteDecorado = reporte;
			    }
			}
			```

			- **Paso D: Decoradores Concretos (Los adornos reales)**

			```JAVA
			public class ReporteConBorde extends ReporteDecorator {
			    public ReporteConBorde(Reporte reporte) { super(reporte); }
			
			    @Override
			    public String leerContenido() {
			        return "**********\n" + reporteDecorado.leerContenido() + "\n**********";
			    }
			}
			
			public class ReporteConFirma extends ReporteDecorator {
			    public ReporteConFirma(Reporte reporte) { super(reporte); }
			
			    @Override
			    public String leerContenido() {
			        return reporteDecorado.leerContenido() + "\nFirmado por: Dr. Alex";
			    }
			}
			```


			- ¿Cómo se usa en el `Main`?
			
				Aquí es donde ocurre la "magia de las capas":
			
			```JAVA
			public class Main {
			    public static void main(String[] args) {
			        // 1. Empezamos con el reporte básico
			        Reporte reporte = new ReporteSimple();
			
			        // 2. Lo envolvemos en un borde
			        reporte = new ReporteConBorde(reporte);
			
			        // 3. ¡Lo envolvemos TAMBIÉN en una firma!
			        reporte = new ReporteConFirma(reporte);
			
			        // Al ejecutar, tiene todas las capas
			        System.out.println(reporte.leerContenido());
			    }
			}
			```
			

		4. ¿Por qué es "Buenísimo"?
		
			- **Combinaciones infinitas:** Puedes crear un reporte con firma pero sin borde, o con dos bordes, simplemente cambiando el orden de los `new`.
			- **Cumple el Principio Open/Closed:** Tu clase `ReporteSimple` nunca se toca, pero su comportamiento cambia totalmente.
		
		- **Diferencia clave con la Herencia:**  
			En la herencia, el comportamiento se define al programar (estático). Con el **Decorator**, el comportamiento se define al ejecutar el programa (dinámico).

	- ==**COMPOSITE (El Compuesto)**==

		1. **La Idea Central**
		
			Imagina que en tu sistema de salud tienes **Médicos individuales** y también **Equipos de Médicos**. Quieres poder darles una orden (por ejemplo: "Atender Emergencia") sin importar si se la das a un solo doctor o a todo un equipo.
		
			El patrón **Composite** permite tratar a los objetos individuales y a las agrupaciones de esos objetos de la **misma manera**.
		
		2. **El Objetivo**
		
			- **Estructuras de árbol:** Representar jerarquías `parte-todo`.
			- **Uniformidad:** Que el cliente (tu `Main`) no tenga que preguntar: "¿Eres un objeto solo o eres una lista?" simplemente llama al método y ya.

		3. Ejemplo en Java: Organización del Hospital

			- **Paso A: La Interfaz Común (El Componente)**

			```JAVA
			public interface Empleado {
			    void mostrarDetalles();
			}
			```

			- **Paso B: El Objeto Simple (La Hoja)**

			```JAVA
			public class Medico implements Empleado {
			    private String nombre;
			    public Medico(String nombre) { this.nombre = nombre; }
			
			    @Override
			    public void mostrarDetalles() {
			        System.out.println("Médico: " + nombre);
			    }
			}
			```


			- **Paso C: El Objeto Compuesto (El Contenedor)**  
				Este objeto contiene una lista de `Empleado` (que pueden ser otros Médicos u otros Equipos).
			
			```JAVA
			import java.util.ArrayList;
			import java.util.List;
			
			public class EquipoMedico implements Empleado {
			    private List<Empleado> subordinados = new ArrayList<>();
			    private String nombreEquipo;
			
			    public EquipoMedico(String nombre) { this.nombreEquipo = nombre; }
			
			    public void agregar(Empleado e) { subordinados.add(e); }
			
			    @Override
			    public void mostrarDetalles() {
			        System.out.println("Equipo: " + nombreEquipo);
			        for (Empleado e : subordinados) {
			            e.mostrarDetalles(); // ¡Aquí ocurre la magia de la recursividad!
			        }
			    }
			}
			```
			
			- ¿Cómo se usa en el `Main`?
		
			```JAVA
			public class Main {
				public static void main(String[] args) {
					// Médicos individuales
					Medico med1 = new Medico("Dr. Casa");
					Medico med2 = new Medico("Dra. Grey");
			
					// Formamos un equipo
					EquipoMedico equipoCirugia = new EquipoMedico("Unidad de Cirugía");
					equipoCirugia.agregar(med1);
					equipoCirugia.agregar(med2);
			
					// Podemos crear un equipo de equipos
					EquipoMedico hospitalCentral = new EquipoMedico("Hospital General");
					hospitalCentral.agregar(equipoCirugia); 
					hospitalCentral.agregar(new Medico("Dr. Strange")); // Un médico suelto
			
					// Tratamos a todos por igual
					hospitalCentral.mostrarDetalles();
				}	
			}
			```
			
			
		4. ¿Por qué es "Buenísimo"?
		
			- **Recursividad:** Puedes meter equipos dentro de equipos infinitamente.
			- **Simplicidad para el cliente:** Si quieres que todo el hospital se "muestre", solo llamas a un método en el objeto raíz y él se encarga de bajar por todas las ramas.
		
			- Diferencia con el Facade (Fachada):
		
				- **Composite:** Une objetos similares para que parezcan uno solo en una jerarquía.
				- **Facade:** Crea un objeto nuevo que "manda" sobre clases que son totalmente diferentes entre sí para que sea más fácil usarlas.


	- ==**FACADE (Fachada):**== Su objetivo es esconder la complejidad de un sistema gigante detrás de una sola clase simple. (Como el botón de "Encender" de una PC que hace mil procesos internos pero tú solo ves un botón).
	
		1. **La Idea Central**

			Imagina que quieres ver una película en tu sistema de cine en casa. Para hacerlo "a mano" tendrías que:
			
			1. Encender las luces y bajarlas al 10%.
			2. Encender el televisor.
			3. Encender el sonido envolvente.
			4. Poner el reproductor en modo "Cine".
			5. Darle a "Play".
			
			¡Es demasiado trabajo! Lo ideal es tener un solo botón que diga **"Modo Cine"** y que él haga todo lo demás por ti. Eso es una **Fachada**: una cara simple que oculta un desorden complejo.
			
		2. **El Objetivo**
			
			- **Simplificar el uso:** Proporcionar una interfaz única de alto nivel para un conjunto de interfaces en un subsistema.
			- **Desacoplar:** Que el usuario no tenga que conocer cómo funcionan las 10 clases internas del sistema, solo la Fachada.

		3. **Ejemplo en Java: El "Botón de Inicio" del Chequeo Médico**

			Imagina que para registrar a un paciente en tu app de IMC necesitas interactuar con tres sistemas distintos: el de **Validación de Identidad**, el de **Historial Clínico** y el de **Notificaciones**.
			
			- **Paso A: Las clases complejas (El "desorden" interno)**

			```java
			class SistemaIdentidad {
			    public void validar(String id) { System.out.println("DNI " + id + " validado."); }
			}
			
			class SistemaHistorial {
			    public void crearRegistro(String id) { System.out.println("Espacio en nube creado para " + id); }
			}
			
			class SistemaNotificacion {
			    public void enviarBienvenida() { System.out.println("Email de bienvenida enviado."); }
			}
			```


			- **Paso B: LA FACHADA (La cara simple)**

			```JAVA
			public class RegistroPacienteFacade {
			    private SistemaIdentidad identidad = new SistemaIdentidad();
			    private SistemaHistorial historial = new SistemaHistorial();
			    private SistemaNotificacion notificacion = new SistemaNotificacion();
			
			    // Este es el único método que el Main necesita conocer
			    public void registrarPacienteCompleto(String nombre, String id) {
			        System.out.println("Iniciando proceso para: " + nombre);
			        identidad.validar(id);
			        historial.crearRegistro(id);
			        notificacion.enviarBienvenida();
			        System.out.println("¡Paciente registrado con éxito!");
			    }
			}
			```

			- **¿Cómo se usa en el `Main`?**
			
				Mira qué limpio queda el código ahora:
				
				```javA
				public class Main {
			    public static void main(String[] args) {
			        // En lugar de llamar a 3 sistemas, solo llamamos a la Fachada
			        RegistroPacienteFacade registro = new RegistroPacienteFacade();
			        
			        registro.registrarPacienteCompleto("Alex", "102030");
			    }
			}
				```

		4. **¿Por qué es "Modularidad Perfecta"?**
		
			- **Encapsulamiento:** Si mañana cambias el sistema de correos por uno de WhatsApp, solo cambias la Fachada. El `Main` no tiene que enterarse.
			- **Orden:** Evitas que tu `Main` parezca una lista de mercado llena de pasos técnicos.
		
3. ==**Patrones de Comportamiento: "El Manual de Comunicación"**==

	- **Objetivo:** Gestionar **cómo se comunican** y qué responsabilidades tiene cada objeto.
	
	- No se trata de cómo están armados, sino de cómo "hablan" entre ellos y cómo se reparten el trabajo.
	
	- **Por qué se usan:** Para evitar que los objetos estén "demasiado pegados" (acoplados). Si un objeto cambia, no debería obligar a todos los demás a cambiar.
	- **En palabras simples:** Es como un árbitro en un partido (Mediador) o como una fila de personas pasándose un mensaje (Cadena de responsabilidad)
	
	1. ==EL STRATEGY (La Estrategia)==

		- **La Idea Central**
		
			Imagina que estás programando tu calculadora de IMC. Hoy usas la fórmula estándar, pero mañana quieres aplicar una fórmula para deportistas, y otra para niños.  
			Normalmente harías un `if (tipo == "deportista") { ... } else if ...`. ¡Eso es mala práctica!
			
			El patrón **Strategy** te permite definir una familia de algoritmos, poner cada uno en una clase separada y hacer que sean **intercambiables**. El objeto principal no sabe _cómo_ se calcula, solo sabe que tiene una "Estrategia" que lo hace.
		
		- **Objetivos**
		 
			- **Eliminar condicionales complejos:** Menos `if/else` y más polimorfismo.
			- **Cambiar de opinión en el camino:** Puedes cambiar la lógica de un objeto mientras el programa está corriendo.

		1. **Ejemplo en Java: Diferentes fórmulas de IMC**
	
			- **Paso A: La Interfaz (El contrato de la estrategia)**
			
				```java
				public interface FormulaIMC {
				    double calcular(double peso, double altura);
				}
				```
			
			- **Paso B: Las Estrategias Concretas (Las fórmulas reales)**
			
				```java
				public class FormulaEstandar implements FormulaIMC {
				    public double calcular(double peso, double altura) {
				        return peso / (altura * altura);
				    }
				}
				
				public class FormulaAtleta implements FormulaIMC {
				    public double calcular(double peso, double altura) {
				        // Una fórmula hipotética que ajusta un 10% por masa muscular
				        return (peso / (altura * altura)) * 0.9;
				    }
				}
				```
			
			- **Paso C: El Contexto (La clase que usa la estrategia)**
			
				```java
				public class CalculadoraContexto {
				    private 
	 estrategia;
				
				    // Permitimos cambiar la estrategia en cualquier momento
				    public void setEstrategia(FormulaIMC nuevaEstrategia) {
				        this.estrategia = nuevaEstrategia;
				    }
				
				    public void ejecutarCalculo(double p, double a) {
				        double resultado = estrategia.calcular(p, a);
				        System.out.println("Resultado con esta estrategia: " + resultado);
				    }
				}
				```
			
			- ¿Cómo se usa en el `Main`?
			
				```java
				public class Main {
				    public static void main(String[] args) {
				        CalculadoraContexto calculadora = new CalculadoraContexto();
				
				        // 1. Usamos la estándar
				        calculadora.setEstrategia(new FormulaEstandar());
				        calculadora.ejecutarCalculo(80, 1.80);
				
				        // 2. ¡Cambiamos la estrategia al vuelo!
				        calculadora.setEstrategia(new FormulaAtleta());
				        calculadora.ejecutarCalculo(80, 1.80);
				    }
				}
				```
	
	
		2. **¿Por qué es "Buenísimo"?**
		
			- **Modularidad total:** Si quieres crear una "FormulaParaAncianos", solo creas una clase nueva que implemente la interfaz. No tienes que tocar ni una línea de la clase `CalculadoraContexto`.
			- **Limpieza:** Tu código deja de ser un laberinto de decisiones y se vuelve una serie de piezas intercambiables.

	2. ==**OBSERVER** (El Observador)==

		1. Define una relación de dependencia uno-a-muchos para que, cuando un objeto cambie de estado, sus dependientes sean notificados.
		
		2. **La Idea Central**

			Imagina que eres un fanático de una banda. Tienes dos opciones para saber si lanzan un nuevo disco:

			1. Ir todos los días a la tienda a preguntar (esto en programación se llama _Polling_ y gasta muchos recursos).
			2. **Suscribirte** a su boletín. En cuanto hay algo nuevo, ellos te avisan a ti.

			El **Observer** permite que un objeto (el **Sujeto**) notifique automáticamente a otros objetos (**Observadores**) cuando su estado cambia.

		3. **El Objetivo**
		
			- **Desacoplamiento:** El objeto principal no necesita saber quiénes lo están mirando ni qué van a hacer con la información.
			- **Reacción en tiempo real:** Ideal para sistemas de notificaciones, alarmas o interfaces que se actualizan solas.


		4. **Ejemplo en Java: El Paciente y sus Monitores**
		
			- Imagina que cuando el IMC de un paciente cambia, queremos avisar automáticamente al **Médico** y enviar una **Notificación al celular** del paciente.
			
			- Paso A: La Interfaz Observador (El contrato de los que escuchan)
			
			```java
			public interface Observador {
			    void actualizar(double nuevoIMC);
			}
			```
			
			- Paso B: El Sujeto (El objeto que es observado)
			
			```java
			import java.util.ArrayList;
			import java.util.List;
			
			public class Paciente {
			    private List<Observador> observadores = new ArrayList<>();
			    private double imc;
			
			    public void suscribir(Observador o) { observadores.add(o); }
			    
			    public void setIMC(double nuevoIMC) {
			        this.imc = nuevoIMC;
			        notificar(); // En cuanto cambia el dato, avisamos a todos
			    }
			
			    private void notificar() {
			        for (Observador o : observadores) {
			            o.actualizar(this.imc);
			        }
			    }
			}
			```
			
			- Paso C: Los Observadores Concretos (Los que reaccionan)
			
			```java
			public class MonitorMedico implements Observador {
			    public void actualizar(double imc) {
			        System.out.println("Médico alerta: El paciente tiene un nuevo IMC de " + imc);
			    }
			}
			
			public class AppPaciente implements Observador {
			    public void actualizar(double imc) {
			        System.out.println("Celular: ¡Tu nuevo IMC ha sido registrado!");
			    }
			}
			```
			
			- ¿Cómo se usa en el `Main`?
			
			```java
			public class Main {
			    public static void main(String[] args) {
			        Paciente paciente = new Paciente();
			
			        // Creamos los interesados
			        MonitorMedico medico = new MonitorMedico();
			        AppPaciente app = new AppPaciente();
			
			        // Los suscribimos (los ponemos a observar)
			        paciente.suscribir(medico);
			        paciente.suscribir(app);
			
			        // Cambiamos el dato y ¡BOOM!, todos se enteran solos
			        paciente.setIMC(26.5);
			    }
			}
			```
			

		5. ¿Por qué es "Buenísimo"?
		
			- **Flexibilidad:** Si mañana quieres que también se entere la **Aseguradora**, solo creas la clase `MonitorAseguradora`, la suscribes y listo. No tocaste ni una sola letra de la clase `Paciente`.
			- **Orden:** Cada observador hace lo que le toca (el médico analiza, la app muestra) sin mezclar el código.
				
		
Conclusión de tu viaje por los Patrones

¡Lo has logrado! Hemos recorrido los pilares de la arquitectura de software:

1. **Creacionales:** (Singleton, Factory, Builder...) - _¿Cómo nazco?_
2. **Estructurales:** (Adapter, Decorator, Facade...) - _¿Cómo me armo?_
3. **Comportamiento:** (Strategy, Observer...) - _¿Cómo me comunico?_