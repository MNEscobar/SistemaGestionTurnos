# Herencia

## Descripción
La herencia es un principio de la programación orientada a objetos que permite que una clase (subclase) herede atributos y métodos de otra clase (superclase).
Este mecanismo promueve la reutilización de código y permite modelar relaciones jerárquicas entre clases, especialmente cuando varias clases comparten comportamientos comunes.

### ¿Por qué es importante?
Gracias a la herencia se evita duplicar el código, ya que los atributos y métodos comunes entre clases se definen solo una vez. Permite construir sistemas más organizados mediante jerarquía de clases claras, y facilita la extensibilidad del código, pudiendo crear nuevas funcionalidades extendiendo clases existentes.
### Relación con los Principios SOLID
- LSP: Las subclases deben poder reemplazar a sus clases base sin alterar el comportamiento esperado del programa. Esto es esencial para que la herencia sea segura y coherente.
- OCP: Heredar de una clase base permite agregar comportamiento nuevo sin modificar el código existente (abierto a extensióncerrado a modificación).
### Relación con patrones de diseño
Algunos patrones clásicos se basan en herencia, como:

- Template Method: define una estructura de algoritmo en la clase base y deja que las subclases redefinan partes específicas sin cambiar el flujo general.
- Decorator y Adapter: Ambos pueden usar herencia para modificar o adaptar comportamientos de forma dinámica, aunque es más frecuente combinarlos con composición.
- Factory Method: Este patrón usa herencia para que las subclases decidan qué instancia crear, delegando la lógica de creación de objetos.

---

## Ejemplo en el proyecto

