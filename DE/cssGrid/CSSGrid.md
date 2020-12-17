# CSS-Grid in a nutshell

## Was ist CSSGrid?
CSSGrid ist ein Konzept in CSS, welches dem Entwickler erlaubt, das Layouting für eine Website ohne eigene Berechnungen im Styling durchführen zu müssen. 
Auch lassen sich mithilfe von CSSGrid unter Anderem Darstellungs-Elemente wie Informationskarten mit relativ wenig Aufwand im Vergleich zu anderen Konzepten erstellen.

In CSSGrid wird (im besten Fall) jedes angezeigte HTML-Element einem Bereich (im Nachfolgenden area genannt) zugeordnet, im folgenden Beispiel sind dies 'header', 'main', 'aside' & 'footer':

## Was sind die Vor- und Nachteile von CSSGrid?

| Vorteile                                                      | Nachteile                                             |
| ------------------------------------------------------------- |-------------------------------------------------------| 
| schnell und unkompliziert umgesetzt                           | Änderungen im Nachhinein unter Umständen zeitaufwändig|
| keine Berechnungen im Style-Sheet nötig                       | Anpassungen zur Nutzung im IE11 erforderlich          |
| eigene Einheit zur Festlegung der Höhe/ Breite einer Area     |                                                       |


Nun da das erste Grid definiert ist, fahren wir damit fort, dieses mehr und mehr auf eventuelle Anforderungen anzupassen. <br>
Eine solche Anforderung könnte zum Beispiel sein, dass die Grids nucht unmittelbar miteinander verbunden sind. Auch zu diesem
 Zweck bietet CSSGrid ein Attribut, welches uns erlaubt eine sogenante Gap zwischen den einzelnen Areas anzuwenden: grid-gap


## Der Weg zur ersten View mit CSSGrid

Im nachfolgenden Beispiel wird eine HTML-Page erzeugt die Schritt für Schritt um CSSGrid-Attribute erweitert wird. Ziel dieses Vorgehens ist es, aufzuzeigen, wie schnell und einfach eine übersichtliche Anzeige mithilfe von CSSGrid erzeugt werden kann. Alle folgenden Beispiele in diesem Markdown-Dokument sind in CSS-Grid umgesetzt und nicht als Foto eingefügt.  

### Das Grundgerüst in HTML



```html 
<div id="my-beautiful-webside">
    <header class="header">HEADER</header>
    <main class="main">MAIN</main>
    <aside class="aside">ASIDE</aside>
    <footer class="footer" >FOOTER</footer>
</div>
``` 

### Ergebnis:

<style>
    #my-beautiful-webside1{
        max-width: 500px;
        max-height: 500px;
        background-color: lightgrey;
        color: black;
    }
</style>
<div id="my-beautiful-webside1">
    <header class="header1">HEADER</header>
    <main class="main1">MAIN</main>
    <aside class="aside1">ASIDE</aside>
    <footer class="footer1" >FOOTER</footer>
</div>


## Erweiterung um Hintergrundfarben und die Zuweisung von Area-Attributen

In diesem Code-Snippet wird unser HTML um eine Hintergrundfarbe für jedes enthaltene HTML-Element erweitert. Dieses Vorgehen soll dabei helfen nachfolgende Anpassungen optisch besser nachvollziehen zu können. 
Des Weiteren werden an dieser Stelle bereits die Grid-Area-Zuweisungen der Elemente durchgeführt. 
Mit dem zugehörigen css (die background-color ist optional):

```css
.header{
    grid-area: header;
    background-color: lightcoral;
}

.main{
    grid-area: main;
    background-color: lightskyblue;
}

.aside{
    grid-area: aside;
    background-color: lemonchiffon;
}

.footer{
    grid-area: footer;
    background-color: lightgreen;
}
```

### Ergebnis:
<style>
#my-beautiful-webside2{
    max-width: 500px;
    max-height: 500px;
    color: black;
}

.header2{
    grid-area: header;
    background-color: lightcoral;
}

.main2{
    grid-area: main;
    background-color: lightskyblue;
}

.aside2{
    grid-area: aside;
    background-color: lemonchiffon;
}

.footer2{
    grid-area: footer;
    background-color: lightgreen;
}
</style>
<div id="my-beautiful-webside2">
    <header class="header2">HEADER</header>
    <main class="main2">MAIN</main>
    <aside class="aside2">ASIDE</aside>
    <footer class="footer2" >FOOTER</footer>
</div>

Die grid-area Zuweisungen allein bewirken leider jedoch nichts, um die zuvor definierten areas nutzen zu können ist es notwendig, der Webside die display-Eigenschaft 'grid' zuzuweisen und eine Vorlage (im Nachfolgenden template genannt) inklusive Reihen und Spaltengröße zu definieren: 

```css
#my-beautiful-webside {
    display: grid;
    color:black;
    grid-template-areas: "header header header" "main main aside" "footer footer footer";
    grid-template-rows: auto;
    grid-template-columns: auto;
}
```

<style>
#my-beautiful-webside {
    display: grid;
    max-width: 500px;
    max-height: 500px;
    color:black;
    grid-template-areas: "header header header" "main main aside" "footer footer footer";
    grid-template-rows: auto;
    grid-template-columns: auto;
}

.header{
    grid-area: header;
    background-color: lightcoral;
}

.main{
    grid-area: main;
    background-color: lightskyblue;
}

.aside{
    grid-area: aside;
    background-color: lemonchiffon;
}

.footer{
    grid-area: footer;
    background-color: lightgreen;
}
</style>
<div id="my-beautiful-webside">
    <header class="header">HEADER</header>
    <main class="main">MAIN</main>
    <aside class="aside">ASIDE</aside>
    <footer class="footer" >FOOTER</footer>
</div>

## Grid-Gap

## Eigene Einheit zur Definition der Größe des Elements

Besonders an CSS-Grid ist, dass es mit einer eigenen Maßeinheit zur Größenbestimmung der Elemente kommt. Mithilfe dee Einheit 'fr' (fractionals) ist es nun nicht mehr nötig die Größe eines Elements über 'calc()'-Berechnungen durchzuführen, stattdessen wird das Grid in Fractions aufgeteilt.
Mithilfe der Fractions ist es nun möglich, das zuvor generierte neun-Area-große Grid in sechs Areas darzustellen.

### Ergebnis
<style>
#my-beautiful-webside-fr {
    display: grid;
    max-width: 500px;
    max-height: 500px;
    color:black;
    grid-template-areas: "header header" "main aside" "footer footer";
    grid-template-rows: 1fr 1fr 1fr;
    grid-template-columns: 1fr 1fr 1fr;
}

.header-fr{
    grid-area: header;
    background-color: lightcoral;
}

.main-fr{
    grid-area: main;
    background-color: lightskyblue;
}

.aside-fr{
    grid-area: aside;
    background-color: lemonchiffon;
}

.footer-fr{
    grid-area: footer;
    background-color: lightgreen;
}
</style>
<div id="my-beautiful-webside-fr">
    <header class="header-fr">HEADER</header>
    <main class="main-fr">MAIN</main>
    <aside class="aside-fr">ASIDE</aside>
    <footer class="footer-fr" >FOOTER</footer>
</div>

## Fazit

Mit wenigen Zeilen Code und Styling entsteht so schon ein Grid welches die horizontale und vertikale Anzeige in neun Felder aufteilt und deren Inhalt nach den Angaben in CSS aufteilt.
