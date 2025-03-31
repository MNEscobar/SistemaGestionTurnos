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

### Caso 1
   
| Caso de uso        | Registro de usuarios                   |
|--------------------|----------------------------------------|
| **Actores**        | Pacientes, Médicos y Administrativos   |
| **Descripción**    | El administrativo registra los datos   |
|                    | al centro de salud y crea un usuario   |
| **flujo principal**| 1. El administrativo ingresa al sistema|
|                    | con sus credenciales                   |
|                    | 2. Selecciona "Registrar nuevo usuario"|
|                    | 3. Completa los datos del usuario      |
|                    | 4. Guarda la información del usuario   |
| **Precondiciones** | El usuario no debe estar registrado    |
|                    | en el sistema                          |
| **Postcondiciones**| El usuario queda registrado y puede    |
|                    | acceder al sistema según su rol        |
| **Extiende a**     | "Validar datos del usuario"            |
| **Hereda de**      |                                        |


### Caso 2

| **Caso de uso**    | Reservar un turno       |                         
|--------------------|-------------------------|
| **Actores**        | Cliente                 |
| **Descripción**    | El cliente seleeciona un|
|                    | servicio y reserva un   |
|                    | turno disponible        |
| **Flujo principal**| 1. El cliente accede    |  
|                    | al sistema              |
|                    | 2. Selecciona un servicio|
|                    | 3. Escoge una fecha y   |
|                    | hora disponible         |
|                    | 4. Confirma la reserva  |
| **Precondiciones** | El cliente debe estar   | 
|                    | registrado              |
|**Postcondiciones** | El turno queda guardado |
|                    | en el sistema           |
| **Extiende a**     | "Gestión de turnos"     |
| **Hereda de**      | "Registro de usuarios"  |

### Caso 3
| **Caso de uso**      | Notificación de Confirmación o Cancelación de Turno |
|--------------------- |-----------------------------------------------------|
| **Actores**          | Sistema                                             |
| **Descripción**      | El sistema notifica a los usuarios participes del   |
|                      | turno                                               |
| **Flujo Principal**  | 1. Un administrativo o paciente confirma o cancela un turno|
|                      | 2. El sistema procesa el cambio                     |
|                      | 3. Se envía una notificación automática al paciente |
|                      | y al médico por correo o mensaje                    |
|                      | 4. El usuario recibe y visualiza la notificación    |
| **Precondiciones**   | Debe existir un turno asignado en el sistema        |
| **Postcondición**    | Los usuarios quedan informados sobre la confirmación|
|                      | o cancelación del turno                             |
| **Extiende a**       | "Gestionar turnos"                                  |
| **Hereda de**       | "Reservar turno"                                    |

### Caso 4
| **Caso de uso**      | Almacenar Historial Médico                          |
|----------------------|-----------------------------------------------------|
| **Actor**            | Médico                                              |
| **Descripción**      | El médico proscribe sobre el historial del paciente |
| **Flujo Principal**  | 1. El médico accede al sistema con sus credenciales |
|                      | 2. Busca al paciente en la base de datos            |
|                      | 3. Selecciona la opción "Actualizar historial médico"|
|                      | 4. Ingresa diagnóstico, tratamiento y observaciones  |
|                      | 5. Guarda los cambios                                |
|                      | 6. El sistema almacena la información y la asocia    |
|                      |    al paciente                                       |
| **Precondición**     | El paciente debe estar registrado en el sistema     |
| **Postcondición**    | El historial médico queda actualizado y accesible   |
|                      | para futuras consultas                              |
| **Extienda a**       |                                                     |
| **Hereda de**        | "Gestionar datos de pacientes"                      |

---






