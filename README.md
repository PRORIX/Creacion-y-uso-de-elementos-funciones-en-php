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
