# Principio de Responsabilidad Única - SRP

## Definición

Este principio establece que una clase debe tener una única responsabilidad o motivo para cambiar. Es decir, debe encargarse de una única cosa, de manera clara y separada de otras funciones del sistema. Si una clase requiere ser modificada por más de un motivo, significa que está violando este principio.
En sistemas mal diseñados, es común encontrar clases que acumulan múltiples responsabilidades. Esto provoca que cualquier cambio, por mínimo que sea, pueda generar efectos inesperados en partes del código que no deberían verse afectadas. Además, dificulta la comprensión del sistema, complica su mantenimiento y lo vuelve más propenso a errores.
Por ejemplo, si una misma clase gestiona datos, envía notificaciones, guarda información en la base de datos y genera comprobantes, cualquier modificación en una de esas funciones obliga a revisar y potencialmente modificar toda la clase. Esto hace que el código sea más frágil y difícil de mantener.
Al separar las responsabilidades en diferentes clases, cada una se vuelve más fácil de entender, mantener y reutilizar. Además, el sistema en general se vuelve más robusto y predecible ante cambios.

## Aplicación del principio SRP al sistema de gestión de turnos

En el sistema, encontramos que la clase Turno realiza diversas tareas:

- Almacena datos del turno (fecha, hora, IDs del paciente y médico, etc.)

- Confirma o cancela turnos
- Reprograma turnos
- Genera resúmenes
- Envía correos electrónicos relacionados al turno

Esto indica que la clase Turno no solo cumple una función de modelo de datos, sino que también controla lógica de negocio y funcionalidades de comunicación (correo), lo cual rompe el SRP.

Algo similar ocurre con la clase Administrador, que además de gestionar usuarios, también:

- Asigna turnos
- Genera estadísticas
- Gestiona la lógica de turnos

Estas clases, al tener más de una responsabilidad, están acopladas a distintas áreas del sistema. Si en algún momento se decide modificar cómo se envían correos o cómo se calculan las estadísticas, estas clases deberán cambiar, aun si su rol principal (modelar un turno o un administrador) no debería verse afectado.


Una forma de corregir esto es delegando las responsabilidades específicas a nuevas clases, especializadas y desacopladas. Por ejemplo:

| Responsabilidad actual          |	Clase actual	        | Clase nueva sugerida    |
|---------------------------------|------------------------|------------------------|
| Representar un turno	                 | Turno	        | (se mantiene)           |
|Confirmar, cancelar, reprogramar turnos | Turno	        | estadoDelTurnos         |
Enviar correos relacionados al turno     | Turno	        | servicioDeCorreoTurnos  |
Generar resumen del turno	               | Turno	        | generadorDeResumenTurno |
Asignar turnos a pacientes/médicos       | Administrador	| asignadorDeTurnos       |
Calcular estadísticas del sistema        | Administrador	| generadorDeEstadísticas |

De este modo:

La clase Turno se ocupa solamente de representar los datos de un turno.

La lógica para gestionar turnos (confirmar, cancelar, etc.) se delega a otra clase.

El envío de correos queda completamente aislado y puede evolucionar sin afectar a Turno.

Esto mejora el diseño, facilita las pruebas unitarias, reduce la probabilidad de errores y permite una mayor escalabilidad en el futuro.

## Ejemplo del mundo real
Imaginemos un restaurante donde un solo empleado toma los pedidos, cocina, atiende las mesas, cobra y lava los platos.

Si esa persona falta o comete un error, afecta todo el sistema.

No se puede escalar ni mejorar la eficiencia.

Al dividir responsabilidades:

Un mozo toma pedidos.

Un cocinero cocina.

Un cajero cobra.

Cada uno tiene una sola responsabilidad, clara y separada.
