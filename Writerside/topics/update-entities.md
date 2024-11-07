# 21. Actualizando el Jugador y los Enemigos

De aquí en adelante, deberemos de realizar una serie de actualizaciones en las clases `Player` y `Enemy` para que puedan
interactuar entre sí y con el resto de la aplicación. En esta sección, veremos cómo actualizar estas clases para que
puedan atacar, recibir daño y mostrar mensajes al jugador.

## Actualizando al Jugador

Nuestro jugador, representado por la clase `Player`, necesita ser actualizado para que pueda atacar a los enemigos y
recibir daño de ellos. Para ello, veamos la suma de funciones de la clase.

```java
package rpg.entities;

import rpg.enums.Stats;
import rpg.exceptions.ItemNotFoundException;
import rpg.inventory.Inventory;
import rpg.items.Item;
import rpg.items.miscs.Misc;
import rpg.utils.Randomize;

import javax.swing.*;
import java.io.*;
import java.util.HashMap;

public class Player extends GameCharacter implements Serializable {

    private final Inventory inventory;

    public Player(String name) {

        super(name);
        inventory = new Inventory();
    }

    public boolean tryToFlee() {

        return Randomize.getRandomBoolean();
    }

    public void levelUp() {

        stats.put(Stats.LEVEL, stats.get(Stats.LEVEL) + 1);
        stats.put(Stats.MAX_HP, stats.get(Stats.MAX_HP) + Randomize.getRandomInt(5, 10));
        stats.put(Stats.HP, stats.get(Stats.MAX_HP));
        stats.put(Stats.MAX_MP, stats.get(Stats.MAX_MP) + Randomize.getRandomInt(2, 5));
        stats.put(Stats.MP, stats.get(Stats.MAX_MP));
        stats.put(Stats.ATTACK, stats.get(Stats.ATTACK) + Randomize.getRandomInt(1, 3));
        stats.put(Stats.DEFENSE, stats.get(Stats.DEFENSE) + Randomize.getRandomInt(1, 3));
        stats.put(Stats.NEEDED_EXPERIENCE, stats.get(Stats.NEEDED_EXPERIENCE) + 50);
        stats.put(Stats.EXPERIENCE, 0);
    }

    @Override
    protected void initCharacter() {

        stats.put(Stats.LEVEL, 1);
        stats.put(Stats.MAX_HP, 100);
        stats.put(Stats.HP, 100);
        stats.put(Stats.MAX_MP, 50);
        stats.put(Stats.MP, 50);
        stats.put(Stats.ATTACK, 10);
        stats.put(Stats.DEFENSE, 5);
        stats.put(Stats.EXPERIENCE, 0);
        stats.put(Stats.NEEDED_EXPERIENCE, 100);
        stats.put(Stats.GOLD, 0);
    }

    public void addItemToInventory(Item item) {

        if (item instanceof Misc misc) {
            if (misc.isStackable()) {
                boolean found = false;
                for (Item i : inventory.getMiscs()) {
                    if (i.getName().equals(misc.getName())) {
                        misc.increaseQuantity(1);
                        inventory.removeItem(i);
                        inventory.addItem(misc);
                        found = true;
                        break;
                    }
                }
                if (!found) {
                    inventory.addItem(item);
                }
            } else {
                inventory.addItem(item);
            }
        } else {
            inventory.addItem(item);
        }
    }

    public void removeItemFromInventory(Item item) {

        if (item instanceof Misc misc) {
            if (misc.isStackable()) {
                for (Item i : inventory.getMiscs()) {
                    if (i.getName().equals(item.getName())) {
                        misc.decreaseQuantity(1);
                        if (misc.getQuantity() == 0) {
                            inventory.removeItem(i);
                        }
                        break;
                    }
                }
            } else {
                inventory.removeItem(item);
            }
        } else {
            inventory.removeItem(item);
        }
    }

    public void sellItem(Item item) {

        try {
            Item getItem = inventory.getItem(item);
            if (getItem instanceof Misc misc) {
                if (misc.isStackable()) {
                    if (misc.getQuantity() > 1) {
                        misc.decreaseQuantity(1);
                    } else {
                        inventory.removeItem(item);
                    }
                }
            } else {
                inventory.removeItem(getItem);
            }
        } catch (ItemNotFoundException e) {
            JOptionPane.showMessageDialog(null, e.getMessage());
        }
    }

    public void showInventory() {

        StringBuilder content = new StringBuilder("Inventory: \n");
        String format = """
                Name: %s, Price: %d
                Description: %s
                """;
        String formatQuantity = """
                Name: %s, Price: %d, Quantity: %d
                Description: %s
                """;
        for (Item item : inventory.getItems()) {

            if (item instanceof Misc misc) {
                if (misc.isStackable()) {
                    content.append(String.format(formatQuantity, item.getName(),
                            item.getPrice(), misc.getQuantity(), item.getDescription()));
                } else {
                    content.append(String.format(format, item.getName(), item.getPrice(),
                            item.getDescription()));
                }
            } else {
                content.append(String.format(format, item.getName(), item.getPrice(),
                        item.getDescription()));
            }
        }
        JOptionPane.showMessageDialog(null, content.toString());
    }

    public Inventory getInventory() {
        return inventory;
    }
}
```

