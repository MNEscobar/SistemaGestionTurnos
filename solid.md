# Principios SOLID

Los principios SOLID constituyen un conjunto de cinco reglas fundamentales para el diseño de software orientado a objetos, formuladas por Robert C. Martin. Su finalidad es facilitar el desarrollo de sistemas que sean más fáciles de mantener, ampliar y adaptar a cambios. En términos simples, aplicar SOLID permite construir código más claro, comprensible y flexible, minimizando el riesgo de introducir errores al modificarlo.

El término SOLID es un acrónimo, cada una de sus letras representa uno de estos principios. A continuación, se presenta una explicación detallada de estos principios:

- [S – SRP: Single Responsibility Principle (Principio de Responsabilidad Única)](srp.md)

- [O – OCP: Open/Closed Principle (Principio de Abierto/Cerrado)](ocp.md)

- [L – LSP: Liskov Substitution Principle (Principio de Sustitución de Liskov)](lsp.md)

- [I – ISP: Interface Segregation Principle (Principio de Segregación de Interfaces)](isp.md)

- [D – DIP: Dependency Inversion Principle (Principio de Inversión de Dependencias)](dip.md)

---
## Aplicación de Principios SOLID en Tres Clases principales del Sistema de Gestión de Turnos
---

### Clase Turno

La clase `Turno` tiene como única responsabilidad representar los datos y el estado de un turno médico. Sus funciones deben limitarse a almacenar información como la fecha y hora del turno, el médico asignado, el paciente correspondiente y el estado del turno (pendiente, confirmado, cancelado, etc.).

Para cumplir con el SRP, esta clase no debe encargarse de tareas como notificar al paciente o persistir información en la base de datos. En su lugar, debe delegar esas responsabilidades a otras clases especializadas, como `NotificadorTurno`.


### Clase NotificadorTurno

La clase o interfaz `NotificadorTurno` se encarga de definir la estructura para enviar notificaciones relacionadas a los turnos (recordatorios, confirmaciones, cancelaciones, etc.). Esta lógica debe estar abierta a la extensión pero cerrada a la modificación, respetando el principio OCP permitiendo agregar nuevas formas de notificación (por ejemplo, por email o SMS) sin modificar el código existente.

Se define una interfaz `NotificadorTurno` con un método `notificar(Turno turno)`. Las distintas implementaciones concretas (`NotificadorEmail`, `NotificadorSMS`, etc.) implementan este método según el canal de comunicación elegido. De esta manera, las clases que utilizan `NotificadorTurno` dependen de una abstracción y no de una implementación concreta, cumpliendo con el principio DIP.


### Clase Paciente

El principio LSP establece que una subclase debe poder sustituir a su clase padre sin alterar el comportamiento esperado del programa. En el sistema, esto se aplica a la clase Paciente, que podría tener subclases como `PacienteParticular` o `PacienteObraSocial`. Las subclases de Paciente deben implementar los métodos definidos en la clase base sin romper su funcionalidad esperada. Por ejemplo, si Paciente tiene un método obtenerDatosDeContacto(), todas sus subclases deben proveer una implementación coherente con el propósito del método. Esto garantiza la intercambiabilidad de objetos en contextos donde se espera un Paciente.
