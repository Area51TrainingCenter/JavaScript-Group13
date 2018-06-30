# Funciones

## Tradicionales
```js
function saludo(mensaje) {
  console.log(mensaje);
};

saludo('hola!');
```
```js
const saludo = function (mensaje) {
  console.log(mensaje);
};

saludo('hola!');
```

## Tipo flecha
```js
const saludo = (mensaje) => {
  console.log(mensaje);
};

saludo('hola!');
```
```js
const saludo = (mensaje) => {
  console.log(mensaje);
};

saludo('hola!');
```
También tenemos una forma abreviada solo posible cuando se maneja solo un parámetro, una sola línea de código dentro de la función y que retornará un resultado.
```js
const elevadorAlCuadrado = (n) => { return n * n }
elevadoAlCuadrado(3);
```
```js
const elevadorAlCuadrado = n => n * n;
elevadoAlCuadrado(3);
```

## Ejercicios

### Ejercicio 1

1. Crear una variable que contenga un Array.
2. Crear una función "flecha" que reciba 2 parámetros
3. Dentro de la función concatenar los 2 parámetros
4. El valor concatenado agregarlo al Array

```js
const miLista = [];

const agregarALaLista = (cantidad, ingrediente) => {
  const resultado = cantidad + ingrediente;

  miLista.push(resultado);
}

agregarALaLista(3, 'Panes');
```

### Ejercicio 2

1. Crear una variable que contenga un Array.
2. Crear una función "flecha" que reciba 2 parámetros
3. Dentro de la función crear un objeto que reciba los 2 parámetros
4. El objeto agregarlo al Array

```js
// Forma 1
const miLista = [];

const agregarALaLista = (cantidad, ingrediente) => {
  const item = { cantidad: cantidad, ingrediente: ingrediente };
  miLista.push(item);
  // o
  // miLista.push({ cantidad: cantidad, ingrediente: ingrediente });
}

agregarALaLista(10, 'Panes');
agregarALaLista(1, 'Leche');
agregarALaLista(6, 'Huevos');
```
```js
// Forma 2
const miLista = [];

const agregarALaLista = (cantidad, ingrediente) => {
  const item = {};
  item.cantidad = cantidad;
  item.ingrediente = ingrediente;

  miLista.push(item);
}

agregarALaLista(10, 'Panes');
agregarALaLista(1, 'Leche');
agregarALaLista(6, 'Huevos');
```

# Condicionales

## Operadores condicionales
```js
> // mayor que
< // menor que
>= // mayor o igual que
<= // menor o igual que
=== // igual a (estricto)
!== // distinto de (estricto)
== // igual a
!= // distinto de
```

## Negacion (!)
```js
const soltero = false;

// si soy soltero
if (soltero) {
  console.log('soy soltero');
}

// si no es soltero
if (!soltero) {
  console.log('no soy soltero');
}
```

## Estructuras if, else
```js
const nota = 20;

if (nota > 10) {
  console.log('aprobaste');
} else {
  console.log('jalaste');
}
```
```js
const nota = 9;

if (nota > 10) {
  console.log('aprobaste');
} else {
  if (nota > 8) {
    console.log('susti');
  } else {
    console.log('jalaste');
  }
}
```
```js
const nota = 9;
const vaASustitutorio = false;

if (nota > 8 && nota <= 10) {
  vaASustitutorio = true;
}

console.log('Va a sustitutorio:', vaASustitutorio);
```

# Array: .forEach, .map, .filter y .reduce

## .forEach

Recibe un parámetro de tipo `Function` en el cual se
recorre uno a uno cada elemento del Array.

### Ejemplos

```js
const numeros = [1, 2, 3];

const mostrarEnConsola = (item) => {
  console.log(item);
};

numeros.forEach(mostrarEnConsola);
// 1
// 2
// 3
```
```js
const numeros = [1, 2, 3];

numeros.forEach(item => console.log(item));
// 1
// 2
// 3
```

## .map

Igual a `.forEach` con la diferencia que ese retorna un Array con la misma cantidad de elementos de Array original. Este contendrá el resultado que devolvamos a través de la función que pasamos en el primer parámetro.

### Ejemplos

```js
const numeros = [1, 2, 3];

const sumarUno = (item) => {
  return item + 1;
};

const numerosNuevos = numeros.map(sumarUno);
console.log(numerosNuevos);
// [2, 3, 4]
```
```js
const numeros = [1, 2, 3];

const numerosNuevos = numeros.map(item => item + 1);

console.log(numerosNuevos);
// [2, 3, 4]
```

