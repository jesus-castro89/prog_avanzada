# 19. Los sprites

Los sprites son imágenes que se utilizan para representar a los personajes, objetos y enemigos en un videojuego. En la
mayoría de los casos, los sprites son imágenes bidimensionales que se muestran en la pantalla del juego. Los sprites se
utilizan para representar a los personajes, objetos y enemigos en un videojuego. En la mayoría de los casos, los sprites
son imágenes bidimensionales que se muestran en la pantalla del juego.

Para efectos de nuestro juego, vamos a utilizar sprites que representen a los personajes y objetos que aparecerán en la
pantalla. Los sprites se pueden crear utilizando programas de diseño gráfico como Photoshop, GIMP o Inkscape. También
puedes encontrar sprites gratuitos en Internet que puedes utilizar en tu juego.

## Los paneles de sprites

En nuestro juego en Java, tenemos el panel central, este será el lugar que dividiremos en dos paneles, uno para los
sprites de los personajes y otro para los sprites de los enemigos.

En el panel de la izquierda, agregaremos una sola etiqueta que su ubique centrada y hacia abajo, esta etiqueta será la
que muestre el sprite del personaje. En el panel de la derecha, agregaremos una etiqueta en la parte inferior que se
encuentre centrada y hacia abajo, esta etiqueta será la que muestre el sprite del enemigo. Sobre esta etiqueta,
agregaremos dos más, la primera centrada y hacia la derecha y la segunda centrada y hacia la izquierda, estas serán las
que muestren el nombre del enemigo y su vida.

![sprites_panel.png](..%2Fimages%2Fsprites_panel.png){display:block}

> **Nota:** En el panel de sprites de los personajes, solo se mostrará un sprite, mientras que en el panel de sprites de
> los enemigos, se mostrarán tres sprites, uno para el enemigo, otro para el nombre del enemigo y otro para la vida del
> enemigo.

> **Nota:** Los sprites de los personajes y enemigos se mostrarán en el panel de sprites, pero no se moverán.

> **Nota:** Recuerda quitar la opacidad de las etiquetas y paneles que agregues para que se muestren los sprites.

## El sprite del personaje

Para el sprite del personaje, vamos a utilizar la imagen `player.png` que se encuentra en la carpeta `image` o en el
directorio de tu preferencia en tu proyecto.

Para mostrarla crearemos una clase llamada `PlayerSpriteLabel` que extienda de `PortraitLabel` dentro del paquete
`rpg.gui.labels`. Esta clase será la encargada de mostrar el sprite del personaje en el panel de sprites.

```java
package rpg.gui.labels;

import rpg.utils.cache.ImageCache;

import java.awt.*;

public class PlayerSpriteLabel extends PortraitLabel {

    public PlayerSpriteLabel() {

    super();
    }

    @Override
    public void initComponents() {
    ImageCache.addImage("playerSprite", "player/player.png");
    icon = ImageCache.getImageIcon("playerSprite");
    setPreferredSize(new Dimension(icon.getIconWidth(),
        icon.getIconHeight()));
    setIcon(icon);
    }
}
```

> **Nota:** La clase `PortraitLabel` es una clase que extiende de `JLabel` y que se encarga de mostrar una imagen en
> un panel. La clase `ImageCache` es una clase que se encarga de almacenar las imágenes que se utilizan en el juego.

## Actualizando a los enemigos

Para los enemigos, haremos que la clase abstracta `Enemy` tenga una función abstracta que se encargue de recuperar la
imagen del enemigo, de la siguiente manera:

```java
package rpg.entities.enemies;

import rpg.entities.GameCharacter;
import rpg.enums.EnemyType;
import rpg.enums.Stats;

import javax.swing.*;
import java.awt.image.BufferedImage;

public abstract class Enemy extends GameCharacter {

    protected EnemyType type;

    public Enemy(String name) {
    super(name);
    }

    public abstract ImageIcon getSprite();
    
    public abstract void getLoot();

    public abstract void attack(GameCharacter enemy);

    public EnemyType getType() {
    return type;
    }

    public void setName(String name) {
    this.name = name;
    }
}
```

Recuerda que en el constructor de cada enemigo, se debe asignar el tipo de enemigo, por ejemplo, tomento la clase
WoodBear:

```java
    public WoodBear() {
        super("Wood Bear");
        ImageCache.addImage("wood_bear", "enemies/MountainScarbear.png");
    }

    @Override
    protected void initCharacter() {
        this.type = EnemyType.BASIC;
        this.stats.put(Stats.MAX_HP, 50);
        this.stats.put(Stats.HP, 50);
        this.stats.put(Stats.ATTACK, 8);
        this.stats.put(Stats.DEFENSE, 4);
        this.stats.put(Stats.EXPERIENCE, 30);
        this.stats.put(Stats.GOLD, 20);
    }
    
    @Override
    public ImageIcon getSprite() {
        return ImageCache.getImageIcon("wood_bear");
    }
```

> **Nota:** Como puedes notar, en el constructor de la clase `WoodBear` se agrega la imagen del enemigo al caché de
> imágenes y en la función `getSprite` se recupera la imagen del enemigo.

