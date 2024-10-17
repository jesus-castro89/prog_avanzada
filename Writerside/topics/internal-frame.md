# Las ventanas internas

La clase `JInternalFrame` es una clase que representa una ventana interna en una aplicación de escritorio. Es una clase
que hereda de la clase `JComponent` y proporciona una forma de mostrar contenido dentro de una ventana interna que se
puede mover, redimensionar y minimizar.

## Características de la clase JInternalFrame

- **Contenedor de contenido**: Permite mostrar contenido dentro de una ventana interna.
- **Movimiento y redimensionamiento**: Permite mover y redimensionar la ventana interna.
- **Minimización y restauración**: Permite minimizar y restaurar la ventana interna.
- **Personalización de la apariencia**: Permite personalizar la apariencia de la ventana interna con títulos, iconos y
  botones de control.
- **Interacción con la ventana interna**: Permite la interacción con la ventana interna mediante eventos de ratón y
  teclado.
- **Diseño de aplicaciones de escritorio**: Es ideal para el diseño de aplicaciones de escritorio con múltiples ventanas
  internas.
- **Facilidad de uso**: Es fácil de usar y permite la creación de aplicaciones de escritorio con una interfaz gráfica
  intuitiva.
- **Flexibilidad**: Permite la personalización de la apariencia y el comportamiento de las ventanas internas.
- **Administración de ventanas internas**: Permite la gestión de múltiples ventanas internas en una aplicación de
  escritorio.

## Creación de un JInternalFrame

Para crear un `JInternalFrame`, puedes hacerlo de la siguiente manera:

```java
import javax.swing.*;

public class MyInternalFrame extends JInternalFrame {

    public MyInternalFrame() {
        super("Internal Frame", true, true, true, true);
        setSize(300, 200);
        setVisible(true);
    }

    public static void main(String[] args) {
        JFrame frame = new JFrame("Internal Frame Example");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setSize(800, 600);
        frame.setLocationRelativeTo(null);

        JDesktopPane desktop = new JDesktopPane();
        frame.setContentPane(desktop);

        MyInternalFrame internalFrame = new MyInternalFrame();
        desktop.add(internalFrame);

        frame.setVisible(true);
    }
}
```

En este ejemplo, creamos una clase `MyInternalFrame` que hereda de `JInternalFrame` y configuramos el título, la
resizabilidad, la maximización, la minimización y la cierre de la ventana interna. Luego, creamos un `JFrame` que
contiene un `JDesktopPane` y agregamos la ventana interna al `JDesktopPane`.

## Métodos útiles de la clase JInternalFrame

* `setTitle(String title)`: Establece el título de la ventana interna.
* `setResizable(boolean resizable)`: Establece si la ventana interna es redimensionable.
* `setMaximizable(boolean maximizable)`: Establece si la ventana interna es maximizable.
* `setIconifiable(boolean iconifiable)`: Establece si la ventana interna es minimizable.
* `setClosable(boolean closable)`: Establece si la ventana interna es cerrable.
* `setSize(int width, int height)`: Establece el tamaño de la ventana interna.
* `setVisible(boolean visible)`: Establece la visibilidad de la ventana interna.
* `setLocation(int x, int y)`: Establece la posición de la ventana interna.
* `toFront()`: Coloca la ventana interna en la parte delantera.
* `toBack()`: Coloca la ventana interna en la parte trasera.
* `dispose()`: Libera los recursos asociados con la ventana interna.
* `getContentPane()`: Devuelve el contenedor de contenido de la ventana interna.
* `getDesktopPane()`: Devuelve el `JDesktopPane` que contiene la ventana interna.
* `isSelected()`: Devuelve si la ventana interna está seleccionada.

Estos son solo algunos de los métodos que se pueden utilizar para personalizar y gestionar una ventana interna en una
aplicación de escritorio. La clase `JInternalFrame` proporciona una serie de métodos adicionales que permiten
personalizar diferentes aspectos de la apariencia y el comportamiento de las ventanas internas.