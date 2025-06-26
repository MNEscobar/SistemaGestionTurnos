# Patrones de Diseño Creacionales

## ¿Qué son los patrones de diseño creacionales?

Los patrones de diseño creacionales se enfocan en cómo se crean los objetos en un sistema. Su objetivo es abstraer y encapsular el proceso de instanciación, para que el código cliente no dependa directamente de las clases concretas, sino de interfaces o clases abstractas.
Estos patrones proporcionan mecanismos de creación de objetos que incrementan la flexibilidad y la reutilización del código existente.

#### Ejemplo de tipos de patrones
- Singleton
- Factory Method
- Abstract Factory
- Builder
- Prototype

---

## Relación con los principios SOLID
Los patrones creacionales fortalecen la aplicación de SOLID al momento de crear objetos.

---

#### Principio de Responsabilidad Única (SRP)
Separan la lógica de creación de objetos de la lógica de negocio. Por ejemplo, una clase TurnoFactory crea objetos Turno, mientras que GestorDeTurnos solo se encarga de gestionar.

---

### Principio de Abierto/Cerrado (OCP)
Permiten extender el comportamiento sin modificar las clases existentes. Por ejemplo, un método fábrica puede generar nuevos tipos de turnos sin alterar el código que los usa.

---

#### Principio de Sustitución de Liskov (LSP)
Favorecen el uso de clases base o interfaces para crear objetos, asegurando que cualquier clase derivada pueda sustituirse sin alterar el funcionamiento del sistema.

---

#### Principio de Segregación de Interfaces (ISP)
Respetan el principio al construir interfaces específicas para los objetos a crear.

---

#### Principio de Inversión de Dependencias (DIP)
Estos patrones promueven que el código dependa de abstracciones y no de clases concretas, lo cual es exactamente lo que este principio estipula.

---
## Propósito y Tipo del Patrón

En el sistema de gestión de turnos, el proceso de creación de un turno, que debe ser una de las funcionalidades más importantes del sistema, implica varios pasos que deben cumplirse en conjunto para cumplir con el pbjetivo: asignar un médico y un paciente, establecer una fecha y hora, y configurar una notificación automatizada. Para evitar que esta lógica esté dispersa en distintas partes del sistema, se decidió aplicar el patrón **Factory Method**, un patrón creacional que permite centralizar y encapsular la creación de objetos complejos. Con esto, el sistema gana en claridad, flexibilidad y capacidad de extensión, permitiendo generar distintos tipos de turnos sin afectar el resto del código.

---

## Motivación

La motivación principal para aplicar el patrón Factory Method en este sistema radica en la necesidad de desacoplar la lógica de construcción de los objetos `Turno` del resto de la lógica del sistema. En la versión previa del diseño, las clases encargadas de gestionar turnos, como `GestionDeTurnos`, debían conocer en detalle cómo se instanciaba un turno: incluyendo validaciones, programación de notificaciones, asociaciones con el médico y el paciente correspondiente y cómo registrar el `Slot` tomado de la agenda, además de deshabilitar ese slot para futuros turnos. Esta acumulación de responsabilidades generaba un diseño rígido, propenso a errores, difícil de mantener y limitaba la escalabilidad del sistema ante posibles extensiones, como nuevos tipos de turnos por ejemplo: virtuales, de urgencia, a domicilio, etc.


Al aplicar el patrón, se introduce una clase `CreadorTurno`, que encapsula toda la lógica necesaria para construir un turno válido a partir de un `Slot` previamente seleccionado por el paciente, y el paciente autenticado en el sistema. Esta clase se encarga de validar la disponibilidad del horario, crear el objeto `Turno`, asociar al médico correspondiente (a partir del slot), registrar la reserva en `Agenda` y configurar el notificador. De este modo, `GestorDeTurnos` solo debe delegar la creación a través del método `crearTurno(slot, paciente)`, sin preocuparse por cómo se construye el turno en sí. Esto mejora la organización del código, permite centralizar las reglas de construcción y facilita futuras mejoras en la lógica de creación sin afectar el resto del sistema.

---

## Estructura de Clases

![Imagen](https://drive.google.com/uc?export=view&id=1fbZBMvx-B4QPKf2u4PReQkCcCRTiVHRe)

https://drive.google.com/file/d/1fbZBMvx-B4QPKf2u4PReQkCcCRTiVHRe/view?usp=sharing