> **Nota:** La función `initCharacter` se encarga de inicializar los atributos del enemigo, como la vida, ataque,
> defensa, experiencia y oro. Es importante que esta función inicialice los atributos del enemigo, ya que de lo
> contrario, el enemigo no podrá atacar, recibir daño o morir y causará errores en el juego.

## Mostrando el sprite del enemigo

Luego crearemos la clase `EnemySpriteLabel` que extiende de `JLabel`, mostraremos el sprite del enemigo.

```java
package rpg.gui.labels;

import rpg.entities.enemies.Enemy;
import rpg.gui.ui.EnemyLabelUI;
import rpg.gui.ui.GameLabelUI;
import rpg.utils.cache.ImageCache;

import javax.swing.*;
import java.awt.*;

public class EnemySpriteLabel extends JLabel {

    ImageIcon icon;
    Enemy enemy;

    public EnemySpriteLabel(Enemy enemy) {

    this.enemy = enemy;
    initComponents();
    setUI(new EnemyLabelUI(icon));
    }

    public void initComponents() {

    icon = enemy.getSprite();
    setPreferredSize(getMinDimension());
    setSize(getMinDimension());
    setIcon(icon);
    }

    private Dimension getMinDimension() {

    if (icon.getIconWidth() > 350 || icon.getIconHeight() > 184) {
        icon = new ImageIcon(icon.getImage().getScaledInstance(450, 250, Image.SCALE_SMOOTH));
    }
    return new Dimension(icon.getIconWidth(), icon.getIconHeight());
    }
}
```

Como se puede ver, la clase `EnemySpriteLabel` recibe un objeto de tipo `Enemy` en su constructor, este objeto es el
enemigo que se mostrará en el panel de sprites.

Mientras la función `getMinDimension` se encarga de redimensionar la imagen del enemigo si es muy grande. Esto es útil
para los jefes o enemigos secretos.

Así mismo necesitamos definir la clase `EnemyLabelUI` que extiende de `BasicLabelUI` y que se encargará de mostrar de
forma correcta el sprite del enemigo.

```java
package rpg.gui.ui;

import javax.swing.plaf.basic.BasicLabelUI;

import javax.swing.*;
import java.awt.*;

public class EnemyLabelUI extends BasicLabelUI {

    ImageIcon icon;

    public EnemyLabelUI(ImageIcon icon) {

    this.icon = icon;
    }

    @Override
    protected void installDefaults(JLabel c) {

    c.setOpaque(false);
    c.setBorder(null);
    }

    @Override
    public void paint(Graphics g, JComponent c) {

    Graphics2D g2d = (Graphics2D) g;
    g2d.setRenderingHint(RenderingHints.KEY_ANTIALIASING, RenderingHints.VALUE_ANTIALIAS_ON);
    g2d.setRenderingHint(RenderingHints.KEY_INTERPOLATION, RenderingHints.VALUE_INTERPOLATION_BICUBIC);
    g2d.drawImage(icon.getImage(), 0, 0, icon.getIconWidth(),
        icon.getIconHeight(), c);
    }
}
```

> **Nota:** Como se puede ver, haremos que la imagen se estire hasta ocupar todo el espacio de la etiqueta.

## Mostrando el nombre y la vida del enemigo

Para mostrar el nombre y la vida del enemigo, haremos que esas etiquetas se creen con `Custom Create` en la vista de
diseño y haremos que se muestre la información de un enemigo.

```java
private void createUIComponents() {
    topPanel = new TopPanel();
    middlePanel = new MiddlePanel();
    bottomPanel = new BottomPanel();
    blacksmithButton = new BlacksmithButton();
    shopButton = new ShopButton();
    inventoryButton = new InventoryButton();
    exitButton = new ExitButton();
    saveButton = new SaveButton();
    atacarButton = new AttackButton();
    habilidadesButton = new SkillPanelButton();
    huirButton = new FleeButton();
    exampleLabel = new PortraitLabel();
    lifeLabel = new BarLabel(100, 100, BarType.LIFE);
    magicLabel = new BarLabel(30, 100, BarType.MAGIC);
    expLabel = new BarLabel(0, 350, BarType.EXPERIENCE);
    goldLabel = new GoldLabel();
    nameLabel = new NameLabel("Miguel LVL. 1");
    playerSprite = new PlayerSpriteLabel();
    Enemy enemy = new RookieGoblin();
    enemyNameLabel = new NameLabel(enemy.getName());
    enemyLifeLabel = new BarLabel(100, 100, BarType.LIFE);
    enemySprite = new EnemySpriteLabel(enemy);
}
```

Como se puede apreciar, se crea un objeto de tipo `RookieGoblin` y se le asigna a la etiqueta `enemySprite` para que
muestre el sprite del enemigo. Así mismo, se crea una etiqueta `enemyNameLabel` que mostrará el nombre del enemigo y
una etiqueta `enemyLifeLabel` que mostrará la vida del enemigo.

El resto de datos son referencia a las etiquetas que se han creado en el proyecto.

## Conclusión

En este capítulo, hemos aprendido a mostrar los sprites de los personajes y enemigos en el panel de sprites. Hemos
aprendido a crear una clase que se encargue de mostrar el sprite del personaje y otra clase que se encargue de mostrar
el sprite del enemigo. También hemos aprendido a mostrar el nombre y la vida del enemigo en el panel de sprites.