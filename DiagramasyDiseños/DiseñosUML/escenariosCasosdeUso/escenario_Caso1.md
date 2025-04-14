# Registrar Nuevo Usuario
## Descripción
Este caso de uso permite que un nuevo usuario se registre en el sistema. El sistema almacena sus datos personales básicos como nombre, correo electrónico, contraseña, tipo de usuario (paciente o médico), entre otros, y le asigna un ID único.
## Escenario principal
 - Una persona accede al formulario de registro
 - Completa sus datos personales
 - El sistema valida la información ingresada
 - Si es válida, crea una cuenta de usuario y le envía una confirmación
## Condiciones:
 - Precondiciones:
     El usuario no debe estar registrado, y debe cumplir con las normas de registro (correo valido, contraseña segura)
 - Poscondición:
     El usuario queda registrado en el sistema y puede iniciar sesión según su rol asignado.

 ![](Escenario_1.png)
