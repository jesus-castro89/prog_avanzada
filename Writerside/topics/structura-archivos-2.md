# 26. Estructura de archivos

La estructura actual de nuestro proyecto debería de verse de la siguiente manera:

```
📦 src
   └─ rpg
      ├─ entities
      │  ├─ Game.java
      │  ├─ GameCharacter.java
      │  ├─ Player.java
      │  └─ enemies
      │     ├─ Enemy.java
      │     ├─ bears
      │     │  └─ WoodBear.java
      │     ├─ goblins
      │     │  ├─ GoblinGeneral.java
      │     │  └─ RookieGoblin.java
      │     ├─ slimes
      │     │  └─ BasicSlime.java
      │     └─ wolfs
      │        └─ StrayWolf.java
      ├─ enums
      │  ├─ BarType.java
      │  ├─ EnemyType.java
      │  ├─ ItemType.java
      │  └─ Stats.java
      ├─ exceptions
      │  ├─ EnemyDeathException.java
      │  ├─ InventoryFullException.java
      │  └─ ItemNotFoundException.java
      ├─ factory
      │  └─ EnemyFactory.java
      ├─ gui
      │  ├─ UIConstants.java
      │  ├─ buttons
      │  │  ├─ AttackButton.java
      │  │  ├─ BaseButton.java
      │  │  ├─ BlacksmithButton.java
      │  │  ├─ ExitButton.java
      │  │  ├─ FleeButton.java
      │  │  ├─ InventoryButton.java
      │  │  ├─ LoadFileButton.java
      │  │  ├─ NewFileButton.java
      │  │  ├─ SaveButton.java
      │  │  ├─ ShopButton.java
      │  │  ├─ SkillPanelButton.java
      │  │  ├─ UserButton.java
      │  │  └─ events
      │  │     └─ AttackEvent.java
      │  ├─ internalFrames
      │  │  ├─ InternalStatusBar.form
      │  │  ├─ InternalStatusBar.java
      │  │  ├─ StatusFrame.form
      │  │  └─ StatusFrame.java
      │  ├─ labels
      │  │  ├─ BarLabel.java
      │  │  ├─ EnemySpriteLabel.java
      │  │  ├─ GoldLabel.java
      │  │  ├─ NameLabel.java
      │  │  ├─ PlayerSpriteLabel.java
      │  │  └─ PortraitLabel.java
      │  ├─ panels
      │  │  ├─ BackgroundPanel.java
      │  │  ├─ BottomPanel.java
      │  │  ├─ CenterPanel.java
      │  │  ├─ FilesPanel.java
      │  │  ├─ LeftCornerPanel.java
      │  │  ├─ MessagePanel.java
      │  │  ├─ MiddlePanel.java
      │  │  ├─ RightCornerPanel.java
      │  │  └─ TopPanel.java
      │  ├─ ui
      │  │  ├─ BarLabelUI.java
      │  │  ├─ EnemyLabelUI.java
      │  │  ├─ GameLabelUI.java
      │  │  ├─ HoverButtonUI.java
      │  │  ├─ NameLabelUI.java
      │  │  ├─ StatusBarUI.java
      │  │  ├─ TransparentFrameUI.java
      │  │  └─ UserHoverUI.java
      │  └─ windows
      │     ├─ MainWindow.form
      │     ├─ MainWindow.java
      │     ├─ NewFileWindow.form
      │     ├─ NewFileWindow.java
      │     ├─ StartWindow.form
      │     └─ StartWindow.java
      ├─ interfaces
      │  ├─ Equipable.java
      │  └─ Sellable.java
      ├─ inventory
      │  ├─ Inventory.java
      │  └─ InventoryTest.java
      ├─ items
      │  ├─ Equipment.java
      │  ├─ Item.java
      │  ├─ armors
      │  │  ├─ Armor.java
      │  │  └─ helmet
      │  │     ├─ IronHelmet.java
      │  │     └─ WoodHelmet.java
      │  └─ miscs
      │     ├─ Misc.java
      │     └─ WolfPelt.java
      └─ utils
         ├─ Example.java
         ├─ FileManager.java
         ├─ Randomize.java
         └─ cache
            ├─ FontCache.java
            ├─ FontLoader.java
            ├─ ImageCache.java
            └─ ImageLoader.java
```

©generated by [Project Tree Generator](https://woochanleee.github.io/project-tree-generator)

Toma en consideración que algunas clases son propuestas como una referencia, como por ejemplos los items y los enemigos,
mientras que otras son clases que ya hemos implementado en el proyecto.

## `rpg.entities`

En este paquete se encuentran todas las clases que representan a los personajes del juego, tanto al jugador como a los
enemigos.

## `rpg.enums`

En este paquete se encuentran todas las enumeraciones que utilizamos en el proyecto, como por ejemplo los tipos de
enemigos, los tipos de items, los tipos de estadísticas, etc.

## `rpg.exceptions`

En este paquete se encuentran todas las excepciones que hemos creado para manejar los errores que puedan surgir en el
juego.

## `rpg.factory`

En este paquete se encuentra la clase `EnemyFactory`, que es la encargada de crear a los enemigos del juego.

## `rpg.gui`

En este paquete se encuentran todas las clases que representan la interfaz gráfica del juego, como por ejemplo los
botones, las etiquetas, los paneles, etc.

## `rpg.interfaces`

En este paquete se encuentran todas las interfaces que hemos creado para definir el comportamiento de ciertas clases,
como por ejemplo los objetos equipables y los objetos vendibles.

## `rpg.inventory`

En este paquete se encuentran las clases que representan el inventario del jugador, así como una clase de prueba para
verificar su funcionamiento.

## `rpg.items`

En este paquete se encuentran todas las clases que representan los items del juego, como por ejemplo las armaduras y los
objetos misceláneos.

## `rpg.utils`

En este paquete se encuentran todas las clases de utilidades que hemos creado para facilitar el desarrollo del juego,
como por ejemplo una clase para manejar archivos, una clase para generar números aleatorios, etc.

## `rpg.utils.cache`

En este paquete se encuentran todas las clases que hemos creado para cachear las imágenes y las fuentes que utilizamos
en el juego.

Puedes consultar el código fuente completo del proyecto en el siguiente
enlace: [U5-U6](https://github.com/jesus-castro89/repos/tree/U5_U6)