## Boceto inicial del diseño de clases  
![Diagrama de Clases](https://viewer.diagrams.net/?tags=%7B%7D&lightbox=1&highlight=0000ff&edit=_blank&layers=1&nav=1&title=Diagrama%20sin%20t%C3%ADtulo.drawio&dark=auto#R%3Cmxfile%3E%3Cdiagram%20id%3D%22C5RBs43oDa-KdzZeNtuy%22%20name%3D%22Page-1%22%3E7V1bd5s4EP41Pmf3wTncHT8mzqXdTXqyTXfb7psCsq0WI6%2FASdxfv%2BJqkGQsEzA24bQ9RQIE6BvNjD7NyAN9sni9JWA5v8cOdAea4rwO9KuBpqmKqdD%2Fwpp1UjPStbhmRpCT1G0qHtEvmN6a1K6QA%2F3ChQHGboCWxUobex60g0IdIAS%2FFC%2BbYrf41CWYQa7i0QYuX%2FsVOcE8rj3XRpv6DxDN5umTVWscn1mA9OLkS%2Fw5cPBLrkq%2FHugTgnEQHy1eJ9ANey%2Ftl68f11%2Fdu5%2FW7R9%2F%2Bf%2BBvy%2F%2F%2FPLpn2Hc2M0%2Bt2SfQKAXVG7618%2FpzYd%2FjB%2Fflg83f70otxdPfwyTW5Rn4K6S%2FvrbXwGCcPLJwTrtR%2F8FLVzg0dLlFHvBY3JGpWXgoplHj236epDQimdIAkQhuEhOBHhJa%2B05cp07sMar8CP8ANg%2F09LlHBP0izYL3KRNepoEiTRpVuGKx%2FBOWq3QWgJ9es1D2jNqVnUH%2FCC5xsauC5Y%2BespeeAHIDHmXOAjwIm0IrzwHOkkpgzoqBAT%2FzIQnvH%2BKXHeCXUyirtGnU2jZdnZl7owS%2FQnPJL13k7vTgVOwcsOvl8Q3kYOwd%2BFrTroTvG8hXsCArOklyVltlOCbDt6k%2BLIZCOo4qZvnBoGmWskATAbfLGs6e9pnOliBN6N9unmcxjxOEzzPEj2PeRxwqRx5IICXISp%2BXqzpQe5LN1WRsO8h%2BCon%2BJ%2Fw4olATu5pVwc5GXfhNNgq4f4S2Mib3UXXXBmbms%2FJt4ZVmN47dSPpmiPHgV4kfQEIQCygocgtMfKCqDPMS%2FqXdtlEOTMHJn2hCS2rmzL9G15Oggn2qPgBFEkQpNL%2FAn2xbJUqgt2ytS5itlOWSkSpAOq%2BCGocglefPnYOvhK9NA8WbnLYFMim1jLIOgfyDbTnIHRIQsXjUXgWiH40b6964N8C%2FOj8cMB7%2F36fP5Lpuf5wvR5%2BsH4ocHQv0M%2BT0Pjb7xxpDkFZ8LcirSpG21DrHKTQoT58UqQ9N8cz7AH3elPLdNrmmjsc4hx5aT9gEKwTFxKsqOBk%2FRmeha8o%2BJY7%2Fh42RRGLS1evSctRYV3AIHy5CgjQD8QrYsOSntDFSBHoggA9Fx9a4po9hLK5ccv0cdEtG6ZeYdoEdbVnMEjuys8gmIY0hfHvTKah%2BAO5hi4IAevcZcnY2frCmsk8x9DL38sUf%2BC263W99Hp6EL9xVYdzO7acQiPAh4OJPrhUQa%2FX6tVruuxkpynfxeAQ5yB2UTShzqklfrK5A%2F8FRTLSiAngXyL9N1Q5odB5odAFAuCCJ%2Bg%2BYB8FCIftk%2FhaRjDamnWopuS047whY2W2Yquoolh%2F2xiosPg9f25jrqJSTfYqtgslnaFtGYJvNFjDjCRgiYR9LdZQZRqy5CxWXUqfn6N%2BxuFNvz3QcRiyZfR4SP%2FdhzbgYuwgGyc1F84Ceb93ziY0pu2tA3qxwvczOag%2FeshGgDxCP9Sk3USyAQ0%2FbttuWxySX1bEw4OJNrhQOBx7Xvz0eHHGvBgiV1HIU1fjxVVmvqGfHy8vPuKEPyHc3qf6sqRFq4QWl4G2Nu11zgF4TXWG875ps%2FpxFjHjTeEs5hP4kXoPYwfyHQNdxbO0SoEWMeGHBZof0ZvZQw91jVALqfCDKu8xBzUH8XunjPbW1EIiUIRqDZSRONSAD7KhfTBFhLrbnRvB%2BTmQ0hykB1TKYkz59cl77KApBal7mDYGo4i0Oaxt5RXuBHg2dDuLYgNWU0TYHHYw8jQrhx70nIswmpSWnlwc8iSXtCohUtSYOndCFkLke%2FAWtuio2CvynBXy6wHQfcIv%2BaWAqIKeSMVmUCT3rfNBjt4fKmeKog3KOf6o9AAJon0ZkkxbZj1lxEme5y8b2cxCAi8RIgl441rAiOFOsjXoHQw%2Bv%2BjLLAXokqvgtQUc8rTiiQppXkSVHdJZXRCF%2BtpQj0gSxxUl0WTpR0NOEvcNo7CYcI00DqSuMAexmPO0xNbZak%2BdnyB1zowCVRRTLrL%2B7GiRo84tdgFX9nEtUOcaP8%2F7gPyAChkI7y2s8XbMt6yVi81UyOmQ7hof3cVh%2FN6Jm%2F1hleXYmyJuND6C6xG7yEZBOD1U4lXhrg3lxtC02p4mavt54HgZdfUbfOzMV1creNz7GfB8aLFsSFcprjs97ATzUKwKzqxai7OdLZFnJINW0dk2djQkHUrGNKQz7eDp1IeNzBw1fgEoRX0juJGLmtMIqf5JVTqrgJ4STzW2AZfU%2FZ1Fopx6kh7e%2BOXJ%2FFOT1w7pUEuSepP3GmQJgvL%2BZj3ilIY1pEJ6MOh4fnG4a%2FEu5yCwoPJ2WWaqlHkN5VDvN115m1wIWEixqMjrnXE9gpKuLKTNKg2ISkksbXFFoWTG0M%2Bdm54772DKt1vjrTLLpEcPZdOxsxXMTqRji6WfX0%2B79pfQplNn5ABnm648cS97h4jtFXPfQlq2%2BP00Dskr5C%2Bxh55QN7GsMWilCuKHzNEWvx9P%2BXIYd5z8aABW2QzsphKdBK7rRUCntJCkDqzfuZHcGJjnbWtlnbevUYbRMfmVutL7lZX8SsviHMves8wkv0%2FDraLQ9HIyVza5mp0%2F16fQ%2BHy7Gf1m2lmARMR8b52kwRxJgtmcdeKZeQJnKOwFsm0%2Fuh7NLWiO2%2FY10jF%2FmpFO8auW5szvY6IbCETalRwvuzSiMtumGKwzUFMcErs9S7r9SqPbrRi8w%2Fs5Vil4S5pUz6ienuc7YkPpLFPOEeUGzUln8opHAE%2FEdTZvrLoxNY4nski83wxvTFM91nu40jC2nq1rSMSe9LPQfWGVzc1tiiM1eOYbzOjMBZB0jHZuiAry%2BxoAVsSXHlbtivaHDqL8PhtFG%2FbpR8Wd9h5kRQ9SZydBsmGK78CDTK1mfik35NjoU3tKRqAujtiL5OPT76Hngx%2F9VEAaxNZ9SLNfyWgA1rZ9SJNfyIDeMwKkqwO0Jg9yB6zte5B81DYH5fGy4Onu6MqZrp8P8jukK6o%2BKNsjPSyI09ErcuoS%2B6Zvk4UGyHd9ZBX9Rck90LmGjHSzodRHaIh9Z3d%2F14pZwPx7MRmXxiHYelNi46PjHyzFnxJQRqO9B8omzX6QT7I%2FU01jUJ5oX7INRC3jrnRno515%2B7HvdJABqjETLMuId9GoNEhN5ge0RuzuE3UtkTHpTkbNqfpCUFJNdhx7mcvtJNGcDbEEsrzPRtTSYvsmryJ9y3xKKvIDuOB3aO3ZqNNjo9gf7Bvq0rE51fZXOKVIPovnZPvgILGCON70EIvnFDsartd0WsgOpFtPC7F4znH3EkoP%2BptAb%2F1n%2Byyeo9wRdtUj%2FibE2%2F%2F5PqtP%2F2oCV9kI%2B6Z46RE%2F05gQ2MdjV0CybaU8Evz2YAhllzcwagJI2d%2BYKkuqehuQvHW97ZNeKqI5bh1NfoUoQzPbOLCjXlNjsGab%2B7QHK7%2Bg2%2F15T3N4mrJ4NmY9Rxxah6TJ1TNFzSrSXcENa9DuclBpkvnO5aBRQxw6LRKMgzztSMByfo8dGF7xPw%3D%3D%3C%2Fdiagram%3E%3C%2Fmxfile%3E)  
[Ver en línea](https://viewer.diagrams.net/?tags=%7B%7D&lightbox=1&highlight=0000ff&edit=_blank&layers=1&nav=1&title=Diagrama%20sin%20t%C3%ADtulo.drawio&dark=auto#R%3Cmxfile%3E%3Cdiagram%20id%3D%22C5RBs43oDa-KdzZeNtuy%22%20name%3D%22Page-1%22%3E7V1bd5s4EP41Pmf3wTncHT8mzqXdTXqyTXfb7psCsq0WI6%2FASdxfv%2BJqkGQsEzA24bQ9RQIE6BvNjD7NyAN9sni9JWA5v8cOdAea4rwO9KuBpqmKqdD%2Fwpp1UjPStbhmRpCT1G0qHtEvmN6a1K6QA%2F3ChQHGboCWxUobex60g0IdIAS%2FFC%2BbYrf41CWYQa7i0QYuX%2FsVOcE8rj3XRpv6DxDN5umTVWscn1mA9OLkS%2Fw5cPBLrkq%2FHugTgnEQHy1eJ9ANey%2Ftl68f11%2Fdu5%2FW7R9%2F%2Bf%2BBvy%2F%2F%2FPLpn2Hc2M0%2Bt2SfQKAXVG7618%2FpzYd%2FjB%2Fflg83f70otxdPfwyTW5Rn4K6S%2FvrbXwGCcPLJwTrtR%2F8FLVzg0dLlFHvBY3JGpWXgoplHj236epDQimdIAkQhuEhOBHhJa%2B05cp07sMar8CP8ANg%2F09LlHBP0izYL3KRNepoEiTRpVuGKx%2FBOWq3QWgJ9es1D2jNqVnUH%2FCC5xsauC5Y%2BespeeAHIDHmXOAjwIm0IrzwHOkkpgzoqBAT%2FzIQnvH%2BKXHeCXUyirtGnU2jZdnZl7owS%2FQnPJL13k7vTgVOwcsOvl8Q3kYOwd%2BFrTroTvG8hXsCArOklyVltlOCbDt6k%2BLIZCOo4qZvnBoGmWskATAbfLGs6e9pnOliBN6N9unmcxjxOEzzPEj2PeRxwqRx5IICXISp%2BXqzpQe5LN1WRsO8h%2BCon%2BJ%2Fw4olATu5pVwc5GXfhNNgq4f4S2Mib3UXXXBmbms%2FJt4ZVmN47dSPpmiPHgV4kfQEIQCygocgtMfKCqDPMS%2FqXdtlEOTMHJn2hCS2rmzL9G15Oggn2qPgBFEkQpNL%2FAn2xbJUqgt2ytS5itlOWSkSpAOq%2BCGocglefPnYOvhK9NA8WbnLYFMim1jLIOgfyDbTnIHRIQsXjUXgWiH40b6964N8C%2FOj8cMB7%2F36fP5Lpuf5wvR5%2BsH4ocHQv0M%2BT0Pjb7xxpDkFZ8LcirSpG21DrHKTQoT58UqQ9N8cz7AH3elPLdNrmmjsc4hx5aT9gEKwTFxKsqOBk%2FRmeha8o%2BJY7%2Fh42RRGLS1evSctRYV3AIHy5CgjQD8QrYsOSntDFSBHoggA9Fx9a4po9hLK5ccv0cdEtG6ZeYdoEdbVnMEjuys8gmIY0hfHvTKah%2BAO5hi4IAevcZcnY2frCmsk8x9DL38sUf%2BC263W99Hp6EL9xVYdzO7acQiPAh4OJPrhUQa%2FX6tVruuxkpynfxeAQ5yB2UTShzqklfrK5A%2F8FRTLSiAngXyL9N1Q5odB5odAFAuCCJ%2Bg%2BYB8FCIftk%2FhaRjDamnWopuS047whY2W2Yquoolh%2F2xiosPg9f25jrqJSTfYqtgslnaFtGYJvNFjDjCRgiYR9LdZQZRqy5CxWXUqfn6N%2BxuFNvz3QcRiyZfR4SP%2FdhzbgYuwgGyc1F84Ceb93ziY0pu2tA3qxwvczOag%2FeshGgDxCP9Sk3USyAQ0%2FbttuWxySX1bEw4OJNrhQOBx7Xvz0eHHGvBgiV1HIU1fjxVVmvqGfHy8vPuKEPyHc3qf6sqRFq4QWl4G2Nu11zgF4TXWG875ps%2FpxFjHjTeEs5hP4kXoPYwfyHQNdxbO0SoEWMeGHBZof0ZvZQw91jVALqfCDKu8xBzUH8XunjPbW1EIiUIRqDZSRONSAD7KhfTBFhLrbnRvB%2BTmQ0hykB1TKYkz59cl77KApBal7mDYGo4i0Oaxt5RXuBHg2dDuLYgNWU0TYHHYw8jQrhx70nIswmpSWnlwc8iSXtCohUtSYOndCFkLke%2FAWtuio2CvynBXy6wHQfcIv%2BaWAqIKeSMVmUCT3rfNBjt4fKmeKog3KOf6o9AAJon0ZkkxbZj1lxEme5y8b2cxCAi8RIgl441rAiOFOsjXoHQw%2Bv%2BjLLAXokqvgtQUc8rTiiQppXkSVHdJZXRCF%2BtpQj0gSxxUl0WTpR0NOEvcNo7CYcI00DqSuMAexmPO0xNbZak%2BdnyB1zowCVRRTLrL%2B7GiRo84tdgFX9nEtUOcaP8%2F7gPyAChkI7y2s8XbMt6yVi81UyOmQ7hof3cVh%2FN6Jm%2F1hleXYmyJuND6C6xG7yEZBOD1U4lXhrg3lxtC02p4mavt54HgZdfUbfOzMV1creNz7GfB8aLFsSFcprjs97ATzUKwKzqxai7OdLZFnJINW0dk2djQkHUrGNKQz7eDp1IeNzBw1fgEoRX0juJGLmtMIqf5JVTqrgJ4STzW2AZfU%2FZ1Fopx6kh7e%2BOXJ%2FFOT1w7pUEuSepP3GmQJgvL%2BZj3ilIY1pEJ6MOh4fnG4a%2FEu5yCwoPJ2WWaqlHkN5VDvN115m1wIWEixqMjrnXE9gpKuLKTNKg2ISkksbXFFoWTG0M%2Bdm54772DKt1vjrTLLpEcPZdOxsxXMTqRji6WfX0%2B79pfQplNn5ABnm648cS97h4jtFXPfQlq2%2BP00Dskr5C%2Bxh55QN7GsMWilCuKHzNEWvx9P%2BXIYd5z8aABW2QzsphKdBK7rRUCntJCkDqzfuZHcGJjnbWtlnbevUYbRMfmVutL7lZX8SsviHMves8wkv0%2FDraLQ9HIyVza5mp0%2F16fQ%2BHy7Gf1m2lmARMR8b52kwRxJgtmcdeKZeQJnKOwFsm0%2Fuh7NLWiO2%2FY10jF%2FmpFO8auW5szvY6IbCETalRwvuzSiMtumGKwzUFMcErs9S7r9SqPbrRi8w%2Fs5Vil4S5pUz6ienuc7YkPpLFPOEeUGzUln8opHAE%2FEdTZvrLoxNY4nski83wxvTFM91nu40jC2nq1rSMSe9LPQfWGVzc1tiiM1eOYbzOjMBZB0jHZuiAry%2BxoAVsSXHlbtivaHDqL8PhtFG%2FbpR8Wd9h5kRQ9SZydBsmGK78CDTK1mfik35NjoU3tKRqAujtiL5OPT76Hngx%2F9VEAaxNZ9SLNfyWgA1rZ9SJNfyIDeMwKkqwO0Jg9yB6zte5B81DYH5fGy4Onu6MqZrp8P8jukK6o%2BKNsjPSyI09ErcuoS%2B6Zvk4UGyHd9ZBX9Rck90LmGjHSzodRHaIh9Z3d%2F14pZwPx7MRmXxiHYelNi46PjHyzFnxJQRqO9B8omzX6QT7I%2FU01jUJ5oX7INRC3jrnRno515%2B7HvdJABqjETLMuId9GoNEhN5ge0RuzuE3UtkTHpTkbNqfpCUFJNdhx7mcvtJNGcDbEEsrzPRtTSYvsmryJ9y3xKKvIDuOB3aO3ZqNNjo9gf7Bvq0rE51fZXOKVIPovnZPvgILGCON70EIvnFDsartd0WsgOpFtPC7F4znH3EkoP%2BptAb%2F1n%2Byyeo9wRdtUj%2FibE2%2F%2F5PqtP%2F2oCV9kI%2B6Z46RE%2F05gQ2MdjV0CybaU8Evz2YAhllzcwagJI2d%2BYKkuqehuQvHW97ZNeKqI5bh1NfoUoQzPbOLCjXlNjsGab%2B7QHK7%2Bg2%2F15T3N4mrJ4NmY9Rxxah6TJ1TNFzSrSXcENa9DuclBpkvnO5aBRQxw6LRKMgzztSMByfo8dGF7xPw%3D%3D%3C%2Fdiagram%3E%3C%2Fmxfile%3E)  
