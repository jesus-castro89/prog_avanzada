# 13. Creando los paneles

Para efecto de nuestro juego, crearemos una clase que hederá de `JPanel` y que nos permitirá personalizar la apariencia
de los paneles de la interfaz de usuario.

## Actualizando el JFrame

Para esta actualización deberemos de crear un JDesktopPane que nos permitirá colocar los paneles de la interfaz de
usuario.

```java
package rpg.gui;

import rpg.gui.buttons.BaseButton;
import rpg.gui.internalFrames.CristalFrame;
import rpg.gui.internalFrames.StatusFrame;
import rpg.gui.panels.BottomPanel;
import rpg.gui.panels.MiddlePanel;
import rpg.gui.panels.TopPanel;

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class MainWindow extends JFrame {
    private JPanel mainPanel;
    private JPanel topPanel;
    private JPanel middlePanel;
    private JPanel bottomPanel;
    private JButton button1;
    private JButton b2;
    private JButton b3;
    private JLabel exampleLabel;
    private JDesktopPane desktopPane;

    public MainWindow() {
        initComponents();
    }

    private void initComponents() {
        // Creamos un DesktopPane para poder agregar los componentes
        desktopPane = new JDesktopPane();
        // Hacemos que el tamaño del DesktopPane sea igual al
        // tamaño del panel principal
        desktopPane.setPreferredSize(mainPanel != null ?
                mainPanel.getPreferredSize() : null);
        // Definimos los Bounds del panel principal
        mainPanel.setBounds(0, 0, mainPanel.getPreferredSize().width,
                mainPanel.getPreferredSize().height);
        // Agregamos el panel principal al DesktopPane
        desktopPane.add(mainPanel, JLayeredPane.DEFAULT_LAYER);
        // Agregamos el panel principal a la ventana
        setContentPane(desktopPane);
        // Definimos el título de la ventana
        setTitle("RPG Game");
        // Definimos la operación por defecto al cerrar la ventana
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        // Tomamos el tamaño de los componentes
        pack();
        // Centramos la ventana
        setLocationRelativeTo(null);
        // Hacemos visible la ventana
        setVisible(true);
        // Definimos que la ventana no se pueda redimensionar
        setResizable(false);
    }

    public static void main(String[] args) {
        new MainWindow();
    }

    /**
     * Esta función permite personalizar los componentes de la ventana.
     * Como por ejemplo usar clases propias que extiendan de JPanel u otros componentes.
     * <p>
     * **IMPORTANTE**: Si marcamos algún componente en el editor de diseño como
     * "Custom Create", deberemos que especificar como se creara en esta función.
     */
    private void createUIComponents() {
        // Creamos el contenido personalizado de la ventana
        };
    }
}
```

Recuerda que todos los elementos a excepción del JDekstopPane deberán de ser creados ya sea en el editor de diseño o
manualmente dentro de la función `createUIComponents`.

## Clase `BackgroundPanel`

La clase `BackgroundPanel` es una clase que define un panel con un fondo personalizado. Esta clase es una subclase de la
clase `JPanel` y proporciona una implementación básica de un panel con un fondo personalizado. La clase
`BackgroundPanel` define un fondo personalizado utilizando una imagen de fondo y proporciona métodos para personalizar
la apariencia del panel.

```java
package rpg.gui.panels;

import rpg.utils.cache.ImageCache;

import javax.swing.*;
import java.awt.*;

/**
 * Clase abstracta que define un panel con una imagen de fondo.
 */
public abstract class BackgroundPanel extends JPanel {

    /**
     * Imagen de fondo del panel.
     */
    protected ImageIcon backgroundImage;
    /**
     * Dimensiones del panel.
     */
    protected Dimension dimension;

    /**
     * Constructor de la clase.
     */
    public BackgroundPanel() {
        init();
    }

    protected abstract void init();

    /**
     * Establece las dimensiones del panel.
     *
     * @param dimension Dimensiones del panel.
     */
    protected void setDimension(Dimension dimension) {
        this.dimension = dimension;
        setPreferredSize(dimension);
        setMinimumSize(dimension);
        setMaximumSize(dimension);
    }

    /**
     * Función que se encarga de pintar el panel.
     *
     * @param g Gráficos del panel.
     */
    @Override
    protected void paintComponent(Graphics g) {
        super.paintComponent(g);
        // Gestor en 2D para gestionar mejor las cosas
        Graphics2D g2d = (Graphics2D) g;
        // Activamos el antialiasing para que las imágenes se vean mejor
        g2d.setRenderingHint(RenderingHints.KEY_ANTIALIASING,
                RenderingHints.VALUE_ANTIALIAS_ON);
        g2d.setRenderingHint(RenderingHints.KEY_TEXT_ANTIALIASING,
                RenderingHints.VALUE_TEXT_ANTIALIAS_ON);
        // Activamos la interpolación bicúbica para que las imágenes se vean mejor
        g2d.setRenderingHint(RenderingHints.KEY_INTERPOLATION,
                RenderingHints.VALUE_INTERPOLATION_BICUBIC);
        // Dibujamos la imagen de fondo estirada a lo largo del panel.
        g2d.drawImage(backgroundImage.getImage(), 0, 0,
                dimension.width, dimension.height, null);
    }
}
```

