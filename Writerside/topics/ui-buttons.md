# 15. Agregando los primeros botones

Para efectos de nuestro juego, deberemos de agregar al menos cuatro botones que nos permitirán interactuar con la
interfaz de usuario. Estos botones serán los siguientes:

1. **Botón de guardado**: Este botón nos permitirá guardar la partida en cualquier momento.
2. **Botón de salida**: Este botón nos permitirá salir del juego en cualquier momento.
3. **Botón de inventario**: Este botón nos permitirá acceder al inventario del personaje en cualquier momento.
4. **Botón de estadísticas**: Este botón nos permitirá acceder a las estadísticas del personaje en cualquier momento.

Para agregar estos botones, deberemos de crear una clase que herede de `JButton` y que nos permita personalizar la
apariencia de los botones. A continuación, se muestra el código de la clase `BaseButton`:

```java
package rpg.gui.buttons;

import rpg.utils.cache.ImageCache;

import javax.swing.*;

public class BaseButton extends JButton {

    public BaseButton(String text) {

        setText(text);
        // Agregamos los iconos a la caché de imágenes.
        setIcon(
                new ImageIcon(ImageCache.addImage("shopIdle", "icons/shopIdle.png")));
        setRolloverIcon(
                new ImageIcon(ImageCache.addImage("shopHover", "icons/shopHover.png")));
        // Establecemos el manger de UI.
        setUI(new HoverButtonUI());
    }
}
```

En este código, hemos creado una clase llamada `BaseButton` que hereda de `JButton`. En el constructor de la clase,
establecemos el texto del botón y agregamos los iconos a la caché de imágenes. Luego, establecemos el `UI` del botón
utilizando la clase `HoverButtonUI`.

La clase `HoverButtonUI` es una clase que nos permite personalizar la apariencia de los botones cuando el cursor del
ratón pasa sobre ellos. A continuación, se muestra el código de la clase `HoverButtonUI`, tomando en cuenta que para
efectos de este ejemplo, se dividen el botón en tres partes: el borde izquierdo, el centro y el borde derecho.

```java
package rpg.gui.buttons;

import rpg.utils.cache.FontCache;
import rpg.utils.cache.ImageCache;

import javax.swing.*;
import javax.swing.plaf.basic.BasicButtonUI;
import java.awt.*;

public class HoverButtonUI extends BasicButtonUI {

    protected int width;
    protected int height;
    protected ImageIcon[] parts;
    protected ImageIcon[] partsHover;

    @Override
    protected void installDefaults(AbstractButton b) {

        initParts();
        b.setFont(FontCache.addFont("M6X",
                "fonts/M6X.ttf").deriveFont(22.5f));
        b.setForeground(Color.BLACK);
        b.setDoubleBuffered(true);
        b.setOpaque(false);
        b.setBorderPainted(false);
        b.setFocusPainted(false);
        b.setContentAreaFilled(false);
        b.setIconTextGap(5);
        b.setCursor(new Cursor(Cursor.HAND_CURSOR));
        String text = b.getText();
        this.width = b.getFontMetrics(b.getFont()).stringWidth(text) + (5);
        this.height = 48;
    }

    @Override
    public Dimension getPreferredSize(JComponent c) {

        return new Dimension(Math.max(width + 54, 84), 48);
    }

    @Override
    public Dimension getMaximumSize(JComponent c) {
        return getPreferredSize(c);
    }

    @Override
    public Dimension getMinimumSize(JComponent c) {
        return getPreferredSize(c);
    }

    /**
     * Inicializa las partes del botón.
     * En sus estados normal y hover.
     */
    private void initParts() {
        //Inicializamos los arreglos de imágenes.
        parts = new ImageIcon[3];
        partsHover = new ImageIcon[3];
        // Agregamos las imágenes a la caché.
        ImageCache.addImage("userLeftSide", "buttons/idle/user/leftSide.png");
        ImageCache.addImage("userCenterSide", "buttons/idle/user/centerSide.png");
        ImageCache.addImage("userRightSide", "buttons/idle/user/rightSide.png");
        ImageCache.addImage("userHoverLeftSide", "buttons/hover/user/leftSide.png");
        ImageCache.addImage("userHoverCenterSide", "buttons/hover/user/centerSide.png");
        ImageCache.addImage("userHoverRightSide", "buttons/hover/user/rightSide.png");
        // Obtenemos las imágenes de la caché y las almacenamos en los arreglos correspondientes.
        parts[0] = ImageCache.getImageIcon("userLeftSide");
        parts[1] = ImageCache.getImageIcon("userCenterSide");
        parts[2] = ImageCache.getImageIcon("userRightSide");
        partsHover[0] = ImageCache.getImageIcon("userHoverLeftSide");
        partsHover[1] = ImageCache.getImageIcon("userHoverCenterSide");
        partsHover[2] = ImageCache.getImageIcon("userHoverRightSide");
    }

    @Override
    public void paint(Graphics g, JComponent c) {
        super.paint(g, c);
        Graphics2D g2d = (Graphics2D) g;
        AbstractButton button = (AbstractButton) c;
        g2d.setRenderingHint(RenderingHints.KEY_ANTIALIASING, RenderingHints.VALUE_ANTIALIAS_ON);
        ImageIcon[] images = button.getModel().isRollover() ? partsHover : parts;
        drawButtonParts(g2d, images);
        g2d.translate(-width - 27, 0);
        g2d.setColor(Color.WHITE);
        super.paint(g2d, c);
    }

    private void drawButtonParts(Graphics2D g2d, ImageIcon[] parts) {

        g2d.drawImage(parts[0].getImage(), 0, 0, null);
        g2d.translate(27, 0);
        g2d.drawImage(parts[1].getImage(), 0, 0,
                width, height, null);
        g2d.translate(width, 0);
        g2d.drawImage(parts[2].getImage(), 0, 0, null);
    }
}
```

