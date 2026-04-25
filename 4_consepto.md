- Clases abstractas: Plantillas que permiten definir atributos y comportamientos generales que serán heredados por las subclases. Permiten incluir tanto métodos abstractos como concretos y campos con estado (atributos). Son útiles cuando varias clases comparten comportamiento parcial (Cairo Battistutti, 2022). 

- Interfaces: Definen un contrato que las clases implementadoras deben cumplir, sin preocuparse por cómo implementan los métodos. Las interfaces no pueden contener estado (atributos) salvo constantes, y son ideales para modelar capacidades comunes entre clases no relacionadas jerárquicamente (Garay Avendaño, 2022). 

- Diseño orientado a interfaces: En lugar de depender de clases concretas, los módulos dependen de interfaces, lo cual facilita cambiar las implementaciones sin alterar el código cliente, favoreciendo el bajo acoplamiento (Vázquez, 2020). 

- Dependencia inversa: Un principio del diseño que establece que las clases de alto nivel no deben depender de clases concretas, sino de abstracciones (interfaces o clases abstractas), promoviendo la flexibilidad y la mantenibilidad (Hernández & Baquero, 2023). 

- Interfaces funcionales: Interfaces con un solo método abstracto, usadas ampliamente en programación funcional, como en expresiones lambda y streams en Java 8+ (Gil Prado, 2023).