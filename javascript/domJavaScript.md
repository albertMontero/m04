# Tutorial: Manipulació Bàsica del DOM amb JavaScript

## 1. Accedir a elements per ID, Classe i Etiqueta

### Mètode 1: `getElementById()`

- **Descripció**: Selecciona un únic element en funció de l'atribut `id`.
- **Sintaxi**: `document.getElementById("elementId")`

```html
<!DOCTYPE html>
<html lang="ca">
  <head>
    <meta charset="UTF-8" />
    <title>Exemple getElementById</title>
  </head>
  <body>
    <h1 id="title">Hola, món!</h1>
    <button onclick="changeTitle()">Canvia el títol</button>

    <script>
      function changeTitle() {
        const titleElement = document.getElementById("title");
        titleElement.textContent = "Hola, JavaScript!";
      }
    </script>
  </body>
</html>
```

**Exemple 1**: Canvia el color de fons de l'element amb `id="title"` a blau quan es clica un botó.

<details>
<summary>Solució</summary>

```javascript
function changeTitleColor() {
  const titleElement = document.getElementById("title");
  titleElement.style.backgroundColor = "blue";
}
```

</details>

### Mètode 2: `getElementsByClassName()`

- **Descripció**: Retorna una HTMLCollection de tots els elements amb la classe especificada.
- **Sintaxi**: `document.getElementsByClassName("className")`

```html
<div class="message">Aquest és el missatge 1</div>
<div class="message">Aquest és el missatge 2</div>
<button onclick="highlightMessages()">Destaca Missatges</button>

<script>
  function highlightMessages() {
    const messages = document.getElementsByClassName("message");
    for (let i = 0; i < messages.length; i++) {
      messages[i].style.color = "red";
    }
  }
</script>
```

**Exemple 2**: Canvia la mida de lletra de tots els elements amb la classe `message` a 20px.

<details>
<summary>Solució</summary>

```javascript
function enlargeMessages() {
  const messages = document.getElementsByClassName("message");
  for (let i = 0; i < messages.length; i++) {
    messages[i].style.fontSize = "20px";
  }
}
```

</details>

### Mètode 3: `getElementsByTagName()`

- **Descripció**: Retorna una HTMLCollection de tots els elements amb el nom d'etiqueta especificat.
- **Sintaxi**: `document.getElementsByTagName("tagName")`

```html
<p>Aquest és el paràgraf 1</p>
<p>Aquest és el paràgraf 2</p>
<button onclick="changeParagraphs()">Canvia Paràgrafs</button>

<script>
  function changeParagraphs() {
    const paragraphs = document.getElementsByTagName("p");
    for (let i = 0; i < paragraphs.length; i++) {
      paragraphs[i].style.fontStyle = "italic";
    }
  }
</script>
```

**Exemple 3**: Fes que tots els elements `<p>` tinguin un color de text verd.

<details>
<summary>Solució</summary>

```javascript
function greenParagraphs() {
  const paragraphs = document.getElementsByTagName("p");
  for (let i = 0; i < paragraphs.length; i++) {
    paragraphs[i].style.color = "green";
  }
}
```

</details>

---

## 2. Ús de Selectors de Consulta

### Mètode 4: `querySelector()`

- **Descripció**: Selecciona el primer element que coincideix amb el selector CSS.
- **Sintaxi**: `document.querySelector("cssSelector")`

```html
<div id="container">
  <p class="text">Primer paràgraf</p>
  <p class="text">Segon paràgraf</p>
</div>
<button onclick="highlightFirstParagraph()">Destaca Primer Paràgraf</button>

<script>
  function highlightFirstParagraph() {
    const firstParagraph = document.querySelector("#container .text");
    firstParagraph.style.fontWeight = "bold";
  }
</script>
```

**Exemple 4**: Canvia el color del text del primer paràgraf dins del `container` a taronja.

<details>
<summary>Solució</summary>

```javascript
function colorFirstParagraph() {
  const firstParagraph = document.querySelector("#container .text");
  firstParagraph.style.color = "orange";
}
```

</details>

### Mètode 5: `querySelectorAll()`

- **Descripció**: Retorna una NodeList de tots els elements que coincideixen amb el selector CSS.
- **Sintaxi**: `document.querySelectorAll("cssSelector")`

```html
<ul>
  <li class="item">Element 1</li>
  <li class="item">Element 2</li>
  <li class="item">Element 3</li>
</ul>
<button onclick="underlineItems()">Subratlla Elements</button>

<script>
  function underlineItems() {
    const items = document.querySelectorAll(".item");
    items.forEach((item) => (item.style.textDecoration = "underline"));
  }
</script>
```

**Exemple 5**: Canvia el color de fons de tots els elements amb la classe `item` a gris clar.

<details>
<summary>Solució</summary>

```javascript
function grayItems() {
  const items = document.querySelectorAll(".item");
  items.forEach((item) => (item.style.backgroundColor = "lightgray"));
}
```

</details>

## 3. Gestionar Esdeveniments amb Funcions en JavaScript

Què és un esdeveniment?

Els esdeveniments són coses que succeeixen al sistema que estàs programant: el sistema produeix (o "dispara") un senyal d'algun tipus quan es produeix un esdeveniment i proporciona un mecanisme pel qual es pot prendre una acció automàticament (és a dir, un codi en execució) quan es produeix l'esdeveniment. Els esdeveniments es desenvolupen dins de la finestra del navegador i solen adjuntar-se a un element específic que hi resideix. Pot ser un únic element, un conjunt d'elements, el document HTML carregat a la pestanya actual o tota la finestra del navegador. Hi ha molts tipus diferents d'esdeveniments que poden ocórrer.

