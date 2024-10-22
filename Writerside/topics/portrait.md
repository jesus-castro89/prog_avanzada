# 16. El retrato del personaje

Para poder mostrar el retrato del personaje en la interfaz de usuario, deberemos de crear una clase que herede de
`JPanel` y que nos permita personalizar la apariencia del retrato. A continuación, se muestra el código de la clase
`PortraitLabel` que permite heredar de la clase `JLabel` y personalizar la apariencia del retrato del personaje:

```java
package rpg.gui.labels;

import rpg.gui.ui.LabelUI;
import rpg.utils.cache.ImageCache;

import javax.swing.*;
import java.awt.*;

public class PortraitLabel extends JLabel {

    protected ImageIcon icon;

    public PortraitLabel() {
        initComponents();
        setUI(new LabelUI(getPreferredSize(), icon));
    }

    public void initComponents() {
        ImageCache.addImage("portrait",
                "player/portrait.png");
        icon = ImageCache.getImageIcon("portrait");
        setPreferredSize(
                new Dimension(icon.getIconWidth(),
                        icon.getIconHeight()));
        setIcon(icon);
    }

    @Override
    public void paintComponent(Graphics g) {

        Graphics2D g2d = (Graphics2D) g;
        g2d.setRenderingHint(RenderingHints.KEY_ANTIALIASING, RenderingHints.VALUE_ANTIALIAS_ON);
        g2d.drawImage(icon.getImage(), 0, 0,
                getPreferredSize().width,
                getPreferredSize().height, this);
    }
}
```

En este código, hemos creado una clase llamada `PortraitLabel` que hereda de `JLabel`. En el constructor de la clase,
inicializamos los componentes y establecemos el `UI` del retrato utilizando la clase `LabelUI`. La clase `LabelUI` es
una clase que nos permite personalizar la apariencia de los componentes `JLabel` en la interfaz de usuario.

## La clase `LabelUI`

La clase `LabelUI` es una clase auxiliar que se encarga de personalizar la apariencia de los componentes `JLabel`. Aquí
tienes un ejemplo de cómo implementar la clase `LabelUI`:

```java
package rpg.gui.ui;

import javax.swing.*;
import javax.swing.plaf.basic.BasicLabelUI;
import java.awt.*;

public class LabelUI extends BasicLabelUI {

    private Dimension size;
    ImageIcon icon;

    public LabelUI(Dimension size, ImageIcon icon) {

        this.size = size;
        this.icon = icon;
    }

    @Override
    protected void installDefaults(JLabel c) {

        c.setOpaque(false);
        c.setBorder(null);
    }
}
```

En este código, hemos creado una clase llamada `LabelUI` que hereda de `BasicLabelUI`. En el constructor de la clase,
establecemos el tamaño del componente y el icono que se mostrará en el componente. Luego, sobrescribimos el método
`installDefaults` para establecer algunas propiedades del componente, como el color de fondo y el borde.

Con estas clases, podremos personalizar la apariencia del retrato del personaje en la interfaz de usuario y mostrarlo
de forma adecuada en nuestra aplicación.

### MainWindow

En nuestra clase MainWindow deberemos de agregar el retrato del personaje a la interfaz de usuario. A continuación, se
muestra un ejemplo de cómo agregar el retrato del personaje a la ventana principal de la aplicación:

```java
    private void createUIComponents() {
        topPanel = new TopPanel();
        middlePanel = new MiddlePanel();
        bottomPanel = new BottomPanel();
        button1 = new BaseButton("Button 1");
        b2 = new BaseButton("Tiendas");
        b3 = new BaseButton("Inventario");
        atacarButton = new AttackButton();
        habilidadesButton = new SkillPanelButton();
        huirButton = new FleeButton();
        exampleLabel = new PortraitLabel();
    }
```

Recuerde que deberá de agregar el retrato del personaje a la caché de imágenes para poder mostrarlo en la interfaz de
usuario. Además, deberá de definir las dimensiones y la posición del retrato en la ventana principal de la aplicación.

Con estos pasos, podremos mostrar el retrato del personaje en la interfaz de usuario y personalizar su apariencia de
acuerdo a nuestras necesidades.