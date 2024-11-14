# Tutorial Introducció JavaScript

## 1. Conceptes Bàsics de JavaScript

### 1. Introducció a JavaScript

- **Què és JavaScript?**

  - JavaScript és un llenguatge de programació utilitzat per afegir interactivitat a les pàgines web. Funciona en el navegador i permet manipular HTML i CSS per crear experiències web dinàmiques i interactives.

- **Configuració: On Escriure JavaScript**
  - Obre un editor de text (com VSCode) o prova d'escriure directament a la consola del navegador.
  - Pots incrustar JavaScript en un fitxer HTML dins de les etiquetes `<script>`:
    ```html
    <script>
      // El teu codi JavaScript va aquí
    </script>
    ```
  - O al document `html`, al `head` amb `<script defer src="script.js"></script>`
  - També podem executar JavaScript amb `node.js`

### 2. Hello World: mostrar text per consola

- **Codi:**
  ```javascript
  console.log("Hello, World!");
  ```
- **Explicació:** `console.log()` mostra el text dins dels parèntesis a la consola. Obre les eines de desenvolupador del teu navegador (normalment `F12`) per veure el resultat.

---

### 3. Variables i Tipus de Dades

- **Tipus de Variables:** `let`, `const`, i `var`.

  - **`let`**: Variable de bloc que es pot modificar.
  - **`const`**: Variable de bloc que no es pot modificar.
  - **`var`**: deprecated (estil més antic), es recomana utilitzar `let`.

- **Sintaxi Bàsica:**
  ```javascript
  let name = "Alice"; // String
  const age = 25; // Number
  let isStudent = true; // Boolean
  ```
- **Explicació:** Les variables emmagatzemen dades que pots utilitzar i manipular en el teu codi. Alguns tipus de dades inclouen strings, nombres i booleans.

---

### 4. Operadors

- **Exemples d'Operadors:**

  - **Operadors aritmètics:** `+`, `-`, `*`, `/`, `%`
  - **Operadors de comparació:** `==`, `!=`, `>`, `<`, `>=`, `<=`
  - **Operadors lògics:** `&&` (AND), `||` (OR), `!` (NOT)

- **Codi:**
  ```javascript
  let x = 10;
  let y = 5;
  console.log(x + y); // Sortida: 15
  console.log(x > y); // Sortida: true
  console.log(x === y); // Sortida: false
  ```

---

### 5. Condicionals

- **Sintaxi:**
  ```javascript
  let age = 18;
  if (age >= 18) {
    console.log("Ets un adult.");
  } else {
    console.log("Ets menor d'edat.");
  }
  ```
- **Explicació:** Les sentències `if` permeten executar codi només si es compleix una certa condició. `else` proporciona una alternativa si la condició és falsa.

---

### 6. Bucles

- **Tipus de Bucles:** `for`, `while`, i `do...while`
  - **For Loop:**
    ```javascript
    for (let i = 0; i < 5; i++) {
      console.log(i); // Sortida: 0, 1, 2, 3, 4
    }
    ```
  - **While Loop:**
    ```javascript
    let i = 0;
    while (i < 5) {
      console.log(i); // Sortida: 0, 1, 2, 3, 4
      i++;
    }
    ```
- **Explicació:** Els bucles ajuden a automatitzar tasques repetitives executant un bloc de codi diverses vegades.

---

### 7. Funcions

- **Sintaxi:**
  ```javascript
  function greet(name) {
    return "Hello, " + name;
  }
  console.log(greet("Alice")); // Sortida: "Hello, Alice"
  ```
- **Explicació:** Les funcions permeten encapsular codi en un sol lloc i reutilitzar-lo cridant la funció.

---

### 8. Arrays

- **Sintaxi:**
  ```javascript
  let fruits = ["Apple", "Banana", "Orange"];
  console.log(fruits[1]); // Sortida: "Banana"
  ```
- **Explicació:** Els arrays són llistes que poden emmagatzemar múltiples valors. Accedeix als elements usant el seu índex (posició en l’array).

---

### 9. Objects

- **Sintaxi:**
  ```javascript
  let person = {
    name: "Alice",
    age: 25,
    isStudent: true,
  };
  console.log(person.name); // Sortida: "Alice"
  ```
- **Explicació:** Els objects són col·leccions de dades relacionades. Cada propietat té una clau (nom) i un valor (dada associada).

### 10. Operadors `==` i `===`

En JavaScript, `==` i `===` són operadors de comparació, però funcionen de manera diferent:

