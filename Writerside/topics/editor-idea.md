# El editor GUI de IntelliJ IDEA

Dentro del editor IntelliJ IDEA, existe una herramienta que nos permite crear interfaces de manera intuitiva y visual,
sin embargo, hay que tener en consideración algunas consideraciones para con él.

## Los elementos nombrados

Dentro del editor podemos usar la paleta de componentes para agregar lo que necesitemos dentro de nuestra ventana, pero
cuando hacemos esto, solo algunos elementos son nombrados y por consiguiente agregados a la clase vinculada a nuestra
ventana.

Es decir, si el componente no tiene un nombre propio dentro de la ventana de propiedades del editor, este no será parte
de los atríbutos de la clase, y por consiguiente no podremos trabajar con el.

Así mismo, al trabajar con componentes es de suma importancia destacar que al usar la opción `Custom Create`, deberemos
de usar el nombre que le hemos dado al o los componentes que deseemos crear de forma manual, y tener en cuenta que si
no iniciamos adecuadamente a cada componente marcado, el sistema no indicará un error, ya que espera que nosotros
generemos dicho componente dentro de la función `createUIComponents()`.

## La paleta de componentes

Dentro de la paleta de componentes, podemos encontrar una gran cantidad de elementos que podemos agregar a nuestra
ventana, sin embargo, no todos los elementos son visibles en la paleta, por lo que deberemos de buscarlos dentro de la
barra de búsqueda.

## Las opciones de los componentes

Al seleccionar un componente, podemos ver las opciones que este tiene, y en caso de no encontrar alguna opción, podemos
usar la opción `Custom Create` para crear un componente de forma manual, y así poder personalizarlo a nuestro gusto.

Aunque también podemos ver las opciones de los componentes en la ventana de propiedades, en la pestaña `Properties`.