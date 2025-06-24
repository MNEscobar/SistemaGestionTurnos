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


![CRC Usuario](https://drive.google.com/uc?export=view&id=1ZsgvDOmbY_v7DM733NGxl12iTNssZayL)


#### Tarjeta CRC:Perfil
La clase Perfil encapsula la información de presentación de un usuario, como su foto, biografía y roles asignados. Sirve para formatear y exponer los datos que el sistema muestra en la interfaz de usuario. Interactúa principalmente con la clase Usuario, que delega en Perfil la tarea de “armar” la vista de sus datos personales.

![CRC Perfil](https://drive.google.com/uc?export=view&id=1PZ2fAC1jGntbctAT9MnZWKYA4bqSRRaC)

#### Tarjeta CRC: Paciente
El Paciente hereda de Usuario y representa a quienes utilizan el sistema para recibir atención médica. Puede reservar turnos, consultar sus citas y acceder a su historial médico. Colabora estrechamente con la clase Turno y Médico para llevar adelante sus acciones.

![CRC Paciente](https://drive.google.com/uc?export=view&id=1eZxfUR3Q2GjMmbpq6lAylCyE9skemw3A)


### Tarjeta CRC: Historial
La clase Historial gestiona el conjunto de registros médicos asociados a un Paciente. Almacena entradas de tipo RegistroMedico y provee operaciones para agregar nuevos registros o consultar la lista completa. Se conecta con Paciente, que accede a él para revisar su información clínica, y con Médico, que añade anotaciones tras cada consulta.

![CRC Historial](https://drive.google.com/uc?export=view&id=1uuFGQaROtbfSCgV81ni18W4w20FLapEB)

#### Tarjeta CRC: Médico
El Médico también hereda de Usuario y está encargado de brindar atención a los pacientes. Su rol incluye cargar historiales, gestionar su disponibilidad y visualizar sus turnos asignados. Colabora con Turno, Paciente e Historial Médico.


![CRC Médico](https://drive.google.com/uc?export=view&id=1Uj6NehMJN9AwsTHKR9LvmTODRvDE5zoV)

#### Trajeta CRC: Agenda
La clase Agenda modela el calendario de disponibilidad de un profesional de la salud. Mantiene una colección de franjas horarias (slots) que el Médico puede agregar o eliminar según su conveniencia. Colabora estrechamente con Médico, que invoca sus métodos para actualizar sus turnos disponibles, y con Turno, al validar si una fecha y hora solicitadas están libres.

![CRC Agenda](https://drive.google.com/uc?export=view&id=1bc7kXLKoOYXh9YVvE2Ux-UM3NBkuOFEU)

#### Tarjeta CRC: Administrador
El Administrativo, una subclase de Usuario, cumple funciones de gestión como registrar usuarios, organizar turnos y mantener el orden administrativo. Interactúa con el sistema de gestión de usuarios y con Turno para modificar datos o asignaciones.


![CRC Administrativo](https://drive.google.com/uc?export=view&id=1-OO0SJB4f2a4TUHLaor9hb5XYcAV-rrB)


#### Tarjeta CRC: Turno
La clase Turno es clave para el funcionamiento del sistema. Representa una cita médica programada, con fecha, hora, paciente y médico asociados. Se comunica con Paciente, Médico y el sistema de notificaciones para reflejar el estado y coordinación de la atención médica.


![CRC Turno](https://drive.google.com/uc?export=view&id=15kwkwpnz9MfzozPBJCpU_P-El19_qt6e)



[Planilla Tarjetas CRC](https://docs.google.com/spreadsheets/d/1aLxJNcpcsDVDc4BZh3GDFItkQbP6LOxz/edit?usp=sharing&ouid=113574952751855851904&rtpof=true&sd=true)