#### `==` (Operador d'Igualtat)

- **Conversió de Tipus**: L'operador `==` comprova la igualtat **després** de convertir els dos valors a un tipus comú si són de tipus diferents. Aquest procés es coneix com a _conversió de tipus_.
- **Ús**: Sovint es diu "igualtat laxa" perquè no compara estrictament els tipus dels valors, fet que de vegades pot donar lloc a resultats inesperats.

**Exemples**:

```javascript
console.log(5 == "5"); // true (la cadena "5" es converteix en el número 5)
console.log(false == 0); // true (false es converteix en el número 0)
console.log(null == undefined); // true (es consideren iguals en comparació laxa)
```

#### `===` (Operador d'Igualtat Estricta)

- **Sense Conversió de Tipus**: L'operador `===`, sovint anomenat "igualtat estricta", comprova la igualtat **sense** convertir els tipus. Tant el valor com el tipus han de ser idèntics perquè `===` retorni `true`.
- **Ús**: És preferible per a la majoria de comparacions, ja que evita conversions de tipus inesperades, cosa que fa que el codi sigui més previsible.

**Exemples**:

```javascript
console.log(5 === "5"); // false (tipus diferents: número vs. cadena)
console.log(false === 0); // false (tipus diferents: booleà vs. número)
console.log(null === undefined); // false (tipus diferents: null vs. undefined)
console.log(5 === 5); // true (el tipus i el valor són els mateixos)
```

#### Resum

- Utilitza `==` quan vulguis comprovar la igualtat amb conversió de tipus.
- Utilitza `===` quan vulguis comprovar la igualtat sense conversió de tipus (recomanat per obtenir resultats predictibles).

En general, **utilitzar `===` és més segur** i ajuda a evitar errors relacionats amb la conversió de tipus implícita.

## Exercicis

### Exercici 1: Canvi de Temperatura

Escriu una funció que converteixi una temperatura de graus Celsius a Fahrenheit.

**Instruccions:**

1. Crea una funció `celsiusToFahrenheit` que accepti una temperatura en graus Celsius com a paràmetre.
2. La funció ha de retornar la temperatura equivalent en graus Fahrenheit.
3. La fórmula per convertir Celsius a Fahrenheit és: `(Celsius * 9/5) + 32`.

<details>
<summary> <strong style="color: #006A67">Solució: </strong> </summary>

```javascript
function celsiusToFahrenheit(celsius) {
  return (celsius * 9) / 5 + 32;
}

// Exemple d'ús
console.log(celsiusToFahrenheit(25)); // Sortida: 77
```

**Explicació:** La funció `celsiusToFahrenheit` agafa un valor en graus Celsius i l’utilitza en la fórmula de conversió per retornar el valor en Fahrenheit.

</details>

---

### Exercici 2: Verificar Nombre Parell o Senar

Escriu una funció que determini si un nombre és parell o senar.

**Instruccions:**

1. Crea una funció `isEven` que accepti un número com a paràmetre.
2. La funció ha de retornar `true` si el número és parell i `false` si és senar.

<details>
<summary> <strong style="color: #006A67">Solució: </strong> </summary>

```javascript
function isEven(number) {
  return number % 2 === 0;
}

// Exemple d'ús
console.log(isEven(4)); // Sortida: true
console.log(isEven(7)); // Sortida: false
```

**Explicació:** La funció `isEven` utilitza l'operador `%` (mòdul) per verificar si el residu de `number / 2` és 0. Si és 0, el número és parell; si no, és senar.

</details>

---

### Exercici 3: Comptar Lletres en una Frase

Escriu una funció que compti el nombre de vegades que una lletra específica apareix en una frase.

**Instruccions:**

1. Crea una funció `countLetter` que accepti una frase (`string`) i una lletra (`char`) com a paràmetres.
2. La funció ha de retornar el nombre de vegades que la lletra apareix en la frase.

<details>
<summary> <strong style="color: #006A67">Solució: </strong> </summary>

```javascript
function countLetter(phrase, letter) {
  let count = 0;
  for (let i = 0; i < phrase.length; i++) {
    if (phrase[i] === letter) {
      count++;
    }
  }
  return count;
}

// Exemple d'ús
console.log(countLetter("javascript", "a")); // Sortida: 2
```

**Explicació:** La funció `countLetter` recorre cada lletra de la frase i incrementa el `count` si troba una coincidència amb la lletra especificada.

</details>

---

### Exercici 4: FizzBuzz

