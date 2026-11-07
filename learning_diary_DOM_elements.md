-- Task 1

- what is the "document" variable in javascript?

const heading = document.querySelector("h1");
heading.textContent = "Hello!";

Das document ist ein Objekt eines DOM (Struktur einer Website).
DOM ist die Darstellung einer Website als "Baum".
Hier: <body>
  <h1>Hallo</h1>
  <p>Willkommen!</p>
</body>

vereinfacht:
document
└── body
    ├── h1
    └── p

> HTML liefert den Inhalt, das DOM macht ihn für JavaScript zugänglich und veränderbar.
> mit zB button = document.getElementById("submitBtn") greife ich auf den Button von HTML im JS zu.

- what can I do with the "document" variable?

zB: Ein Element erstellen und einfügen:
const neuerAbsatz = document.createElement("p");
neuerAbsatz.textContent = "Hallo!";
document.body.append(neuerAbsatz);

> document ist der Einstiegspunkt um Elemente zu finden, zu ändern, zu erstellen oder auf Ereignisse zu reagieren.

Das document wird vom Browser bereit gestellt. Ich muss es nicht selbst definieren.

Das document verändere ich nicht sondern nur Elemente im document.
Ich sehe document nicht als Eintrag in meinem JS/HTML Code > "Der Browser stellt es bereit, wenn er deine Webseite lädt".

- erstell mir Code, der die Farbe der Überschrift h1 verändert:
<h1>Meine Überschrift</h1>

<script>
  const ueberschrift = document.querySelector("h1");
  ueberschrift.style.color = "red";
</script>

> Ich brauche document, wenn ich mit JavaScript mit der geladenen Webseite arbeiten will. Nur so kann es HTML Elemente einbinden. Aber wenn mein Script nichts an der Webseite ändert, brauch ich es nicht.

-- Task 2

- How can I access the list "myList" in the html file?

So könnte ich sie in JS auswählen:
const myList = document.getElementById("myList");
console.log(myList);

So könnte ich die Einträge der Liste auslesen:
const eintraege = myList.querySelectorAll("li");
eintraege.forEach(eintrag => console.log(eintrag.textContent));

> myList muss im HTML als ID gesetzt werden!
> (hier:  <ul id="myList">
        <li>Item 1</li>
        <li>Item 2</li>
        <li>Item 3</li>
>    </ul>)

- How can I change the list "myList" in the html file?

zB Eintrag hinzufügen "Banane":
const myList = document.getElementById("myList");

const neuerEintrag = document.createElement("li");
neuerEintrag.textContent = "Banane";
myList.append(neuerEintrag);

zB alles entfernen:
myList.replaceChildren();

> Änderungen betreffen die geladene Webseite! Es hat keinen Einfluss auf die dauerhafte HTML Datei. Nach einem Neuladen wird der ursprüngliche Inhalt angezeigt.

-- Task 3

- Which parameters of this DOM (button) element can be accessed from javascript?

>Hier im HTML definiert:
<button type="button" id="submitBtn">Submit</button>

Er hat die ID "submitBtn", den Typ "button" und zeigt den Text „Submit“ an.
In JS kann man viele Eigenschaften auslesen oder ändern.

Häufig verwendete Eigenschaften:

button.textContent – der angezeigte Text.
> Hier button.textContent = "Abschicken";
button.id – die ID des Buttons, 
> Hier "submitBtn".
button.type – seine Funktion: "button", "submit" oder "reset". 
> Hier ist es "button".
button.disabled – ob der Button deaktiviert ist.
zB: button.disabled =   true; deaktiviert ihn; 
                        false aktiviert ihn wieder.
button.classList – CSS-Klassen hinzufügen oder entfernen.
zB: button.classList.add("aktiv");
button.style – Inline-CSS ändern.
zB: button.style.backgroundColor = "lightblue";
zB: button.form – Zugriff auf das Formular, zu dem der Button gehört. 
> Hier ist es das Formular myForm.

- What do these parameters do?

> Hier: Er hat die ID "submitBtn", den Typ "button" und zeigt den Text „Submit“ an.

zB: Code im HTML, der die Hintergrundfarbe des "buttons" verändert:
<style>
        #submitBtn {
            background-color: lightblue;
        }
    </style>

zB: Code im script.js, ändert die Anzeige, wenn man auf den Button klickt:
    const button = document.getElementById("submitBtn");

    button.addEventListener("click", () => {
        button.textContent = "Abgeschickt!";
    });