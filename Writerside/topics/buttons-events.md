# 25. Botones y eventos

Para efectos de nuestro proyecto, necesitamos que los botones tengan un comportamiento específico. En este caso,
necesitamos que el botón de ataque realice una acción y que el botón de huir cierre la ventana de combate, etc.

## Los botones

En nuestro juego en Java, tenemos el panel inferior, este será el lugar donde agregaremos los botones de ataque, huir y
usar habilidad. Estos botones serán los que el jugador utilizará para interactuar con el juego.

En la parte superior del panel, agregaremos los botones de guardar y salir. Estos botones serán los que el jugador
utilizará para guardar la partida y salir del juego.

Además de ellos, deberemos de agregar los botones del inventario (estos serán los que el jugador utilizará para
interactuar con los objetos que tenga en su inventario), y los botones necesarios para la interacción con los personajes
no jugadores (Herrero, Tienda, etc.).

## Los eventos

Para que los botones realicen una acción, necesitamos agregar un evento a cada uno de ellos. En este caso, necesitamos
que el botón de ataque realice una acción y que el botón de huir cierre la ventana de combate, etc.

Para agregar un evento a un botón, necesitamos crear una clase que implemente la interfaz `ActionListener` y
sobreescribir el método `actionPerformed`. Este método será el encargado de realizar la acción que deseamos cuando se
presione el botón.

## Diferenciando los botones de la aplicación

Para diferenciar nuestro botones, debemos recordar que tenemos dos clases para las UI de los botones: `HoverButtonUI`
y `UserHoverUI`, las cuales nos permiten hacer que los botones cambien de color cuando el mouse pase sobre ellos.

Como complemento, toma el siguiente código de la clase `UserHoverUI`:

```java
    package rpg.gui.ui;

    import rpg.utils.cache.ImageCache;

    import javax.swing.*;
    import java.awt.*;

    public class UserHoverUI extends HoverButtonUI {

        private final int staticWidth = 180;

        protected void installDefaults(AbstractButton b) {
            super.installDefaults(b);
            // Establecemos el borde del botón.
            b.setForeground(Color.WHITE);
        }

        @Override
        public Dimension getPreferredSize(JComponent c) {

            return new Dimension(staticWidth, 48);
        }

        protected void initParts() {
            //Inicializamos los arreglos de imágenes.
            parts = new ImageIcon[3];
            partsHover = new ImageIcon[3];
            // Agregamos las imágenes a la caché.
            ImageCache.addImage("actionLeftSide", "buttons/idle/ui/leftSide.png");
            ImageCache.addImage("actionCenterSide", "buttons/idle/ui/centerSide.png");
            ImageCache.addImage("actionRightSide", "buttons/idle/ui/rightSide.png");
            ImageCache.addImage("actionHoverLeftSide", "buttons/hover/ui/leftSide.png");
            ImageCache.addImage("actionHoverCenterSide", "buttons/hover/ui/centerSide.png");
            ImageCache.addImage("actionHoverRightSide", "buttons/hover/ui/rightSide.png");
            // Obtenemos las imágenes de la caché y las almacenamos en los arreglos correspondientes.
            parts[0] = ImageCache.getImageIcon("actionLeftSide");
            parts[1] = ImageCache.getImageIcon("actionCenterSide");
            parts[2] = ImageCache.getImageIcon("actionRightSide");
            partsHover[0] = ImageCache.getImageIcon("actionHoverLeftSide");
            partsHover[1] = ImageCache.getImageIcon("actionHoverCenterSide");
            partsHover[2] = ImageCache.getImageIcon("actionHoverRightSide");
        }

        protected void drawButtonParts(Graphics2D g2d, ImageIcon[] parts) {

            g2d.drawImage(parts[0].getImage(), 0, 0, null);
            g2d.translate(27, 0);
            g2d.drawImage(parts[1].getImage(), 0, 0,
                    staticWidth - 54, height, null);
            g2d.translate(staticWidth - 54, 0);
            g2d.drawImage(parts[2].getImage(), 0, 0, null);
            g2d.translate(-staticWidth + width + 54, 0);
        }
    }
```

Ten en cuenta que esta clase hace referencia a un conjunto de imágenes que se encuentran en la carpeta `buttons` de la
carpeta `image` o en el directorio de tu preferencia en tu proyecto.

Por consiguiente, deberás de definir las imágenes que utilizarás para los botones de tu juego.

## El botón de ataque

Para el botón de ataque, vamos a utilizar la imagen `attack.png` que se encuentra en la carpeta `image` o en el
directorio de tu preferencia en tu proyecto.

Para mostrarla crearemos una clase llamada `AttackButton` que extienda de `UserButton` dentro del paquete
`rpg.gui.buttons`.

```java
package rpg.gui.buttons;

import rpg.gui.windows.MainWindow;
import rpg.gui.buttons.events.AttackEvent;

public class AttackButton extends UserButton {

    public AttackButton(MainWindow game) {

        super("Atacar");
    }
}
```

Al igual que este ejemplo, deberemos de crear las clases para los demás botones que necesitemos en nuestro juego.

> **Nota:** Recuerda que puedes utilizar las imágenes que desees para los botones de tu juego.

> **Nota:** Toma en cuenta que por ahora no estamos agregando los eventos a los botones, solo estamos creando las clases
> que los representan.

> **Nota:** Recuerda quitar la opacidad de los botones que agregues para que se muestren correctamente.

## El evento de ataque

Para el evento de ataque, vamos a crear una clase llamada `AttackEvent` que implemente la interfaz `ActionListener`
dentro del paquete `rpg.gui.buttons.events`.

```java
package rpg.gui.buttons.events;

import rpg.entities.Player;
import rpg.entities.enemies.Enemy;
import rpg.gui.windows.MainWindow;

import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class AttackEvent implements ActionListener {

    private final MainWindow game;

    public AttackEvent(MainWindow game) {

        this.game = game;
    }

    @Override
    public void actionPerformed(ActionEvent e) {

        Enemy enemy = this.game.getEnemy();
        Player player = this.game.getPlayer();
        if (enemy != null) {

            this.game.appendText(player.attack(enemy));
            if (enemy.isAlive())
                this.game.appendText(enemy.attack(player));
            this.game.checkGameStatus();
        }
    }
}
```

Al igual que este ejemplo, deberemos de crear las clases para los demás eventos que necesitemos en nuestro juego.

> **Nota:** Recuerda que por ahora no estamos agregando los eventos a los botones, solo estamos creando las clases que
> los representan.

> **Nota:** Recuerda quitar la opacidad de las etiquetas y paneles que agregues para que se muestren los sprites.

## Otros Botones y Eventos

Para los demás botones y eventos, deberemos de seguir el mismo procedimiento que hemos seguido para el botón de ataque y
su evento.