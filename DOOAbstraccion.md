# Abstracción

## Descripción 
La abstracción consiste en identificar y modelar las características esenciales de un objeto, ignorando aquellos detalles que no son relevantes para el contexto del sistema. Es decir, implica representar entidades del mundo real mediante clases que contienen únicamente lo necesario para cumplir un propósito específico dentro del software, dejando de lado la información que no aporta al funcionamiento del sistema que se está desarrollando.
### ¿Por que es importante?
Gracias a la abtraccion se simplifica el sistema mostrando solo lo necesario para cada clase, haciendo el código más facil de leer, mantener y extender. Se mejora la separación de responsabilidades, asignando a cada clase tareas bien definidas. Esto promueve el desarrollo de sistemas más modulares, flexibles y estables.
### Relación con los Principios SOLID
- SRP: La abstracción ayuda a definir clases que tienen una única razón para cambiar, enfocándose solo en una parte del comportamiento del sistema.
- DIP: Este principio se basa en programar interfaces o clases abstractas en lugar de implementaciones concretas. Esto reduce el acoplamiento entre componentes y mejora la flexibilidad del diseño.
### Relación con patrones de diseño
Muchos patrones de diseño se basan en la abstracción para separar responsabilidades y permitir la extensión del sistema sin modificar código existente. Por ejemplo:

- Factory Method o Abstract Factory: abstraen el proceso de creación de objetos.
- Strategy: permite definir una familia de algoritmos intercambiables mediante una interfaz común.
- Observer: abstrae la relación entre un sujeto y sus observadores para permitir una comunicación desacoplada.
