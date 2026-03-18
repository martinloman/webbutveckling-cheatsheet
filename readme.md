
# Webbutveckling 1: Cheat Sheet

Detta dokument täcker grunderna i HTML5 och CSS3 för dig som bygger din första webbplats.



## HTML5 – Struktur & Innehåll

### Grundläggande Taggar
* `<h1>` till `<h6>`: Rubriker. Använd endast en `<h1>` per sida (sidans huvudtitel).
* `<p>`: Paragraf för vanlig brödtext.
* `<a href="url">Länktext</a>`: Skapar en klickbar länk.
* `<ul>` & `<li>`: Punktlista (Unordered List).
* `<ol>` & `<li>`: Numrerad lista (Ordered List).
* `<img src="bild.jpg" alt="Beskrivning">`: Visar en bild. `alt`-texten är obligatorisk för tillgänglighet.

### Semantiska Taggar (Ge sidan mening)
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

**Google Fonts:**
1. Hämta länk på [fonts.google.com](https://fonts.google.com).
2. Klistra in `@import url('https://fonts.googleapis.com/css2?...');` i CSS-filen.
3. CSS: `font-family: 'Roboto', sans-serif;`.

### Bakgrund & Gradients
* **Bakgrundsfärg:** `background-color: lightblue;`.
* **Bakgrundsbild:** `background-image: url('bild.jpg'); background-size: cover;`.
* **Gradients:** `background: linear-gradient(to right, red, orange);`.
    * *Verktyg:* [cssgradient.io](https://cssgradient.io) för att generera snygga övergångar.

### Box-modellen
Box-modellen består av: 

**Content** (innehåll), 
**Padding** (inneravstånd), 
**Border** (kant) och **Margin** (ytteravstånd). 

![Box model](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Box_model/boxmodel.png)

Värden kan anges individuellt eller i shorthand-form.

**Detaljerat:**
  `padding-top: 10px; padding-right: 20px; padding-bottom: 10px; padding-left: 20px;`

**Shorthand:** (Tänk klockan: Topp, Höger, Botten, Vänster)
  `padding: 10px 20px 15px 5px;`

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

Keyframes kan också användas för att skapa loopande animationer (t.ex. `animation: bounce 2s infinite;`).

## Kodstruktur
### Shorthand-notation (Kompaktare CSS)
Många egenskaper kan skrivas på en rad för att spara plats:
* **Background:** `background: #fff url('img.jpg') no-repeat center;`
* **Font:** `font: italic bold 16px/1.5 'Roboto', sans-serif;`
* **Border:** `border: 2px solid red;`