![Imagen](https://drive.google.com/uc?export=view&id=1ZneY_9p6QGaH8BRN76ZrQKA6mlZpNFLj)

[Drive](https://drive.google.com/file/d/1ZneY_9p6QGaH8BRN76ZrQKA6mlZpNFLj/view?usp=sharing)

El sistema utiliza un principio de jerarquía para organizar los roles de usuario. Se define una entidad base, `Usuario`, que agrupa atributos (DNI, nombre, email, etc.) y comportamientos (registrar, iniciar sesión, ver perfil) comunes a todas las personas que interactúan con el sistema.
A partir de esta base, se especializan tres roles: `Paciente`, `Médico` y `Administrador`. Cada uno de estos roles "extiende" la funcionalidad del Usuario genérico.

Un `Paciente` es un `Usuario` que además posee una obraSocial y puede solicitarTurno o consultarHistorial.

Un `Médico` es un `Usuario` con una matricula, especialidad y agenda, capaz de modificarTurnos o atenderMedico.

Un `Administrador` es un Usuario que tiene un areaAdministrativa y puede eliminarUsuario o otorgarPermisos.

```java

class Perfil {
    private String nombrePerfil;
    private List<String> roles;

    public Perfil(String nombrePerfil, List<String> roles) {
        this.nombrePerfil = nombrePerfil;
        this.roles = roles;
    }
    public String getNombrePerfil() {
        return nombrePerfil;
    }
    public List<String> getRoles() {
        return roles;
    }
}

public abstract class Usuario {
    
    protected String dni;
    protected String nombre;
    protected String apellido;
    protected Date fechaNacimiento;
    protected String email;
    protected String password;
    protected Perfil perfil;

    public Usuario(String dni, String nombre, String apellido, Date fechaNacimiento, String email, String password, Perfil perfil) {
        this.dni = dni;
        this.nombre = nombre;
        this.apellido = apellido;
        this.fechaNacimiento = fechaNacimiento;
        this.email = email;
        this.password = password; 
        this.perfil = perfil;
    }

    public void registrar() {
        System.out.println("DEBUG: Usuario " + nombre + " " + apellido + " (DNI: " + dni + ") registrado.");
    }

    public boolean iniciarSesion(String email, String password) {
        if (this.email.equals(email) && this.password.equals(password)) {
            System.out.println("DEBUG: Inicio de sesión exitoso para " + nombre + " " + apellido + ".");
            return true;
        }
        System.out.println("DEBUG: Credenciales incorrectas para " + email + ".");
        return false;
    }

    public Perfil verificarPerfil() {
        return this.perfil;
    }

    public String getDni() { return dni; }
    public String getNombre() { return nombre; }
    public String getApellido() { return apellido; }
    public String getEmail() { return email; }
    public Perfil getPerfil() { return perfil; }

    public String toString() {
        return "Usuario [DNI=" + dni + ", Nombre=" + nombre + ", Apellido=" + apellido + ", Perfil=" + perfil.getNombrePerfil() + "]";
    }
}

class Paciente extends Usuario {
    private String obraSocial;

    public Paciente(String dni, String nombre, String apellido, Date fechaNacimiento, String email, String password, Perfil perfil, String obraSocial) {
        super(dni, nombre, apellido, fechaNacimiento, email, password, perfil); 
        this.obraSocial = obraSocial;
    }

    public void solicitarTurno(String medicoApellido, Date fecha, String hora) {
        System.out.println("DEBUG: Paciente " + getNombre() + " (" + obraSocial + ") solicita turno con Dr. " + medicoApellido + " para el " + fecha + " a las " + hora + ".");
    }

    public void consultarHistorial() {
        System.out.println("DEBUG: Paciente " + getNombre() + " consulta su historial médico.");
    }

    public String getObraSocial() {
        return obraSocial;
    }

    public String toString() {
        return "Paciente [DNI=" + getDni() + ", Nombre=" + getNombre() + ", Obra Social=" + obraSocial + ", Perfil=" + getPerfil().getNombrePerfil() + "]";
    }
}

class Medico extends Usuario {
    private String matricula;
    private String especialidad;

    public Medico(String dni, String nombre, String apellido, Date fechaNacimiento, String email, String password, Perfil perfil, String matricula, String especialidad) {
        super(dni, nombre, apellido, fechaNacimiento, email, password, perfil);
        this.matricula = matricula;
        this.especialidad = especialidad;
    }

    public void modificarTurnos(String idTurno, Date nuevaFecha, String nuevaHora) {
        System.out.println("DEBUG: Dr. " + getApellido() + " (Matrícula: " + matricula + ") modifica turno ID " + idTurno + " a " + nuevaFecha + " " + nuevaHora + ".");
    }

    public void atenderTurno(String idTurnoPaciente) {
        System.out.println("DEBUG: Dr. " + getApellido() + " atiende el turno del paciente " + idTurnoPaciente + ".");
    }


    public String getMatricula() { return matricula; }
    public String getEspecialidad() { return especialidad; }

}

class Administrador extends Usuario {
    private String areaAdministrativa;

    public Administrador(String dni, String nombre, String apellido, Date fechaNacimiento, String email, String password, Perfil perfil, String areaAdministrativa) {
        super(dni, nombre, apellido, fechaNacimiento, email, password, perfil);
        this.areaAdministrativa = areaAdministrativa;
    }

    public void verEstadisticas() {
        System.out.println("DEBUG: Administrador " + getNombre() + " (" + areaAdministrativa + ") visualiza estadísticas del sistema.");
    }

    public void eliminarUsuario(String dniUsuario) {
        System.out.println("DEBUG: Administrador " + getNombre() + " elimina usuario con DNI: " + dniUsuario + ".");
    }

    public void otorgarPermisos(Usuario usuarioObjetivo, List<String> nuevosPermisos) {
        System.out.println("DEBUG: Administrador " + getNombre() + " otorga permisos a " + usuarioObjetivo.getNombre() + ". Permisos: " + nuevosPermisos + ".");

        if (usuarioObjetivo.getPerfil() != null) {
            usuarioObjetivo.getPerfil().getRoles().addAll(nuevosPermisos);
        }
    }


    public String getAreaAdministrativa() {
        return areaAdministrativa;
    }
}

```
