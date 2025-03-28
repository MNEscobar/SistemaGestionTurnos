# Introducción  

## ¿Qué es la Programación Orientada a Objetos y por qué es importante?  
La programación orientada a objetos (POO) es un modelo de programación basado en la abstracción de entidades denominadas objetos, los cuales se organizan en clases. Cada objeto posee atributos, que representan sus características o datos propios, y métodos, que definen sus comportamientos o funcionalidades.
Este paradigma es importante porque, al basarse en la idea de que todo en el mundo real puede modelarse como un objeto, permite una mejor estructura y organización en el diseño del software. Los objetos interactúan y colaboran entre sí mediante el intercambio de mensajes, lo que facilita la comunicación entre componentes del sistema. Además, la POO promueve la reutilización de código, ya que permite definir clases con comportamientos esperados, y favorece el mantenimiento del software, dado que los objetos pueden evaluarse y modificarse de manera individual. Gracias a este enfoque, es posible diseñar aplicaciones más robustas, flexibles y fáciles de mantener.

## Fundamentos de la POO  
### Encapsulamiento  
Restricción del acceso a los datos de un objeto, permitiendo interactuar solo a través de métodos específicos. 
### Herencia  
Permite que una clase derive características y comportamientos de otra, evitando duplicación de código. 
### Polimorfismo  
Capacidad de un mismo método de comportarse de diferentes formas según la clase que lo implemente.
### Abstracción  
Oculta los detalles internos y muestra solo lo esencial para su uso. 

## Requisitos iniciales del sistema  
1. Permitir que un usuario registre un turno.  
2. Notificar a los usuarios sobre turnos confirmados.  
3. Permitir la cancelación de turnos.  
4. Registrar los turnos en una base de datos.  
5. Gestionar diferentes tipos de usuarios (clientes y empleados).  

## Casos de uso  
### **Caso 1: Reservar un turno**  
- **Actor**: Cliente  
- **Descripción**: Un cliente selecciona un servicio y reserva un turno disponible.  
- **Flujo principal**:  
  1. El cliente accede al sistema.  
  2. Selecciona un servicio.  
  3. Escoge una fecha y hora disponible.  
  4. Confirma la reserva.  
- **Precondiciones**: El cliente debe estar registrado.  
- **Postcondiciones**: El turno queda guardado en el sistema.  

(Otros 4 casos de uso similares)  

## Boceto inicial del diseño de clases  
![Diagrama de Clases](ruta-de-la-imagen.png)  
[Ver en línea](https://enlace-a-la-imagen.com)  
