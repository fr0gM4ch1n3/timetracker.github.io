
### **Timer mit  `Observable`**

Ziel:

-   Erstelle einen Timer, der jede Sekunde einen Zählerwert emittiert.
-   Zeige die Werte in einer Angular-Komponente an.
-   Begrenze die Ausgaben auf 10 Sekunden.

----------

#### **Schritte:**

1.  **Angular-Projekt vorbereiten:**
    
    -   Erstelle eine neue Angular-Komponente:  `TimerComponent`.
2.  **RxJS-Operatoren verwenden:**
    
    -   Nutze  `interval`  zum Emittieren von Werten.
    -   Begrenze die Ausgabe mit  `take(10)`.
    -   Transformiere die Werte mit  `map`, sodass sie in der UI besser lesbar sind.
3.  **HTML und CSS:**
    
    -   Zeige die aktuellen Zählerwerte in der UI an.

----------

#### **Beispielcode**

**Component:  `timer.component.ts`**

    import { Component, OnInit } from '@angular/core';
    import { interval, map, take } from 'rxjs';
    
    @Component({
      selector: 'app-timer',
      templateUrl: './timer.component.html',
      styleUrls: ['./timer.component.css']
    })
    export class TimerComponent implements OnInit {
      timerValues: number[] = []; // Array, um Zählerwerte zu speichern
    
      ngOnInit() {
        // Erstelle den Timer-Observable
        interval(1000) // Emittiere jede Sekunde
          .pipe(
            take(10), // Begrenze auf 10 Werte
            map(value => value + 1) // Transformation: Start bei 1 statt 0
          )
          .subscribe({
            next: (value) => {
              this.timerValues.push(value); // Werte im Array speichern
            },
            complete: () => {
              console.log('Timer abgeschlossen!');
            }
          });
      }
    } 

----------

**Template:  `timer.component.html`**

    <div class="timer-container">
      <h1>RxJS Timer</h1>
      <p>Die aktuellen Timer-Werte:</p>
      <ul>
        <li *ngFor="let value of timerValues">{{ value }} Sekunden</li>
      </ul>
    </div>

----------

**Styles:  `timer.component.css`**

    .timer-container {
      text-align: center;
      font-family: Arial, sans-serif;
    }
    
    h1 {
      color: #4caf50;
    }
    
    ul {
      list-style: none;
      padding: 0;
    }
    
    li {
      background-color: #f0f0f0;
      margin: 5px 0;
      padding: 10px;
      border-radius: 5px;
      display: inline-block;
      min-width: 100px;
      text-align: center;
    }

----------

#### **Erklärung:**

1.  **RxJS Operators:**
    
    -   `interval(1000)`: Erstellt einen Observable, der jede Sekunde einen Wert emittiert.
    -   `take(10)`: Begrenzt die Ausgabe auf 10 Werte.
    -   `map(value => value + 1)`: Transformiert den Startwert von  `0`  zu  `1`.
2.  **Subscription:**
    
    -   Im  `subscribe`  wird jeder neue Wert im Array  `timerValues`  gespeichert.
    -   Die UI wird automatisch aktualisiert, weil Angular Change Detection aktiv ist.
3.  **Kompletter Timer:**
    
    -   Nach 10 Sekunden wird die Subscription automatisch abgeschlossen (`complete`  wird aufgerufen).

----------

Das Ergebnis ist ein einfacher Timer, der die Werte jede Sekunde aktualisiert und nach 10 Sekunden stoppt. Möchtest du weitere Funktionen hinzufügen, wie z. B. Start/Stopp-Buttons? 😊
