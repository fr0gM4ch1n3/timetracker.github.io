### **HTTP-Request simulieren mit  `of`  und  `delay`**

#### **Ziel:**

-   Simuliere einen API-Aufruf mit RxJS-Operatoren.
-   Verwende  `of`  zur Emission von Testdaten.
-   Verzögere die Antwort künstlich mit  `delay`.
-   Zeige die Daten in einer Angular-Komponente an.

----------

### **Schritte:**

1.  **API-Daten simulieren:**
    
    -   Verwende RxJS  `of`  zum Erstellen eines Observables, das JSON-ähnliche Testdaten enthält.
    -   Nutze  `delay`, um die Antwortzeit zu simulieren.
2.  **Observable abonnieren:**
    
    -   Abonniere den Observable in der Komponente, um die simulierten Daten zu erhalten.
    -   Zeige die Daten in der UI an.
3.  **HTML und Styling:**
    
    -   Zeige die Daten übersichtlich an (z. B. als Liste).

----------

### **Beispielcode**

**Service:  `data.service.ts`**

    import { Injectable } from '@angular/core';
    import { of } from 'rxjs';
    import { delay } from 'rxjs/operators';
    
    @Injectable({
      providedIn: 'root'
    })
    export class DataService {
      // Simuliere API-Daten
      getData() {
        const mockData = [
          { id: 1, name: 'Alice', role: 'Developer' },
          { id: 2, name: 'Bob', role: 'Designer' },
          { id: 3, name: 'Charlie', role: 'Manager' }
        ];
    
        // Simuliere einen HTTP-Request mit einer Verzögerung von 2 Sekunden
        return of(mockData).pipe(delay(2000));
      }
    }

----------

**Component:  `data.component.ts`**

    import { Component, OnInit } from '@angular/core';
    import { DataService } from './data.service';
    
    @Component({
      selector: 'app-data',
      templateUrl: './data.component.html',
      styleUrls: ['./data.component.css']
    })
    export class DataComponent implements OnInit {
      data: any[] = []; // Daten aus dem Service
      isLoading = true; // Ladezustand
    
      constructor(private dataService: DataService) {}
    
      ngOnInit() {
        // Simulierten HTTP-Request abonnieren
        this.dataService.getData().subscribe({
          next: (response) => {
            this.data = response; // Daten speichern
            this.isLoading = false; // Ladezustand beenden
          },
          error: (err) => {
            console.error('Fehler beim Laden der Daten:', err);
            this.isLoading = false;
          }
        });
      }
    }

----------

**Template:  `data.component.html`**

    <div class="data-container">
      <h1>Simulierte API-Daten</h1>
    
      <!-- Ladeanzeige -->
      <p *ngIf="isLoading" class="loading">Daten werden geladen...</p>
    
      <!-- Datenanzeige -->
      <ul *ngIf="!isLoading">
        <li *ngFor="let item of data">
          <strong>{{ item.name }}</strong> - {{ item.role }}
        </li>
      </ul>
    </div>

----------

**Styles:  `data.component.css`**

    .data-container {
      font-family: Arial, sans-serif;
      max-width: 400px;
      margin: 20px auto;
      text-align: center;
    }
    
    h1 {
      color: #2196f3;
    }
    
    .loading {
      color: #ff9800;
      font-weight: bold;
    }
    
    ul {
      list-style: none;
      padding: 0;
    }
    
    li {
      background-color: #f1f1f1;
      margin: 5px 0;
      padding: 10px;
      border-radius: 5px;
    }

----------

### **Erklärung:**

1.  **Service (`DataService`):**
    
    -   `of(mockData)`: Erstellt einen Observable, der die simulierten Daten emittiert.
    -   `.pipe(delay(2000))`: Fügt eine Verzögerung von 2 Sekunden hinzu, um einen echten API-Aufruf nachzuahmen.
2.  **Komponente (`DataComponent`):**
    
    -   `isLoading`: Wird verwendet, um den Ladezustand in der UI zu steuern.
    -   `subscribe`: Holt die Daten vom Observable und speichert sie in der Komponente.
3.  **UI:**
    
    -   Zeigt eine Ladeanzeige (`Daten werden geladen...`) an, bis die Daten geladen sind.
    -   Nach dem Laden wird die Liste der Daten angezeigt.

----------

### **Erweiterungen:**

-   **Fehlerbehandlung:**  Zeige eine Fehlermeldung, wenn der Request fehlschlägt.
-   **Styling:**  Füge Hover-Effekte für die Listenelemente hinzu.
-   **Pagination:**  Simuliere eine Paginierung der Daten.

Möchtest du eine dieser Erweiterungen ausprobieren? 😊
