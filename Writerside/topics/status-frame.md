# 27. La ventana de estado

Una parte importante del juego es saber cual es estatus del jugador, desde su ataque, defensa, hasta su armamento.

## La ventana de estado

Para la ventana de estado, vamos a utilizar un JInternalFrame que se mostrará en el centro de la ventana principal. Este
JInternalFrame se llamará `StatusFrame` y se ubicará en el centro de la ventana principal.

Para crear la ventana de estado, vamos a seguir los siguientes pasos:

1. Crearemos un JInternalFrame llamado `StatusFrame` que contendrá la información del jugador, como su ataque, defensa,
   armamento, etc.
2. En el JInternalFrame, agregaremos etiquetas para mostrar la información del jugador, como su ataque, defensa,
   armamento, etc.
3. Cambiaremos el tamaño del JInternalFrame a tu gusto, pero asegúrate de que sea lo suficientemente grande para mostrar
   toda la información del jugador.
4. Agregaremos un botón de cierre en la esquina superior derecha del JInternalFrame para cerrar la ventana de estado.
5. Cambiaremos el título del JInternalFrame a "Estado del jugador".
6. Cambiaremos el color de fondo del JInternalFrame a un color oscuro para que resalte sobre el fondo de la ventana
   principal.
7. Cambiaremos el color de las etiquetas a blanco para que se vean claramente sobre el fondo oscuro del JInternalFrame.
8. Agregaremos un borde al JInternalFrame para que se vea claramente en la ventana principal.
9. Agregaremos un método para actualizar la información del jugador en la ventana de estado.
10. Agregaremos un método para mostrar la ventana de estado en la ventana principal.
11. Agregaremos un método para ocultar la ventana de estado en la ventana principal.

> **Nota:** Recuerda que el JInternalFrame se creará como una ventana de interfaz mediante el editor de formularios de
> IntelliJ IDEA.

Con estos cambios, hemos creado la ventana de estado que se mostrará en el centro de la ventana principal. En esta
ventana de estado, se mostrará la información del jugador, como su ataque, defensa, armamento, etc.

> **Nota:** La ventana de estado debe tener un tamaño adecuado para que se muestre correctamente la información del
> jugador.

## Ejemplo de ventana de estado

Aquí tienes un ejemplo de cómo se vería la ventana de estado en la ventana principal:



En este ejemplo, la ventana de estado muestra la información del jugador, como su ataque, defensa, armamento, etc. La
ventana de estado se encuentra en el centro de la ventana principal y se puede cerrar haciendo clic en el botón de
cierre en la esquina superior derecha.

La clase `StatusFrame` es una clase que representa la ventana de estado del jugador y contiene métodos para actualizar
la información del jugador y mostrar u ocultar la ventana de estado en la ventana principal.

Su código fuente se vería algo así:

```java
package rpg.gui.internalFrames;

import rpg.enums.Stats;
import rpg.gui.UIConstants;
import rpg.gui.labels.IconLabel;
import rpg.gui.labels.NameLabel;
import rpg.gui.panels.InternPanel;
import rpg.gui.panels.ItemDisplayPanel;
import rpg.gui.ui.TransparentFrameUI;
import rpg.gui.windows.MainWindow;
import rpg.utils.cache.ImageCache;

import javax.swing.*;
import javax.swing.border.EmptyBorder;
import java.awt.*;

public class StatusFrame extends JInternalFrame {

    private JPanel mainPanel;
    private JLabel attackIcon;
    private JLabel defenseIcon;
    private JLabel headIcon;
    private JLabel chestIcon;
    private JLabel legsIcon;
    private JLabel feetIcon;
    private JLabel handIcon;
    private JLabel weaponIcon;
    private JPanel headItemDisplay;
    private JPanel chestItemDisplay;
    private JPanel legsItemDisplay;
    private JPanel feetItemDisplay;
    private JPanel handItemDisplay;
    private JPanel weaponItemDisplay;
    private JLabel attackDisplay;
    private JLabel defenseDisplay;
    private InternalStatusBar internalStatusBar;
    private Dimension dimension;
    private MainWindow window;

    public StatusFrame(MainWindow window) {

        this.window = window;
        setContentPane(mainPanel);
        dimension = new Dimension(UIConstants.STATUS_FRAME_WIDTH, UIConstants.STATUS_FRAME_HEIGHT);
        setUI(new TransparentFrameUI(this, dimension));
        setSize(getPreferredSize());
    }

    private void createUIComponents() {
        int displayHeight = UIConstants.STATUS_FRAME_HEIGHT -
                UIConstants.INTERNAL_FRAME_HEADER_HEIGHT;
        mainPanel = new InternPanel(UIConstants.STATUS_FRAME_WIDTH, displayHeight);
        mainPanel.setBorder(new EmptyBorder(2, 10, 18, 10));
        ImageCache.addImage("attackIcon", "icons/attackIcon.png");
        ImageCache.addImage("defenseIcon", "icons/defenseIcon.png");
        ImageCache.addImage("headIcon", "icons/headArmorIcon.png");
        ImageCache.addImage("chestIcon", "icons/chestArmorIcon.png");
        ImageCache.addImage("legsIcon", "icons/legArmorIcon.png");
        ImageCache.addImage("feetIcon", "icons/feetArmorIcon.png");
        ImageCache.addImage("handIcon", "icons/handArmorIcon.png");
        ImageCache.addImage("weaponIcon", "icons/weaponIcon.png");
        attackIcon = new IconLabel(ImageCache.getImageIcon("attackIcon"));
        attackDisplay = new NameLabel(window.getPlayer().getStats().get(Stats.ATTACK).toString());
        defenseIcon = new IconLabel(ImageCache.getImageIcon("defenseIcon"));
        defenseDisplay = new NameLabel(window.getPlayer().getStats().get(Stats.DEFENSE).toString());
        headIcon = new IconLabel(ImageCache.getImageIcon("headIcon"));
        headItemDisplay = new ItemDisplayPanel(null);
        chestIcon = new IconLabel(ImageCache.getImageIcon("chestIcon"));
        chestItemDisplay = new ItemDisplayPanel(null);
        legsIcon = new IconLabel(ImageCache.getImageIcon("legsIcon"));
        legsItemDisplay = new ItemDisplayPanel(null);
        feetIcon = new IconLabel(ImageCache.getImageIcon("feetIcon"));
        feetItemDisplay = new ItemDisplayPanel(null);
        handIcon = new IconLabel(ImageCache.getImageIcon("handIcon"));
        handItemDisplay = new ItemDisplayPanel(null);
        weaponIcon = new IconLabel(ImageCache.getImageIcon("weaponIcon"));
        weaponItemDisplay = new ItemDisplayPanel(null);
    }
}
```

Ten en cuenta que este código es solo un ejemplo y puede variar dependiendo de tus necesidades y requerimientos.

Con estos cambios, hemos creado la ventana de estado que se mostrará en el centro de la ventana principal. En esta
ventana de estado, se mostrará la información del jugador, como su ataque, defensa, armamento, etc.