## .filter

### Ejemplos

Ejemplo 1

```js
const notas = [13, 20, 7, 11, 9];

const esAprobado = (nota) => {
  return (nota > 10);
};

const notasDeAprobados = notas.filter(esAprobado);

console.log(notasDeAprobados);
// [13, 20, 11]
```
```js
const notas = [13, 20, 7, 11, 9];

const notasDeAprobados = notas.filter(nota => nota > 10);

console.log(notasDeAprobados);
// [13, 20, 11]
```

Ejemplo 2

```js
const amigos = ['Mateo', 'Lucas', 'Juan', 'Judas'];

const culpable = (item) => {
	if (item === 'Judas') {
		return true;
	} else {
		return false;
	}
};

const amigoCulpable = amigos.filter(culpable);

console.log(amigoCulpable);
// ["Judas"]
```
```js
// Forma un poco mas corta

const amigos = ['Mateo', 'Lucas', 'Juan', 'Judas'];

const culpable = (item) => {
	return (item === 'Judas');
};

const amigoCulpable = amigos.filter(culpable);

console.log(amigoCulpable);
// ["Judas"]
```
```js
// Forma mas corta

const amigos = ['Mateo', 'Lucas', 'Juan', 'Judas'];

const amigoCulpable = amigos.filter(item => item === 'Judas');

console.log(amigoCulpable);
// ["Judas"]
```

## .reduce

### Ejemplos

```js
const numeros = [1, 2, 3];

const sumar = (a, b) => {
  return a + b;
};

const resultado = numeros.reduce(sumar);
console.log(resultado);
// 6
```
```js
const numeros = [1, 2, 3];

const resultado = numeros.reduce((a, b) => a + b);

console.log(resultado);
// 6
```

Obtener las edades y sacar el promedio de ellas.

```js
const personas = [
  { nombre: 'pedro', edad: 18 },
  { nombre: 'juan', edad: 23 },
  { nombre: 'alberto', edad: 21 },
  { nombre: 'diana', edad: 27 },
  { nombre: 'jessica', edad: 32 }
];

const obtenerEdad = (item) => {
  return item.edad;
};

const edades = personas.map(obtenerEdad);
// edades = [18, 23, 21, 27, 32]

const sumar = (a, b) => {
  return a + b;
};

const promedio = (lista) => {
  return lista.reduce(sumar) / lista.length;
};

const promedioDeEdades = promedio(edades);
console.log('Promedio de edades:', promedioDeEdades);
// "Promedio de edades:" 24.2
```
```js
// Forma un poco mas abreviada

const personas = [
  { nombre: 'pedro', edad: 18 },
  { nombre: 'juan', edad: 23 },
  { nombre: 'alberto', edad: 21 },
  { nombre: 'diana', edad: 27 },
  { nombre: 'jessica', edad: 32 }
];

const edades = personas.map(item => item.edad);
// edades = [18, 23, 21, 27, 32]

const promedio = (lista) => {
  return lista.reduce((a, b) => a + b) / lista.length;
};

const promedioDeEdades = promedio(edades);
console.log('Promedio de edades:', promedioDeEdades);
// "Promedio de edades:" 24.2
```
```js
// Forma mas abreviada

const personas = [
  { nombre: 'pedro', edad: 18 },
  { nombre: 'juan', edad: 23 },
  { nombre: 'alberto', edad: 21 },
  { nombre: 'diana', edad: 27 },
  { nombre: 'jessica', edad: 32 }
];

const edades = personas.map(item => item.edad);
// edades = [18, 23, 21, 27, 32]

const promedioDeEdades = edades.reduce((a, b) => a + b) / edades.length;
console.log('Promedio de edades:', promedioDeEdades);
// "Promedio de edades:" 24.2
```

Obtener los nombres y poner su primera letra en mayúsculas.
```js
const personas = [
  { nombre: 'pedro', edad: 18 },
  { nombre: 'juan', edad: 23 },
  { nombre: 'alberto', edad: 21 },
  { nombre: 'diana', edad: 27 },
  { nombre: 'jessica', edad: 32 }
];

const empezarConMayusculas = texto => {
	const letraEnMayusculas = texto.substr(0, 1).toUpperCase();
	const restoDelTextoEnMinusculas = texto.substr(1).toLowerCase();

	return letraEnMayusculas + restoDelTextoEnMinusculas;
}

const nombreConMayusculas = (item) => {
	return item.nombre;
};

const personasNombres = personas.map(nombreConMayusculas);
```