+++
weight = 2
date = "2017-03-23T03:00:00Z"
title = "JS - Valores y sus Tipos"
description = "Son los valores quienes definen el tipo, no las variables."
tags = ["javascript"]
+++

JS es un lenguaje NO tipado, por lo que -a diferencia de la mayoría de lenguajes- las variables son declaradas sin un tipo definido. Lo que significa que una variable puede tener tu nombre (string), y luego puedes sobrescribir este valor por tu edad (number).

Los Valores (nombre, edad) son los que llevan consigo una definición o Tipo.

#### ¿Y de qué tipo pueden ser los valores?

* **string**
* **number**
* **boolean**
* **null**
* **undefined**
* **object**
* **symbol** (este vino nuevo con ES6)

#### ¿Cómo puedo saber que tipo de valor tiene asignado una variable?

Utilizando el operador `typeof` de esta manera:

```javascript
var x;
typeof x; // "undefined"


x = "Juancho";
typeof x; // "string"


x = 7;
typeof x; // "number"


x = true;
typeof x; // "boolean"


x = null;
typeof x; // "object" - :confused:


x = undefined;
typeof x; // "undefined"


x = { y: "z"};
typeof x; // "object"
```

El valor que retorna `typeof` SIEMPRE es un string indicando el tipo.

También se puede notar que el operador no está verificando el tipo de variable -ya dijimos que las variables no tienen tipo-, sino el tipo de Valor que tiene en el momento. 

#### :fire: Ok todo pero, ¿Por qué null es de tipo "object"? ¿No debería ser tipo "null"?
Por lo que he investigado, esto es un Bug de JavaScript que lleva años -creo que desde sus inicios-, pero que no creo que arreglen porque muchas cosas ya depende de este comportamiento extraño. Es importante tenerlo en cuenta si por ejemplo:

**Detectar si una variable es de tipo "object", pero puede ser null en algún momento**

```javascript
var bar = {a: "b"};
if(...) {
    bar = null; //alguna condición hace que sea null
}

console.log(typeof bar === "object");  // true - oops, no queríamos esto! :scream:
```

Una posible solución sería algo como:

```javascript
console.log((bar !== null) && (typeof bar === "object"));
```

Más adelante veremos por qué esta solución no es del todo correcta, pero por ahora va bien!