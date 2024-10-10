# El uso de ventanas con JFrame

En Java, una ventana es un contenedor que contiene los componentes de la interfaz de usuario, como botones, etiquetas,
campos de texto, etc. La clase `JFrame` es una clase de la biblioteca de Java Swing que se utiliza para crear y mostrar
ventanas en una aplicación de escritorio.

A continuación, se muestra un ejemplo de cómo crear una ventana simple con `JFrame`:

```java
import javax.swing.JFrame;

public class SimpleWindow {

    public static void main(String[] args) {
        JFrame frame = new JFrame("Simple Window");
        frame.setSize(400, 300);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setVisible(true);
    }

}
```

En este ejemplo, se crea una instancia de `JFrame` con el título "Simple Window", se establece su tamaño en 400x300
píxeles, se configura la operación de cierre para salir de la aplicación cuando se cierra la ventana y se hace visible
la ventana.

Puedes personalizar la ventana agregando componentes como botones, etiquetas, campos de texto, etc., y ajustando su
diseño y comportamiento según tus necesidades.

Es importante tener en cuenta que la clase `JFrame` es solo una de las muchas clases disponibles en la biblioteca de
Java Swing para crear interfaces de usuario en aplicaciones de escritorio. Puedes explorar otras clases y componentes
para crear interfaces más complejas y personalizadas.