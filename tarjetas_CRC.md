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


![](https://drive.google.com/file/d/1UHAS-9jTJmWhNI-kWkNaWXMvDgZkTTh3/view?usp=drive_link)

## Vista previa

![Imagen desde Google Drive](https://drive.google.com/uc?export=view&id=1YPQzEEtq3POo9bAft8kiHpnSRBdKfGg_)

📎 [Abrir imagen en Google Drive](https://drive.google.com/file/d/1YPQzEEtq3POo9bAft8kiHpnSRBdKfGg_/view?usp=drive_link)

#### Tarjeta CRC: Paciente
El Paciente hereda de Usuario y representa a quienes utilizan el sistema para recibir atención médica. Puede reservar turnos, consultar sus citas y acceder a su historial médico. Colabora estrechamente con la clase Turno y Médico para llevar adelante sus acciones.


![](https://drive.google.com/file/d/1qUMG1d2-6_U25_1dHdYd9jZJs3U9lXNi/view?usp=drive_link)

#### Tarjeta CRC: Médico
El Médico también hereda de Usuario y está encargado de brindar atención a los pacientes. Su rol incluye cargar historiales, gestionar su disponibilidad y visualizar sus turnos asignados. Colabora con Turno, Paciente e Historial Médico.


![](https://drive.google.com/file/d/1g7vt1E4icDCsTZnS4M_vxXmkM7fDCnjf/view?usp=drive_link)

#### Tarjeta CRC: Administrativo
El Administrativo, una subclase de Usuario, cumple funciones de gestión como registrar usuarios, organizar turnos y mantener el orden administrativo. Interactúa con el sistema de gestión de usuarios y con Turno para modificar datos o asignaciones.


![](https://drive.google.com/file/d/1iB1J7rYfpsRZQcju1tuFjiO374Z4T2qY/view?usp=drive_link)


#### Tarjeta CRC: Turno
La clase Turno es clave para el funcionamiento del sistema. Representa una cita médica programada, con fecha, hora, paciente y médico asociados. Se comunica con Paciente, Médico y el sistema de notificaciones para reflejar el estado y coordinación de la atención médica.


![](https://drive.google.com/file/d/1fK9tHqZOkacc-2sLm4kisbIA1p-2qsvB/view?usp=drive_link)


[Planilla Tarjetas CRC](https://docs.google.com/spreadsheets/d/13zP70Rb4vhZzoa_iHvP-ABAVd9V9eto1/edit?usp=drive_link&ouid=113574952751855851904&rtpof=true&sd=true)