Per exemple:

- L'usuari selecciona, fa clic o passa el cursor per sobre d'un determinat element.
- L'usuari tria una tecla del teclat.
- L'usuari canvia la mida o tanca la finestra del navegador.
- S'acaba de carregar una pàgina web.
- S'envia un formulari.
- Un vídeo es reprodueix, es posa en pausa o s'acaba.
- Es produeix un error.

Teniu una llista a sota els esdeveniments més importants.

Per reaccionar davant d'un esdeveniment, podeu associar un gestor d'esdeveniments. Aquest és un bloc de codi (normalment una funció JavaScript que creeu vosaltres com a programador) que s'executa quan s'activa l'esdeveniment. Quan aquest bloc de codi es defineix per executar-se en resposta a un esdeveniment, diem que estem registrant un gestor d'esdeveniments.

**Nota**: els gestors o controladors d'esdeveniments de vegades s'anomenen listeners d'esdeveniments; són pràcticament intercanviables per als nostres propòsits, tot i que en sentit estricte, funcionen junts. El listener escolta l'esdeveniment que passa i el controlador és el codi que s'executa en resposta al fet que passa.

---

<details>
<summary style="font-size: 1.2em">
Llista dels tipus d'events més importants i comuns en JavaScript per treballar amb el DOM:
</summary>

> 1.  **click**: Activat quan l'usuari fa clic en un element.
> 2.  **dblclick**: Activat quan es fa doble clic en un element.
> 3.  **mousedown**: Activat quan es prem un botó del ratolí sobre un element.
> 4.  **mouseup**: Activat quan es deixa anar un botó del ratolí sobre un element.
> 5.  **mousemove**: Activat quan es mou el ratolí sobre un element.
> 6.  **mouseover**: Activat quan el ratolí entra a l'àrea d'un element.
> 7.  **mouseout**: Activat quan el ratolí surt de l'àrea d'un element.
> 8.  **input**: Activat quan es modifica el contingut d'un element d'entrada, com un `<input>` o `<textarea>`.
> 9.  **change**: Activat quan el valor d'un element canvia (ex. en elements com `<input>`, `<select>`, `<textarea>`).
> 10. **focus**: Activat quan un element guanya el focus, com en fer clic dins d'un camp de text.
> 11. **blur**: Activat quan un element perd el focus.
> 12. **keydown**: Activat quan es prem una tecla del teclat.
> 13. **keyup**: Activat quan es deixa anar una tecla del teclat.
> 14. **keypress**: Activat quan es manté una tecla (en desús, millor utilitzar `keydown` o `keyup`).
> 15. **submit**: Activat quan es fa clic al botó de submit d'un formulari.
> 16. **reset**: Activat quan es fa clic al botó de reset d'un formulari.
> 17. **load**: Activat quan una pàgina o element (com una imatge) s'ha carregat completament.
> 18. **unload**: Activat quan l'usuari surt de la pàgina (en desús, millor usar altres mètodes per treballar amb canvis de pàgina).
> 19. **scroll**: Activat quan es fa scroll dins d'un element o de la finestra.
> 20. **resize**: Activat quan la mida de la finestra del navegador canvia.
> 21. **contextmenu**: Activat quan es fa clic amb el botó dret per obrir el menú contextual.
> 22. **drag**: Activat quan es comença a arrossegar un element.
> 23. **drop**: Activat quan es deixa anar un element arrossegat en un altre element.
> 24. **touchstart**: Activat quan es detecta un toc en pantalles tàctils.
> 25. **touchmove**: Activat quan es mou un dit sobre una pantalla tàctil.
> 26. **touchend**: Activat quan es deixa d'interactuar amb una pantalla tàctil.

Aquests events són fonamentals per crear interfícies dinàmiques i interactives en aplicacions web, permetent respondre a accions de l'usuari i canvis en el DOM.

## </details>

### 1. **Assignar Gestors (handlers) d’Esdeveniments amb JavaScript en línia**

Una de les maneres més senzilles de gestionar un esdeveniment és utilitzar JavaScript en línia dins d’atributs HTML com `onclick`, `onmouseover`, `onchange`, etc. Aquest enfocament generalment no es recomana per a projectes més grans, però és útil per entendre la base.

**Exemple:**

```html
<button onclick="alert('Botó clicat!')">Fes clic aquí</button>
```

Aquí, l’atribut `onclick` executa directament una funció quan es fa clic en el botó. En aquest cas, mostra un missatge d’alerta amb el text "Botó clicat!" quan es fa clic en el botó.

---

### 2. **Utilitzar `addEventListener` per Gestionar Esdeveniments**

La manera més flexible de gestionar esdeveniments és utilitzar `addEventListener`. Aquest mètode permet afegir múltiples gestors d’esdeveniments a un sol element sense sobreescriure els gestors existents.

#### Sintaxi Bàsica

```javascript
element.addEventListener("tipusEsdeveniment", handler);
```

- `tipusEsdeveniment` és una cadena de text que representa l’esdeveniment, com ara `"click"`, `"input"`, `"mouseover"`, etc.
- `handler` és la funció que s’executarà quan es produeixi l’esdeveniment.

#### Exemple 1: Esdeveniment de Clic