## TopPanel, MiddlePanel y BottomPanel

Estas tres clases herearán de `BackgroundPanel` y nos permitirán personalizar la apariencia de los paneles de la
interfaz de usuario.

### Clase `TopPanel`

```java
package rpg.gui.panels;

import rpg.gui.WindowConstants;
import rpg.utils.cache.ImageCache;

import javax.swing.*;

public class TopPanel extends BackgroundPanel {

    @Override
    protected void init() {
        // Buscamos la imagen por ahora directamente en los directorios
        backgroundImage = new ImageIcon(ImageCache.addImage("topPanel",
                "panels/statusPanel.png"));
        setDimension(WindowConstants.TOP_DIMENSION);
        setBorder(WindowConstants.EMPTY_BORDER);
    }
}
```

### Clase `MiddlePanel`

```java
package rpg.gui.panels;

import rpg.gui.WindowConstants;
import rpg.utils.cache.ImageCache;

import javax.swing.*;

public class MiddlePanel extends BackgroundPanel {

    @Override
    protected void init() {
        // Buscamos la imagen por ahora directamente en los directorios
        backgroundImage = new ImageIcon(ImageCache.addImage("midPanel",
                "panels/mainBackground.png"));
        setDimension(WindowConstants.MIDDLE_DIMENSION);
        setBorder(WindowConstants.EMPTY_BORDER);
    }
}
```

### Clase `BottomPanel`

```java
package rpg.gui.panels;

import rpg.gui.WindowConstants;
import rpg.utils.cache.ImageCache;

import javax.swing.*;

public class BottomPanel extends BackgroundPanel {

    @Override
    protected void init() {
        // Buscamos la imagen por ahora directamente en los directorios
        backgroundImage = new ImageIcon(ImageCache.addImage("bottomPanel",
                "panels/battlePanel.png"));
        setDimension(WindowConstants.MIDDLE_DIMENSION);
        setBorder(WindowConstants.EMPTY_BORDER);
    }
}
```

## Uso de los paneles

Para poder usar estos paneles, recuerda actualizar la interfaz de dimensiones de la siguiente manera:

```java
package rpg.gui;

import javax.swing.border.EmptyBorder;
import java.awt.*;

/**
 * Constantes para las dimensiones de las ventanas.
 */
public interface WindowConstants {
    /**
     * Ancho de la ventana.
     */
    int WINDOW_WIDTH = 1500;
    /**
     * Alto de la parte superior de la ventana.
     */
    int TOP_HEIGHT = 150;
    /**
     * Alto de la parte media de la ventana.
     */
    int MIDDLE_HEIGHT = 320;
    /**
     * Alto de la parte inferior de la ventana.
     */
    int BOTTOM_HEIGHT = 350;
    /**
     * Margen simple.
     */
    int SIMPLE_MARGIN = 18;
    /**
     * Dimensión de la parte superior de la ventana.
     */
    Dimension TOP_DIMENSION = new Dimension(WINDOW_WIDTH, TOP_HEIGHT);
    /**
     * Dimensión de la parte media de la ventana.
     */
    Dimension MIDDLE_DIMENSION = new Dimension(WINDOW_WIDTH, MIDDLE_HEIGHT);
    /**
     * Dimensión de la parte inferior de la ventana.
     */
    Dimension BOTTOM_DIMENSION = new Dimension(WINDOW_WIDTH, BOTTOM_HEIGHT);
    /**
     * Borde vacío de margen simple. Que se puede usar para dar un margen a los paneles.
     */
    EmptyBorder EMPTY_BORDER = new EmptyBorder(SIMPLE_MARGIN, SIMPLE_MARGIN,
            SIMPLE_MARGIN, SIMPLE_MARGIN);
}
```

Recuerda que estas dimensiones y margen son sugeridos y que puedes cambiarlos en todo momento.