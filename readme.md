
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
- [Kodstruktur](#kodstruktur)
  - [Shorthand-notation (Kompaktare CSS)](#shorthand-notation-kompaktare-css)
- [Grundläggande sidstruktur](#grundläggande-sidstruktur)



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