Creem un botó que canvia el seu propi text quan es fa clic.

```html
<button id="changeTextButton">Fes clic aquí!</button>

<script>
  document
    .getElementById("changeTextButton")
    .addEventListener("click", function () {
      this.innerText = "Botó clicat!";
    });
</script>
```

Aquí, `addEventListener` s’utilitza per afegir un esdeveniment `click` al botó. La funció anònima (definida directament dins de `addEventListener`) canvia el text del botó mateix accedint-hi amb `this`.

#### Exemple 2: Esdeveniment d’Entrada (Input)

Podem crear un camp d’entrada de text que mostra una resposta en temps real actualitzant un altre element cada vegada que l’usuari escriu.

```html
<input type="text" id="nameInput" placeholder="Escriu el teu nom" />
<p id="nameOutput"></p>

<script>
  document.getElementById("nameInput").addEventListener("input", function () {
    document.getElementById("nameOutput").innerText = "Hola, " + this.value;
  });
</script>
```

L’esdeveniment `input` s’activa cada vegada que l’usuari escriu alguna cosa al camp d’entrada. Aquí, el paràgraf `nameOutput` s’actualitza amb "Hola, " seguit del valor actual de `nameInput`.

---

### 3. **Funcions Gestores d’Esdeveniments**

Fins ara hem fet servir funcions anònimes en les definicions dels listeners, peró els handlers d’esdeveniments poden definir-se per separat de la crida `addEventListener`, cosa que fa que el codi sigui més llegible i reutilitzable.

#### Exemple: botó de Clic amb una Funció Nominal

Creem un comptador que incrementa cada vegada que es fa clic en un botó.

```html
<button id="incrementButton">Clica per incrementar</button>
<p id="countDisplay">0</p>

<script>
  let count = 0;

  function incrementCount() {
    count++;
    document.getElementById("countDisplay").innerText = count;
  }

  document
    .getElementById("incrementButton")
    .addEventListener("click", incrementCount);
</script>
```

`incrementCount` és una funció nominal que incrementa la variable `count` i actualitza el nombre mostrat. La funció es passa com a referència a `addEventListener`, que la cridarà cada vegada que es faci clic en el botó.

---

### 4. **Objecte d’Esdeveniment**

L'objecte `event` en JavaScript proporciona informació sobre un esdeveniment que ocorre, com ara detalls sobre l'element que el provoca, les coordenades d'un clic o el valor d'un camp d'entrada. A continuació, alguns exemples d'event handlers que utilitzen l'objecte `event`.

---

#### Exemple 1: Accedint a Detalls de l'Esdeveniment amb un Click Event

Quan es fa clic en un botó, l'objecte `event` proporciona detalls com les coordenades del clic i l'element clicat. Aquest exemple mostra com accedir a aquests detalls mitjançant `event`.

**HTML:**

```html
<button id="myButton">Clica'm</button>
```

**JavaScript:**

```javascript
const button = document.getElementById("myButton");

function buttonHandler(event) {
  console.log("Botó clicat!");
  console.log("Tipus d'esdeveniment:", event.type); // Output: click
  console.log("Element clicat:", event.target); // Output: <button id="myButton">
  console.log("Posició X del ratolí:", event.clientX); // Coordenada X del ratolí
  console.log("Posició Y del ratolí:", event.clientY); // Coordenada Y del ratolí
}

button.addEventListener("click", buttonHandler);
```

---

#### Exemple 2: Keypress Event en un Input Field

Aquest exemple captura l'`keypress` event en un camp d'entrada per detectar quina tecla es prem. Mostra el valor de la tecla i el seu codi.

**HTML:**

```html
<input type="text" id="myInput" placeholder="Escriu alguna cosa" />
```

**JavaScript:**

```javascript
const inputField = document.getElementById("myInput");

inputField.onkeypress = function (event) {
  console.log("Tecla premuda:", event.key); // Output: Tecla premuda (ex: "a")
  console.log("Codi de tecla:", event.keyCode); // Output: Codi de tecla (ex: 65 per "A")
};
```

o

```javascript
const inputField = document.getElementById("myInput");

function keypressHandler(event) {
  console.log("Tecla premuda:", event.key); // Output: Tecla premuda (ex: "a")
  console.log("Codi de tecla:", event.keyCode); // Output: Codi de tecla (ex: 65 per "A")
}

inputField.addEventListener("keypress", keypressHandler);
```

<details>
<summary>Quina és la principal diferència entre aquests dos mètodes?</summary>

La diferència principal entre `addEventListener` i assignar directament `button.onclick` és la flexibilitat i la funcionalitat. Aquí tens una comparació dels dos enfocaments:

1. **Múltiples Event Listeners**:

   - **`addEventListener`**: Pots afegir múltiples listeners al mateix esdeveniment en un sol element. Per exemple, pots afegir diverses funcions perquè s'executin quan es clica un botó.
   - **`button.onclick`**: Només es pot assignar una funció a `onclick`. Si l'assignes diverses vegades, la darrera assignació sobreescriu les anteriors.

   ```javascript
   // Usant addEventListener
   button.addEventListener("click", functionOne);
   button.addEventListener("click", functionTwo); // Les dues funcions s'executen en fer clic

   // Usant onclick
   button.onclick = functionOne;
   button.onclick = functionTwo; // Només functionTwo s'executa en fer clic
   ```

