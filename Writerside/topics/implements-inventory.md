# Implementando un inventario

En este capítulo, aprenderemos a implementar un inventario de objetos en Java. Un inventario es una colección de objetos
que un personaje puede llevar consigo. En un juego de rol, un inventario puede contener armas, armaduras, pociones, etc.

## Clase `Item`

Para implementar un inventario de objetos, primero necesitamos definir una clase base para los objetos que se pueden
almacenar en el inventario. Crearemos una clase abstracta `Item` que representará un objeto genérico en nuestro juego.

```java
package rpg.items;

import rpg.enums.ItemType;

public abstract class Item {

    protected String name;
    protected String description;
    protected int price;
    protected ItemType type;

    public Item() {

        initItem();
    }

    protected abstract void initItem();
}
```

En este ejemplo, la clase `Item` es una clase abstracta que define los atributos comunes de un objeto en el juego, como
el nombre, la descripción, el precio y el tipo de objeto. La clase `Item` tiene un constructor sin argumentos que llama
al método `initItem`, que es un método abstracto que debe ser implementado por las clases derivadas.

## Clase `Armadura`

A continuación, crearemos una clase `Armadura` que hereda de la clase `Item` y representa una armadura en nuestro juego.

```java
package rpg.items.armors;

import rpg.items.Equipment;

public abstract class Armor extends Equipment {

}
```

## Clave `Equipment`

```java
package rpg.items;

import rpg.entities.Player;
import rpg.enums.Stats;
import rpg.interfaces.Equipable;

import java.util.HashMap;

public abstract class Equipment extends Item implements Equipable {

    protected HashMap<Stats, Integer> stats;

    @Override
    public void equip(Player player) {

    }

    @Override
    public void unequip(Player player) {

    }
}
```

## Clase `Inventario`

Finalmente, crearemos una clase `Inventario` que representará el inventario de un personaje en nuestro juego.

```java
package rpg.items;

import rpg.items.armors.Armor;
import rpg.items.miscs.Misc;

import java.util.ArrayList;

public class Inventory {

    private ArrayList<Item> items;
    private int capacity;

    public Inventory(int capacity) {
        this.capacity = capacity;
        items = new ArrayList<>();
    }

    public void addItem(Item item) {
        if (items.size() < capacity) {
            items.add(item);
        } else {
            System.out.println("Inventory is full");
        }
    }

    public void removeItem(Item item) {
        items.remove(item);
    }

    public Item getItem(int index) {
        return items.get(index);
    }

    public void getItemCount() {
        items.size();
    }

    public boolean isFull() {
        return items.size() == capacity;
    }

    public boolean isEmpty() {
        return items.isEmpty();
    }

    public void clear() {
        items.clear();
    }

    public void increaseCapacity(int amount) {
        capacity += amount;
        items.ensureCapacity(capacity);
    }

    public ArrayList<Armor> getArmors() {

        ArrayList<Armor> armors = new ArrayList<>();
        for (Item item : items) {
            if (item instanceof Armor) {
                armors.add((Armor) item);
            }
        }
        return armors;
    }

    public ArrayList<Misc> getMiscs() {

        ArrayList<Misc> miscs = new ArrayList<>();
        for (Item item : items) {
            if (item instanceof Misc) {
                miscs.add((Misc) item);
            }
        }
        return miscs;
    }
}
```

En este ejemplo, la clase `Inventario` tiene una lista de objetos `Item` y un atributo de capacidad que determina
cuántos objetos puede contener el inventario. La clase `Inventario` tiene métodos para agregar, eliminar, obtener y
contar objetos en el inventario, así como para verificar si el inventario está lleno o vacío. También tiene métodos para
aumentar la capacidad del inventario y listar armaduras y objetos misceláneos en el inventario.

## Probando el inventario

Para probar nuestro inventario, podemos crear una instancia de la clase `Inventario` y agregar algunos objetos a él.

```java
public class Main {

    public static void main(String[] args) {

        Inventory inventory = new Inventory(10);

        Armor armor = new WoodArmor();
        inventory.addItem(armor);

        Misc misc = new WolfPelt();
        inventory.addItem(misc);

        System.out.println("Armors in inventory:");
        for (Armor a : inventory.getArmors()) {
            System.out.println(a.getName());
        }

        System.out.println("Miscs in inventory:");
        for (Misc m : inventory.getMiscs()) {
            System.out.println(m.getName());
        }
    }
}
```