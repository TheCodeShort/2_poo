[[2_SDLC_sofware.pdf#search=Conceptos, tecnologías y arquitectura para el desarrollo web|2_SDLC_sofware, p.614]]
# Internet y la web: idea general

El arranque de esta sección explica que las aplicaciones web actuales son más interactivas, rápidas, seguras y fáciles de usar, y que eso solo es posible por una infraestructura sólida de hardware y redes. La web no aparece por magia: depende de una base técnica que permite mover información entre dispositivos y servir aplicaciones y servicios.

# Fundamentos de la internet

Aquí el documento define **Internet** como la infraestructura técnica que hace posible la web, una red enorme de computadoras comunicándose entre sí. La idea central es que Internet es el soporte, mientras que la web es uno de los servicios que corren sobre ese soporte.

# Historia de la internet

La historia que presenta el libro arranca con **ARPANET** en la década de 1960, impulsada por el ejército de Estados Unidos, y luego explica que en los años 80 esa red evolucionó hacia una infraestructura pública con apoyo de instituciones públicas y privadas. El mensaje de fondo es que Internet no nació como un producto comercial, sino como una solución de investigación que terminó volviéndose infraestructura global.

# Hardware de red

Esta parte explica cómo se conectan físicamente los equipos. Puede ser por cable, como **Ethernet**, o de forma inalámbrica con tecnologías como **Wi-Fi, Bluetooth y ZigBee**. El documento usa ejemplos de conexión entre dos equipos y entre diez equipos para mostrar que la complejidad crece rápido cuando aumentan los nodos.

La idea importante aquí es que la red no es solo “internet”; son también los medios físicos que permiten que dos máquinas se hablen. En otras palabras: antes del software viene el cable, el enlace o el medio inalámbrico que hace posible la comunicación.

# Redes de área local LAN

Luego el texto baja a las **LAN**. Las define como redes privadas que operan dentro de un lugar concreto, como una casa, oficina o fábrica, y que sirven para compartir recursos e intercambiar información. También explica que en redes alámbricas se usa con frecuencia el estándar **IEEE 802.3 / Ethernet**, donde los equipos se conectan a un **switch** mediante enlaces punto a punto.

La función del switch es clave: recibe paquetes y decide a qué equipo enviarlos usando la dirección incluida en cada paquete. Eso te muestra que una red local no es solo “varios computadores juntos”, sino un sistema organizado de transmisión.

# Modelo de referencia TCP/IP

Aquí empieza la capa lógica de la comunicación. El documento explica que **TCP/IP** es el estándar común que usan la mayoría de los equipos modernos para interactuar, y que viene normalmente preinstalado. Su objetivo es permitir que sistemas distintos se comuniquen con reglas compartidas.

El texto también aclara que TCP/IP divide las tareas de comunicación en capas y que los datos pasan por cuatro capas antes de llegar al otro extremo. Eso es fundamental porque cada capa resuelve una parte distinta del problema.

- ## 8) Funcionamiento del modelo TCP/IP

	El libro dice que TCP/IP toma un mensaje y lo **divide en paquetes** para enviarlo por partes, y luego los **reensambla** al llegar al destino. Eso permite que, si una ruta falla o se congestiona, los paquetes puedan tomar caminos diferentes. Es la razón por la que Internet es tan resistente y distribuida.

- ## 9) Cuatro capas del modelo TCP/IP

	Aquí entra la parte más técnica del bloque. Las capas que aparecen son:
	
	**Capa de aplicación**: donde viven servicios con los que interactúa el usuario, como correo o mensajería.  
	**Capa de transporte**: se encarga de la conexión fiable entre dos dispositivos y del acuse de recibo.  
	**Capa de internet**: controla el movimiento de paquetes por la red.  
	**Capa de enlace de datos**: maneja el envío físico mediante Ethernet, tarjeta de red, inalámbrico y otros medios.
	
	El documento incluso asocia protocolos a esas capas: **HTTP y DNS** aparecen en aplicación, **TCP y UDP** en transporte, **IP e ICMP** en internet, y **Ethernet y ARP** en enlace. Eso te sirve para entender que cada protocolo tiene su lugar, no está ahí por adorno académico.


# Proceso de comunicación

Esta parte formula las preguntas que toda comunicación de red debe resolver: quién inicia, a quién le toca hablar, cómo se sabe si el mensaje llegó bien y cómo termina la conversación. La conclusión es que para comunicar equipos se necesitan **protocolos**, o sea reglas claras de comportamiento entre sistemas.


# Dirección IP

La **dirección IP** se presenta como el identificador lógico y jerárquico de cada computadora en una red. El texto usa el ejemplo de cuatro números separados por puntos, como `192.168.2.19`. Su función es ubicar de forma única a un equipo dentro de la red.

# Sistema de Nombres de Dominio (DNS)

Los **DNS** se explican como una libreta de direcciones de sitios web. Cuando escribes un dominio, el navegador consulta DNS para encontrar la IP correspondiente y así ubicar el servidor correcto. El libro incluso pone el ejemplo de `google.com` asociado a una IP concreta.

# Protocolo HTTP

El **HTTP** es el protocolo de aplicación que permite la comunicación entre cliente y servidor. El texto lo compara con el lenguaje usado para hacer un pedido en una tienda: el cliente hace una solicitud y el servidor responde con datos o recursos, normalmente páginas HTML.

La idea importante es esta: HTTP es el idioma que usa la web para pedir y entregar cosas. Si DNS encuentra la dirección, HTTP hace posible el intercambio real de información.

# Arquitectura web

Ahora el material pasa de Internet como infraestructura a la **arquitectura web** como forma de organizar el sistema. El modelo base es **cliente/servidor**: el cliente, normalmente un navegador, solicita información; el servidor la procesa y responde.

- ## Cliente web

	El **cliente web** es la aplicación o dispositivo del usuario que permite acceder a Internet y mostrar o solicitar documentos. El texto lo ubica como responsable de la capa de presentación: ahí viven el navegador y la interfaz con la que el usuario interactúa.

- ## Servidor web

	El **servidor web** atiende las solicitudes de los clientes, procesa las aplicaciones y gestiona los datos. También almacena páginas, sitios o aplicaciones y devuelve al navegador una copia de la información que debe mostrarse.
	
	El ejemplo de Facebook que usa el libro es muy claro: el usuario entra credenciales, el cliente envía una petición, el servidor valida datos con bases de datos y responde permitiendo o negando el acceso. Esa secuencia deja ver que la web es multiplataforma y distribuida.

# Web Workers

Los Web Workers permiten que un script siga ejecutándose en segundo plano mientras la página está abierta. El texto los relaciona con capacidades sin conexión y con notificaciones como Web Push. Su ventaja es técnica y muy importante: no bloquean la interfaz mientras hacen trabajo pesado.

==es una **herramienta técnica del navegador web** (una API de JavaScript) que permite implementar la **programación paralela o multihilo** (_multithreading_) en la web==

🧵 El Problema: JavaScript es de "Un Solo Hilo"

Por defecto, los navegadores ejecutan todo el código de una página web en un único camino central llamado **Hilo Principal** (_Main Thread_). Este hilo se encarga de todo al mismo tiempo: 

- Procesar los clics del usuario.
- Mostrar las animaciones y renderizar el HTML/CSS.
- Ejecutar la lógica de los scripts. 

**🚨 ¿Qué pasa si ejecutas una tarea muy pesada?**  
Si necesitas procesar una estructura de datos gigantesca con miles de registros (como las que se mencionan en las páginas 537–546 de tu libro) o realizar un cálculo matemático complejo, el hilo principal se "congela". El usuario verá que la página no responde, los botones no se pueden presionar y el navegador parecerá bloqueado. 

## La Solución: ¿Qué hace en realidad un Web Worker?

Un Web Worker te permite crear un **"trabajador secundario" en un hilo totalmente aislado**.

Funciona exactamente como una oficina secundaria:

1. El **Hilo Principal** está atendiendo al público (la pantalla de la aplicación).
2. Cuando llega un trabajo pesado (por ejemplo, ordenar un millón de datos), el hilo principal mete los datos en un "sobre de mensajes" (`postMessage()`) y se lo envía al **Web Worker**.
3. El **Web Worker** realiza todo el procesamiento pesado en segundo plano en su propia computadora interna (procesador), sin molestar al hilo principal.
4. La interfaz de usuario sigue funcionando fluida y perfecta (el usuario puede seguir haciendo clics).
5. Cuando el Worker termina, le devuelve un mensaje con el resultado final al hilo principal para que lo muestre en pantalla.

🛑 Sus Restricciones Técnicas Importantes

Como el Web Worker vive en un hilo completamente aislado para no interferir con la pantalla, tiene una limitación crucial de seguridad y arquitectura:

- **No puede acceder directamente al DOM (HTML):** Un Web Worker no puede cambiar el color de un botón ni modificar un texto de tu página web directamente. Solo procesa datos lógicos puros. Toda comunicación con el usuario debe pasar obligatoriamente a través del hilo principal mediante mensajes de texto o datos estructurados.

💡 En Resumen

Es una **funcionalidad de infraestructura** introducida en la web moderna. Te sirve para que tus aplicaciones web actúen con el mismo poder de rendimiento y procesamiento en paralelo que tiene un software de escritorio tradicional de alta complejidad.
# Web Sockets

WebSockets proporcionan una conexión persistente y bidireccional entre cliente y servidor. El libro los menciona para casos como chats y notificaciones. Aquí la diferencia con HTTP clásico es conceptual: en vez de pedir y responder una vez, la comunicación queda viva para intercambiar datos en tiempo real.

es una ==tecnología de comunicación web que permite un **canal de comunicación bidireccional, persistente y en tiempo real** entre el navegador del usuario y el servidor==.

Al igual que los Web Workers, no es una forma de programar, sino un **protocolo de red** (técnicamente llamado `ws://` o `wss://`) diseñado para romper las limitaciones del modelo web tradicional.

Para entender su verdadero valor, debemos comparar cómo funciona la web normal frente a la web con Web Sockets:


🥖 La Web Tradicional: El Modelo de "Petición y Respuesta" (HTTP)

La web normal funciona como un restaurante donde el navegador es el cliente y el servidor es el mesero:

1. El cliente pide algo (**Petición / Request**).
2. El mesero va a la cocina, trae el plato y se retira (**Respuesta / Response**).
3. La conexión **se cierra de inmediato**. Si la cocina tiene un plato nuevo listo 5 minutos después, el mesero _no se lo puede llevar al cliente_ a menos que el cliente levante la mano y vuelva a pedirlo de forma explícita.

**🚨 El problema:** Si estás haciendo una aplicación de chat, tu navegador tendría que preguntarle al servidor cada 2 segundos: _"¿Tengo mensajes nuevos? ¿Tengo mensajes nuevos?"_ (un proceso ineficiente llamado _Polling_ que satura los servidores).


📞 La Web con Web Sockets: Una Llamada Telefónica Abierta

Un Web Socket funciona de una manera totalmente diferente:

1. El navegador le envía una petición especial al servidor para establecer la conexión (llamado el _Handshake_ o saludo inicial).
2. Si el servidor acepta, **la conexión se queda abierta permanentemente** como una llamada telefónica.
3. A partir de ese momento, **ambos pueden hablar cuando quieran sin pedir permiso**:
    - El navegador puede enviarle datos al servidor.
    - El servidor puede **empujar (_Push_) datos hacia el navegador de forma inmediata** en el milisegundo exacto en que ocurren, sin que el usuario tenga que recargar la página ni pedir nada.

🎮 ¿En qué aplicaciones del mundo real se utiliza?

Cualquier sistema moderno que requiera datos instantáneos utiliza Web Sockets por debajo:

- **Aplicaciones de Chat (WhatsApp Web, Slack):** Para que el mensaje te aparezca en pantalla al instante en que tu amigo lo envía.
- **Videojuegos Multijugador en el navegador:** Para transmitir las coordenadas y movimientos de los otros jugadores en tiempo real sin retrasos (_lag_).
- **Plataformas Financieras (Criptomonedas, Bolsa de Valores):** Para actualizar las gráficas de precios segundo a segundo de forma fluida.
- **Herramientas de Trabajo Colaborativo (Figma, Google Docs):** Para ver el cursor de tu compañero moviéndose por la pantalla en tiempo real.


# ⚖️ Resumen de Diferencias (Web Workers vs. Web Sockets)

Es muy común confundirlos cuando se empieza en el software porque ambos inician con "Web", pero hacen cosas totalmente distintas:

- **Web Worker:** Resuelve un problema de **rendimiento interno** (crea un hilo extra para procesar datos pesados en tu propia computadora sin congelar la pantalla).
- **Web Socket:** Resuelve un problema de **comunicación externa** (mantiene una conexión abierta con internet para recibir y enviar datos en tiempo real).