2. **Eliminació de Event Listeners**:

   - **`addEventListener`**: Pots eliminar un event listener usant `removeEventListener`, sempre que facis referència a la mateixa funció.
   - **`button.onclick`**: Eliminar una funció assignada a `onclick` requereix assignar-li `null`, cosa que elimina qualsevol funció assignada prèviament.

   ```javascript
   // Afegir i eliminar amb addEventListener
   button.addEventListener("click", functionOne);
   button.removeEventListener("click", functionOne); // functionOne eliminada

   // Afegir i "eliminar" amb onclick
   button.onclick = functionOne;
   button.onclick = null; // Neteja l'assignació d'onclick
   ```

3. **Opcions d'Esdeveniment**:

   - **`addEventListener`**: Proporciona opcions com `once` (executar només una vegada), `capture` (executar durant la fase de captura) i `passive` (millora el rendiment per esdeveniments de desplaçament i de tacte).
   - **`button.onclick`**: No admet cap d'aquestes opcions. Només assigna una funció a l'esdeveniment `onclick`.

4. **Pràctica Recomanada**:
   - **`addEventListener`** es recomana generalment perquè és més versàtil i permet un maneig d'esdeveniments més avançat.
   - **`button.onclick`** és més senzill i funciona bé per esdeveniments únics on no necessites les funcionalitats addicionals d'`addEventListener`.

En resum, `addEventListener` ofereix més flexibilitat, especialment quan es treballa amb interaccions complexes o diverses funcions en el mateix esdeveniment, mentre que `button.onclick` és un enfocament senzill, adequat per a un ús únic.

</details>

#### Exemple 3: Form Submit Event

Quan es fa el submit d'un formulari, pots utilitzar el `submit` event per evitar l'acció per defecte i gestionar-lo amb JavaScript. En aquest exemple, es prevé l'enviament real del formulari i es mostra el valor de l'input.

**HTML:**

```html
<form id="myForm">
  <input type="text" name="username" placeholder="Nom d'usuari" />
  <button type="submit">Enviar</button>
</form>
```

**JavaScript:**

```javascript
const form = document.getElementById("myForm");

function formSubmitHandler(event) {
  event.preventDefault(); // Evita que el formulari s'enviï realment
  console.log("Formulari enviat amb les següents dades:");
  console.log("Valor de l'input:", form.elements["username"].value);
}

form.addEventListener("submit", formSubmitHandler);
```

---

#### Exemple 4: Mouseover Event

Aquest exemple utilitza el `mouseover` event en un element per obtenir informació sobre la posició del ratolí quan passa per sobre d'un element. S'imprimeixen les coordenades del ratolí en relació a la pàgina.

**HTML:**

```html
<div
  id="myBox"
  style="width: 200px; height: 200px; background-color: lightblue;"
>
  Passa el ratolí per aquí
</div>
```

**JavaScript:**

```javascript
const box = document.getElementById("myBox");

function mouseoverHandler(event) {
  console.log("Mouseover event en l'element:", event.target);
  console.log("Posició X del ratolí:", event.pageX);
  console.log("Posició Y del ratolí:", event.pageY);
}

box.addEventListener("mouseover", mouseoverHandler);
```

---

#### Exemple 5: Change Event en un Dropdown

Aquest exemple detecta canvis en un menú desplegable (`dropdown`) i obté el nou valor seleccionat per l'usuari.

**HTML:**

```html
<select id="myDropdown">
  <option value="opcio1">Opció 1</option>
  <option value="opcio2">Opció 2</option>
  <option value="opcio3">Opció 3</option>
</select>
```

**JavaScript:**

```javascript
const dropdown = document.getElementById("myDropdown");

function changeHandler(event) {
  console.log("Valor del dropdown canviat:");
  console.log("Nou valor:", event.target.value);
}

dropdown.addEventListener("change", changeHandler);
```

---

#### Exemple 6: Input Event en un Text Field

L'`input` event es dispara cada vegada que el valor d'un input de text canvia, permetent actualitzacions en temps real. Aquest exemple mostra el valor actualitzat cada vegada que l'usuari escriu.

**HTML:**

```html
<input type="text" id="myTextField" placeholder="Escriu alguna cosa" />
```

**JavaScript:**

```javascript
const textField = document.getElementById("myTextField");

function inputHandler(event) {
  console.log("Valor de l'input canviat a:", event.target.value);
}

textField.addEventListener("input", inputHandler);
```

---

### 5. **Eliminar gestors d’Esdeveniments**

De vegades pot ser útil eliminar un Gestor d’esdeveniments després que s’hagi utilitzat. Això es pot fer amb `removeEventListener`. Per eliminar un Gestor d’esdeveniments, la funció ha de definir-se com una funció nominal, no com una funció anònima.

#### Exemple: eliminar un Gestor d’Esdeveniments

Aquest exemple afegeix un esdeveniment de clic per incrementar un comptador i després l’elimina després de tres clics.

```html
<button id="limitedButton">Només 3 clics!</button>
<p id="clickLimit">Clics restants: 3</p>

<script>
  let clickCount = 0;

  function countClicks() {
    clickCount++;
    document.getElementById("clickLimit").innerText =
      "Clics restants: " + (3 - clickCount);

    if (clickCount >= 3) {
      document
        .getElementById("limitedButton")
        .removeEventListener("click", countClicks);
      document.getElementById("clickLimit").innerText =
        "Ja no es poden fer més clics!";
    }
  }

  document
    .getElementById("limitedButton")
    .addEventListener("click", countClicks);
</script>
```

