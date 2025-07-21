# Polimorfismo

## Descripción
El polimorfismo permite que objetos de diferentes clases, que comparten una misma interfaz o descienden de una misma clase base, sean tratados de manera uniforme a través de una referencia común. Es decir, un mismo mensaje (llamada a un método) enviado a diferentes objetos puede producir resultados diferentes. Esto se logra mediante la sobrescritura de métodos (cuando las subclases proporcionan implementaciones específicas de un método heredado) o la implementación de interfaces comunes.
### ¿Por qué es importante?
El polimorfismo es crucial para desarrollar sistemas flexibles, extensibles y fáciles de mantener. Permite escribir código más genérico y menos acoplado a tipos concretos, lo que reduce la necesidad de condicionales complejos para determinar el tipo de objeto y su comportamiento. Esto simplifica el código, lo hace más legible y facilita la adición de nuevas funcionalidades. Cuando se introduce un nuevo tipo de objeto que se ajusta a la interfaz común, el código existente que utiliza esa interfaz no necesita ser modificado para interactuar con el nuevo tipo, lo que promueve la extensibilidad sin cambios disruptivos.
### Relación con los Principios SOLID
- SRP: Al permitir que los objetos respondan a un mensaje de manera diferente, el polimorfismo facilita que cada clase mantenga una única responsabilidad, ya que la lógica específica para cada comportamiento está encapsulada dentro de la clase que lo implementa.
- OCP: Un módulo está "abierto para extensión" (se pueden añadir nuevas implementaciones) pero "cerrado para modificación" (el código que usa la interfaz polimórfica no necesita cambiar). Permite añadir nuevas funcionalidades simplemente creando nuevas clases que implementen la misma interfaz o sobrescriban un método base.
- LSP: Los objetos de una superclase deben poder ser sustituidos por objetos de una subclase sin alterar la corrección del programa. El polimorfismo permite tratar a las subclases como si fueran instancias de la superclase, esperando que su comportamiento sea coherente con la definición de la superclase.
- DIP: Permite que los módulos de alto nivel dependan de abstracciones (interfaces o clases abstractas) en lugar de implementaciones concretas. Los detalles (clases concretas) implementan estas abstracciones, y el polimorfismo asegura que el código de alto nivel pueda interactuar con cualquier detalle que cumpla con la abstracción.

### Relación con patrones de diseño
El polimorfismo es un elemento central y facilitador de numerosos patrones de diseño, permitiendo flexibilidad y extensibilidad en las soluciones:
- Patrones Creacionales: El **Factory Method** define una interfaz para crear un objeto, pero permite que las subclases alteren el tipo de objetos que se crearán a través de su interfaz común, sin necesidad de conocer su tipo real.
- Patrones Estructurales (Composite, Decorator):**Composite** Utiliza el polimorfismo para tratar objetos individuales y composiciones de objetos de manera uniforme que implementan la misma interfaz, permitiendo que el cliente interactúe con ellos polimórficamente. Decorator: Permite añadir responsabilidades adicionales a un objeto dinámicamente. El decorador y el objeto decorado comparten una interfaz común, permitiendo que el cliente los utilice polimórficamente.
- Patrones de Comportamiento (Strategy, State, Template Method):**Strategy** implementan una interfaz común, y el cliente interactúa con la interfaz sin conocer la implementación concreta del algoritmo. **State** Utiliza el polimorfismo para que un objeto cambie su comportamiento cuando su estado interno cambia. **Template Method** Define el esqueleto de un algoritmo en una operación, delegando algunos pasos a las subclases. Las subclases sobrescriben estos pasos polimórficamente para proporcionar su implementación específica.

## Ejemplo en el proyecto

![Imagen](https://drive.google.com/uc?export=view&id=16ey4nq-8FFqqwQDazYs7a0P5qgJ9fIVP)

[Drive](https://drive.google.com/file/d/16ey4nq-8FFqqwQDazYs7a0P5qgJ9fIVP/view?usp=sharing)

En el sistema de gestión de turnos, el polimorfismo permite que distintas entidades respondan a un mismo mensaje de manera diferente. La aplicación más clara se ve en la gestión del estado de la clase Turno. 

Turno delega el manejo de operaciones como confirmar() o cancelar() a su objeto de estado actual, el cual implementa una interfaz común. El polimorfismo asegura que la lógica específica para cada estado se ejecute, sin que Turno necesite saber la implementación concreta.
De forma similar, en la jerarquía de Usuario, el polimorfismo permite tratar colecciones de Pacientes, Medicos y Administradors de forma uniforme para operaciones comunes como iniciarSesion(). Cada tipo de usuario responde de manera especializada, sin que el código llamador deba conocer el tipo exacto.

Esta aplicación del polimorfismo reduce el acoplamiento y elimina lógica condicional compleja, favoreciendo un diseño adaptable y fácil de extender con nuevas funcionalidades sin modificar el código existente.

```java