En este código, hemos creado una clase llamada `HoverButtonUI` que hereda de `BasicButtonUI`. En esta clase, hemos
sobrescrito los métodos `installDefaults`, `getPreferredSize`, `getMaximumSize` y `getMinimumSize` para personalizar la
apariencia del botón. Además, hemos creado un método llamado `initParts` que inicializa las partes del botón en sus
estados normal y hover.

## Creando tus propios botones

Para crear tus propios botones, puedes seguir los siguientes pasos:

1. Crea objetos de tipo `JButton` y personalízalos según tus necesidades.
2. Utiliza la opción de `Custom Create` para personalizar la apariencia de los botones, haciendo que los mismo sean
   objetos de la clase `BaseButton`.

> **Nota**: Los botones personalizados pueden ser utilizados en cualquier parte de la interfaz de usuario, permitiéndote
> interactuar con el usuario de una forma más amigable y atractiva.

> **Nota**: Puedes heredar de BaseButton para crear botones con diferentes apariencias y comportamientos. Lo cual es más
> sencillo que crear un botón desde cero. Además de que posteriormente podrás reutilizar estos botones en otros
> proyectos. E inclusive agregar eventos a estos botones para que realicen acciones específicas.

## Usando los botones en la interfaz de usuario

Para usar los botones en la interfaz de usuario, puedes seguir los siguientes pasos:

1. Crea una instancia de la clase `BaseButton` y personalízala según tus necesidades.
2. Agrega un botón a un panel o a otro contenedor de la interfaz de usuario utilizando el método `add`.
3. Habilita el `Custom Create` para personalizar la apariencia de los botones.
4. Crea y personaliza tus bótones según tus necesidades desde la clase `MainWindow`.
   ```java
   private void createUIComponents() {
           topPanel = new TopPanel();
           middlePanel = new MiddlePanel();
           bottomPanel = new BottomPanel();
           button1 = new BaseButton("Button 1");
           b2 = new BaseButton("Tiendas");
           b3 = new BaseButton("Inventario");
   }
   ```

# Conclusión

En este tutorial, hemos aprendido cómo crear botones personalizados en una interfaz de usuario utilizando Java Swing.
Hemos creado una clase llamada `BaseButton` que hereda de `JButton` y nos permite personalizar la apariencia de los
botones. Además, hemos creado una clase llamada `HoverButtonUI` que hereda de `BasicButtonUI` y nos permite personalizar
la apariencia de los botones cuando el cursor del ratón pasa sobre ellos.