`countClicks` s’executa cada vegada que es fa clic en el botó, actualitzant `clickCount` i el text de visualització. Després de tres clics, `removeEventListener` elimina `countClicks`, de manera que els clics posteriors no tenen cap efecte.

---

### Event Listeners i Accés als Elements Parent i Child

En JavaScript, els event listeners ens permeten respondre a interaccions de l'usuari com clics, pulsacions de teclat o accions de hover. Quan treballem amb el DOM, és habitual necessitar accedir als elements al voltant del target de l'event (l'element que ha desencadenat l'event), incloent-hi elements pare i fill. Vegem com treballar amb aquestes relacions dins d'un event listener.

#### Afegir un Event Listener

Per afegir un event listener, utilitzem el mètode `addEventListener`. Per exemple:

**HTML:**

```html
<button id="myButton">Clica'm!</button>
```

**JavaScript:**

```javascript
const button = document.querySelector("#myButton");
button.addEventListener("click", function (event) {
  console.log("Botó clicat!");
});
```

Aquí, quan es fa clic al botó amb `id` `myButton`, la funció dins de `addEventListener` s'executa, mostrant "Botó clicat!" a la consola.

#### Accedint a l'Element Target

L'objecte `event`, que es passa a la funció, conté una propietat anomenada `target`, que fa referència a l'element que ha activat l'event. Pots fer servir `target` per accedir directament a l'element que ha generat l'event:

**HTML:**

```html
<button id="myButton">Clica'm!</button>
```

**JavaScript:**

```javascript
button.addEventListener("click", function (event) {
  console.log(event.target); // Mostra l'element del botó
});
```

#### Accedint a Elements Pare

Per accedir al pare del target de l'event, utilitza `event.target.parentElement`. Això és útil quan vols fer canvis a l'element que conté el target:

**HTML:**

```html
<div class="parent">
  <button id="myButton">Clica'm!</button>
</div>
```

**JavaScript:**

```javascript
const button = document.querySelector("#myButton");
button.addEventListener("click", function (event) {
  const parent = event.target.parentElement;
  parent.style.backgroundColor = "lightblue"; // Canvia el color de fons del pare
});
```

També pots encadenar `parentElement` per pujar més amunt en la jerarquia i accedir al avi o altres elements superiors si cal.

#### Accedint a Elements Fill

Si vols accedir als fills de l'element target, pots fer servir `querySelector` o `querySelectorAll` sobre `event.target`:

**HTML:**

```html
<div class="container">
  <button id="myButton">Clica'm!</button>
  <div class="child-class">Sóc un fill</div>
</div>
```

**JavaScript:**

```javascript
const button = document.querySelector("#myButton");
button.addEventListener("click", function (event) {
  const child = event.target.parentElement.querySelector(".child-class");
  if (child) {
    child.style.color = "red"; // Canvia el color del text del fill
  }
});
```

Aquí, `.child-class` és el nom de classe d'un element fill dins de `container`. Això només funcionarà si `.child-class` és un fill directe o un fill en cascada del `parentElement`.

### Exemple: accedint Tant a l'Element Pare com al Fill

Considerem la següent estructura HTML:

**HTML:**

```html
<div class="parent">
  <button class="myButton">Fes clic aquí</button>
  <div class="child">Sóc un fill</div>
</div>
```

**JavaScript:**

```javascript
const button = document.querySelector(".myButton");
button.addEventListener("click", function (event) {
  const parent = event.target.parentElement;
  parent.style.border = "2px solid green"; // Accedeix i estilitza el pare

  const child = parent.querySelector(".child");
  if (child) {
    child.style.fontWeight = "bold"; // Accedeix i estilitza el fill
  }
});
```

En aquest exemple, quan es fa clic al botó, la vora del `div` pare i el pes de la font del `div` fill canvien. Això demostra com accedir i modificar tant elements pare com fill des d'un event listener.

### Exemple: accedint a Germans (Siblings) d'un Element Target

També pots accedir als germans d'un element dins d'un event listener. Això és útil quan vols modificar altres elements en el mateix nivell de jerarquia que el target.

**HTML:**

```html
<ul>
  <li class="list-item">Item 1</li>
  <li class="list-item">Item 2</li>
  <li class="list-item">Item 3</li>
</ul>
```

**JavaScript:**

```javascript
const listItem = document.querySelectorAll(".list-item");
listItem.forEach((item) => {
  item.addEventListener("click", function (event) {
    const sibling = event.target.nextElementSibling; // Agafa el germà següent
    if (sibling) {
      sibling.style.color = "blue"; // Canvia el color del text del germà següent
    }
  });
});
```

Aquí, `nextElementSibling` agafa l'element germà que segueix el target. També pots fer servir `previousElementSibling` per agafar el germà anterior.

### Exemple amb Múltiples Events en Elements Parentals

Suposem que volem que un event de clic en qualsevol botó dins d'un contenidor canviï el color de fons del contenidor. Això es pot aconseguir fent servir `addEventListener` sobre el pare i controlant el `event.target`:

**HTML:**

```html
<div class="container">
  <button>Botó 1</button>
  <button>Botó 2</button>
</div>
```

**JavaScript:**

```javascript
const container = document.querySelector(".container");
container.addEventListener("click", function (event) {
  if (event.target.tagName === "BUTTON") {
    event.currentTarget.style.backgroundColor = "lightcoral";
  }
});
```

