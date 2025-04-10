# Introducción 

---
## ¿Qué es la Programación Orientada a Objetos y por qué es importante?  
La programación orientada a objetos (POO) es un modelo de programación basado en la abstracción de entidades denominadas objetos, los cuales se organizan en clases. Cada objeto posee atributos, que representan sus características o datos propios, y métodos, que definen sus comportamientos o funcionalidades.
Este paradigma es importante porque, al basarse en la idea de que todo en el mundo real puede modelarse como un objeto, permite una mejor estructura y organización en el diseño del software. Los objetos interactúan y colaboran entre sí mediante el intercambio de mensajes, lo que facilita la comunicación entre componentes del sistema. Además, la POO promueve la reutilización de código, ya que permite definir clases con comportamientos esperados, y favorece el mantenimiento del software, dado que los objetos pueden evaluarse y modificarse de manera individual. Gracias a este enfoque, es posible diseñar aplicaciones más robustas, flexibles y fáciles de mantener.

---
## Fundamentos de la POO  
### Encapsulamiento  
Restricción del acceso a los datos de un objeto, permitiendo interactuar solo a través de métodos específicos.

Un ejemplo de la vida real puede ser un sistema de pedidos en un restaurante, el cliente hace el pedido al mozo pero no tiene acceso a como el mozo comanda su pedido, ni como es preparado y vuelve a salir hacia su mesa.
### Herencia  
Permite que una clase derive características y comportamientos de otra, evitando duplicación de código. 

Un ejemplo de herencia, siguiendo el mismo ejemplo del caso anterior, en ese restaurant hay distintos tipos de empleados: mozos, cocineros y encargados. Todos ellos comparten ciertas características generales como nombre, horario de trabajo, y sueldo base. Sin embargo, cada uno tiene funciones particulares: el cocinero prepara los platos, el mozo toma pedidos y el encargado supervisa. Existe una clase general "**Empleado**" puede ser la clase padre, y "**Mozo**", "**Cocinero**" y "**Encargado**" heredan de ella sus atributos y métodos comunes, pero también pueden tener comportamientos propios que los diferencian.
### Polimorfismo  
Capacidad de un mismo método de comportarse de diferentes formas según la clase que lo implemente.

Siguiendo con los empleados, supongamos que todos tienen un método llamado realizarTarea. Para un mozo, realizarTarea puede significar “tomar el pedido”; para un cocinero, “preparar el plato”; y para el encargado, “controlar el stock”. Un mismo método (con el mismo nombre) puede tener comportamientos diferentes según el tipo de objeto que lo implemente, aunque todos respondan a la misma interfaz o estructura común.
### Abstracción  
Oculta los detalles internos y muestra solo lo esencial para su uso.

Cuando un cliente pide una "pizza", no necesita conocer todos los ingredientes ni el proceso exacto de cocción. Solo interactúa con un menú que muestra los platos disponibles, sus nombres, una breve descripción y el precio.

---
## Requisitos iniciales del sistema  
1. Registro de usuarios y gestión de usuarios diferenciados para médicos, administrativos y pacientes.  
2. Gestión de turnos con registro de fecha, hora, médico y especialidad en base a la disponibilidad médica.   
3. Almacenamiento del historial médico y consultas previas.  
4. Notificación automática a pacientes y médicos sobre turnos confirmados, modificados o cancelados.  
5. Acceso restringido a datos e información médica y solo disponible para personal autorizado.

---
## Casos de uso  

### Caso 1
   
| Caso de uso        | Registro de usuarios                                                        |
|--------------------|-----------------------------------------------------------------------------|
| **Actores**        | Pacientes, Médicos y Administrativos                                        |
| **Descripción**    | El administrativo registra los datos al centro de salud y crea un usuario   |
| **flujo principal**| 1. El administrativo ingresa al sistema con sus credenciales                |
|                    | 2. Selecciona "Registrar nuevo usuario"                                     |
|                    | 3. Completa los datos del usuario                                           |
|                    | 4. Guarda la información del usuario                                        |
| **Precondiciones** | El usuario no debe estar registrado en el sistema                           |
| **Postcondiciones**| El usuario queda registrado y puede acceder al sistema según su rol         |
| **Extiende a**     | "Validar datos del usuario"                                                 |
| **Hereda de**      |                                                                             |