Escriu una funció que imprimeixi els nombres de l'1 al 20, però seguint aquestes regles:

- Si el nombre és divisible per 3, mostra `"Fizz"`.
- Si el nombre és divisible per 5, mostra `"Buzz"`.
- Si el nombre és divisible per 3 i per 5, mostra `"FizzBuzz"`.
- Si no és divisible ni per 3 ni per 5, mostra el nombre.

<details>
<summary> <strong style="color: #006A67">Solució: </strong> </summary>

```javascript
function fizzBuzz() {
  for (let i = 1; i <= 20; i++) {
    if (i % 3 === 0 && i % 5 === 0) {
      console.log("FizzBuzz");
    } else if (i % 3 === 0) {
      console.log("Fizz");
    } else if (i % 5 === 0) {
      console.log("Buzz");
    } else {
      console.log(i);
    }
  }
}

// Exemple d'ús
fizzBuzz();
```

**Explicació:** La funció `fizzBuzz` utilitza un bucle `for` per recórrer els números de l'1 al 20 i comprova les condicions amb `if...else if` per mostrar el resultat corresponent.

</details>

---

### Exercici 5: Calcular el Factorial d'un Número

Escriu una funció que calculi el factorial d’un nombre.

**Instruccions:**

1. Crea una funció `factorial` que accepti un número com a paràmetre.
2. La funció ha de retornar el factorial del número. El factorial de `n` és `n * (n - 1) * ... * 1`.

<details>
<summary> <strong style="color: #006A67">Solució: </strong> </summary>

```javascript
function factorial(number) {
  let result = 1;
  for (let i = 1; i <= number; i++) {
    result *= i;
  }
  return result;
}

// Exemple d'ús
console.log(factorial(5)); // Sortida: 120
```

**Explicació:** La funció `factorial` utilitza un bucle `for` per multiplicar cada número de l'1 al número especificat i així obtenir el factorial.

</details>

---

### Exercici 6: Trobar el Màxim en un Array

Escriu una funció que trobi el valor màxim dins d’un array de nombres.

**Instruccions:**

1. Crea una funció `findMax` que accepti un array de nombres com a paràmetre.
2. La funció ha de retornar el valor més alt dins de l’array.

<details>
<summary> <strong style="color: #006A67">Solució: </strong> </summary>

```javascript
function findMax(numbers) {
  let max = numbers[0];
  for (let i = 1; i < numbers.length; i++) {
    if (numbers[i] > max) {
      max = numbers[i];
    }
  }
  return max;
}

// Exemple d'ús
console.log(findMax([3, 7, 2, 8, 5])); // Sortida: 8
```

**Explicació:** La funció `findMax` compara cada element de l’array amb el valor actual de `max` i actualitza `max` si troba un número més gran.

</details>

---

### Exercici 7: Comprovar si una Paraula és Palíndrom