Aquí, `event.currentTarget` fa referència al contenidor, mentre que `event.target` s'usa per verificar que l'event ha estat activat per un `button`. Aquest patró és útil per aplicar accions dinàmiques en grups d'elements dins d'un mateix contenidor.

Amb aquestes tècniques, podem navegar la jerarquia del DOM de manera dinàmica i crear interfícies d'usuari més reactives i versàtils.

## Emmagatzematge Local (Local Storage) en JavaScript

L’`emmagatzematge local` o `localStorage` en JavaScript és una eina que ens permet guardar dades en el navegador de l'usuari. Això és útil per recordar informació entre sessions o guardar configuracions d'usuari que necessitem mantenir disponibles mentre l'usuari utilitza la nostra aplicació. Les dades emmagatzemades en `localStorage` es mantenen fins que es borren explícitament, fins i tot si l'usuari tanca el navegador.

### Conceptes Bàsics d'Ús

El `localStorage` guarda les dades en format de text (claus i valors). Per utilitzar-lo, cal:

- Assignar un valor a una clau mitjançant el mètode `setItem`.
- Recuperar el valor associat a una clau amb el mètode `getItem`.
- Esborrar una clau amb el mètode `removeItem`.
- Esborrar totes les dades emmagatzemades amb `clear`.

### Exemple 1: Guardar i Recuperar un Nom d'Usuari

En aquest exemple, guardarem el nom d'un usuari a `localStorage` quan es faci clic a un botó, i el mostrarem a la pantalla cada vegada que l'usuari torni a carregar la pàgina.

**HTML:**

```html
<div>
  <input type="text" id="username" placeholder="Escriu el teu nom" />
  <button id="saveButton">Guardar Nom</button>
  <p id="greeting"></p>
</div>
```

**JavaScript:**

```javascript
const usernameInput = document.querySelector("#username");
const saveButton = document.querySelector("#saveButton");
const greeting = document.querySelector("#greeting");

// Guardar el nom d'usuari en localStorage
saveButton.addEventListener("click", function () {
  const username = usernameInput.value;
  localStorage.setItem("username", username);
  showGreeting();
});

// Mostrar un missatge de benvinguda si hi ha un nom guardat
function showGreeting() {
  const savedUsername = localStorage.getItem("username");
  if (savedUsername) {
    greeting.textContent = `Hola, ${savedUsername}!`;
  }
}

// Carregar el nom guardat al carregar la pàgina
document.addEventListener("DOMContentLoaded", showGreeting);
```

Amb aquest codi, quan l'usuari introdueix el seu nom i fa clic a "Guardar Nom", el nom es guarda a `localStorage`. Quan l'usuari torna a visitar la pàgina, es mostra un missatge de benvinguda amb el nom guardat.

---

### Exemple 2: Comptador de Visites

Aquest exemple mostra com mantenir un comptador que s'incrementa cada vegada que l'usuari visita la pàgina.

**HTML:**

```html
<div>
  <p id="visitCount">Visites: 0</p>
</div>
```

**JavaScript:**

```javascript
const visitCountDisplay = document.querySelector("#visitCount");

// Incrementa el comptador de visites i actualitza localStorage
function incrementVisitCount() {
  let visitCount = localStorage.getItem("visitCount");
  visitCount = visitCount ? parseInt(visitCount) + 1 : 1;
  localStorage.setItem("visitCount", visitCount);
  visitCountDisplay.textContent = `Visites: ${visitCount}`;
}

// Carregar el comptador al carregar la pàgina
document.addEventListener("DOMContentLoaded", incrementVisitCount);
```

Aquest codi incrementa el comptador de visites cada vegada que es carrega la pàgina. El valor es manté en `localStorage` i es carrega i mostra cada vegada que l'usuari torna a visitar la pàgina.

---

### Exemple 3: Guardar i Recuperar Preferències d'Estil

En aquest exemple, permetrem a l'usuari seleccionar un color de fons per a la pàgina i el guardarem a `localStorage` perquè es mantingui entre sessions.

**HTML:**

```html
<div>
  <label for="colorPicker">Tria un color de fons:</label>
  <input type="color" id="colorPicker" />
</div>
```

**JavaScript:**

```javascript
const colorPicker = document.querySelector("#colorPicker");

// Guardar el color seleccionat en localStorage
colorPicker.addEventListener("input", function () {
  const selectedColor = colorPicker.value;
  localStorage.setItem("backgroundColor", selectedColor);
  document.body.style.backgroundColor = selectedColor;
});

// Carregar el color guardat al carregar la pàgina
document.addEventListener("DOMContentLoaded", function () {
  const savedColor = localStorage.getItem("backgroundColor");
  if (savedColor) {
    document.body.style.backgroundColor = savedColor;
    colorPicker.value = savedColor; // Actualitza el color seleccionat
  }
});
```

Amb aquest codi, l'usuari pot seleccionar un color de fons per a la pàgina. Aquest color es guarda a `localStorage` i es torna a aplicar automàticament cada vegada que es torna a visitar la pàgina.

---

### Exemple 4: Esborrar Dades de `localStorage`

És important que els usuaris també puguin esborrar les seves dades si ho desitgen. En aquest exemple, afegirem un botó per esborrar totes les dades guardades a `localStorage`.

**HTML:**

```html
<div>
  <button id="clearStorageButton">Esborrar Dades Guardades</button>
</div>
```

**JavaScript:**

