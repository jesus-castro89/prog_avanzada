# 10. Iniciando la GUI del juego

En esta lección, aprenderás a iniciar la interfaz gráfica de usuario (GUI) de tu juego en Java. La GUI es la parte de la
aplicación que interactúa con el usuario y le permite interactuar con el juego a través de elementos visuales como
botones, etiquetas, campos de texto, etc.

## Creando una ventana principal

Para iniciar la GUI de tu juego, primero debes crear una ventana principal donde se mostrarán los elementos de la
interfaz de usuario. Puedes utilizar la clase `JFrame` de la biblioteca de Java Swing para crear una ventana en una
aplicación de escritorio.

Para crear una ventana simple con `JFrame`, puedes seguir estos pasos:

1. Crea un nuevo paquete llamado `gui` dentro de `rpg`.
2. Crea una nueva `GUIForm` clase que extienda `JFrame` y defina los componentes de la interfaz de usuario en su
   constructor dentro de dicho paquete.
   ![new_gui.png](..%2Fimages%2Fnew_gui.png) {style="block"}
3. En el constructor de la clase `GUIForm`, configura el título de la ventana, su tamaño, la operación de cierre y otros
   atributos necesarios.
4. Nombra el panel principal de la ventana como `mainPanel`.
5. Establece el panel principal como el panel de contenido de la ventana utilizando el método `setContentPane`.
   ![component_panel_name.png](..%2Fimages%2Fcomponent_panel_name.png) {style="block"}
6. Crea una instancia de la clase `GUIForm` en el método `main` de la clase `Game` para mostrar la ventana principal.

A continuación, se muestra un ejemplo de cómo crear una ventana simple con `JFrame`:

```java
package rpg.gui;

import javax.swing.JFrame;

public class MainWindow extends JFrame {

   private JPanel mainPanel;

    public MainWindow() {
        setTitle("RPG Game");
        setSize(800, 600);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setContentPane(mainPanel);
        setVisible(true);
    }
    
    public static void main(String[] args) {
        new MainWindow();   
    }
}
```

En este ejemplo, se crea una instancia de `JFrame` con el título "RPG Game", se establece su tamaño en 800x600 píxeles,
se configura la operación de cierre para salir de la aplicación cuando se cierra la ventana y se hace visible la
ventana.

## Personalizando la ventana

Genera una interfaz para guardar las constantes como el tamaño de la ventana y el margen interno de la ventana. Esto
facilitará la personalización de la ventana en el futuro.

```java
package rpg.gui;

plubic interface WindowConstants {

   Dimension WINDOW_SIZE = new Dimension(1280, 720);
   Insets WINDOW_INSETS = new Insets(10, 10, 10, 10);
}
```

Luego, puedes utilizar estas constantes en la clase `MainWindow` para personalizar la ventana.

```java
package rpg.gui;

import javax.swing.JFrame;

public class MainWindow extends JFrame implements WindowConstants {

    private JPanel mainPanel;

    public MainWindow() {
        setTitle("RPG Game");
        setSize(WINDOW_SIZE);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setContentPane(mainPanel);
        setVisible(true);
    }

    public static void main(String[] args) {
        new MainWindow();
    }
}
```

Al utilizar constantes para el tamaño de la ventana y el margen interno, puedes ajustar fácilmente estos valores en un
solo lugar y aplicar los cambios en toda la aplicación.

## Resumen

En esta lección, aprendiste a iniciar la interfaz gráfica de usuario (GUI) de tu juego en Java utilizando la clase
`JFrame` de la biblioteca de Java Swing. Creaste una ventana principal para mostrar los elementos de la interfaz de
usuario y personalizaste la ventana utilizando constantes para el tamaño y el margen interno. En la próxima lección,
aprenderás a agregar componentes a la ventana para crear una interfaz de usuario interactiva para tu juego.