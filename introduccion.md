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
| **Descripción**      | El sistema notifica a los usuarios participes del turno                              |
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

[Diagrama de Clases](https://viewer.diagrams.net/?tags=%7B%7D&lightbox=1&target=blank&highlight=0000ff&edit=_blank&layers=1&nav=1&title=Diagrama%20de%20Clases.drawio&dark=auto#R%3Cmxfile%3E%3Cdiagram%20id%3D%22C5RBs43oDa-KdzZeNtuy%22%20name%3D%22Page-1%22%3E7Vxbc5u6Fv4t58Ez6YM7XHyJH2Onabt32pPd9Hae9sggY%2B0A8hbYjvvrzxKSMAhBSGKaNPVMp0EXFmJ9S0vrZnruLLp9y9Bq%2BYH6OOw5ln%2Fbc897jmNbgwH84T072TO2XNETMOLLvn3HNfmB1a2yd018nJQmppSGKVmVOz0ax9hLS32IMbotT1vQsPzUFQpwpePaQ2G19xvx06XoPXXG%2B%2F53mARL9WR7NBEjEVKT5ZskS%2BTTbaHLfdNzZ4zSVFxFtzMccu4pvnx7v%2FsWXt6M3v7xV%2FIv%2BjL98%2FPHr31B7OI%2Bt%2BSvwHCcPpj0j5vFxbuvg3%2B%2Br64u%2Ftpab8%2Fmf%2FTlLdYGhWvJry%2FJGjFC5SunO8XHZEuiEMXQmi5onF7LERvaKCRBDNceLA8z6NhglhKA4EwOpHQFvd6ShP4l2tE1f4kkRd6Nak2XlJEfQBaFkiYMs1RKkzMqzbjmd0K3Bb0MJzDnSnHGzrsuUZLKOR4NQ7RKyDxfcIRYQOIpTVMaKUJ0HfvYl60c6qyRMnqTCw%2FAPg0Y8gk8cUZDCu97HtOML4pFFyQM1ZCPF2gd8ldsCaIEm7MQ3xZEWIL6FtMIp2wHU%2BSocypB3O7F23Fl37Ig2s5QdiK5pYKcVk7%2BE2xBFAfAqT19RUtpgEH1efbI9LxR%2BXEoBOmIUYqnnNdJUVjhovBq%2B65MhO8hznZFnHszp3dm9fldZ%2Fxu4L0u2cDntCDFIV6ktTKcrJBH4uAym3M%2B2Pd8ku%2FNuyjcuwgz%2BVkS38dxJl8pSpEQQS5UKwpLyRgznMI%2FYN%2FMej3sDWFBM2jb%2Bzb849MZSFsMoohIJj4Y5HuLE7NgNW71uwVrV8bvLrmyB%2FViVQL4vmg6dWjGNJozLBAFlrw4RBuU0TKNQnnZFe6G%2FW3WJw3q5FG4u3W4%2BzEpgA7i6doZI8ToAntL9BGwi7hupg0zcYRI2DDObRQMUkPjJipgsQB4Ce7N3N7URg0zwdih51idrEex7URsRy3F1racjuR2UJVbHeKQZJaCZIddsS7su%2FGPAMkQ7wH%2FzOXhvG9XhMKtCoVrEIAQzXF4RROSEsrpMzFXE4ynOoTskdMO1tOOQB3WKKOeA5ZmQDgzWIJPXoltvaFA7KXt686wHbc9aUaPB%2Fdy9mU2H0z%2FO%2F24%2Bvzn1%2B%2Fu9O9PQ9OOVeCSmHgEsWvwJmh8Ik4M4FzmqBbVvgR%2BDj7tEfi2wE9ampadAW%2FY1Q4H5gr4S8Ljbn6Iu%2BC01NSHANW45FEF1CtgNg9KVEA8RjP20YwnCluUowrOxCA9jsl8GzeIT30Uw9aiGK4havJcohjjOv%2BHzhm6pnAsmZ2Xit%2BxBPMEBA2FH7BPPOl5hND5uyq1UWspbYiBmKRy2FUMZHL0KQ4OqilgagK1K5dCpUZMZmeCPMQ%2Br1lMT6Js0773hdmZRTdKxmb9xgc6Hoo9HCpSKf%2F%2Fvd%2F%2BdmDmO6U84CYwiF6o4iie%2FlZnAnfaUuC6ikzYhlCqjiSO%2FTOeb4PWPKTcJplClzRaMumAJrcR7rYq7IoJ4q3ZJm9gP8CK5zic0%2B2bfcc064ABJUL3NkESumYevhs%2BvopG8EyWAYM9lZJNObfYYIlc0SzjsDd6NKtHJVMVCbF4eZdTSOZphNzJsExIz%2B2AwRngtEIIEEa7wjS5k%2BoXfKot%2BLSUZIQLQfGwWZxqAPjMj8Ah5zvYp9XA6dGaf3JrXpMT162esa5lMq8tTXDbmfPuoIU5P34e5rxdF2XqAwxoL9mgV9DLTQ60PFvzvf8YE90saV2Z6LYpmHS00R8J67ClAhk06I9HhQiNsI4yLeqTDVwG4v1HKOJ7Lp4nq6zNzecAmANcRUzm%2FJKTtbjIbXARWtTvrbSl0r4oP9GwiKxrzvSeyq1Ni818haQc%2FGzxwu0XaXj4BmP2Bg5UH1QgSHv%2BdHB90i7ev92qUAJ7LmfISkYRlSt2p2NmfLRZnxc0Qtv9nxkRtUqab1i0TmkiDfdc1WjFSouCfSC7OtvLk5Z72bYPsJnNa67Ghn9fB0gBKHyEhonWE3pKtmbgjR%2FqKWmEnLG2lgN5ShWPbPIzPKVqqDjTWUcP6dl5SK6W8BiZopATg1J0H%2BYhDYfl5z3rss3TOg%2FpWLe53%2BOPSlqYJKuzRKxtyFoIPHPT6cWietAiuPtjP3SeGHul5qrYF8zoI%2FrdoD82JBp%2BLvq1FfiZm%2FRyw1tPDLxtDZ4aeUOKSVYhUGYujq7UK0QUPIZjgXRnQmIIyhuFZNyVG%2B4YSvuPodJH23tWS1y7Kmhw6utos1oEGi8IA7dNCy3qVQfFuoUWUxleMRowxAmL0yWLx3F1c%2FfNwN1POFlHOFZPMv1yQ8zF8YYgNqOMYXpHMBDzUCY1%2B%2BC%2FuvbqUH5bmi2qRvDgsf5qdPADL%2B8%2Bm2Rlc8dgynMLpoz0ak7boAGNwQ2rQQf%2BculmoyzXVo9GKGXEW4d3GWN9nKwwLzIlPvLvmsu1LSP0nCQrGgu5%2Bo2KTBuVyaPiNSbhPT1ABtu4YkP47Te2yg4Dqt1WJR3AKDPnrw2KoCYFq2V%2BxebtPstaLDIt2FWG%2FPMTZIADhgPEzgkKgDMgx1XLLwZ5bLFWsxJ83nnfQ20Bg11n2gKTA%2Fib5j1gCEfpgDzftC%2B%2BJel3fi%2BcT6L1P0UJrs9vi41dry540DZV3IT5U2SA3cngdTmlmhcV3r9aVifVVb3sUDNMD10vawTJEHRV%2BO7FXNceSuuoU1NXO3PpEohjdgp%2BRpCJtq5OuAMk94pzb%2FmTH32Sy%2BrlRfH3SKuOygwfNdWDmTHru5MSif5AKzWgi0WC056ujA6BXDVoarVGrua8%2BEWAy4OMKnXR4utEOnBaaYf6lcNPwK3Fpx4K54pkeeHML58Se0VvWXZR1b8ej8eN6p43rjAj8EI83CD6Yng5Qc49HaoOQW8yGamOPcGstSu2dJIPP1Ua88PasVKuSGooymw8f4YGA2N4oCPJ0WVWk7i2B9JAK5cf6TUeHf18Qy24bl36fLWu2vewGud3dNyZkgjC9gavMS7twtG%2Fa%2F55Ph744sqP2%2BosmJ9YwoJXf14Js5%2BrxP4CRSTcianvcLjBXLkWxoV9zUdtZ3VbHBAPPcs8AxbJwj0xtkHg48BfUNEoXTP%2BPcTGeR5a1U3ZSrHmg5z92UiIU9isfek0V%2B%2BkbLVEsSQptL3FHZG%2BPEsyvkhDQA0RUFCxfJCl3jQbATc6ThZAXj1IehF8F2bfayw8ZUuZX15XTgteZX5DgBynKQzpvtzHpXnbJUlxRiNn75Yh6arN8%2FOtr2EMpoGAt3jxqvAaPvYo%2F9UFjfvpkng3MU4SVZlAUqJ4p88t4Nw4r7Cc0jyfJKsQ7dRIFlhxrP%2BQiEcpUCwhWIQUpRp%2FlTAr39IuuJxC8pt9zoyR14KP55KFhTPpfkq%2B%2FUmvK4mhIQ05MCjtB1T2Q3P%2FPU6hb%2FafNXXf%2FB8%3D%3C%2Fdiagram%3E%3C%2Fmxfile%3E)

![](DiagramasyDiseños/DiseñosUML/Imagenes/CasoDeUso1.png)