```javascript
const clearStorageButton = document.querySelector("#clearStorageButton");

// Esborrar totes les dades de localStorage
clearStorageButton.addEventListener("click", function () {
  localStorage.clear();
  alert("Les dades guardades s'han esborrat.");
  location.reload(); // Refresca la pàgina per actualitzar els canvis
});
```

Quan es fa clic al botó "Esborrar Dades Guardades", totes les dades de `localStorage` s’esborren i es refresca la pàgina per reflectir els canvis.

---

### Consideracions de Seguretat i Compatibilitat

- `localStorage` només pot guardar dades en format de text, així que quan guardem dades complexes, com ara objectes, cal fer servir `JSON.stringify` per convertir-los a text i `JSON.parse` per recuperar-los.
- Tingues en compte que `localStorage` no és segur per guardar dades sensibles com contrasenyes o informació confidencial, ja que qualsevol persona amb accés al navegador pot veure aquestes dades.
- `localStorage` té un límit d'emmagatzematge (normalment de 5MB per domini), suficient per a la majoria de configuracions d'usuari i preferències bàsiques.

---

## Exercicis

Les solucions donades estan implementades amb handlers online. Mireu d'adaptar-les amb event listeners.

### Exercici 1

Crea un formulari amb un camp d'entrada de text i un botó. Quan l'usuari clica el botó, mostra el contingut del camp de text en un paràgraf nou a sota del formulari.

<details>
<summary>Solució</summary>

```html
<form>
  <input type="text" id="inputText" placeholder="Escriu aquí" />
  <button type="button" onclick="displayText()">Mostra Text</button>
</form>
<p id="output"></p>

<script>
  function displayText() {
    const inputText = document.getElementById("inputText").value;
    const output = document.getElementById("output");
    output.textContent = inputText;
  }
</script>
```

</details>

---

### Exercici 2

Crea una taula amb tres files i dues columnes. Afegeix un botó que canviï el color de fons de totes les cel·les a groc quan es clica.

<details>
<summary>Solució</summary>

```html
<table id="myTable">
  <tr>
    <td>Fila 1, Columna 1</td>
    <td>Fila 1, Columna 2</td>
  </tr>
  <tr>
    <td>Fila 2, Columna 1</td>
    <td>Fila 2, Columna 2</td>
  </tr>
  <tr>
    <td>Fila 3, Columna 1</td>
    <td>Fila 3, Columna 2</td>
  </tr>
</table>
<button onclick="highlightTable()">Canvia Color</button>

<script>
  function highlightTable() {
    const cells = document.querySelectorAll("#myTable td");
    cells.forEach((cell) => (cell.style.backgroundColor = "yellow"));
  }
</script>
```

</details>

---

### Exercici 3

Crea una llista desordenada amb cinc elements de llista (`<li>`). Afegeix un botó que esborri el darrer element de la llista cada cop que es clica.

<details>
<summary>Solució</summary>

```html
<ul id="myList">
  <li>Element 1</li>
  <li>Element 2</li>
  <li>Element 3</li>
  <li>Element 4</li>
  <li>Element 5</li>
</ul>
<button onclick="removeLastItem()">Esborra darrer element</button>

<script>
  function removeLastItem() {
    const list = document.getElementById("myList");
    list.removeChild(list.lastElementChild);
  }
</script>
```

</details>

---

### Exercici 4

Crea una secció amb diversos paràgrafs. Afegeix un botó que faci que el text de tots els paràgrafs aparegui en majúscules.

<details>
<summary>Solució</summary>

```html
<div id="textSection">
  <p>Paràgraf 1</p>
  <p>Paràgraf 2</p>
  <p>Paràgraf 3</p>
</div>
<button onclick="uppercaseText()">Majúscules</button>

<script>
  function uppercaseText() {
    const paragraphs = document.querySelectorAll("#textSection p");
    paragraphs.forEach(
      (paragraph) => (paragraph.style.textTransform = "uppercase")
    );
  }
</script>
```

</details>

---

### Exercici 5

Crea un botó que afegeixi una nova imatge dins d'un `div` cada cop que es clica. Utilitza una URL d'imatge de mostra.

<details>
<summary>Solució</summary>

```html
<div id="imageContainer"></div>
<button onclick="addImage()">Afegeix Imatge</button>

<script>
  function addImage() {
    const imageContainer = document.getElementById("imageContainer");
    const newImage = document.createElement("img");
    newImage.src = "https://via.placeholder.com/100";
    imageContainer.appendChild(newImage);
  }
</script>
```

</details>

---

### Exercici 6

Crea un text i un botó que permeti alternar entre mostrar i amagar el text cada cop que es clica.

<details>
<summary>Solució</summary>

```html
<p id="toggleText">Aquest és el text que es mostrarà i amagarà.</p>
<button onclick="toggleVisibility()">Mostra/Amaga Text</button>

<script>
  function toggleVisibility() {
    const text = document.getElementById("toggleText");
    text.style.display = text.style.display === "none" ? "block" : "none";
  }
</script>
```

</details>

---

### Exercici 7

Crea tres botons amb diferents colors (vermell, verd i blau). Cada botó ha de canviar el color de fons de la pàgina al seu color quan es clica.

<details>
<summary>Solució</summary>

```html
<button onclick="changeColor('red')">Vermell</button>
<button onclick="changeColor('green')">Verd</button>
<button onclick="changeColor('blue')">Blau</button>

<script>
  function changeColor(color) {
    document.body.style.backgroundColor = color;
  }
</script>
```

