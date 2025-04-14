# Descripción general de las tarjetas CRC
Las tarjetas CRC (Clase, Responsabilidad, Colaboración) son una herramienta utilizada en el diseño orientado a objetos para representar de forma simple y visual la responsabilidad de una clase y cómo se relaciona con otras.
##### Cada tarjeta contiene:
 - Clase: el nombre de la entidad.
 - Responsabilidades: lo que la clase debe saber o hacer.
 - Colaboradores: otras clases con las que se comunica para cumplir sus responsabilidades.
 - Pensamiento del objeto: una frase que resume la esencia del objeto en primera persona.
 - Propiedades: atributos clave que definen al objeto.
Estas tarjetas son útiles para pensar en el diseño de sistemas desde la perspectiva de los objetos que lo componen, promoviendo la separación de responsabilidades y la colaboración entre entidades.
#### Tarjeta CRC: Usuario
El Usuario es la clase base del sistema, que representa a cualquier persona registrada, ya sea paciente, médico o administrativo. Su principal responsabilidad es gestionar su autenticación y sus datos personales. Interactúa con el sistema de registro y otras clases derivadas según su rol.


![](Imagenes/CRC_usuario.png)

#### Tarjeta CRC: Paciente
El Paciente hereda de Usuario y representa a quienes utilizan el sistema para recibir atención médica. Puede reservar turnos, consultar sus citas y acceder a su historial médico. Colabora estrechamente con la clase Turno y Médico para llevar adelante sus acciones.


![](Imagenes/CRC_paciente.png)

#### Tarjeta CRC: Médico
El Médico también hereda de Usuario y está encargado de brindar atención a los pacientes. Su rol incluye cargar historiales, gestionar su disponibilidad y visualizar sus turnos asignados. Colabora con Turno, Paciente e Historial Médico.


![](Imagenes/CRC_medico.png)

#### Tarjeta CRC: Administrativo
El Administrativo, una subclase de Usuario, cumple funciones de gestión como registrar usuarios, organizar turnos y mantener el orden administrativo. Interactúa con el sistema de gestión de usuarios y con Turno para modificar datos o asignaciones.


![](Imagenes/CRC_admin.png)


#### Tarjeta CRC: Turno
La clase Turno es clave para el funcionamiento del sistema. Representa una cita médica programada, con fecha, hora, paciente y médico asociados. Se comunica con Paciente, Médico y el sistema de notificaciones para reflejar el estado y coordinación de la atención médica.


![](Imagenes/CRC_turno.png)
