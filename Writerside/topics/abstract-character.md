# 7. Las clases Abstractas y las Interfaces

Para efectos de nuestro proyecto, la clase `GameCharacter` es una clase abstracta que define un personaje de juego
genérico. La clase `GameCharacter` tiene un constructor que inicializa el nombre del personaje y un método abstracto
`attack` que debe ser implementado por las clases que heredan de `GameCharacter`.

```java
package rpg.characters;

public abstract class GameCharacter{

    protected String name;

    public GameCharacter(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public abstract void attack(GameCharacter enemy);

}
```