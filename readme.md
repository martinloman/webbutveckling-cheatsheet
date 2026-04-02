
# Webbutveckling 1: Cheat Sheet

Detta dokument täcker grunderna i HTML5 och CSS3 för dig som bygger din första webbplats.

Innehållsförteckning:
- [HTML5 – struktur & innehåll](#html5--struktur--innehåll)
  - [Grundläggande taggar](#grundläggande-taggar)
  - [Semantiska taggar](#semantiska-taggar)
  - [Exempel: Menystruktur](#exempel-menystruktur)
  - [Formulär & Inputs](#formulär--inputs)
  - [Tabeller](#tabeller)
  - [Ikoner (FontAwesome)](#ikoner-fontawesome)
- [CSS – Design & Stil](#css--design--stil)
  - [Selektorer](#selektorer)
  - [Färger & Fonter](#färger--fonter)
  - [Tabeller](#tabeller-1) 
  - [Listor](#listor)
  - [Bakgrund & Gradients](#bakgrund--gradients)  
  - [Dekorativa effekter](#dekorativa-effekter)
  - [Box-modellen](#box-modellen) 
  - [Display & Position](#display--position)
- [Layout & Interaktivitet](#layout--interaktivitet)
  - [Flexbox](#flexbox)   
  - [Media Queries (Responsivitet)](#media-queries-responsivitet)
  - [Pseudo-klasser](#pseudo-klasser)
  - [Animationer](#animationer)
    - [Loopande animationer](#loopande-animationer)
- [Kodstruktur](#kodstruktur)
  - [Shorthand-notation (Kompaktare CSS)](#shorthand-notation-kompaktare-css)
- [Grundläggande sidstruktur](#grundläggande-sidstruktur)
- [Javascript](#javascript)
  - [Visa/dölj element med JavaScript](#visadolj-element-med-javascript)
  - [Ändra CSS-stil med JavaScript](#andra-css-stil-med-javascript)
  - [Lägg till element med JavaScript](#lagg-till-element-med-javascript)
  - [Event Listeners](#event-listeners)
  
  - [DOM-manipulation](#dom-manipulation)
  - [Enkel hamburgarmeny (HTML + CSS + JavaScript)](#enkel-hamburgarmeny-html--css--javascript)
  - [Anropa ett API](#anropa-ett-api)
    - [JSON](#json)



## HTML5 – struktur & innehåll

### Grundläggande taggar
* `<h1>` till `<h6>`: Rubriker. Använd endast en `<h1>` per sida (sidans huvudtitel).
* `<p>`: Paragraf för vanlig brödtext.
* `<a href="url">Länktext</a>`: Skapar en klickbar länk.
* `<ul>` & `<li>`: Punktlista (Unordered List).
* `<ol>` & `<li>`: Numrerad lista (Ordered List).
* `<img src="bild.jpg" alt="Beskrivning">`: Visar en bild. `alt`-texten är obligatorisk för tillgänglighet.
* `<div>`: Generisk block-container utan egen semantisk betydelse. Används för att gruppera och styla element.
* `<span>`: Generisk inline-container. Används för att styla delar av text inne i ett stycke.

### Semantiska taggar 
Använd dessa istället för `<div>` för att berätta för webbläsaren vad innehållet faktiskt är:
| Tagg | Beskrivning |
| :--- | :--- |
| `<header>` | Sidans huvud (ofta logotyp och toppmeny). |
| `<nav>` | Innehåller navigeringslänkar. |
| `<main>` | Sidans unika huvudinnehåll (ska bara finnas en per sida). |
| `<section>` | Grupperar relaterat innehåll (t.ex. "Om oss"-sektionen). |
| `<article>` | En fristående del som kan läsas självständigt (t.ex. ett blogginlägg). |
| `<footer>` | Sidfot (kontaktinfo, copyright, sociala medier). |

### Exempel: Menystruktur
En klassisk uppbyggnad för en navigationsmeny:
```html
<header>
  <nav class="menu">
    <ul>
      <li><a href="index.html" class="menu-item">Hem</a></li>
      <li><a href="portfolio.html" class="menu-item">Portfolio</a></li>
      <li><a href="kontakt.html" class="menu-item">Kontakt</a></li>
    </ul>
  </nav>
</header>
```

### Formulär & Inputs
| Typ | HTML-exempel | Användning |
| :--- | :--- | :--- |
| **Text** | `<input type="text">` | Namn eller korta fritextsvar. |
| **E-post** | `<input type="email">` | Validerar att det finns ett `@` i texten. |
| **Lösenord** | `<input type="password">` | Döljer tecknen som skrivs. |
| **Nummer** | `<input type="number">` | Tillåter endast siffror. |
| **Checkbox** | `<input type="checkbox">` | Kryssruta för att välja flera alternativ. |
| **Knapp** | `<button type="submit">` | Skickar iväg formulärets data. |

Alla dessa input-taggar kan också ha attribut som `name`, `id`, `placeholder` och `required` för att förbättra funktionaliteten och användarupplevelsen.

Alla inputs ska ligga i ett `<form>`-element:
```html
<form action="/submit" method="post">
  <input type="text" name="namn" placeholder="Ditt namn" required>
  <input type="email" name="email" placeholder="Din e-post" required>
  <button type="submit">Skicka</button>
</form>
```

### Tabeller
Tabeller används för att visa data i rader och kolumner. De består av `<table>`, `<tr>` (table row), `<th>` (table header) och `<td>` (table data).

```html
<table>
  <tr>
    <th>Produkt</th>
    <th>Pris</th>
  </tr>
  <tr>
    <td>Skor</td>
    <td>500 kr</td>
  </tr>
  <tr>
    <td>Jacka</td>
    <td>1200 kr</td>
  </tr>
</table>
```

Tabeller kan också innehålla `<thead>`, `<tbody>` och `<tfoot>` för att strukturera data ytterligare, men det är inte obligatoriskt.

### Ikoner (FontAwesome)
1. Klistra in din Kit-länk (från FontAwesome) i HTML-dokumentets `<head>`.
2. Använd taggen: `<i class="fa-solid fa-house"></i>`.


## CSS – Design & Stil

### Selektorer
* `h1 { ... }` : **Tagnamn** (Väljer alla h1-element).
* `.menu-item { ... }` : **Klass** (Väljer alla element med `class="menu-item"`).
* `#header { ... }` : **ID** (Väljer elementet med `id="header"`. Ska bara finnas ett!).
* `.menu a { ... }` : **Kombinerad** (Väljer alla länkar som ligger *inuti* klassen `.menu`).

### Färger & Fonter
**Färg:** `color: #333;` (Hex), `rgb(255, 0, 0)` eller `hsl(0, 100%, 50%)`.

**Font:** `font-family: Arial, sans-serif;` (Först försöker den använda Arial, om det inte finns, använder den en generisk sans-serif).

**Textstorlek:** `font-size: 16px;` (px), `1.5em` (1.5 gånger förälderns storlek) eller `120%` (120% av förälderns storlek).

**Textegenskaper:**
| Egenskap | Exempel | Beskrivning |
| :--- | :--- | :--- |
| `text-align` | `text-align: center;` | Justering: `left`, `center`, `right`. |
| `text-decoration` | `text-decoration: underline;` | Understrykning. `none` tar bort understrykning från länkar. |
| `text-transform` | `text-transform: uppercase;` | Skiftläge: `uppercase`, `lowercase`, `capitalize`. |

**Google Fonts:**
1. Hämta länk på [fonts.google.com](https://fonts.google.com).
2. Klistra in `@import url('https://fonts.googleapis.com/css2?...');` i CSS-filen.
3. CSS: `font-family: 'Roboto', sans-serif;`.

### Tabeller
Tabeller kan stylas med CSS, tex:
```css
table {
  border-collapse: collapse;
}

th, td {
  border: 1px solid #ddd;
  padding: 8px;
}
```

### Listor
Listor kan också stylas, t.ex.:
```css
ul {
  list-style-type: disc;
  padding-left: 20px;
}
li {
  margin-bottom: 5px;
}
```


### Bakgrund & Gradients
**Bakgrundsfärg** 
```css 
background-color: lightblue;
```
**Bakgrundsbild** 
```css
background-image: url('bild.jpg');
background-size: cover;
```
**Gradients** 
```css
background: linear-gradient(to right, red, orange);
```
*Verktyg:* [cssgradient.io](https://cssgradient.io) för att generera snygga övergångar.

### Dekorativa effekter
**Rundade hörn**
```css
border-radius: 8px;   /* Alla hörn */
border-radius: 50%;   /* Cirkel (på kvadratiska element) */
```

**Skuggor**
```css
box-shadow: 2px 4px 8px rgba(0, 0, 0, 0.2);  /* Skugga på element */
text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.4); /* Skugga på text */
```

### Box-modellen
Box-modellen består av: 

* **Content** (innehåll), 
* **Padding** (inneravstånd), 
* **Border** (kant) och 
* **Margin** (ytteravstånd till närliggande element). 

![Box model](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Box_model/boxmodel.png)

**Storlek:**
| Egenskap | Beskrivning |
| :--- | :--- |
| `width` / `height` | Sätter elementets bredd och höjd. |
| `max-width` | Elementet växer inte bredare än detta värde. Bra för läsbarhet på stora skärmar. |
| `min-height` | Elementet är aldrig kortare än detta värde. |

**box-sizing**

Som standard räknas `width` och `height` bara på *content* — padding och border läggs till utanpå, vilket gör det svårt att förutsäga den faktiska storleken. Med `box-sizing: border-box` ingår padding och border i det angivna måttet istället.
```css
* {
  box-sizing: border-box; /* Rekommenderas globalt */
}
```

Värden kan anges individuellt eller i shorthand-form.

**Detaljerat:**
```css
  padding-top: 10px; 
  padding-right: 20px;
  padding-bottom: 10px;
  padding-left: 20px;
```

**Shorthand:** 

Sätt flera värden på en rad. (Tänk klockan: Topp, Höger, Botten, Vänster)
```css
  padding: 10px 20px 15px 5px;
```

```css
  padding: 10px 20px;
  /*** 10px = Topp & Botten
    20px = Höger & Vänster **/
```

```css
  padding: 10px;
  /*** 10px = alla sidor **/
```
**Centrering:** `margin: auto;` (Centrerar ett block-element horisontellt (i sin förälder) om det har en fast `width`).

**margin-left: auto;**
Skapar så mycket utrymme som möjligt till vänster, vilket i praktiken flyttar elementet så långt höger som möjligt. Detsamma gäller `margin-right: auto;` som flyttar elementet så långt vänster som möjligt.


### Display & Position
Alla element har en `display`-egenskap som styr hur de beter sig i layouten, och en `position`-egenskap som styr hur de placeras på sidan.
| Värde | Beskrivning |
| :--- | :--- |
| `display: block` | Tar upp hela bredden, börjar på ny rad (t.ex. `<div>`, `<h1>`). |
| `display: inline` | Tar bara platsen texten behöver, kan ej ha bredd/höjd (t.ex. `<a>`, `<span>`). |
| `display: inline-block` | Som inline, men du kan sätta bredd och höjd. |
| `display: none` | Gömmer elementet helt (det tar ingen plats). |
| **Position:** | |
| `static` | Standardläget. Följer det naturliga flödet. |
| `relative` | Flyttas baserat på sin originalplats utan att påverka andra element. T.ex. `top: 10px; left: 20px;` |
| `absolute` | Placeras exakt i förhållande till närmaste förälder som är `relative`. Om ingen sådan finns, placeras den i förhållande till dokumentet. |
| `sticky` | Fastnar vid kanten (t.ex. `top: 0;`) när man scrollar förbi. |

---

## Layout & Interaktivitet

### Flexbox
Läggs på föräldern (containern) för att styra barnen.
```css
.container {
  display: flex;
  justify-content: center; /* Horisontell centrering */
  align-items: center;     /* Vertikal centrering */
  gap: 20px;               /* Mellanrum mellan elementen */
}
```
Läs mer om Flexbox på [CSS-Tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/).

### Media Queries (Responsivitet)
Används för att ändra designen beroende på skärmbredd (t.ex. för mobiler).
```css
@media (max-width: 600px) {
  /* Denna kod körs bara på skärmar som är 600px eller smalare */
  .menu ul {
    flex-direction: column; /* Stapla menyvalen på varandra */
  }
}
```

### Pseudo-klasser
| Pseudo-klass | Beskrivning |
| :--- | :--- |
| `:hover` | När muspekaren vilar över elementet. |
| `:nth-child(n)` | Väljer barn nummer *n* (t.ex. `:nth-child(2)` för andra elementet). |
| `:not(selektor)` | Väljer alla element utom de som matchar selektorn (t.ex. `:not(.aktiv)`). |

Exempel: 
```css
a:hover {
  color: blue;
}
```

### Animationer
**1. Transition (mjuk övergång):**
`transition: background-color 0.3s ease;` (Sätts på grundelementet för att animera ändringar).
Detta används ofta tillsammans med `:hover` för att skapa en smidig effekt.

**Exempel:**
```css
button {
  background-color: red;
  transition: background-color 0.3s ease;
}
button:hover {
  background-color: green;
}
``` 
**2. Keyframes (avancerad rörelse):**
```css
@keyframes slide-in {
  from { transform: translateX(-100%); opacity: 0; }
  to { transform: translateX(0); opacity: 1; }
}

.hero-box {
  animation: slide-in 1s forwards;
}
```

Keyframes kan också anges med % för att skapa mer komplexa animationer:
```css 
@keyframes bounce {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-20px); }
}
```
#### Loopande animationer

Keyframes kan också användas för att skapa loopande animationer t.ex.
```css
animation: bounce 2s infinite;
```

## Kodstruktur
### Shorthand-notation (Kompaktare CSS)
Många egenskaper kan skrivas på en rad för att spara plats:

**Background**
```css
background: #fff url('img.jpg') no-repeat center;
/* Färg, bild, upprepning och position i en rad * /
```

**Font**
```css
font: italic bold 16px/1.5 'Roboto', sans-serif;
/* Stil, vikt, storlek/linjehöjd och familj i en rad * /
```

**Border**
```css
border: 2px solid red;
/* Tjocklek, stil och färg i en rad * /
```

## Grundläggande sidstruktur
Här är en enkel mall för en HTML-sida som inkluderar en header med navigationsmeny, ett main-innehåll och en footer. Den länkar också till en extern CSS-fil för styling.
```html
<!DOCTYPE html>
<html lang="sv">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Min Första Webbplats</title>
  <link rel="stylesheet" href="styles.css"> </head>
<body>
<header>
  <nav class="menu">
    <ul>
      <li><a href="index.html" class="menu-item">Hem</a></li>
      <li><a href="portfolio.html" class="menu-item">Portfolio</a></li>
      <li><a href="kontakt.html" class="menu-item">Kontakt</a></li>
    </ul>
  </nav>
</header>
<main>
<h1>Välkommen till min webbplats!</h1>
<p>Detta är en enkel sida byggd med HTML och CSS.</p>
</main>
<footer>
  <p>&copy; 2023 Min Webbplats. Alla rättigheter förbehållna.</p>
</footer>
</body>
</html>
```

# Javascript
För att lägga till interaktivitet på din webbplats kan du använda JavaScript. Här är ett enkelt exempel som visar hur man kan ändra texten i ett element när en knapp klickas:

HTML
```html

  <p id="text">Detta är en enkel sida med JavaScript-interaktivitet.</p>
  <button onclick="changeText()">Klicka mig!</button>

```
JavaScript
```javascript
function changeText() {
  document.getElementById("text").innerHTML = "Texten har ändrats!";
}
```

### Visa/dölj element med JavaScript
Man kan visa/dölja element genom att ändra deras `display`-egenskap. Här är ett exempel.

HTML
```html
  <div id="element" style="display: none;">
    Detta element är dolt tills du klickar på knappen.
  </div>
  <button onclick="toggleElement()">Visa/Dölj Element</button>
```
JavaScript
```javascript
function toggleElement() {
  const element = document.getElementById("element");
  if (element.style.display === "none") {
    element.style.display = "block";
  } else {
    element.style.display = "none";
  }
}
```

### Ändra CSS-stil med JavaScript
Du kan också ändra CSS-stil direkt från JavaScript. Här är ett exempel som änd  rar bakgrundsfärgen på en div när en knapp klickas:

```html
  <div id="colorBox" style="width: 100px; height: 100px; background-color: red;"></div>
  <button onclick="changeColor()">Ändra Färg</button>
```

```javascript
function changeColor() {
  document.getElementById("colorBox").style.backgroundColor = "blue";
}
```

### Lägg till element med JavaScript
Du kan skapa och lägga till nya element i DOM:en (Document Object Model) med JavaScript. Här är ett exempel som lägger till en ny paragraf när en knapp klickas:

```html
  <div id="container"></div>
  <button onclick="addParagraph()">Lägg till Paragraf</button>
```

```javascript
function addParagraph() {
  const container = document.getElementById("container");
  const newParagraph = document.createElement("p");
  newParagraph.textContent = "Detta är en ny paragraf.";
  // Lägg till den nya paragrafen i containern
  container.appendChild(newParagraph);
}
```

### Event Listeners
Istället för att använda `onclick`-attributet i HTML kan du lägga till event listeners i JavaScript för att hålla din HTML renare. Här är ett exempel:

```html
  <button id="myButton">Klicka mig!</button>
```

```javascript
const myButton = document.getElementById("myButton");
myButton.addEventListener("click", function() {
  alert("Knappen klickades!");
});
```

#### Vanliga event-typer
| Event-typ | Beskrivning |
| :--- | :--- |
| `click` | När ett element klickas. |
| `mouseover` | När pekaren flyttas över ett element. |
| `mouseout` | När pekaren flyttas bort från ett element. |
| `keydown` | När en tangent på tangentbordet trycks ned. |
| `keyup` | När en tangent på tangentbordet släpps. |



### DOM-manipulation
DOM (Document Object Model) är en programmeringsgränssnitt som representerar HTML-dokumentet som en trädstruktur av noder. Med JavaScript kan du manipulera DOM för att ändra innehåll, struktur och stil på din webbplats dynamiskt. Här är några vanliga metoder för DOM-manipulation:  
| Metod | Beskrivning | Exempel |
| :--- | :--- | :--- |
| `document.getElementById(id)` | Hämtar ett element med det angivna ID:t. | `document.getElementById("menu")` |
| `document.querySelector(selector)` | Hämtar det första elementet som matchar CSS-selektorn. | `document.querySelector(".menu-item")` |
| `document.querySelectorAll(selector)` | Hämtar alla element som matchar CSS-selektorn. | `document.querySelectorAll("li")` |
| `element.textContent` | Ändrar eller hämtar textinnehållet i ett element. | `title.textContent = "Ny rubrik"` |
| `element.innerHTML` | Ändrar eller hämtar HTML-innehållet i ett element. | `box.innerHTML = "<strong>Hej</strong>"` |
| `element.style.property` | Ändrar en specifik CSS-egenskap för ett element. | `box.style.backgroundColor = "blue"` |
| `element.classList.add(className)` | Lägger till en CSS-klass på ett element. | `menu.classList.add("open")` |
| `element.classList.remove(className)` | Tar bort en CSS-klass från ett element. | `menu.classList.remove("open")` |
| `element.classList.toggle(className)` | Växlar en CSS-klass på ett element (lägger till om den inte finns, tar bort om den finns). | `menu.classList.toggle("open")` |
| `element.appendChild(newElement)` | Lägger till ett nytt element som barn till det angivna elementet. | `list.appendChild(newItem)` |
| `element.removeChild(childElement)` | Tar bort ett barn-element från det angivna elementet. | `list.removeChild(oldItem)` |
| `element.insertAdjacentHTML(position, html)` | Infogar HTML-kod på en specifik position i förhållande till elementet. `position` kan vara "beforebegin", "afterbegin", "beforeend", eller "afterend". | `card.insertAdjacentHTML("beforeend", "<p>Ny text</p>")` |


### Enkel hamburgarmeny (HTML + CSS + JavaScript)
Ett vanligt användningsområde för JavaScript är att skapa en interaktiv hamburgarmeny för mobilanpassade webbplatser.
Här är ett mycket enkelt exempel där menyn visas/döljs när man klickar på hamburgarikonen (`fa-bars`).

HTML
```html
<!-- Lägg i <head> för att kunna använda Font Awesome-ikoner -->
<script src="https://kit.fontawesome.com/your-kit-id.js" crossorigin="anonymous"></script>

<button id="menuToggle" class="menu-toggle" aria-label="Öppna meny">
  <i class="fa-solid fa-bars"></i>
</button>

<ul id="mobileMenu" class="mobile-menu">
  <li><a href="#">Hem</a></li>
  <li><a href="#">Om</a></li>
  <li><a href="#">Kontakt</a></li>
</ul>
```
CSS
```css
.menu-toggle {
  font-size: 24px;
  border: none;
  background: none;
  cursor: pointer;
}

.mobile-menu {
  display: none; /* Dölj menyn som standard */
  list-style: none;
  padding: 0;
  margin: 10px 0 0;
}
/* När "show" klassen läggs till, visas menyn */
.mobile-menu.show {
  display: block;
}
```
Javascript
```javascript
const menuToggle = document.getElementById("menuToggle");
const mobileMenu = document.getElementById("mobileMenu");

menuToggle.addEventListener("click", function() {
  mobileMenu.classList.toggle("show");
});
```

### Anropa ett API
För att hämta data från ett API (Application Programming Interface) kan du använda `fetch`-funktionen i JavaScript. Här är ett enkelt exempel som hämtar data från ett API och visar det på sidan:

HTML
```html
<div id="dataContainer"></div>
<button onclick="hamtaData()">Hämta Data</button>
```

JavaScript
```javascript
async function hamtaData() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json(); // Konvertera svaret till JSON

    // Gör något med datan, t.ex. visa den på sidan
    const container = document.getElementById('dataContainer');
    container.textContent = JSON.stringify(data);
  } catch (error) {
    console.error('Fel vid hämtning av data:', error);
  }
}
```

Koden ovan använder `async/await` för att hantera asynkrona operationer på ett mer läsbart sätt. När knappen klickas, anropas `hamtaData`-funktionen som gör en `fetch`-förfrågan till det angivna API:et, konverterar svaret till JSON och visar det i `dataContainer`-diven. Om det uppstår ett fel under hämtningen loggas det i konsolen.

#### JSON
JSON (JavaScript Object Notation) är ett lättviktigt format för att utbyta data. Det är lätt att läsa och skriva för både människor och maskiner. JSON används ofta i API:er för att skicka data mellan klient och server.

Ett objekt i JSON-format:
```json
{
  "name": "Alice",
  "age": 30,
  "city": "Stockholm"
}
```

En array i JSON-format:
```json
[
  {
    "name": "Alice",
    "age": 30,
    "city": "Stockholm"
  },
  {
    "name": "Bob",
    "age": 25,
    "city": "Göteborg"
  }
]
```

JSON kan ha objekt i objekt, arrayer i objekt, och så vidare, vilket gör det mycket flexibelt för att representera komplexa data.

Exempel:
```json
{
  "users": [
    {
      "name": "Alice",
      "age": 30,
      "city": "Stockholm"
    },
    {
      "name": "Bob",
      "age": 25,
      "city": "Göteborg"
    }
  ],
  "count": 2
}
```

För att hämta information från ett JSON-objekt i JavaScript, kan du använda punktnotation eller hakparenteser:
```javascript
const data = {
  "users": [
    {
      "name": "Alice",
      "age": 30,
      "city": "Stockholm"
    },
    {
      "name": "Bob",
      "age": 25,
      "city": "Göteborg"
    }
  ],
  "count": 2
};
console.log(data.users[0].name); // Output: Alice
console.log(data["users"][1]["city"]); // Output: Göteborg
```