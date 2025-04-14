# Notificación del Turno
## Descripción:
Este caso de uso se activa cuando un turno es confirmado, reprogramado o cancelado. El sistema envía una notificación automática por correo electrónico tanto al médico como al paciente.
## Escenario principal:
Se actualiza el estado de un turno (creación, modificación o cancelación).
 - Se actualiza el estado de un turno (creación, modificación o cancelación).
 - El sistema obtiene los datos de contacto de las partes involucradas.
 - Se genera un correo con los detalles del turno y el cambio efectuado.
 - Se envía la notificación.

## Condiciones:
 - Precondición: El turno debe existir en el sistema.
 - Poscondición: El paciente y el médico están informados del estado actual del turno.
