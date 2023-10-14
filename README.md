# Análisis-de-Hábitos-de-Compra-en-Instacart

# Introducción
Instacart es una plataforma de entregas de comestibles donde la clientela puede registrar un pedido y hacer que se lo entreguen, similar a Uber Eats y Door Dash. El conjunto de datos que te hemos proporcionado tiene modificaciones del original. Redujimos el tamaño del conjunto para que tus cálculos se hicieran más rápido e introdujimos valores ausentes y duplicados. Tuvimos cuidado de conservar las distribuciones de los datos originales cuando hicimos los cambios.

Debes completar tres pasos. Para cada uno de ellos, escribe una breve introducción que refleje con claridad cómo pretendes resolver cada paso, y escribe párrafos explicatorios que justifiquen tus decisiones al tiempo que avanzas en tu solución. También escribe una conclusión que resuma tus hallazgos y elecciones.

# Plan de solución de la primera sección
Importar librerías: Iniciaremos importando la librería pandas, que nos permitirá trabajar con los DataFrames y realizar operaciones de análisis de datos.

Leer Conjuntos de Datos en DataFrames: Utilizaremos la función pd.read_csv() para leer cada uno de los archivos de datos. Es importante asegurarse de especificar los parámetros adecuados para leer los datos correctamente. Cada archivo se leerá en un DataFrame separado.

Mostrar Información del DataFrame: Utilizaremos el método .info() en cada uno de los DataFrames creados. Este método proporciona información esencial sobre la estructura de los datos, incluyendo el número de filas, el número de columnas, los tipos de datos en cada columna y si hay valores nulos. Esta información es crucial para comprender la calidad de los datos y decidir cómo proceder en los pasos siguientes.

# Conclusiones de la primera sección
Al parecer los datos no contienen valores nulos, lo que es una buena señal para continuar con el análisis de datos. Sin embargo, se debe considerar el manejo de valores duplicados, ya que se mencionó que se introdujeron valores duplicados en el conjunto de datos.

# Plan de solución de la segunda sección
Verificar y corregir los tipos de datos: Para las columnas que representan identificadores (por ejemplo, 'order_id', 'user_id', 'product_id', 'aisle_id', 'department_id'), confirmaremos que los tipos de datos sean números enteros. Si alguna de estas columnas no tiene el tipo de dato correcto, la convertiremos a tipo entero.

Identificar y completar los valores ausentes: Revisaremos cada DataFrame para identificar si existen valores ausentes en alguna columna. En caso de encontrar valores ausentes, determinaremos si podemos completarlos de manera significativa o si es necesario eliminar las filas correspondientes.

Identificar y eliminar los valores duplicados: Buscaremos duplicados en función de las características únicas de cada conjunto de datos para cada DataFrame. Si encontramos filas duplicadas, evaluaremos si deben ser eliminadas o si reflejan información legítima.

# Conclusiones de la segunda sección
En el proceso de preparación de datos de Instacart:

Se corrigieron los tipos de datos, asegurando que las columnas de identificación fueran números enteros.

Se llenaron valores faltantes: En productos, se agregó "Unknown" para productos sin nombre en ciertos pasillos y departamentos; En pedidos, se encontraron valores faltantes en 'days_since_prior_order', pero solo en el primer pedido de cada cliente, lo que tiene sentido; En order_products, se llenaron los valores faltantes en 'add_to_cart_order' con 999 y se convirtieron a enteros.

Se eliminaron duplicados: En pedidos, se eliminaron pedidos duplicados; En productos, se identificaron nombres de productos duplicados, incluso con diferencias de mayúsculas/minúsculas.

Podemos decir que estos pasos aseguraron que los datos estuvieran limpios y listos para análisis, abordando valores faltantes y duplicados.

# Conclusiones de la tercera sección
Las verificaciones realizadas en los datos de la columna 'order_hour_of_day' y 'order_dow' en la tabla 'orders' confirman que todos los valores son sensibles y se encuentran dentro de los rangos esperados. Esto indica que los registros de pedidos tienen horarios y días de la semana coherentes y válidos para realizar el análisis.

La mayoría de los pedidos se realizan durante las horas diurnas, con un pico alrededor de las 10:00 a. m. Hay una disminución significativa de pedidos durante las horas nocturnas y una pequeña cantidad temprano en la mañana.

La mayoría de las personas compran víveres principalmente los días domingo y lunes, seguidos por el día martes. Los días viernes y sábados también tienen un número significativo de pedidos de víveres, mientras que los miércoles y jueves, son los días en los que se realizan menos pedidos de víveres en comparación con los demás días.

El tiempo que las personas esperan para hacer otro pedido en Instacart varía ampliamente. El valor mínimo es de 0 días, lo que indica compras diarias, mientras que el valor máximo es de 30 días, sugiriendo compras mensuales. La mayoría espera entre 5 y 15 días, Sin embargo, un alto número de personas también esperan los 30 días.

En términos generales, los patrones de compra de los miércoles y sábados son bastante similares. Ambos días experimentan picos de actividad de compra entre las 9 de la mañana y las 4 de la tarde, seguidos de una disminución gradual en la noche. Sin embargo, hay una ligera diferencia en el momento exacto de los picos. Los miércoles muestran su punto máximo de actividad un poco más temprano en el día, mientras que los sábados alcanzan su punto máximo un poco más tarde, lo que sugiere que las personas tienden a hacer compras un poco más tarde los sábados en comparación con los miércoles.

La distribución del número de pedidos por cliente en Instacart muestra que la mayoría de los clientes han realizado un solo pedido, seguido de un descenso gradual en la cantidad de clientes a medida que aumenta el número de pedidos. En resumen, la mayoría de los clientes realizan entre 1 y 10 pedidos, con solo pocos clientes que han realizado más.

Podemos apreciar que los 20 productos más populares en Instacart son principalmente productos orgánicos, frutas y verduras. Esto podría indicar una preferencia por alimentos frescos y saludables entre los clientes.

En promedio, las personas compran alrededor de 10.099 productos por pedido en Instacart, con una mediana de 8 productos por pedido. La distribución muestra que la mayoría de los pedidos tienen entre 1 y 15 productos, aunque hay casos extremos, como o pedidos con hasta 127 productos. Esto sugiere que la mayoría de los clientes realizan pedidos de tamaño moderado, pero también hay variabilidad en el número de productos por pedido.

Los 20 principales productos que los clientes vuelven a pedir con mayor frecuencia en sus compras posteriores incluyen una variedad de alimentos orgánicos como frutas, verduras y productos lácteos. Esto sugiere que los clientes valoran la calidad y la frescura de estos productos y optan por comprarlos de nuevo en pedidos posteriores. Además, se incluyen productos básicos como bananas, cebollas y ajo, lo que indica que los clientes tienden a reabastecer sus despensas con productos esenciales en sus compras recurrentes.

El conjunto de datos proporciona información sobre la repetición de productos en los pedidos. La tasa de repetición muestra cuántas veces se vuelve a pedir un producto en comparación con el total de veces que se ha pedido, mientras que la "proporción de veces que se vuelve a pedir" es similar pero no se rellena con ceros, lo que permite identificar productos que rara vez se vuelven a pedir.

En promedio, alrededor del 59.96% de los productos que los clientes compran son productos que ya habían pedido anteriormente. Esto indica una tendencia a la repetición de compra de productos específicos por parte de los clientes.

Los 20 principales artículos que las personas suelen poner primero en sus carritos incluyen productos básicos como leche, frutas y verduras, así como bebidas como agua y soda. Podemos decir que estos son productos orgánicos y saludables.
