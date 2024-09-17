# Los Wrappers

Los *wrappers* son clases que envuelven los tipos de datos primitivos en Java. Estas clases proporcionan métodos y
funcionalidades adicionales para trabajar con los tipos de datos primitivos de una manera más flexible y orientada a
objetos.

## Tipos de Wrappers

Los *wrappers* en Java son:

| Tipo primitivo | Wrapper     |
|----------------|-------------|
| `byte`         | `Byte`      |
| `short`        | `Short`     |
| `int`          | `Integer`   |
| `long`         | `Long`      |
| `float`        | `Float`     |
| `double`       | `Double`    |
| `char`         | `Character` |
| `boolean`      | `Boolean`   |

Cada tipo primitivo tiene su correspondiente *wrapper* en Java. Siendo este una clase con el mismo nombre que el tipo
primitivo, pero con la primera letra en mayúscula. A excepción de `char`, que se llama `Character` e `int`, que se llama
`Integer`.

## Conversión entre Tipos Primitivos y Wrappers

Para convertir un tipo primitivo en su *wrapper* correspondiente, se puede utilizar el método estático `valueOf` de la
clase *wrapper*. Por ejemplo, para convertir un `int` en un `Integer`, se puede hacer lo siguiente:

```java
int numero = 10;
Integer numeroWrapper = Integer.valueOf(numero);
```

Para convertir un *wrapper* en su tipo primitivo correspondiente, se puede utilizar el método `xxxValue` del *wrapper*.
Por ejemplo, para convertir un `Integer` en un `int`, se puede hacer lo siguiente:

```java
Integer numeroWrapper = Integer.valueOf(10);
int numero = numeroWrapper.intValue();
```

## Autoboxing y Unboxing

Java proporciona una característica llamada *autoboxing* que convierte automáticamente un tipo primitivo en su *wrapper*
correspondiente cuando es necesario. Por ejemplo, se puede asignar un `int` a un `Integer` de la siguiente manera:

```java
int numero = 10;
Integer numeroWrapper = numero;
```

Java también proporciona una característica llamada *unboxing* que convierte automáticamente un *wrapper* en su tipo
primitivo correspondiente cuando es necesario. Por ejemplo, se puede asignar un `Integer` a un `int` de la siguiente
manera:

```java
Integer numeroWrapper = Integer.valueOf(10);
int numero = numeroWrapper;
```

El *autoboxing* y *unboxing* hacen que sea más fácil trabajar con tipos primitivos y *wrappers* en Java, ya que se
encargan de las conversiones automáticamente.

## Conclusiones

Los *wrappers* son clases que envuelven los tipos de datos primitivos en Java y proporcionan funcionalidades adicionales
para trabajar con ellos. La conversión entre tipos primitivos y *wrappers* se puede hacer de forma explícita utilizando
los métodos `valueOf` y `xxxValue`, o de forma implícita utilizando el *autoboxing* y *unboxing*. Estas características
hacen que sea más fácil y flexible trabajar con tipos primitivos y *wrappers* en Java.