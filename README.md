# Acceso a datos
## Tarea: Creación y uso de elementos funciones en php
## Alumno: Romen Gilberto Garcia Gomez (PRORIX)


### EJERCICIO 1: Numero capicua
#### Implementa una funcion esCapicua que determine si un numero entero positivo es capicua

Code:

```php

<?php
declare(strict_types=1);

/**
* EJERCICIO 1
* @author prorix
* @version 1.0.0
*/

$numeroCapicua = 123321;
$numeroNoCapicua = 123;
$numeroNoValido = -123321;

echo "$numeroCapicua? " . var_export(esCapicua($numeroCapicua), true) . "<br>";
echo "$numeroNoCapicua? " . var_export(esCapicua($numeroNoCapicua), true) . "<br>";
echo "$numeroNoValido? " . var_export(esCapicua($numeroNoValido), true) . "<br>";

/** 
* Metodo que comprueba si un numero dado es capicua
* @param n numero dado
* @return True / False
*/
function esCapicua(int $n): bool {
    if ($n < 0) {
        echo "$n es un numero negativo.<br>";
        return false;
    } else {
        $numeroInvertido = strrev((string)$n);
        return (string)$n === $numeroInvertido;
    }
}
?>

```

Output:

```

123321? true
123? false
-123321 es un numero negativo.
-123321? false

```


### EJERCICIO 2: Escalera de asteriscos
#### Implementa una funcion montañaAsteriscos que imprima una escalera de asteriscos de altura n y tamanio m

Code:

```php

<!DOCTYPE html>
<html>
<body>

<?php

/**
* EJERCICIO 2
* @author prorix
* @version 1.0.0
*/

$ejemplos = montaniaAsteriscos(4, 2);

echo "<pre>" . implode("\n", $ejemplos) . "</pre>";

/** 
* Metodo que construye una escalera de asteriscos
* @param n numero dado
* @return True / False
*/
function montaniaAsteriscos(int $n, int $m): array {
    $solucion = [];

    for ($i = 1; $i <= $n; $i++) {
        $linea = "";
        $huecos = str_repeat(" ", $n - $i);
        $puntos  = str_repeat("*", $i);

        for ($j = 0; $j < $m; $j++) {
            if ($j % 2 != 0) {
                $linea .= $huecos . $puntos;
            } else {
                $linea .= $puntos . $huecos;
            }
        }

        $solucion[] = $linea;
    }

    return $solucion;
}
?>

</body>
</html>

```

Output:

```

*      *
**    **
***  ***
********

```


### EJERCICIO 3: Suma de digitos
#### Implementa una funcion sumaDigitos que calcule la suma de los digitos de un numero positivo.

Code:

```php

<!DOCTYPE html>
<html>
<body>

<?php

/**
* EJERCICIO 3
* @author prorix
* @version 1.0.0
*/

$numeroValido = 12345;
$numeroNegativo = -12345;
$numeroDecimal = 123.45;

sumaDigitos($numeroValido);
sumaDigitos($numeroNegativo);
sumaDigitos($numeroDecimal);

/** 
* Metodo que suma los digitos de un numero
* @param n numero dado
* @return suma
*/
function sumaDigitos($n) {
    if (!is_int($n) || $n < 0) {
        echo "El numero ha de ser un entero positivo.<br>";
    } else {
        $digitos = str_split((string)$n);
        $suma = array_sum(array_map('intval', $digitos));
        echo "La suma de los dígitos de $n da $suma<br>";
    }
}

?>

</body>
</html>

```

Code:

```

La suma de los dígitos de 12345 da 15
El numero ha de ser un entero positivo.
El numero ha de ser un entero positivo.

```


### EJERCICIO 4: Numero secreto
#### Implementa una funcion multiplosTresOCinco(int $n): array que devuelva todos los multiplos de 3 o 5 menores que N

Code:

```php

<!DOCTYPE html>
<html>
<body>

<?php

/**
* EJERCICIO 4
* @author prorix
* @version 1.0.0
*/

$numero = 20;
$numeros=multiplosTresOCinco($numero);
$suma=0;

foreach($numeros as $numero){
    echo $numero . " ";
    $suma+=$numero;
}

echo "<br> Suma = $suma";

/** 
* Metodo que devuelve una lista con los multiplos de 3 o 5 menores que un numero dado
* @param n numero dado
* @return numeros y suma
*/
function multiplosTresOCinco(int $n): array{

	$listaNumeros = [];

	for ($i = $n -1 ; $i >= 0 ; $i--){
    	if ( $i % 3 == 0 || $i % 5 == 0 ){
        	array_push($listaNumeros, $i);
        }
    }
    
    return $listaNumeros;

}

?>

</body>
</html>

```

Output:

```

18 15 12 10 9 6 5 3 0
Suma = 78

```



### EJERCICIO 5: Secuencia de Collatz
#### Implementa una funcion secuenciaCollatz que genere la secuencia Collatz a partir de un entero positivo

Code:

```php

<!DOCTYPE html>
<html>
<body>

<?php

/**
* EJERCICIO 5
* @author prorix
* @version 1.0.0
*/

$numero = 6;
$numeros=multiplosTresOCinco($numero);

foreach($numeros as $numero){
    echo $numero . " ";
}


/** 
* Metodo que devuelve una lista con los multiplos de 3 o 5 menores que un numero dado
* @param n numero dado
* @return numeros y suma
*/
function multiplosTresOCinco(int $n): array{

	$listaNumeros = [];

	while($n != 1){
    	if ($n % 2 == 0){
        	array_push($listaNumeros, $n);
        	$n = $n / 2;
        } else {
            array_push($listaNumeros, $n);
        	$n = ($n * 3) + 1;
        }
    }
   	array_push($listaNumeros, 1);
    return $listaNumeros;

}

?>

</body>
</html>

```

Output:

```

6 3 10 5 16 8 4 2 1

```
