# La clase `HashMap`

La clase `HashMap` es una clase de la biblioteca estándar de Java que implementa la interfaz `Map` y proporciona una
estructura de datos de tipo tabla hash para almacenar pares clave-valor. Permite almacenar y recuperar elementos de
forma eficiente utilizando una función de dispersión para calcular la ubicación de los elementos en la tabla hash.

## Creación de un HashMap

Para crear un `HashMap` en Java, se utiliza la siguiente sintaxis:

```java
HashMap<String, Integer> map = new HashMap<>();
```

En este ejemplo, se crea un `HashMap` que almacena pares clave-valor donde las claves son de tipo `String` y los valores
son de tipo `Integer`.

## Agregar Elementos a un HashMap

Para agregar elementos a un `HashMap`, se utiliza el método `put` con la clave y el valor como parámetros. Por ejemplo:

```java
map.put("uno", 1);
map.put("dos", 2);
map.put("tres", 3);
```

En este ejemplo, se agregan los pares clave-valor `"uno": 1`, `"dos": 2` y `"tres": 3` al `HashMap`.

## Recuperar Elementos de un HashMap

Para recuperar un elemento de un `HashMap`, se utiliza el método `get` con la clave como parámetro. Por ejemplo:

```java
int valor = map.get("dos");
System.out.println(valor); // 2
```

En este ejemplo, se recupera el valor asociado a la clave `"dos"` del `HashMap` y se imprime por pantalla.

## Verificar si una Clave Existe en un HashMap

Para verificar si una clave existe en un `HashMap`, se utiliza el método `containsKey` con la clave como parámetro. Por
ejemplo:

```java
if (map.containsKey("dos")) {
    System.out.println("La clave 'dos' existe en el HashMap");
} else {
    System.out.println("La clave 'dos' no existe en el HashMap");
}
```

En este ejemplo, se verifica si la clave `"dos"` existe en el `HashMap` e imprime un mensaje dependiendo del resultado.

## Iterar sobre un HashMap

Para iterar sobre un `HashMap`, se puede utilizar un bucle `for-each` o un iterator. Por ejemplo:

```java
for (String clave : map.keySet()) {
    int valor = map.get(clave);
    System.out.println(clave + ": " + valor);
}
```

En este ejemplo, se itera sobre las claves del `HashMap` y se imprime cada par clave-valor por pantalla.

## Eliminar un Elemento de un HashMap

Para eliminar un elemento de un `HashMap`, se utiliza el método `remove` con la clave como parámetro. Por ejemplo:

```java
map.remove("dos");
```

En este ejemplo, se elimina el par clave-valor asociado a la clave `"dos"` del `HashMap`.