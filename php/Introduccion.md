

¿Qué es PHP? es un lenguaje de programación de código abierto muy popular y ampliamente utilizado, especialmente para el desarrollo web del lado del servidor,
PHP se utiliza comúnmente para desarrollar sitios web dinámicos, aplicaciones web, sistemas de gestión de contenido (CMS) como WordPress, y muchas otras aplicaciones web. 

-Como declarar un Print (Imprimir un texto en la pantalla):
echo "Hola mundo";

"VARIABLES"
-Como declarar una variable:
$nombre = "Nombre"; --> Variable chart 
$numero = 7; -->Números enteros 
$numero_decimal = 7.7; --> Numero flotantes
$verdadero = true; --> Números boléanos

//No se necesita especificar de que tipo es (float, chart. int)
//La sintaxis siempre será empezar con el signo " $ " y terminar con " ; "
 
 Para tener buenas practicas es mucho mejor utilizar comillas simples
 echo 'Hola ' . $nombre;  //El punto es para concatenar (indicar que quieres juntar la variable al String) 

Si queremos saber que tipo de variable es la que estamos utilizando esta la función gettype.

echo gettype($nombre); --> y se tendría que mostrar en pantalla el tipo de datos que es

"CONSTANTES"
-Como declarar constantes (Algo ya predefinido que no va a cambiar) 
//Las constantes no llevan comillas
define('PI', 3.1416); -->INT
define('nombre', 'Daniela')
echo PI; --> Esto es solo para que se muestre en pantalla 

"ARREGLOS"
-Como declarar un arreglo (Un arreglo es una variable que puede almacenar mucha información)
$semana = array('Lunes' , 'Martes' , 'Miércoles' , 'Jueves' , 'Viernes' , 'Sábado' , 'Domingo');

-Dentro de arreglos existe otro que se llama arreglos asociativos, lo que los diferencia es que a los valores que tiene dentro se les puede agregar sus propios valores, inserto ejemplo:

$gael = array('teléfono' => '6692239400', 'edad' => '20', 'apellido' => 'Bustamante', 'país' => 'México' );
//Y para verlos en pantalla es casi igual que el primer arreglo
echo  $gael['teléfono'];
echo  $gael['edad'];
echo  $gael['apellido'];
echo  $gael['país'];
//si quiero modificar tendría que ser así
$gael['teléfono'] = '6691633467';
echo $gael['teléfono'];




