# Patrones de Diseño Creacionales

## ¿Qué son los patrones de diseño creacionales?

Los patrones de diseño creacionales se enfocan en cómo se crean los objetos en un sistema. Su objetivo es abstraer y encapsular el proceso de instanciación, para que el código cliente no dependa directamente de las clases concretas, sino de interfaces o clases abstractas.
Estos patrones proporcionan mecanismos de creación de objetos que incrementan la flexibilidad y la reutilización del código existente.

### Ejemplo de tipos de patrones
- Singleton
- Factory Method
- Abstract Factory
- Builder
- Prototype

## Relación con los principios SOLID
Los patrones creacionales fortalecen la aplicación de SOLID al momento de crear objetos.

### Principio de Responsabilidad Única (SRP)
Separan la lógica de creación de objetos de la lógica de negocio. Por ejemplo, una clase TurnoFactory crea objetos Turno, mientras que GestorDeTurnos solo se encarga de gestionar.

### Principio de Abierto/Cerrado (OCP)
Permiten extender el comportamiento sin modificar las clases existentes. Por ejemplo, un método fábrica puede generar nuevos tipos de turnos sin alterar el código que los usa.

### Principio de Sustitución de Liskov (LSP)
Favorecen el uso de clases base o interfaces para crear objetos, asegurando que cualquier clase derivada pueda sustituirse sin alterar el funcionamiento del sistema.

### Principio de Segregación de Interfaces (ISP)
Respetan el principio al construir interfaces específicas para los objetos a crear.

### Principio de Inversión de Dependencias (DIP)
Estos patrones promueven que el código dependa de abstracciones y no de clases concretas, lo cual es exactamente lo que este principio estipula.
