# Introducción 

---
## ¿Qué es la Programación Orientada a Objetos y por qué es importante?  
La programación orientada a objetos (POO) es un modelo de programación basado en la abstracción de entidades denominadas objetos, los cuales se organizan en clases. Cada objeto posee atributos, que representan sus características o datos propios, y métodos, que definen sus comportamientos o funcionalidades.
Este paradigma es importante porque, al basarse en la idea de que todo en el mundo real puede modelarse como un objeto, permite una mejor estructura y organización en el diseño del software. Los objetos interactúan y colaboran entre sí mediante el intercambio de mensajes, lo que facilita la comunicación entre componentes del sistema. Además, la POO promueve la reutilización de código, ya que permite definir clases con comportamientos esperados, y favorece el mantenimiento del software, dado que los objetos pueden evaluarse y modificarse de manera individual. Gracias a este enfoque, es posible diseñar aplicaciones más robustas, flexibles y fáciles de mantener.

---
## Fundamentos de la POO  
### Encapsulamiento  
Restricción del acceso a los datos de un objeto, permitiendo interactuar solo a través de métodos específicos.
Un ejemplo de la vida real puede ser en un sistema de pedidos en un reatauran, el cliente hace el pedido al mozo pero no tiene acceso a como el mozo comanda su pedido ni como llega a su cocina ni como es preparado y vuelve a salir hacia su mesa.
### Herencia  
Permite que una clase derive características y comportamientos de otra, evitando duplicación de código. 
### Polimorfismo  
Capacidad de un mismo método de comportarse de diferentes formas según la clase que lo implemente.
### Abstracción  
Oculta los detalles internos y muestra solo lo esencial para su uso. 

---
## Requisitos iniciales del sistema  
1. Registro de usuarios y gestión de usuarios diferenciados para médicos, administrativos y pacientes.  
2. Gestión de turnos con registro de fecha, hora, médico y especialidad en base a la disponibilidad médica.   
3. Almacenamiento del historial médico y consultas previas.  
4. Notificación automática a pacientes y médicos sobre turnos confirmados, modificados o cancelados.  
5. Acceso restringido a datos e información médica y solo disponible para personal autorizado.

---
## Casos de uso  

### caso 1
   
| Caso de uso        | Registro de usuarios                   |
|--------------------|----------------------------------------|
| **Actores**        | Pacientes, Médicos y Administrativos   |
|____________________|________________________________________|
| **Descripción**    | El administrativo registra los datos   |
|                    | al centro de salud y crea un usuario   |
|____________________|________________________________________|
| **flujo principal**| 1. El administrativo ingresa al sistema|
|                    | con sus credenciales                   |
|                    | 2. Selecciona "Registrar nuevo usuario"|
|                    | 3. Completa los datos del usuario      |
|                    | 4. Guarda la información del usuario   |
|____________________|________________________________________|
| **Precondiciones** | El usuario no debe estar registrado    |
|                    | en el sistema                          |
|____________________|________________________________________|
| **Postcondiciones**| El usuario queda registrado y puede    |
|                    | acceder al sistema según su rol        |
|____________________|________________________________________|
| **Extiende a**     | "Validar datos del usuario"            |
|____________________|________________________________________|
| **Hereda de        |                                        |
|____________________|________________________________________|


### caso 2

| **Caso de uso**    | Reservar un turno       |                         
|--------------------|-------------------------|
| **Actores**        | Cliente                 |
|____________________|_________________________|
| **Descripción**    | El cliente seleeciona un|
|                    | servicio y reserva un   |
|                    | turno disponible        |
|____________________|_________________________|
| **Flujo principal**| 1. El cliente accede    |  
|                    | al sistema              |
|                    | 2. Selecciona un servicio|
|                    | 3. Escoge una fecha y   |
|                    | hora disponible         |
|                    | 4. Confirma la reserva  |
|____________________|_________________________|
| **Precondiciones** | El cliente debe estar   | 
|                    | registrado              |
|____________________|_________________________|
|**Postcondiciones** | El turno queda guardado |
|                    | en el sistema           |
|____________________|_________________________|
| **Actores**        | Cliente                 |
| **Descripción**    | El cliente seleeciona un|
|                    | servicio y reserva un   |
|                    | turno disponible        |
|--------------------|-------------------------|
| **Flujo principal**| 1. El cliente accede    |  
|                    | al sistema              |
|                    | 2. Selecciona un servicio|
|                    | 3. Escoge una fecha y   |
|                    | hora disponible         |
|                    | 4. Confirma la reserva  |
|____________________|_________________________|
| **Precondiciones** | El cliente debe estar   | 
|                    | registrado              |
|____________________|_________________________|
|**Postcondiciones** | El turno queda guardado |
|                    | en el sistema           |
|____________________|_________________________|
| **Extiende a**     | "Gestión de turnos"     |
|____________________|_________________________|
| **Hereda de**      | "Registro de usuarios"  |
|____________________|_________________________|

## Boceto inicial del diseño de clases  
![Diagrama de Clases](ruta-de-la-imagen.png)  
[Ver en línea](https://enlace-a-la-imagen.com)  
