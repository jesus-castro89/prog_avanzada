# Ejemplos de Items

## `WolfPelt`

```java
package rpg.items.miscs;

import rpg.enums.ItemType;
import rpg.utils.cache.ImageCache;

import javax.swing.*;
import java.io.Serializable;

/**
 * The type Wolf pelt.
 */
public class WolfPelt extends Misc implements Serializable {

    @Override
    protected void initItem() {
        this.type = ItemType.MISC;
        this.name = "Piel de lobo";
        this.description = "Una piel de lobo. Se puede vender por un buen precio.";
        this.price = 50;
        this.consumable = false;
        this.stackable = true;
        this.quantity = 1;
    }

    @Override
    public void use() {
        System.out.println("No puedes usar una piel de lobo.");
    }
}
```

## `WoodHelmet`

```java
package rpg.items.armors.helmet;

import rpg.enums.ItemType;
import rpg.enums.Stats;
import rpg.enums.WearType;
import rpg.items.armors.Armor;
import rpg.utils.cache.ImageCache;

import javax.swing.*;
import java.util.HashMap;

/**
 * The type Wood helmet.
 */
public class WoodHelmet extends Armor {

    @Override
    protected void initItem() {
        wearType = WearType.HEAD;
        name = "Casco de madera";
        description = "Un casco de madera. No es muy resistente, pero es mejor que nada.";
        price = 10;
        stats = new HashMap<>();
        stats.put(Stats.DEFENSE, 2);
    }

    /**
     * Protect.
     */
    public void protect() {
        System.out.println("El casco de madera te protege de un golpe y se rompe.");
    }
}
```