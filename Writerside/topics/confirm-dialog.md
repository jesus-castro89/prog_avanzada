# Ventana de confirmación con showConfirmDialog

En Java, la función `showConfirmDialog` de la clase `JOptionPane` se utiliza para mostrar una ventana de confirmación
con botones de opción. Esta función devuelve un valor entero que representa la opción seleccionada por el usuario.

## Sintaxis de la función showConfirmDialog

La sintaxis de la función `showConfirmDialog` es la siguiente:

```java
int option = JOptionPane.showConfirmDialog(Component parentComponent, Object message, String title, int optionType);
```

Donde:

- `parentComponent`: Es el componente padre de la ventana de confirmación. Puede ser `null` si no se desea especificar
  un
  componente padre.
- `message`: Es el mensaje que se mostrará en la ventana de confirmación. Puede ser de tipo `String`, `Icon`,
  `Component` o
  `Object`.
- `title`: Es el título de la ventana de confirmación.
- `optionType`: Es el tipo de opciones que se mostrarán en la ventana de confirmación.

> **Nota**: La función `showConfirmDialog` devuelve un valor entero que representa la opción seleccionada por el
> usuario.

### Tipos de opciones

La función `showConfirmDialog` permite mostrar diferentes tipos de opciones en la ventana de confirmación que son:

| Tipo de opción                     | Descripción                                             |
|------------------------------------|---------------------------------------------------------|
| `JOptionPane.DEFAULT_OPTION`       | Muestra los botones predeterminados (Sí, No, Cancelar). |
| `JOptionPane.YES_NO_OPTION`        | Muestra los botones Sí y No.                            |
| `JOptionPane.YES_NO_CANCEL_OPTION` | Muestra los botones Sí, No y Cancelar.                  |
| `JOptionPane.OK_CANCEL_OPTION`     | Muestra los botones Aceptar y Cancelar.                 |

### Ejemplo de la función showConfirmDialog

```java
int option = JOptionPane.showConfirmDialog(null, "¿Estás seguro de continuar?", "Confirmación", JOptionPane.YES_NO_OPTION);
```

En este ejemplo, se muestra una ventana de confirmación con el mensaje "¿Estás seguro de continuar?", el título
"Confirmación" y los botones Sí y No. El valor de la opción seleccionada por el usuario se guarda en la variable
`option`.