### Caso 2

| **Caso de uso**    | Reservar un turno                                              |                         
|--------------------|----------------------------------------------------------------|
| **Actores**        | Cliente                                                        |
| **Descripción**    | El cliente seleeciona un servicio y reserva un turno disponible|
| **Flujo principal**| 1. El cliente accede al sistema                                |  
|                    | 2. Selecciona un servicio                                      |
|                    | 3. Escoge una fecha y hora disponible                          |
|                    | 4. Confirma la reserva                                         |
| **Precondiciones** | El cliente debe estar registrado                               | 
|**Postcondiciones** | El turno queda guardado en el sistema                          |
| **Extiende a**     | "Gestión de turnos"                                            |
| **Hereda de**      | "Registro de usuarios"                                         |

### Caso 3
| **Caso de uso**      | Notificación de Confirmación o Cancelación de Turno                                  |
|--------------------- |--------------------------------------------------------------------------------------|
| **Actores**          | Sistema                                                                              |
| **Descripción**      | El sistema notifica a los usuarios participes del                                    |
|                      | turno                                                                                |
| **Flujo Principal**  | 1. Un administrativo o paciente confirma o cancela un turno                          |
|                      | 2. El sistema procesa el cambio                                                      |
|                      | 3. Se envía una notificación automática al paciente y al médico por correo o mensaje |
|                      | 4. El usuario recibe y visualiza la notificación                                     |
| **Precondiciones**   | Debe existir un turno asignado en el sistema                                         |
| **Postcondición**    | Los usuarios quedan informados sobre la confirmación o cancelación del turno         |
| **Extiende a**       | "Gestionar turnos"                                                                   |
| **Hereda de**       | "Reservar turno"                                                                      |

### Caso 4
| **Caso de uso**      | Almacenar Historial Médico                                              |
|----------------------|-------------------------------------------------------------------------|
| **Actor**            | Médico                                                                  |
| **Descripción**      | El médico proscribe sobre el historial del paciente                     |
| **Flujo Principal**  | 1. El médico accede al sistema con sus credenciales                     |
|                      | 2. Busca al paciente en la base de datos                                |
|                      | 3. Selecciona la opción "Actualizar historial médico"                   |
|                      | 4. Ingresa diagnóstico, tratamiento y observaciones                     |
|                      | 5. Guarda los cambios                                                   |
|                      | 6. El sistema almacena la información y la asocia al paciente           |
| **Precondición**     | El paciente debe estar registrado en el sistema                         |
| **Postcondición**    | El historial médico queda actualizado y accesible para futuras consultas|
| **Extienda a**       |                                                                         |
| **Hereda de**        | "Gestionar datos de pacientes"                                          |

### Caso 5
| **Caso de uso**      | Consultar Turnos Asignados                                                                        |
|----------------------|---------------------------------------------------------------------------------------------------|
| **Actor**	           | Médico                                                                                            |
| **Descripción**      | El médico accede al sistema para visualizar la lista de turnos asignados en una fecha determinada.|
| **Flujo Principal**  | 1. El médico accede al sistema con sus credenciales.                                              |
|                      | 2. Selecciona la opción “Consultar turnos”.                                                       |
|                      | 3. Elige una fecha del calendario.                                                                |
|                      | 4. El sistema muestra la lista de turnos con horario, nombre del paciente y motivo de consulta.   |
|                      | 5. El médico puede filtrar o buscar turnos por nombre del paciente o por horario.                 |
| **Precondición**     | El médico debe tener al menos un turno asignado en el sistema.                                    |
| **Postcondición**    | El médico visualiza sus turnos organizados y puede planificar su jornada.                         |
| **Extiende a**       |                                                                                                   |
| **Hereda de**        | “Gestionar turnos médicos”                                                                        |






## Boceto inicial del diseño de clases  
[Diagrama de Clases]   ![Uploading Diagrama de Clses.png…]()

