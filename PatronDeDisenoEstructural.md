# Patrón de diseño estructural

## ¿Qué son los patrones de diseño estructurales?
Los patrones estructurales son soluciones reutilizables que abordan cómo se organizan y relacionan las clases y objetos para formar estructuras más grandes y flexibles, sin comprometer su eficiencia ni claridad.
Su propósito es simplificar las dependencias entre componentes del sistema, permitiendo que trabajen juntos incluso si sus interfaces son incompatibles, o que se amplíen sin necesidad de modificar el código existente.

#### Ejemplo de tipos de patrones estructurales
- Adapter
- Composite
- Decorator
- Facade
- Proxy

---

## Relación con los principios SOLID
Los patrones estructurales refuerzan varios principios SOLID al nivel de arquitectura de clases

---

### Principio de Responsabilidad Única (SRP)
Muchos de estos patrones ayudan a separar preocupaciones (por ejemplo, *Facade* aísla una interfaz simple del sistema interno).

---

### Principio de Abierto/Cerrado (OCP)
*Decorator* permite extender funcionalidades sin modificar el objeto original.

---

### Principio de Sustitución de Liskov (LSP)
Estructuras como *Composite* y *Proxy* permiten sustituir componentes sin alterar el comportamiento esperado.

---

### Principio de Segregación de Interfaces (ISP)
*Adapter* puede crear interfaces más específicas para clientes concretos sin modificar la clase adaptada.

---

### Principio de Inversión de Dependencias (DIP)
Al usar interfaces como en *Proxy* o *Adapter*, el sistema depende de abstracciones, no de implementaciones concretas.

---

## Propósito y Tipo de patrón
Para simplificar y desacoplar la interacción entre la capa de presentación (por ejemplo, la UI web o móvil) y los distintos subsistemas implicados en la creación de un turno como: `GestionDeTurno`, `CreadorTurno`, `Agenda` y `NotificadorTurno` se elige aplicar el patrón ***Facade***, un patrón estructural cuya finalidad es proporcionar una interfaz única y coherente que oculte la complejidad interna del sistema y reduzca las dependencias directas de los clientes hacia múltiples clases.

---

## Motivación
En el diseño actual, cualquier cliente por ejemplo, un controlador web que desee gestionar la reserva de un turno debe conocer y orquestar directamente múltiples componentes:

1- Invocar a `GestionDeTurno` para validar los datos del paciente y la elección de especialidad o médico.

2- Llamar a `CreadorTurno` para construir la instancia de `Turno`, implicando validaciones de disponibilidad, creación del objeto, registro en la `Agenda` y programación de la notificación con `NotificadorTurno`.

3- Capturar la excepción de disponibilidad si el `Slot` ya está ocupado, o procesar la respuesta en el flujo de la aplicación.

Este flujo disperso genera un fuerte acoplamiento entre la capa de presentación (o cualquier cliente) y la lógica interna de la aplicación, dificulta la prueba automática y hace que cada cambio en el proceso de creación de un turno requiera modificaciones en múltiples lugares.
Para resolverlo, introducimos la clase TurnosFachada, un **Facade** que actúa como punto único de entrada al subsistema de turnos.

### Función de la nueva clase
- **Unificación de interfaz:** los clientes solo interactúan con `TurnosFachada.solicitarTurno()`, ignorando los pasos intermedios.
- **Reducción de acoplamiento:** si cambia la forma de crear un turno por ej: nuevos pasos de validación o notificación, solo se modifica `TurnosFachada` y/o sus colaboradores, sin tocar controladores ni servicios externos.
- **Mayor cohesión y claridad:** toda la lógica de orquestación permanece en un único lugar, facilitando la lectura, el testing y la documentación.

---

## Estructura de Clases

![Imagen](https://drive.google.com/uc?export=view&id=1VgJNcDNE-sO_h1exq93MG9NBCzSfi9xa)

[Drive](https://drive.google.com/file/d/1VgJNcDNE-sO_h1exq93MG9NBCzSfi9xa/view?usp=sharing)
