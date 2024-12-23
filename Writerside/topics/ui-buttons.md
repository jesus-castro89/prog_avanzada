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

import rpg.gui.ui.HoverButtonUI;
import rpg.utils.cache.ImageCache;

import javax.swing.*;

public abstract class BaseButton extends JButton {

    public BaseButton(String text) {

        setText(text);
        initIcons();
        setUI(new HoverButtonUI());
    }

    protected abstract void initIcons();
}
```

En este código, hemos creado una clase llamada `BaseButton` que hereda de `JButton`. En esta clase, hemos sobrescrito
el constructor para inicializar el texto del botón y llamar al método `initIcons` para inicializar los iconos del 
botón.

> **Nota**: La clase `BaseButton` es una clase abstracta que nos permite personalizar la apariencia de los botones. 
> En este ejemplo, hemos creado un constructor que inicializa el texto del botón y llama al método `initIcons` para
> inicializar los iconos del botón. Además, hemos utilizado la clase `HoverButtonUI` para personalizar la apariencia
> de los botones cuando el cursor del ratón pasa sobre ellos.

La clase `HoverButtonUI` es una clase que nos permite personalizar la apariencia de los botones cuando el cursor del
ratón pasa sobre ellos. A continuación, se muestra el código de la clase `HoverButtonUI`, tomando en cuenta que para
efectos de este ejemplo, se dividen el botón en tres partes: el borde izquierdo, el centro y el borde derecho.

```java
package rpg.gui.ui;

import rpg.gui.UIConstants;
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
        b.setFont(UIConstants.FONT.deriveFont(Font.PLAIN, 24));
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
    protected void initParts() {
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

    protected void drawButtonParts(Graphics2D g2d, ImageIcon[] parts) {

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

> **Nota**: En este ejemplo, hemos dividido el botón en tres partes: el borde izquierdo, el centro y el borde derecho.
> En el método `drawButtonParts`, dibujamos las partes del botón utilizando las imágenes correspondientes.
> En el método `paint`, verificamos si el cursor del ratón pasa sobre el botón y dibujamos las partes del botón
> correspondientes.

> **Nota**: En este ejemplo, hemos utilizado la clase `ImageCache` para almacenar las imágenes en la caché y la clase
> `FontCache` para almacenar las fuentes en la caché. Estas clases nos permiten cargar las imágenes y las fuentes de
> forma eficiente y reutilizarlas en toda la aplicación. Así que recuerda que deberás usar tus propias imágenes y
> fuentes para personalizar la apariencia de los botones y de tu interfaz de usuario.

## Las imágenes de los botones

El ejemplo anterior hace uso de las siguientes imágenes para personalizar la apariencia de los botones:

* ![leftSide.png](..%2Fimages%2FleftSide.png)
* ![centerSide.png](..%2Fimages%2FcenterSide.png)
* ![rightSide.png](..%2Fimages%2FrightSide.png)

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

Veamos un ejemplo de cómo crear un botón personalizado:

```java
package rpg.gui.buttons;

public class AttackButton extends UserButton{

        public AttackButton() {
            super("Atacar");
        }
}
```

En este ejemplo, hemos creado una clase llamada `AttackButton` que hereda de `UserButton`. En esta clase, hemos
sobrescrito el constructor para inicializar el texto del botón con el valor "Atacar".

Por su lado `UserButton` es una clase que hereda de `BaseButton` y que nos permite personalizar la apariencia de los
botones. A continuación, se muestra el código de la clase `UserButton`:

```java
package rpg.gui.buttons;

import rpg.gui.ui.UserHoverUI;

public abstract class UserButton extends BaseButton {

    public UserButton(String text) {
        super(text);
        // Agregamos los iconos a la caché de imágenes.
        setIcon(null);
        setRolloverIcon(null);
        setUI(new UserHoverUI());
    }

    @Override
    protected void initIcons() {
        // No se inicializan iconos.
    }
}
```

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
           button1 = new AttackButton();
   }
   ```

## Conclusión

En este tutorial, hemos aprendido cómo crear botones personalizados en una interfaz de usuario utilizando Java Swing.
Hemos creado una clase llamada `BaseButton` que hereda de `JButton` y nos permite personalizar la apariencia de los
botones. Además, hemos generado una clase llamada `HoverButtonUI` que hereda de `BasicButtonUI` y nos permite
personalizar la apariencia de los botones cuando el cursor del ratón pasa sobre ellos.