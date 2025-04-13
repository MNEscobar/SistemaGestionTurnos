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
[Diagrama de Clases](https://viewer.diagrams.net/?tags=%7B%7D&lightbox=1&target=blank&highlight=0000ff&edit=_blank&layers=1&nav=1&title=Diagrama%20sin%20t%C3%ADtulo.drawio&dark=auto#R%3Cmxfile%3E%3Cdiagram%20id%3D%22C5RBs43oDa-KdzZeNtuy%22%20name%3D%22Page-1%22%3E7Vxbc5u6Fv4t58Ez7YM7XHx9jJ2m7d5tT3bT23naI4OMtQPIW8hx3F9%2FlkDCIAQmiWnS1DOdxkhCiPV9a2ldZPfceXT7hqH16gP1cdhzLP%2B25573HMe2BgP4I1p2smVsuVlLwIgv2%2FYNV%2BQHVrfK1g3xcVIayCkNOVmXGz0ax9jjpTbEGN2Why1pWH7qGgW40nDlobDa%2Bo34fJW1Tpzxvv0tJsFKPdkeTbOeCKnB8k2SFfLpttDkvu65c0Ypzz5Ft3McCukpuXx7t%2FsWvr8evfnjr%2BRf9GX25%2BePX%2FvZZBd3uSV%2FBYZjfu%2Bpf1wvL95%2BHfzzfX158dfWenO2%2BKMvb7FuULiR8vqSbBAjVL4y3yk5JlsShSiGq9mSxvxK9thwjUISxPDZg%2BVhBg03mHECEJzJDk7X0OqtSOi%2FRzu6ES%2BRcORdq6vZijLyA6ZFoZwTuhmXbHJGpRFX4k5otqCV4QTGXCrJ2HnTe5RwOcajYYjWCVnkC44QC0g8o5zTSE1EN7GPfXmVQ51ecEavc%2FIA7LOAIZ%2FAE%2Bc0pPC%2B5zFN5aJEdEHCUHX5eIk2oXjFliBKsIUI8W2BwhLUN5hGmLMdDJG9zkSCuN3T23Fl26pAbWcoG5FUqSCfK5%2F%2BE6ggigOQ1H5%2BNZeyAIPq8%2ByR6Xmj8uNQCOyIEcczIeukSFb4UHi1fVNK4TvQ2a7QuTd3emdWX9x1Ju4G2evMBjnzAotDvOS1HE7WyCNx8D4dcz7Yt3yS7y2aKNy7DFP%2BrIjv4zjlF0ccZRQUpFpTWEoqmOEM%2FoH45tarYW8IC5rDtb2%2Fhn9iOAO2xUBFRFL6YOD3FidmYjWq%2BmFi7cr4HeKVPainVQngu6Lp1KEZ02jBcIYoiOTZIdpgjFY8CuXHrnA36LfZnjSYkwfh7tbh7sekADrQ07VTQWS9S%2Byt0EfALhK2mTaMxBEiYUO%2F8FEwsIbGTbOAxwLgJbg3d3szGzWMBGeHnmO1s55o2wltRy1pa1tOR7wdVHmrQxyS1FOQ4rAr3oV9GP8IkAzxHvDPgg%2FnfbtCCrdKCtdAgBAtcHhJE8IJFfOzbKxGjMfahOyR0w7WSUegDmuMUc8BTzMgQhgswS9eZmp9Q2Gy56bXnWE7brvTjB4O7vv5l%2FliMPvv7OP6859fv7uzvz8NTRqrwCUx8QhiVxBN0PhFtmOA5NJAtWj2JfALiGmfKfAVQNtyoR74aUvXsjPgDVrtCGAuQb4k%2FA20%2BfigOk5LS30MUI3rG1VAvQRhi6REBcRTNmOfzXiktEU5q%2BBMDexxTO7buIE%2B9VkMW8tiuIasyVPJYozr4h%2B6YOiKwrZkDl4qcccK3BMgGgo%2FYJ94MvIIofGZGrWDFmzUmqUNORATK4dd5UCmp5ji6KCaEqYmULsKKVRpxOR2JshD7POGxfRFlCrtOz9zO9PsRsnZrFd8mMdDsYdDNRUX%2F7%2Fz298OwnyrjAfcBA7RMzUcxd3f6oxwk5aE6yozYRtSqTqSOPbPRL0NrhYhFT7JDJqk05KyAy6Fj3DYq7ArLoi3YTf5BfYDrGSOwwXdvt43zNIG6FAUurMLktAN8%2FBh%2BMQqGsEzeQYMdIqTm3JtscETuaRpxWHv9Ghejyqmqimyxcu7nEIxT5vInQ7LE%2Bm1HXA4A8wrEwHCaFcYJjWpfsETbcGTUpERPmQzHreKU00An%2FkRBORCg31aTZyevPlH9%2BY1nriuYY%2BdmNz5iUbcdu68O2jhzo%2Bfhjtv12WZ%2BgAD2jMb7Ap6vsWBlntrrvsPctFNTHO6ctFtUzLp5KM%2FENZhSwMyaLAfD0oRGmEdoUgoWLxI1unLC185AEmACKWvnZSTh6PU7PrkBj4GmcD0OUbSMl%2BURx2%2BMXPUMXsNG5IPJgTYkj8dQgd%2Bl6nTpgXTW%2B65KpQAZ3OBrGUWToUyBwMb46PN9rCgUW31J92Ea42cIDzacJpIxzdXVe2wz7Kwv8qmGoq3Vo9aXZi21IXpEXTBvL5qavX3jR%2BULctc7IaB1iMGGrbmH43vG2hoEzljbS1HCjQqAc30ZwQa1UxrarJOAcaTCzBcrV4wMiXxpgab6Fr3CjCGw%2FLznvSpx0ldgHE69rjX8QcFFCZmdVbHtA1J%2FwzP3HN6tqge9QzZ3bEfOo%2BMvTJzVewLXvQJ%2FW7QHxvy9D8X%2FdoD7GmU9HyzQ48MvG0NHht5Q4VGFvEpM58trpT7IwoRw%2Bl8cWckMeW0TSQZdxWGO4aT8adM44P9Paslrl2dB3Dqj6GmpXwaLwmDsE3LLOpF%2B2LZv8VQhteMBgyJibPdJU3HCXNz%2BGaQ7iecbCIcqyeZvviQjcXxDUFsThnD9EAuEItMJjXH4L%2B69eqQvy3dFnXE7uip8mp28IM4HX02TU%2BdnZIpD0umHEgo1%2BdXapMpI%2F0wpG2wgMbkhtVgA3%2B5aq2Ry7WHLyPEGfE24SFnrI%2BTNRZnNImP%2FENjhbVlhJ6TZE3jjFfP%2FIzmATbX25c75WtM5J0coQBsXJ4h%2FfabeWXHB9Vua5KO4JSZy78GQ1BTgdUKv5nydl9kLZ7RLPhVhvLzIxSAA4YDxM4JCkAywOOq5xcDH1us1WwEf7my771UwODXmVTgGGVfsw4Y0lE6IE%2B37ItvCf8u7oX9Kbv6n5oJPp%2FfFi92vWLyQKvY3q92fBfEO6gAu9PBq3JJNT%2BTd%2FfDpvpUXR03HWqO6bGPmxoxMaXcG1gutb5ggcqcBaKwXca7wWSgGgT17FeWkzfs%2BZde7YpXl5gReCsRAR2DlcWDCg1HnRppOTTYneFxmDpQp0vyL%2FLfk6dDvUasT9TRoWj1nLp11b1gt6yu2m5lpPa01vdEtZcqX1DfTBcy0M2cxxlEz0FKfn2TFGG93AGcnL%2FyF77k43r5NyCOH9%2B6Iw2gpkOCZsz67rQ0RX%2BgHaChy2WCuYbjcZCrlgKs1sjVeEG%2FCHB56lwV5Fr8ZJUOnHZgSX315Sfg1uL3P%2B6yj%2BTui2XZRQfm1Xg8bnRixMWRt5DDh%2BKmj7mF6KeDxkMN9bZbSJ1p73oLUQvudkswlY%2ByqCtZo7jE1NG%2FG%2FG7hiLlKQyEiNJYsHhhZbGb%2BvMyC%2FiE2egvUUTCXTb0LQ5vsDBAhf4sshK9trO%2BLXZkDz1LY0IWySObWd8NgugW%2FoIZQ3zDxA9JNo7z0LpuyFbSTnQOrEwnrBBz0JG%2BTJdU76RsvUKxnDKziJYIQfvS3qZykZul6iKgxLF8kKXeNO3hDOZawvTqQTJ%2BFFqS%2FtBl4SlbyvzyuvK54FUW1wSmE3NmIVRf6llp3HZFOE7nyMW7ZUgG6Yt8D%2BhrGMP2mcFb%2FPCy8Bo%2B9qj4ugqN%2B3xFvOsYJ4k6k0I4UbLTxxZwbhxXWE5pnE%2BSdYh2qidNqTnWf0gk8lMolhAsQ4q4Jl9FZpVVsAvJhoz5zdmGVJBXmRzPpQgLdrur3XCgfVtwaMiJDQxG9R5fiYDL%2FQ%2BZZvZm%2F3uw7uv%2FAw%3D%3D%3C%2Fdiagram%3E%3C%2Fmxfile%3E))