En esta actualización, hemos agregado una serie de funciones que permiten al jugador interactuar con su inventario y
realizar acciones como agregar, eliminar y vender objetos. Además, hemos agregado una función `showInventory` que
muestra el contenido del inventario en un cuadro de diálogo.

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

    public abstract void getLoot();

    public abstract String attack(GameCharacter enemy);

    public EnemyType getType() {
        return type;
    }

    public void setName(String name) {
        this.name = name;
    }

    public abstract ImageIcon getSprite();
}
```

En esta actualización, hemos agregado una función `getSprite` que se encarga de recuperar la imagen del enemigo. Esta
función será implementada por las clases concretas que extiendan de `Enemy` y se encarguen de definir el comportamiento
de cada enemigo en particular.

Ahora veamos como se ve un enemigo con esta actualización:

```java
package rpg.entities.enemies.goblins;

import rpg.entities.GameCharacter;
import rpg.entities.enemies.Enemy;
import rpg.enums.EnemyType;
import rpg.enums.Stats;
import rpg.exceptions.EnemyDeathException;
import rpg.utils.Randomize;
import rpg.utils.cache.ImageCache;

import javax.swing.*;

public class RookieGoblin extends Enemy {

    public RookieGoblin() {

        super("Rookie Goblin");
        ImageCache.addImage("rookie_goblin", "enemies/goblins/rookie_goblin.png");
    }

    @Override
    public void getLoot() {
        System.out.println("The Rookie Goblin drops a small bag of coins.");
    }

    @Override
    protected void initCharacter() {
        this.type = EnemyType.BASIC;
        this.stats.put(Stats.MAX_HP, 35);
        this.stats.put(Stats.HP, 35);
        this.stats.put(Stats.ATTACK, 6);
        this.stats.put(Stats.DEFENSE, 2);
        this.stats.put(Stats.EXPERIENCE, 20);
        this.stats.put(Stats.GOLD, 10);
    }

    @Override
    public String attack(GameCharacter enemy) {
        String message;
        // Se elige un número aleatorio entre 1 y 100
        int random = Randomize.getRandomInt(1, 100);
        // 50% de probabilidad de atacar normalmente
        // 25% de probabilidad de morder
        // 25% de probabilidad de lanzar una roca
        int attack = (random <= 50) ? 3 : (random <= 75) ? 2 : 1;
        // Se elige el ataque a realizar
        switch (attack) {
            case 1:
                try {
                    message = throwRock(enemy);
                } catch (EnemyDeathException e) {
                    enemy.getStats().put(Stats.HP, 0);
                    message = """
                            El Goblin novato lanza una roca y te hace 2 de daño.
                            ¡Has muerto!
                            """;
                }
                break;
            case 2:
                try {
                    message = savageBite(enemy);
                } catch (EnemyDeathException e) {
                    enemy.getStats().put(Stats.HP, 0);
                    message = """
                            El Goblin novato muerde salvajemente y te hace 3 de daño.
                            ¡Has muerto!
                            """;
                }
                break;
            default:
                message = ((GameCharacter) this).attack(enemy);
                break;
        }
        return message;
    }

    protected String throwRock(GameCharacter enemy) throws EnemyDeathException {
        int damage = 2;
        int newHP = reduceHP(enemy, damage);
        String enemyName = enemy.getName();
        String message = String.format("""
                ¡%s lanza una roca a %s por %d de daño!
                %s tiene %d HP restantes.
                """, this.name, enemyName, damage, enemyName, newHP);
        return message;
    }

    protected String savageBite(GameCharacter enemy) throws EnemyDeathException {
        int damage = 3;
        int newHP = reduceHP(enemy, damage);
        String enemyName = enemy.getName();
        String message = String.format("""
                ¡%s muerde salvajemente a %s por %d de daño!
                %s tiene %d HP restantes.
                """, this.name, enemyName, damage, enemyName, newHP);
        return message;
    }

    @Override
    public ImageIcon getSprite() {

        return ImageCache.getImageIcon("rookie_goblin");
    }
}
```

> **Nota:** En este ejemplo, el enemigo `RookieGoblin` tiene una probabilidad del 50% de lanzar una roca, un 25% de
> morder y un 25% de atacar normalmente. Cada ataque hace una cantidad de daño diferente y tiene una probabilidad de
> causar la muerte del jugador.

> **Nota:** Toma en consideración que el valor de los stats de los enemigos y del jugador pueden variar dependiendo de
> cómo quieras balancear el juego. Y que debes de inicializarlos en ambas clases para que pueda funcionar correctamente.

Con estas actualizaciones, hemos preparado al jugador y a los enemigos para interactuar entre sí y con el resto de la
aplicación. En la siguiente sección, veremos cómo implementar la lógica de combate entre el jugador y los enemigos.