</details>

---

### Exercici 8

Crea un paràgraf i un botó que afegeixi un text nou al final del paràgraf cada cop que es clica.

<details>
<summary>Solució</summary>

```html
<p id="text">Això és un text inicial.</p>
<button onclick="appendText()">Afegeix Text</button>

<script>
  function appendText() {
    const paragraph = document.getElementById("text");
    paragraph.textContent += " Text afegit.";
  }
</script>
```

</details>

---

### Exercici 9

Crea un formulari amb un camp de text i un botó de "Reset". Quan es clica el botó, el camp de text ha de tornar a estar buit.

<details>
<summary>Solució</summary>

```html
<form>
  <input type="text" id="textInput" placeholder="Escriu alguna cosa" />
  <button type="button" onclick="resetInput()">Reset</button>
</form>

<script>
  function resetInput() {
    document.getElementById("textInput").value = "";
  }
</script>
```

</details>

---

## Exercicis de accés a parent i chlid

### Exercici 1: Canviar el Color de Fons del Pare

Escriu un JavaScript que faci que, quan es faci clic a un botó dins d'un `div`, canviï el color de fons d'aquest `div`.

**HTML:**

```html
<div class="container">
  <button id="myButton">Fes clic aquí</button>
</div>
```

**Instruccions:** Canvia el color de fons del `div` amb classe `container` quan es faci clic al botó.

<details>
<summary>Solució</summary>

```javascript
const button = document.querySelector("#myButton");
button.addEventListener("click", function (event) {
  const parent = event.target.parentElement;
  parent.style.backgroundColor = "lightblue";
});
```

</details>

---

### Exercici 2: Amagar un Element Fill

Escriu un JavaScript que faci que, quan es faci clic en un botó, el text dins del `div` amb la classe `child` es faci invisible (canvia `display` a `none`).

**HTML:**

```html
<div class="parent">
  <button id="hideButton">Amaga el text</button>
  <div class="child">Aquest és el text que vull amagar.</div>
</div>
```

**Instruccions:** Amaga el `div` amb classe `child` quan es faci clic al botó amb `id` `hideButton`.

<details>
<summary>Solució</summary>

```javascript
const hideButton = document.querySelector("#hideButton");
hideButton.addEventListener("click", function (event) {
  const child = event.target.parentElement.querySelector(".child");
  child.style.display = "none";
});
```

</details>

---

### Exercici 3: Canviar el Text d'un Element Fill

Escriu un JavaScript que faci que, quan es faci clic en un botó, el text d'un element `p` dins del mateix `div` canviï a "Text canviat!".

**HTML:**

```html
<div class="box">
  <button id="changeTextButton">Canvia el text</button>
  <p class="text">Aquest és el text original.</p>
</div>
```

**Instruccions:** Canvia el text dins de l'element `p` a "Text canviat!" quan es faci clic al botó.

<details>
<summary>Solució</summary>

```javascript
const changeTextButton = document.querySelector("#changeTextButton");
changeTextButton.addEventListener("click", function (event) {
  const textParagraph = event.target.parentElement.querySelector(".text");
  textParagraph.textContent = "Text canviat!";
});
```

</details>

---

### Exercici 4: Afegir una Classe a un Element Pare

Escriu un JavaScript que faci que, quan es faci clic en un botó dins d'un `div`, s'afegeixi la classe `highlight` al `div` pare.

**HTML:**

```html
<div class="container">
  <button id="highlightButton">Destaca el contenidor</button>
</div>
```

**Instruccions:** Afegeix la classe `highlight` al `div` amb classe `container` quan es faci clic al botó.

<details>
<summary>Solució</summary>

```javascript
const highlightButton = document.querySelector("#highlightButton");
highlightButton.addEventListener("click", function (event) {
  const parent = event.target.parentElement;
  parent.classList.add("highlight");
});
```

</details>

---

### Exercici 5: Comptar Elements Fill

Escriu un JavaScript que, quan es faci clic en un botó, mostri a la consola el nombre d'elements `li` dins d'un `ul`.

**HTML:**

```html
<div class="list-container">
  <button id="countButton">Compta els elements</button>
  <ul>
    <li>Element 1</li>
    <li>Element 2</li>
    <li>Element 3</li>
  </ul>
</div>
```

**Instruccions:** Mostra a la consola el nombre d'elements `li` dins del `ul` quan es faci clic al botó.

<details>
<summary>Solució</summary>

```javascript
const countButton = document.querySelector("#countButton");
countButton.addEventListener("click", function (event) {
  const listItems = event.target.parentElement.querySelectorAll("ul li");
  console.log("Nombre d'elements li:", listItems.length);
});
```

</details>

---

### Exercici 6: Accedir a un Germà Següent i Canviar el seu Text

Escriu un JavaScript que faci que, quan es faci clic a un element `li`, el text del germà següent canviï a "Text canviat!".

**HTML:**

```html
<ul>
  <li class="item">Element 1</li>
  <li class="item">Element 2</li>
  <li class="item">Element 3</li>
</ul>
```

**Instruccions:** Canvia el text del germà següent de l'element `li` que ha rebut el clic.

<details>
<summary>Solució</summary>

```javascript
const items = document.querySelectorAll(".item");
items.forEach((item) => {
  item.addEventListener("click", function (event) {
    const sibling = event.target.nextElementSibling;
    if (sibling) {
      sibling.textContent = "Text canviat!";
    }
  });
});
```

</details>

---