Escriu una funció que comprovi si una paraula és un palíndrom (la mateixa paraula si es llegeix de dreta a esquerra o d'esquerra a dreta).

**Instruccions:**

1. Crea una funció `isPalindrome` que accepti una paraula com a paràmetre.
2. La funció ha de retornar `true` si la paraula és un palíndrom i `false` si no ho és.

<details>
<summary> <strong style="color: #006A67">Solució: </strong> </summary>

```javascript
function isPalindrome(word) {
  for (let i = 0; i < word.length / 2; i++) {
    if (word[i] !== word[word.length - i - 1]) {
      return false;
    }
  }
  return true;
}

// Exemple d'ús
console.log(isPalindrome("civic")); // Sortida: true
console.log(isPalindrome("javascript")); // Sortida: false
```

**Explicació:** La funció `isPalindrome` utilitza mètodes de strings per invertir la paraula i la compara amb l’original per veure si coincideixen.

</details>

---

### Exercici 8: Filtrar Nombres Positius en un Array

Escriu una funció que filtri i retorni només els nombres positius d’un array.

**Instruccions:**

1. Crea una funció `filterPositiveNumbers` que accepti un array de nombres com a paràmetre.
2. La funció ha de retornar un nou array amb només els nombres positius.

<details>
<summary> <strong style="color: #006A67">Solució: </strong> </summary>

```javascript
function filterPositiveNumbers(numbers) {
  let positives = [];
  for (let i = 0; i < numbers.length; i++) {
    if (numbers[i] > 0) {
      positives.push(numbers[i]);
    }
  }
  return positives;
}

// Exemple d'ús
console.log(filterPositiveNumbers([-2, 5, -1, 3, 0, -6, 7])); // Sortida: [5, 3, 7]
```

**Explicació:** La funció `filterPositiveNumbers` recorre cada element de l’array i afegeix els números positius a un nou array `positives`, que es retorna al final.

</details>

---

### Exercici 9: Crear una Llista amb la Suma Acumulativa

Escriu una funció que retorni un array amb la suma acumulativa de cada element fins a aquesta posició.

**Instruccions:**

1. Crea una funció `cumulativeSum` que accepti un array de nombres com a paràmetre.
2. La funció ha de retornar un nou array on cada element és la suma acumulativa dels elements anteriors i l’element actual.

<details>
<summary> <strong style="color: #006A67">Solució: </strong> </summary>

```javascript
function cumulativeSum(numbers) {
  let result = [];
  let sum = 0;
  for (let i = 0; i < numbers.length; i++) {
    sum += numbers[i];
    result.push(sum);
  }
  return result;
}

// Exemple d'ús
console.log(cumulativeSum([1, 2, 3, 4])); // Sortida: [1, 3, 6, 10]
```

**Explicació:** La funció `cumulativeSum` afegeix cada número de l'array a una variable `sum` i afegeix aquesta suma acumulativa a l'array `result`, que conté el resultat final.

</details>

## 2. Manipulació d'Arrays amb `forEach`, `map`, i `filter`

Els arrays són estructures que permeten emmagatzemar múltiples valors en una sola variable. JavaScript ofereix diversos mètodes que faciliten la manipulació dels elements d’un array de manera senzilla i elegant.

### 1. `forEach`

El mètode `forEach` permet executar una funció en cada element de l’array. Aquest mètode no retorna res; simplement recorre cada element i executa la funció.

**Sintaxi:**

```javascript
array.forEach(function (element, index) {
  // accions a fer amb cada element
});
```

- **`element`**: L'element actual de l'array.
- **`index`** (opcional): L'índex de l'element actual.

**Exemple:**

```javascript
let numbers = [1, 2, 3, 4, 5];
numbers.forEach(function (number) {
  console.log(number * 2); // Mostra el doble de cada número
});
// Sortida: 2, 4, 6, 8, 10

// o amb funcions arrow
numbers.forEach((number) => {
  console.log(number * 2); // Mostra el doble de cada número
});
```

---

### 2. `map`

El mètode `map` crea un nou array amb els resultats d'executar una funció en cada element de l'array original. És útil quan volem transformar cada element en un altre valor.

**Sintaxi:**

```javascript
let nouArray = array.map(function (element, index) {
  // retorna el nou valor per a cada element
});
```

**Exemple:**

```javascript
let numbers = [1, 2, 3, 4, 5];
let doubledNumbers = numbers.map(function (number) {
  return number * 2;
});
console.log(doubledNumbers); // Sortida: [2, 4, 6, 8, 10]

// o també

let doubledNumbers = numbers.map((number) => {
  return number * 2;
});
console.log(doubledNumbers);
```

---

### 3. `filter`

El mètode `filter` crea un nou array amb tots els elements de l'array que compleixen una condició específica. És ideal per a seleccionar o filtrar elements d’un array basant-se en una condició.

**Sintaxi:**

```javascript
let nouArray = array.filter(function (element, index) {
  // retorna true si l'element compleix la condició, false si no
});
```

**Exemple:**

```javascript
let numbers = [1, -2, 3, -4, 5];
let positiveNumbers = numbers.filter(function (number) {
  return number > 0;
});
console.log(positiveNumbers); // Sortida: [1, 3, 5]

// o també
let positiveNumbers = numbers.filter((number) => {
  return number > 0;
});
console.log(positiveNumbers);
```

---

## Exercicis Arrays

### Exercici 1: Mostrar Cada Element amb `forEach`

Utilitza `forEach` per mostrar cada element d'un array amb el seu índex.

**Instruccions:**

1. Crea una funció `printElements` que accepti un array de nombres.
2. La funció ha de recórrer l'array i mostrar cada element amb el seu índex en el format `Índex X: Valor`.

<details>
<summary> <strong style="color: #006A67">Solució: </strong> </summary>

```javascript
function printElements(array) {
  array.forEach(function (element, index) {
    console.log("Índex " + index + ": " + element);
  });
}

// Exemple d'ús
printElements([10, 20, 30, 40]);
// Sortida:
// Índex 0: 10
// Índex 1: 20
// Índex 2: 30
// Índex 3: 40
```

**Explicació:** `forEach` recorre cada element de l'array, i la funció mostra el valor de cada element juntament amb el seu índex.

 </details>

### Exercici 2: Crear un Nou Array amb `map`

Utilitza `map` per crear un nou array amb els quadrats de cada element d’un array donat.

**Instruccions:**

1. Crea una funció `squareElements` que accepti un array de nombres.
2. La funció ha de retornar un nou array amb el quadrat de cada element de l'array original.

<details>
<summary> <strong style="color: #006A67">Solució: </strong> </summary>

```javascript
function squareElements(array) {
  return array.map(function (number) {
    return number * number;
  });
}

// Exemple d'ús
console.log(squareElements([1, 2, 3, 4])); // Sortida: [1, 4, 9, 16]
```

**Explicació:** `map` recorre cada element de l’array, i retorna el quadrat de cada element en un nou array.

 </details>

### Exercici 3: Filtrar Elements Positius amb `filter`

Utilitza `filter` per obtenir només els nombres positius d’un array.

**Instruccions:**

1. Crea una funció `getPositiveNumbers` que accepti un array de nombres.
2. La funció ha de retornar un nou array amb només els nombres positius de l'array original.

<details>
<summary> <strong style="color: #006A67">Solució: </strong> </summary>

```javascript
function getPositiveNumbers(array) {
  return array.filter(function (number) {
    return number > 0;
  });
}

// Exemple d'ús
console.log(getPositiveNumbers([-3, 2, -1, 4, 5])); // Sortida: [2, 4, 5]
```

**Explicació:** `filter` recorre cada element de l'array i només afegeix els nombres positius al nou array.

 </details>

### Exercici 4: Filtrar i Doblar Elements Positius amb `filter` i `map`

Utilitza `filter` per seleccionar els nombres positius d’un array, i després `map` per crear un nou array amb el doble de cada nombre positiu.

**Instruccions:**

1. Crea una funció `doublePositiveNumbers` que accepti un array de nombres.
2. Primer, utilitza `filter` per obtenir només els nombres positius.
3. Després, utilitza `map` per crear un nou array amb el doble de cada nombre positiu.

<details>
<summary> <strong style="color: #006A67">Solució: </strong> </summary>

```javascript
function doublePositiveNumbers(array) {
  return array
    .filter(function (number) {
      return number > 0;
    })
    .map(function (number) {
      return number * 2;
    });
}

// Exemple d'ús
console.log(doublePositiveNumbers([-3, 2, -1, 4, 5])); // Sortida: [4, 8, 10]
```

**Explicació:** Primer, `filter` elimina els nombres negatius i deixa només els positius. Després, `map` multiplica cada nombre positiu per 2.

 </details>

### Exercici 5: Compta els Nombres Parells amb `filter`

Utilitza `filter` per comptar quants nombres parells hi ha en un array.

**Instruccions:**

1. Crea una funció `countEvenNumbers` que accepti un array de nombres.
2. Utilitza `filter` per seleccionar només els nombres parells.
3. La funció ha de retornar el nombre d’elements parells trobats.

<details>
<summary> <strong style="color: #006A67">Solució: </strong> </summary>

```javascript
function countEvenNumbers(array) {
  let evenNumbers = array.filter(function (number) {
    return number % 2 === 0;
  });
  return evenNumbers.length;
}

// Exemple d'ús
console.log(countEvenNumbers([1, 2, 3, 4, 5, 6])); // Sortida: 3
```

**Explicació:** `filter` selecciona només els nombres parells de l'array i `evenNumbers.length` retorna la quantitat d’elements en aquest nou array.

 </details>

### Exercici 6: Convertir Preus amb IVA

Escriu una funció que afegeixi un 21% d’IVA a cada preu d’un array i retorni un nou array amb els preus finals.

**Instruccions:**

1. Crea una funció `addIVA` que accepti un array de preus.
2. Utilitza `map` per afegir un 21% a cada preu.
3. La funció ha de retornar un nou array amb els preus actualitzats.

<details>
<summary> <strong style="color: #006A67">Solució: </strong> </summary>

```javascript
function addIVA(prices) {
  return prices.map(function (price) {
    return price * 1.21;
  });
}

// Exemple d'ús
console.log(addIVA([100, 200, 300])); // Sortida: [121, 242, 363]
```

**Explicació:** `map` recorre cada element de l’array `prices` i retorna el preu amb un 21% d’increment en un nou array.

</details>
